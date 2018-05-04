### <a name="objectcontexttranslate-and-objectcontextexecutestorequery-now-support-enum-type"></a>Enum türü ObjectContext.Translate ve ObjectContext.ExecuteStoreQuery şimdi desteği

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.0, genel parametresini <code>T</code> , <code>ObjectContext.Translate</code> ve <code>ObjectContext.ExecuteStoreQuery</code> yöntemleri enum yüklenemedi. Bu senaryo artık desteklenmektedir.|
|Öneri|.NET Framework 4. 0'ı enum türü üzerinde Çevir veya ExecuteStoreQuery çağrıldı, '0' döndürüldü. Bu davranışı arzu olduysa, çağrıları sabiti 0 (veya bunu enum eşdeğeri) ile değiştirilmelidir.|
|Kapsam|Kenar|
|Sürüm|4,5|
|Tür|Çalışma zamanı|
|Etkilenen API'leri|<ul><li><xref:System.Data.Objects.ObjectContext.Translate%60%601(System.Data.Common.DbDataReader)?displayProperty=nameWithType></li><li><xref:System.Data.Objects.ObjectContext.Translate%60%601(System.Data.Common.DbDataReader,System.String,System.Data.Objects.MergeOption)?displayProperty=nameWithType></li><li><xref:System.Data.Objects.ObjectContext.ExecuteStoreQuery%60%601(System.String,System.Object[])?displayProperty=nameWithType></li><li><xref:System.Data.Objects.ObjectContext.ExecuteStoreQuery%60%601(System.String,System.String,System.Data.Objects.MergeOption,System.Object[])?displayProperty=nameWithType></li></ul>|

