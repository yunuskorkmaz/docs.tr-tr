### <a name="sqlvariant-data-uses-sqlvariant-collation-rather-than-database-collation"></a>Veritabanı harmanlaması yerine sql_variant harmanlama sql_variant veri kullanır

|   |   |
|---|---|
|Ayrıntılar|<code>sql_variant</code> verilerinin kullandığı <code>sql_variant</code> veritabanı harmanlaması yerine alfabe düzeni.|
|Öneri|Veritabanı harmanlaması farklıysa, bu olası veri bozulması adresleri <code>sql_variant</code> alfabe düzeni. Bozulmuş verilere dayanan uygulamalar hatayla karşılaşabilir.|
|Kapsam|Geçirgen|
|Sürüm|4,5|
|Tür|Çalışma zamanı|

