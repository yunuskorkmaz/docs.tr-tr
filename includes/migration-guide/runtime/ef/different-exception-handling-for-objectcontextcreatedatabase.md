### <a name="different-exception-handling-for-objectcontextcreatedatabase-and-dbproviderservicescreatedatabase-methods"></a>Farklı özel durum işleme için ObjectContext.CreateDatabase ve DbProviderServices.CreateDatabase yöntemleri

|   |   |
|---|---|
|Ayrıntılar|Veritabanı oluşturma başarısız olursa, .NET Framework 4.5 içinde başlayarak <code>CreateDatabase</code> yöntemleri boş veritabanı bırakma deneyecek. Bu işlem başarılı olursa, özgün <xref:System.Data.SqlClient.SqlException?displayProperty=name> yayılır (yerine <xref:System.InvalidOperationException?displayProperty=name> , her zaman oluşturuldu .NET Framework 4. 0 ')|
|Öneri|Yakalama zaman bir <xref:System.InvalidOperationException?displayProperty=name> yürütülürken <xref:System.Data.Objects.ObjectContext.CreateDatabase> veya <xref:System.Data.Common.DbProviderServices.CreateDatabase(System.Data.Common.DbConnection,System.Nullable{System.Int32},System.Data.Metadata.Edm.StoreItemCollection)>, SQLExceptions şimdi de yakalandı.|
|Kapsam|Küçük|
|Sürüm|4,5|
|Tür|Çalışma zamanı|
|Etkilenen API'leri|<ul><li><xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=nameWithType></li><li><xref:System.Data.Common.DbProviderServices.CreateDatabase(System.Data.Common.DbConnection,System.Nullable{System.Int32},System.Data.Metadata.Edm.StoreItemCollection)?displayProperty=nameWithType></li></ul>|

