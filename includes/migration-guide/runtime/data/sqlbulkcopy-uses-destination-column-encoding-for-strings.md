### <a name="sqlbulkcopy-uses-destination-column-encoding-for-strings"></a>Hedef sütun için dizeleri kodlama SqlBulkCopy kullanır

|   |   |
|---|---|
|Ayrıntılar|Verileri bir sütun halinde eklerken <xref:System.Data.SqlClient.SqlBulkCopy?displayProperty=name> için varsayılan kodlamayı yerine hedef sütunu kodlama kullanır <code>VARCHAR</code> ve <code>CHAR</code> türleri. Bu değişiklik, hedef sütun varsayılan kodlamayı kullanmadığında varsayılan kodlamayı kullanarak neden olunan veri bozulması olasılığını ortadan kaldırır. Kodlama değişikliği hedef sütuna sığmayacak kadar büyük olan verileri oluşturursa nadir durumlarda varolan bir uygulama SqlException özel durum.|
|Öneri|Bekler <xref:System.Data.SqlClient.SqlBulkCopy?displayProperty=name> farklar kodlama nedeniyle verileri artık bozar. Hedef sütunun boyutuna yakın dizeleri kopyalanır, ya da (verileri hedef sütunu sığacak şekilde denetlemek için Kopyalanacak) veri önceden kodlamak gerekli olabilir veya catch <xref:System.Data.SqlClient.SqlException?displayProperty=name>s.|
|Kapsam|Kenar|
|Sürüm|4,5|
|Tür|çalışma zamanı|
|Etkilenen API'leri|<ul><li><xref:System.Data.SqlClient.SqlBulkCopy?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlBulkCopy.%23ctor(System.Data.SqlClient.SqlConnection)?displayProperty=nameWithType></li></ul>|

