### <a name="different-exception-handling-for-objectcontextcreatedatabase-and-dbproviderservicescreatedatabase-methods"></a>Farklı özel durum işleme için ObjectContext.CreateDatabase ve DbProviderServices.CreateDatabase yöntemi

|   |   |
|---|---|
|Ayrıntılar|Veritabanı oluşturma başarısız olursa, .NET Framework 4.5 içinde başlayan <code>CreateDatabase</code> boş veritabanını bırakmak yöntemleri çalışır. Bu işlem başarılı olursa, özgün <xref:System.Data.SqlClient.SqlException?displayProperty=name> aktarılacaktır (yerine <xref:System.InvalidOperationException?displayProperty=name> , her zaman oluşturuldu .NET Framework 4. 0 ')|
|Öneri|Yakalama sırasında bir <xref:System.InvalidOperationException?displayProperty=name> yürütülürken <xref:System.Data.Objects.ObjectContext.CreateDatabase> veya <xref:System.Data.Common.DbProviderServices.CreateDatabase(System.Data.Common.DbConnection,System.Nullable{System.Int32},System.Data.Metadata.Edm.StoreItemCollection)>, SQLExceptions şimdi de yakalandı.|
|Kapsam|Küçük|
|Sürüm|4,5|
|Tür|Çalışma zamanı|
|Etkilenen API'leri|<ul><li><xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=nameWithType></li><li><xref:System.Data.Common.DbProviderServices.CreateDatabase(System.Data.Common.DbConnection,System.Nullable{System.Int32},System.Data.Metadata.Edm.StoreItemCollection)?displayProperty=nameWithType></li></ul>|

