### <a name="dbparameterprecision-and-dbparameterscale-are-now-public-virtual-members"></a>Genel sanal üyeleri DbParameter.Precision ve DbParameter.Scale sunulmuştur

|   |   |
|---|---|
|Ayrıntılar|<xref:System.Data.Common.DbParameter.Precision> ve <xref:System.Data.Common.DbParameter.Scale> genel sanal özellikleri olarak uygulanır. Bunlar karşılık gelen bir açık arabirim uygulamalarını değiştirir <xref:System.Data.Common.DbParameter.System%23Data%23IDbDataParameter%23Precision> ve <xref:System.Data.Common.DbParameter.System%23Data%23IDbDataParameter%23Scale>.|
|Öneri|Bir ADO.NET veritabanı sağlayıcısı yeniden oluştururken bu farklılıkları 'override' anahtar sözcüğü kesinlik ve ölçek özellikleri uygulanmasını gerektirir. Bu, bileşenleri yeniden oluştururken yalnızca gereklidir; Mevcut ikili dosyaları çalışmaya devam eder.|
|Kapsam|Küçük|
|Sürüm|4.5.1|
|Tür|Yeniden hedefleme|
|Etkilenen API'leri|<ul><li><xref:System.Data.Common.DbParameter.Precision?displayProperty=nameWithType></li><li><xref:System.Data.Common.DbParameter.Scale?displayProperty=nameWithType></li></ul>|

