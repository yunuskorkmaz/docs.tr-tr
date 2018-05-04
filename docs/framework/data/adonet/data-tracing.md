---
title: ADO.NET veri izleme
ms.date: 03/30/2017
ms.assetid: a6a752a5-d2a9-4335-a382-b58690ccb79f
ms.openlocfilehash: 6dd385cd58d1c8400c45139492d84e6ca4fe1bd7
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="data-tracing-in-adonet"></a>ADO.NET veri izleme
ADO.NET özellikleri SQL Server, Oracle, OLE DB ve ODBC yanı için ADO.NET .NET veri sağlayıcıları tarafından desteklenen yerleşik veri izleme işlevselliği <xref:System.Data.DataSet>ve SQL Server ağ protokolleri.  
  
 Veri izleme erişim API çağrıları aşağıdaki sorunları tanılamanıza yardımcı olabilir:  
  
-   İstemci programını ve veritabanı arasındaki şeması uyuşmazlığı.  
  
-   Veritabanı olmadığından ya da ağ kitaplığı sorunları.  
  
-   Yanlış SQL sabit kodlanmış ya da bir uygulama tarafından üretilen.  
  
-   Yanlış programlama mantığı.  
  
-   ADO.NET ve kendi bileşenleri arasındaki etkileşim veya birden çok ADO.NET bileşenleri arasında kaynaklanan sorunlar.  
  
 Bir geliştirici uygulama yığınının herhangi bir düzeyde bir sorun izleyebilirsiniz farklı izleme teknolojilerini desteklemek için izleme genişletilebilir, olduğundan. İzleme yalnızca ADO.NET özelliği olmasa da, Microsoft sağlayıcıları genelleştirilmiş izleme ve araçları API'leri yararlanın.  
  
 Ayarlama ve ADO.NET yönetilen izlemeyi yapılandırma hakkında daha fazla bilgi için bkz: [izleme veri erişimi](http://msdn.microsoft.com/library/hh880086.aspx).  
  
## <a name="accessing-diagnostic-information-in-the-extended-events-log"></a>Genişletilmiş olay günlüğünde tanılama bilgilerine erişme  
 İçinde [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] için SQL Server veri sağlayıcısı, veri erişim izleme ([veri erişim izleme](http://msdn.microsoft.com/library/hh880086.aspx)) daha kolay gelen bağlantı hataları gibi tanılama bilgileriyle istemci olayları ilişkilendirmenize olanak kolaylaştırmak için güncelleştirildi sunucunun bağlantı halka arabelleği ve uygulama performans genişletilmiş olaylar günlüğünde bilgi. Genişletilmiş olay günlüğünü okuma hakkında daha fazla bilgi için bkz: [görünüm olay oturum verilerini](http://msdn.microsoft.com/library/hh710068\(SQL.110\).aspx).  
  
 Bağlantı işlemleri için bir istemci ADO.NET göndereceğiniz bağlantı kimliği. Bağlantı başarısız olursa, bağlantı halka arabelleği erişebilirsiniz ([bağlantı halka arabelleği ile SQL Server 2008'de bağlantı sorunlarını giderme](http://go.microsoft.com/fwlink/?LinkId=207752)) ve Bul `ClientConnectionID` alan ve tanı bilgilerini almak bağlantı hatası. Yalnızca bir hata oluşursa, istemci bağlantı kimlikleri halka arabelleği günlüğe kaydedilir. (Oturum açma öncesi paket göndermeden önce bir bağlantı başarısız olursa, istemci bağlantı kimliği üretilmez.) İstemci bağlantı kimliği 16 bayt GUID değeridir. İstemci bağlantısı da bulabilirsiniz genişletilmiş olaylar hedef çıkış kimliği `client_connection_id` eylemi bir genişletilmiş olaylar oturumu olayları eklenir. Veri erişim izlemeyi etkinleştirebilir ve bağlantı komutu yeniden çalıştırın ve gözlemlemek `ClientConnectionID` daha fazla istemci sürücüsü tanılama yardıma gereksinim duyarsanız veri erişim izleme alan.  
  
 İstemci alabilir kullanarak program aracılığıyla bağlantı kimliği `SqlConnection.ClientConnectionID` özelliği.  
  
 `ClientConnectionID` İçin kullanılabilir bir <xref:System.Data.SqlClient.SqlConnection> başarıyla bir bağlantı kurar nesnesi. Bir bağlantı girişimi başarısız olursa, `ClientConnectionID` aracılığıyla kullanılabilir olan `SqlException.ToString`.  
  
 ADO.NET ayrıca iş parçacığına özgü etkinlik kimliğini gönderir TRACK_CAUSAILITY seçeneği etkin oturumları başlattıysanız, etkinlik kimliği genişletilmiş olaylar oturumlarında yakalanır. Performans sorunları için etkin bir bağlantı, istemcinin veri erişim izlemesinden etkinlik kimliği alabilirsiniz (`ActivityID` alan) ve etkinlik kimliği genişletilmiş olaylar çıktısında bulun. Genişletilmiş olaylar, etkinlik kimliği bir dört bayt sıralı numara ekli 16 bayt (aynı istemci bağlantı kimliği için GUID) GUID'dir. Sıra numarası, bir isteğin bir iş parçacığından sırayı temsil eder ve toplu ve RPC ifadeleri iş parçacığının göreli sıralamasını gösterir. `ActivityID` SQL toplu deyimleri ve RPC istekleri için veri erişim izleme, üzerinde etkindir ve yapılandırma word izleme veri erişim 18 bit açık olduğunda şu anda isteğe bağlı olarak gönderilir.  
  
 Kullanan bir örnek verilmiştir [!INCLUDE[tsql](../../../../includes/tsql-md.md)] bir halka arabelleği saklanan ve etkinlik kimliği kaydedilecek bir genişletilmiş olaylar oturumu başlatmak için gönderilen RPC ve toplu işlemler üzerinde bir istemciden.  
  
```  
create event session MySession on server   
add event connectivity_ring_buffer_recorded,   
add event sql_statement_starting (action (client_connection_id)),   
add event sql_statement_completed (action (client_connection_id)),   
add event rpc_starting (action (client_connection_id)),   
add event rpc_completed (action (client_connection_id))  
add target ring_buffer with (track_causality=on)  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [.NET Framework'te Ağ İzleme](../../../../docs/framework/network-programming/network-tracing.md)  
 [İzleme ve İşaretleme Uygulamaları](../../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
