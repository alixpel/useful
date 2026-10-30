# Useful CPI


## Content modifier


### date
${date:now:yyyy-MM-dd HH:mm:ss}
${date:now:yyyy-MM-dd'T'HH:mm:ss'Z'}
${date:now:yyyyMMdd'T'HH:mm:ss} # Outputs: 20211201T15:34:48
${date:now:yyyyMMdd'T'HH:mm:ss'Z'} # Outputs: 20211201T15:34:48Z
${date:now:yyyyMMdd} # Outputs: 20211201
${date:now:yyyyMMdd HH:mm:ss.SSS Z} # Outputs: 20211201 15:34:48.054 +0000
${date:now:yyyyMMdd HH:mm:ss.SSS aaa} # Outputs: 20211201 15:34:48.054 PM
${date-with-timezone:now:UTC:yyyyMMdd'T'HH:mm:ss} # Outputs: 20211201T15:34:48
