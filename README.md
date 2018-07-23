# Easy Exchange

The Easy Exchange library brings quick and easy currency exchange to Android. 

---

## How to Use 

### Step 1

Include the below dependencies in your `build.gradle` project.

```gradle
buildscript {
    repositories {
        jcenter()
        maven { url "http://code.newtronlabs.com:8081/artifactory/libs-release-local" }
    }
    dependencies {
        classpath 'com.android.tools.build:gradle:3.1.3'
        classpath 'com.newtronlabs.android:plugin:2.0.1'
    }
}

allprojects {
    repositories {
        jcenter()
        maven { url "http://code.newtronlabs.com:8081/artifactory/libs-release-local" }
    }
}

subprojects {
    apply plugin: 'com.newtronlabs.android'
}
```

In the `build.gradle` of your app.

```gradle
dependencies {
    compileOnly 'com.newtronlabs.easyexchange:easyexchange:1.2.0'
}
```

### Step 2

Implement the `ICurrencyExchangeCallback`

```java
public class MainActivity extends AppCompatActivity implements ICurrencyExchangeCallback
{
    public static final String TAG = "EasyExchange";
    
    @Override
    protected void onCreate(Bundle savedInstanceState)
    {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        // Exchange from US Dollars to Australian Dollars
        EasyExchangeManager.getInstance()
	      .performExchange(EasyCurrency.USD, EasyCurrency.AUD, 100, this);
    }

    @Override
    public void onExchangeComplete(ICurrencyExchange exchange)
    {
        exchange = EasyExchangeManager.getInstance().getLastKnownExchange();
        Log.d(TTAG , "Exchanged "+ exchange.getFromAmount() +" "
                + exchange.getFromCurrency() + " To: " + exchange.getToAmount() 
		+ " "+ exchange.getToCurrency() );
    }

    @Override
    public void onExchangeFailed(ICurrencyExchange exchange, Throwable reason)
    {
        Log.e(TAG , "Failed Exchanged "+ exchange.getFromAmount() +" "
                + exchange.getFromCurrency() + " To: " + exchange.getToAmount() 
		+ " "+ exchange.getToCurrency() + " Reason: " + reason);
    }
}
```

