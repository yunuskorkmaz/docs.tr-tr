### <a name="dbparameterprecision-and-dbparameterscale-are-now-public-virtual-members"></a>Genel sanal üyeler DbParameter.Precision ve DbParameter.Scale sunulmuştur

|   |   |
|---|---|
|Ayrıntılar|<xref:System.Data.Common.DbParameter.Precision> ve <xref:System.Data.Common.DbParameter.Scale> ortak sanal özellikleri olarak uygulanır. Karşılık gelen açık arabirim uygulamaları Değiştir <xref:System.Data.Common.DbParameter.System%23Data%23IDbDataParameter%23Precision> ve <xref:System.Data.Common.DbParameter.System%23Data%23IDbDataParameter%23Scale>.|
|Öneri|Bir ADO.NET veritabanı sağlayıcısı yeniden oluştururken bu farklılıklar duyarlık ve ölçek özelliklerine uygulanacak 'override' anahtar sözcüğünü gerektirir. Bu yalnızca bileşenleri yeniden oluştururken gereklidir; Varolan ikili dosyaları çalışmaya devam eder.|
|Kapsam|Küçük|
|Sürüm|4.5.1|
|Tür|Yeniden hedefleme|
|Etkilenen API'leri|<ul><li><xref:System.Data.Common.DbParameter.Precision?displayProperty=nameWithType></li><li><xref:System.Data.Common.DbParameter.Scale?displayProperty=nameWithType></li></ul>|

