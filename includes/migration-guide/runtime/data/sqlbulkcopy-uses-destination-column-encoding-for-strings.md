### <a name="sqlbulkcopy-uses-destination-column-encoding-for-strings"></a>Hedef sütun dizeleri için kodlama SqlBulkCopy kullanır.

|   |   |
|---|---|
|Ayrıntılar|Bir sütuna veri girilirken <xref:System.Data.SqlClient.SqlBulkCopy?displayProperty=name> için varsayılan kodlama yerine hedef sütunun kodlamasını kullanır <code>VARCHAR</code> ve <code>CHAR</code> türleri. Bu değişiklik, hedef sütun varsayılan kodlamayı kullanmadığında varsayılan kodlamayı kullanarak neden olunan veri bozulması olasılığını ortadan kaldırır. Nadiren de olsa, şifrelemede yapılan değişiklik hedef sütununa sığmayacak kadar büyük veri oluşturursa, mevcut bir uygulamayı bir SqlException özel durum oluşturabilir.|
|Öneri|Bekler <xref:System.Data.SqlClient.SqlBulkCopy?displayProperty=name> artık kodlama farklar nedeniyle veri bozulmasına neden. Hedef sütunun sınırına yakın dizeleri kopyalanır, data (verileri hedef sütunu sığacak şekilde denetlemek için Kopyalanacak) ya da önceden kodlamak gerekli olabilir veya catch <xref:System.Data.SqlClient.SqlException?displayProperty=name>s.|
|Kapsam|Kenar|
|Sürüm|4,5|
|Tür|Çalışma zamanı|
|Etkilenen API'leri|<ul><li><xref:System.Data.SqlClient.SqlBulkCopy?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlBulkCopy.%23ctor(System.Data.SqlClient.SqlConnection)?displayProperty=nameWithType></li></ul>|