## Supported Currencies
* AED - United Arab Emirates Dirham
* AFN - Afghan Afghani
* ALL - Albanian Lek
* AMD - Armenian Dram
* ANG - Netherlands Antillean Guilder
* AOA - Angolan Kwanza
* ARS - Argentine Peso
* AUD - Australian Dollar
* AWG - Aruban Florin
* AZN - Azerbaijani Manat
* BAM - Bosnia-Herzegovina Convertible Mark
* BBD - Barbadian Dollar
* BDT - Bangladeshi Taka
* BGN - Bulgarian Lev
* BHD - Bahraini Dinar
* BIF - Burundian Franc
* BMD - Bermudan Dollar
* BND - Brunei Dollar
* BOB - Bolivian Boliviano
* BRL - Brazilian Real
* BSD - Bahamian Dollar
* BTC - Bitcoin
* BTN - Bhutanese Ngultrum
* BWP - Botswanan Pula
* BYN - Belarusian Ruble
* BYR - Belarusian Ruble
* BZD - Belize Dollar
* CAD - Canadian Dollar
* CDF - Congolese Franc
* CHF - Swiss Franc
* CLF - Chilean Unit of Account
* CLP - Chilean Peso
* CNH - CNH
* CNY - Chinese Yuan
* COP - Colombian Peso
* CRC - Costa Rican Colon
* CUP - Cuban Peso
* CVE - Cape Verdean Escudo
* CZK - Czech Koruna
* DEM - German Mark
* DJF - Djiboutian Franc
* DKK - Danish Krone
* DOP - Dominican Peso
* DZD - Algerian Dinar
* EGP - Egyptian Pound
* ERN - Eritrean Nakfa
* ETB - Ethiopian Birr
* EUR - Euro
* FIM - Finnish Markka
* FJD - Fijian Dollar
* FKP - Falkland Islands Pound
* FRF - French Franc
* GBP - British Pound
* GEL - Georgian Lari
* GHS - Ghanaian Cedi
* GIP - Gibraltar Pound
* GMD - Gambian Dalasi
* GNF - Guinean Franc
* GTQ - Guatemalan Quetzal
* GYD - Guyanaese Dollar
* HKD - Hong Kong Dollar
* HNL - Honduran Lempira
* HRK - Croatian Kuna
* HTG - Haitian Gourde
* HUF - Hungarian Forint
* IDR - Indonesian Rupiah
* IEP - Irish Pound
* ILS - Israeli New Shekel
* INR - Indian Rupee
* IQD - Iraqi Dinar
* IRR - Iranian Rial
* ISK - Icelandic Krona
* ITL - Italian Lira
* JMD - Jamaican Dollar
* JOD - Jordanian Dinar
* JPY - Japanese Yen
* KES - Kenyan Shilling
* KGS - Kyrgystani Som
* KHR - Cambodian Riel
* KMF - Comorian Franc
* KPW - North Korean Won
* KRW - South Korean Won
* KWD - Kuwaiti Dinar
* KYD - Cayman Islands Dollar
* KZT - Kazakhstani Tenge
* LAK - Laotian Kip
* LBP - Lebanese Pound
* LKR - Sri Lankan Rupee
* LRD - Liberian Dollar
* LSL - Lesotho Loti
* LTL - Lithuanian Litas
* LVL - Latvian Lats
* LYD - Libyan Dinar
* MAD - Moroccan Dirham
* MDL - Moldovan Leu
* MGA - Malagasy Ariary
* MKD - Macedonian Denar
* MMK - Myanmar Kyat
* MNT - Mongolian Tugrik
* MOP - Macanese Pataca
* MRO - Mauritanian Ouguiya
* MUR - Mauritian Rupee
* MVR - Maldivian Rufiyaa
* MWK - Malawian Kwacha
* MXN - Mexican Peso
* MYR - Malaysian Ringgit
* MZN - Mozambican Metical
* NAD - Namibian Dollar
* NGN - Nigerian Naira
* NIO - Nicaraguan Cordoba
* NOK - Norwegian Krone
* NPR - Nepalese Rupee
* NZD - New Zealand Dollar
* OMR - Omani Rial
* PAB - Panamanian Balboa
* PEN - Peruvian Sol
* PGK - Papua New Guinean Kina
* PHP - Philippine Peso
* PKG - PKG
* PKR - Pakistani Rupee
* PLN - Polish Zloty
* PYG - Paraguayan Guarani
* QAR - Qatari Rial
* RON - Romanian Leu
* RSD - Serbian Dinar
* RUB - Russian Ruble
* RWF - Rwandan Franc
* SAR - Saudi Riyal
* SBD - Solomon Islands Dollar
* SCR - Seychellois Rupee
* SDG - Sudanese Pound
* SEK - Swedish Krona
* SGD - Singapore Dollar
* SHP - St. Helena Pound
* SKK - Slovak Koruna
* SLL - Sierra Leonean Leone
* SOS - Somali Shilling
* SRD - Surinamese Dollar
* STD - Sao Tome & Principe Dobra
* SVC - Salvadoran Colon 
* SYP - Syrian Pound
* SZL - Swazi Lilangeni
* THB - Thai Baht
* TJS - Tajikistani Somoni
* TMT - Turkmenistani Manat
* TND - Tunisian Dinar
* TOP - Tongan  Pa'anga
* TRY - Turkish Lira
* TTD - Trinidad & Tobago Dollar
* TWD - New Taiwan Dollar
* TZS - Tanzanian Shilling
* UAH - Ukrainian Hryvnia
* UGX - Ugandan Shilling
* USD - US Dollar
* UYU - Uruguayan Peso
* UZS - Uzbekistani Som
* VEF - Venezuelan Bolivar
* VND - Vietnamese Dong
* VUV - Vanuatu Vatu
* WST - Samoan Tala
* XAF - Central African CFA Franc
* XCD - East Caribbean Dollar
* XDR - Special Drawing Rights
* XOF - West African CFA Franc
* XPF - CFP Franc
* YER - Yemeni Rial
* ZAR - South African Rand
* ZMK - Zambian Kwacha
* ZMW - Zambian Kwacha
* ZWL - Zimbabwean Dollar

## License

Easy Exchange binaries and source code can only be used in accordance with Freeware license. That is, freeware may be used without payment, but may not be modified. The developer of Easy Exchange retains all rights to change, alter, adapt, and/or distribute the software. Easy Exchange is not liable for any damages and/or losses incurred during the use of Easy Exchange.

You may not decompile, reverse engineer, pull apart, or otherwise attempt to dissect the source code, algorithm, technique or other information from the binary code of Easy Exchange unless it is authorized by existing applicable law and only to the extent authorized by such law. In the event that such a law applies, user may only attempt the foregoing if: (1) user has contacted Newtron Labs to request such information and Newtron Labs has failed to respond in a reasonable time, or (2) reverse engineering is strictly necessary to obtain such information and Newtron Labs has failed to reply. Any information obtained by user from Newtron Labs may be used only in accordance to the terms agreed upon by Newtron Labs and in adherence to Newtron Labs confidentiality policy. Such information supplied by Newtron Labs and received by user shall not be disclosed to a third party or used to create a software substantially similar to the technique or expression of the Newtron Labs Easy Exchange software.

You are solely responsible for determining the appropriateness of using Easy Exchange and assume any risks associated with Your use of Easy Exchange. In no event and under no legal theory, whether in tort (including negligence), contract, or otherwise, unless required by applicable law (such as deliberate and grossly negligent acts) or agreed to in writing, shall Newtron Labs be liable to You for damages, including any direct, indirect, special, incidental, or consequential damages of any character arising as a result of this License or out of the use or inability to use the Easy Exchange (including but not limited to damages for loss of goodwill, work stoppage, computer failure or malfunction, or any and all other commercial damages or losses), even if Newtron Labs has been advised of the possibility of such damages.


## Contact

solutions@newtronlabs.com
