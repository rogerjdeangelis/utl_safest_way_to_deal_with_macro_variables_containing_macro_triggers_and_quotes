# utl_safest_way_to_deal_with_macro_variables_containing_macro_triggers_and_quotes
Safest way to deal with macro variables containing macro triggers and quotes. Macro quoting

    ```  Safest way to deal with macro variables containing macro triggers and quotes                                                                                 ```
    ```                                                                                                                                                               ```
    ```  Original subject:  How to deal with specific tokens - ' &                                                                                                    ```
    ```                                                                                                                                                               ```
    ```  SAS is very inconsistent with automatic quoting and unquoting.                                                                                               ```
    ```  I think it is safer to surround the contents of problematic macro variables with single quotes.                                                              ```
    ```  You can then control macro variable unquoting.                                                                                                               ```
    ```                                                                                                                                                               ```
    ```  Keep the macro variable single quoted until you are ready to dequote it.                                                                                     ```
    ```                                                                                                                                                               ```
    ```  You can eliminate an awfull lot of macro Klingon code usin single quotes?                                                                                    ```
    ```                                                                                                                                                               ```
    ```  INPUT                                                                                                                                                        ```
    ```  =====                                                                                                                                                        ```
    ```   WORK.HAVE total obs=5                                                                                                                                       ```
    ```                                                                                                                                                               ```
    ```     bs    NAME                                                                                                                                                ```
    ```                                                                                                                                                               ```
    ```     1     A&M                                                                                                                                                 ```
    ```     2     M'M                                                                                                                                                 ```
    ```     3     M"M%'                                                                                                                                               ```
    ```     4     1/2                                                                                                                                                 ```
    ```     5     &sysdate                                                                                                                                            ```
    ```                                                                                                                                                               ```
    ```   CODE                                                                                                                                                        ```
    ```   ====                                                                                                                                                        ```
    ```     proc sql noprint;                                                                                                                                         ```
    ```       select quote(strip(name),"'") into :n1 - :n99 from have;                                                                                                ```
    ```     quit;                                                                                                                                                     ```
    ```                                                                                                                                                               ```
    ```     %put &=n1;                                                                                                                                                ```
    ```     %put &=n2;                                                                                                                                                ```
    ```     %put &=n3;                                                                                                                                                ```
    ```     %put &=n4;                                                                                                                                                ```
    ```     %put &=n5;                                                                                                                                                ```
    ```     %put &=n5;                                                                                                                                                ```
    ```                                                                                                                                                               ```
    ```     %put N5 unquoted = %sysfunc(dequote(&n5.));                                                                                                               ```
    ```                                                                                                                                                               ```
    ```   OUTPUT                                                                                                                                                      ```
    ```   ======                                                                                                                                                      ```
    ```     N1='A&M'                                                                                                                                                  ```
    ```     N2='M''M'                                                                                                                                                 ```
    ```     N3='M"M%'''                                                                                                                                               ```
    ```     N4='1/2'                                                                                                                                                  ```
    ```     N5='&sysdate'                                                                                                                                             ```
    ```                                                                                                                                                               ```
    ```     N5 unquoted = 09NOV17                                                                                                                                     ```
    ```                                                                                                                                                               ```
    ```  see                                                                                                                                                          ```
    ```  https://goo.gl/hdcKHw                                                                                                                                        ```
    ```  https://communities.sas.com/t5/Base-SAS-Programming/how-to-deal-with-specific-tokens-amp/m-p/412087                                                          ```
    ```                                                                                                                                                               ```
    ```  *                _                _       _                                                                                                                  ```
    ```   _ __ ___   __ _| | _____      __| | __ _| |_ __ _                                                                                                           ```
    ```  | '_ ` _ \ / _` | |/ / _ \    / _` |/ _` | __/ _` |                                                                                                          ```
    ```  | | | | | | (_| |   <  __/   | (_| | (_| | || (_| |                                                                                                          ```
    ```  |_| |_| |_|\__,_|_|\_\___|    \__,_|\__,_|\__\__,_|                                                                                                          ```
    ```                                                                                                                                                               ```
    ```  ;                                                                                                                                                            ```
    ```                                                                                                                                                               ```
    ```  data have;                                                                                                                                                   ```
    ```    input name $16.;                                                                                                                                           ```
    ```  cards4;                                                                                                                                                      ```
    ```  A&M                                                                                                                                                          ```
    ```  M'M                                                                                                                                                          ```
    ```  M"M%'                                                                                                                                                        ```
    ```  1/2                                                                                                                                                          ```
    ```  &sysdate                                                                                                                                                     ```
    ```  ;;;;                                                                                                                                                         ```
    ```  run;                                                                                                                                                         ```
    ```                                                                                                                                                               ```
    ```  *          _       _   _                                                                                                                                     ```
    ```   ___  ___ | |_   _| |_(_) ___  _ __                                                                                                                          ```
    ```  / __|/ _ \| | | | | __| |/ _ \| '_ \                                                                                                                         ```
    ```  \__ \ (_) | | |_| | |_| | (_) | | | |                                                                                                                        ```
    ```  |___/\___/|_|\__,_|\__|_|\___/|_| |_|                                                                                                                        ```
    ```                                                                                                                                                               ```
    ```  ;                                                                                                                                                            ```
    ```                                                                                                                                                               ```
    ```  proc sql noprint;                                                                                                                                            ```
    ```    select quote(strip(name),"'") into :n1 - :n99 from have;                                                                                                   ```
    ```  quit;                                                                                                                                                        ```
    ```                                                                                                                                                               ```
    ```  %put &n1;                                                                                                                                                    ```
    ```  %put &n2;                                                                                                                                                    ```
    ```  %put &n3;                                                                                                                                                    ```
    ```  %put &n4;                                                                                                                                                    ```
    ```  %put &n5;                                                                                                                                                    ```
    ```                                                                                                                                                               ```
    ```  %put %sysfunc(dequote(&n5.));                                                                                                                                ```
    ```                                                                                                                                                               ```
    ```                                                                                                                                                               ```
    ```                                                                                                                                                               ```

