### <a name="objectcontexttranslate-and-objectcontextexecutestorequery-now-support-enum-type"></a>ObjectContext.Translate ve ObjectContext.ExecuteStoreQuery artık destek enum türü

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.0, genel parametre <code>T</code> , <code>ObjectContext.Translate</code> ve <code>ObjectContext.ExecuteStoreQuery</code> yöntemleri bir sabit listesi yüklenemedi. Bu senaryonun artık desteklenmektedir.|
|Öneri|Enum türü .NET Framework 4. 0'ı üzerinde Çevir veya ExecuteStoreQuery çağrıldı, '0' döndürüldü. Bu davranışı arzu olduysa, çağrıları 0 sabiti (veya onu enum eşdeğeri) ile değiştirilmelidir.|
|Kapsam|Kenar|
|Sürüm|4,5|
|Tür|Çalışma zamanı|
|Etkilenen API'leri|<ul><li><xref:System.Data.Objects.ObjectContext.Translate%60%601(System.Data.Common.DbDataReader)?displayProperty=nameWithType></li><li><xref:System.Data.Objects.ObjectContext.Translate%60%601(System.Data.Common.DbDataReader,System.String,System.Data.Objects.MergeOption)?displayProperty=nameWithType></li><li><xref:System.Data.Objects.ObjectContext.ExecuteStoreQuery%60%601(System.String,System.Object[])?displayProperty=nameWithType></li><li><xref:System.Data.Objects.ObjectContext.ExecuteStoreQuery%60%601(System.String,System.String,System.Data.Objects.MergeOption,System.Object[])?displayProperty=nameWithType></li></ul>|

