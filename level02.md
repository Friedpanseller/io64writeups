# Level 02
## Tags
binary | symbolic solver | Multiplication | overflow | maths

## Writeup
We want *a[1] * 0x1064deadbeef4601u to equal 0xd1038d2e07b42569u

Since 0xd1038d2e07b42569u / 0x1064deadbeef4601u is a decimal, we have to try multiplying it by something that will still let it equal itself after overflow section is cut off

                1064DEADBEEF4601 * 
                ----------------
--------------------------------
----------------d1038d2e07b42569

                1064DEADBEEF4601 * 
                ---------------9
----------------938BD41BB6697609
----------------d1038d2e07b42569

                1064DEADBEEF4601 * 
                --------------69
---------------6B95F55435023B669
----------------d1038d2e07b42569

                1064DEADBEEF4601 * 
                -------------F69
--------------FCA26B8373553DC569
----------------d1038d2e07b42569

                1064DEADBEEF4601 * 
                ------------6F69
-------------72275ECAB0D0F7E2569
----------------d1038d2e07b42569

                1064DEADBEEF4601 * 
                -----------66F69
------------697FADFF24A8B3842569
----------------d1038d2e07b42569

                1064DEADBEEF4601 * 
                ----------366F69
-----------37C696E92F185D3B42569
----------------d1038d2e07b42569

                1064DEADBEEF4601 * 
                ---------4366F69
----------450FE4258EAE9DD7B42569
----------------d1038d2e07b42569

                1064DEADBEEF4601 * 
                --------34366F69
---------357F9A4B95B8BBE07B42569
----------------d1038d2e07b42569

                1064DEADBEEF4601 * 
                ------7034366F69
-------72F7965A8420A2C2E07B42569
----------------d1038d2e07b42569

                1064DEADBEEF4601 * 
                -----17034366F69
------179458136731502D2E07B42569
----------------d1038d2e07b42569

                1064DEADBEEF4601 * 
                ----617034366F69
-----63D67D93B00EB908D2E07B42569
----------------d1038d2e07b42569

                1064DEADBEEF4601 * 
                ---3617034366F69
----376C03E277CEBD938D2E07B42569
----------------d1038d2e07b42569

                1064DEADBEEF4601 * 
                --73617034366F69
---7638D6FE6007D5E038D2E07B42569

                1064DEADBEEF4601 * 
                -373617034366F69
--3892297922CE4F61038D2E07B42569
----------------d1038d2e07b42569

                1064DEADBEEF4601 * 
                7373617034366F69
-764B3957CAB7CEFD1038D2E07B42569
----------------d1038d2e07b42569

therefore the good payload is 7373617034366F69 which is "io64pass"
## Flag
X4DafQbnaTY5hiXe
