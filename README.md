# Easy Exchange

The Easy Exchange library brings quick and easy currency exchange to Android. 

---

## How to Use 

### Step 1

Include the below dependencies in your `build.gradle` project.

```gradle
buildscript {
    repositories {
        google()
        jcenter()
        maven { url "https://newtronlabs.jfrog.io/artifactory/libs-release-local"
            metadataSources {
                artifact()
            }
        }
    }
    dependencies {
        classpath 'com.android.tools.build:gradle:3.5.2'
        classpath 'com.newtronlabs.android:plugin:4.0.5'
    }
}

allprojects {
    repositories {
        google()
        jcenter()
        maven { url "https://newtronlabs.jfrog.io/artifactory/libs-release-local"
            metadataSources {
                artifact()
            }
        }
    }
}

subprojects {
    apply plugin: 'com.newtronlabs.android'
}
```

In the `build.gradle` of your app.

```gradle
dependencies {
    compileOnly 'com.newtronlabs.easyexchange:easyexchange:4.0.0'
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

---

## Support Us
Please support the continued development of these libraries. We host and develop these libraries for free. Any support is deeply appriciated. Thank you!

<p align="center">
  <img src="https://drive.google.com/uc?id=1rbY8qjxvWU8GQgaqDrOY4-fYOWobQKk3" width="200" height="200" title="Support us" alt="Support us">
</p>

<p align="center">
  <strong>BTC Address:</strong> 39JmAfnNhaEPKz5wjQjQQj4jcv9BM11NQb
</p>

---

## License
https://gist.github.com/NewtronLabs/216f45db2339e0bc638e7c14a6af9cc8


## Contact

solutions@newtronlabs.com
