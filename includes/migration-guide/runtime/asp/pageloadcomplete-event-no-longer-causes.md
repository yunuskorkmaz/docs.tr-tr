### <a name="pageloadcomplete-event-no-longer-causes-systemwebuiwebcontrolsentitydatasource-control-to-invoke-data-binding"></a>Page.LoadComplete olay artık veri bağlama çağrılacak System.Web.UI.WebControls.EntityDataSource denetim neden olur.

|   |   |
|---|---|
|Ayrıntılar|<xref:System.Web.UI.Page.LoadComplete> Olay artık neden <xref:System.Web.UI.WebControls.EntityDataSource?displayProperty=name> veri bağlaması oluşturma/güncelleştirme/silme parametrelerinde yapılan değişiklikler için çağrılacak denetim. Bu değişikliği, bir yabancı seyahat veritabanına ortadan kaldırır, denetimleri değerlerini sıfırlamak gelen engeller ve gibi diğer veri denetimleri ile tutarlıdır davranışı üretir <xref:System.Web.UI.WebControls.SqlDataSource?displayProperty=name> ve <xref:System.Web.UI.WebControls.ObjectDataSource?displayProperty=name>. Bu değişiklik farklı bir davranış veri bağlamanın çağırma uygulamaları kullanan olası olay üreten <xref:System.Web.UI.Page.LoadComplete> olay.|
|Öneri|Veri bağlama için bir gereksinimi varsa, el ile databind sonrası arka planda daha eski bir olayı çağırır.|
|Kapsam|Kenar|
|Sürüm|4,5|
|Tür|Çalışma zamanı|

