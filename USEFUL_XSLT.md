# USEFUL XSLT

## Mapping filtrant

```xml
<?xml version="1.0" encoding="UTF-8"?>
<xsl:stylesheet version="1.0"
    xmlns:xsl="http://www.w3.org/1999/XSL/Transform">

    <xsl:output method="xml" indent="yes" encoding="UTF-8"/>

    <xsl:template match="/Projects">
        <Projects>
            <xsl:for-each select="Project[normalize-space(ErrorMessage)]">
                <Project>
                    <ProjectExternalID>
                        <xsl:value-of select="ProjectExternalID"/>
                    </ProjectExternalID>

                    <ErrorMessage>
                        <xsl:value-of select="ErrorMessage"/>
                    </ErrorMessage>

                    <Step>
                        <xsl:value-of select="Step"/>
                    </Step>
                </Project>
            </xsl:for-each>
        </Projects>
    </xsl:template>

</xsl:stylesheet>

```

## Accès valeurs

### variables

```xml
<xsl:param name="companyCode" />

<!-- puis appel: -->
<CompanyCode><xsl:value-of select="$companyCode" /></CompanyCode>

```

### Noeuds xml

```xml
<ProjectDescription><xsl:value-of select="DESC" /></ProjectDescription>
```


## Condition

```xml
    <xsl:variable name="execDateEff">
        <xsl:choose>
            <xsl:when test="string($runDate) != ''">
                <xsl:value-of select="$runDate" />
            </xsl:when>
            <xsl:otherwise>
                <xsl:value-of select="/Start/CTXT/DTEX" />
            </xsl:otherwise>
        </xsl:choose>
    </xsl:variable>
```

## Fonctions
```xml
<!-- Concat -->
<ProjectExternalID><xsl:value-of select="concat($cdetEtab,'_',CODE)" /></ProjectExternalID>

<!-- normalize-space -->
<xsl:variable name="at"   select="normalize-space(ANALYSIS_TYPE)"/>

<!-- substring -->
<xsl:value-of select="substring($jrnl,1,16)"/>

<!--format number -->
<xsl:value-of select="format-number(-1 * $amt, '0.00')"/>

<!-- format date -->
<xsl:value-of select="concat(substring($d,7,4), '-', substring($d,4,2), '-', substring($d,1,2))"/>
<!-- ou -->
<!-- FORMAT DATE dd/mm/yyyy -> yyyy-mm-dd -->
<xsl:template name="fmtDate">
    <xsl:param name="d"/>
    <xsl:choose>
        <xsl:when test="contains($d, '/')">
        <xsl:value-of select="concat(substring($d,7,4), '-', substring($d,4,2), '-', substring($d,1,2))"/>
        </xsl:when>
        <xsl:otherwise><xsl:value-of select="$d"/></xsl:otherwise>
    </xsl:choose>
</xsl:template>
<!-- appel -->
<zz1:ZZ1_BillingDate><xsl:call-template name="fmtDate"><xsl:with-param name="d" select="normalize-space(BILLING_DATE)"/></xsl:call-template></zz1:ZZ1_BillingDate>


<!-- type -->
<xsl:variable name="amt"  select="number(RESOURCE_AMOUNT)"/>
```

## Attributes
```xml
<AmountInTransactionCurrency>
    <xsl:attribute name="currencyCode"><xsl:value-of select="$CurrencyCode"/></xsl:attribute>
    <xsl:value-of select="format-number(-1 * $amt, '0.00')"/>
</AmountInTransactionCurrency>
```