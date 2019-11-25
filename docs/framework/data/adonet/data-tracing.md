---
title: ADO.NET’te Veri İzleme
ms.date: 03/30/2017
ms.assetid: a6a752a5-d2a9-4335-a382-b58690ccb79f
ms.openlocfilehash: e27f1f30ab8626b21421d6d4a7808f8ffef5c26f
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088770"
---
# <a name="data-tracing-in-adonet"></a>ADO.NET’te Veri İzleme

ADO.NET, SQL Server, Oracle, OLE DB ve ODBC için .NET veri sağlayıcılarının yanı sıra ADO.NET <xref:System.Data.DataSet>ve SQL Server ağ protokollerini destekleyen yerleşik veri izleme işlevselliğine sahiptir.

Veri erişimi API 'SI çağrılarını izlemek, aşağıdaki sorunları tanılamanıza yardımcı olabilir:

- İstemci programı ile veritabanı arasında şema uyumsuzluğu.

- Veritabanı kullanım dışı veya ağ kitaplığı sorunları.

- Bir uygulama tarafından sabit olarak kodlanmış veya üretilen hatalı SQL.

- Yanlış programlama mantığı.

- Birden çok ADO.NET bileşeni veya ADO.NET ile kendi bileşenleriniz arasındaki etkileşimden kaynaklanan sorunlar.

Farklı izleme teknolojilerini desteklemek için, izleme Genişletilebilir olduğundan, geliştirici bir sorunu uygulama yığınının herhangi bir düzeyinde izleyebilir. İzleme yalnızca ADO.NET özelliği olmamasına karşın, Microsoft sağlayıcıları Genelleştirilmiş izleme ve araç API 'Lerinden yararlanır.

ADO.NET ' de yönetilen izlemeyi ayarlama ve yapılandırma hakkında daha fazla bilgi için bkz. [veri erişimini izleme](https://docs.microsoft.com/previous-versions/sql/sql-server-2012/hh880086(v=msdn.10)).

## <a name="accessing-diagnostic-information-in-the-extended-events-log"></a>Genişletilmiş olaylar günlüğündeki tanılama bilgilerine erişme

SQL Server için .NET Framework Veri Sağlayıcısı, veri erişimi izleme ([veri erişimi izleme](https://docs.microsoft.com/previous-versions/sql/sql-server-2012/hh880086(v=msdn.10))), istemci olaylarının bağlantı hatalarıyla, sunucunun bağlantı halkası arabelleği ve genişletilmiş olaylar günlüğündeki uygulama performansı bilgileri gibi tanılama bilgileriyle ilişkilendirilmesi daha kolay hale getirmek için güncelleştirilmiştir. Genişletilmiş olaylar günlüğünü okuma hakkında daha fazla bilgi için bkz. [olay oturumu verilerini görüntüleme](https://docs.microsoft.com/previous-versions/sql/sql-server-2012/hh710068(v=sql.110)).

Bağlantı işlemleri için, ADO.NET bir istemci bağlantı KIMLIĞI gönderir. Bağlantı başarısız olursa, bağlantı halkası arabelleğine (bağlantı[sorunlarını SQL Server 2008 ' de bağlantı sorunlarını giderme](https://go.microsoft.com/fwlink/?LinkId=207752)) erişebilir ve `ClientConnectionID` alanını bulabilir ve bağlantı hatası hakkında tanılama bilgileri alabilirsiniz. İstemci bağlantı kimlikleri, yalnızca bir hata oluşursa halka arabelleğine kaydedilir. (Ön oturum açma paketini göndermeden önce bir bağlantı başarısız olursa, bir istemci bağlantı KIMLIĞI oluşturulmaz.) İstemci bağlantı KIMLIĞI, 16 baytlık bir GUID 'dir. Ayrıca, genişletilmiş olaylar oturumunda `client_connection_id` eylemi olaylara eklenirse, istemci bağlantı KIMLIĞINI genişletilmiş olaylar hedef çıktısında bulabilirsiniz. Veri erişimi izlemeyi etkinleştirebilir ve bağlantı komutunu yeniden çalıştırabilir ve daha fazla istemci sürücü tanılama yardımına ihtiyacınız varsa, veri erişim izleme içindeki `ClientConnectionID` alanını gözlemleyebilirsiniz.

İstemci bağlantı KIMLIĞINI `SqlConnection.ClientConnectionID` özelliğini kullanarak programlı bir şekilde alabilirsiniz.

`ClientConnectionID`, bir bağlantıyı başarıyla kuran bir <xref:System.Data.SqlClient.SqlConnection> nesnesi için kullanılabilir. Bir bağlantı girişimi başarısız olursa, `ClientConnectionID` `SqlException.ToString`aracılığıyla bulunabilir.

ADO.NET ayrıca iş parçacığına özgü etkinlik KIMLIĞI gönderir. Oturumlar TRACK_CAUSALITY seçeneği etkin olarak başlatılırsa, etkinlik KIMLIĞI genişletilmiş olaylar oturumlarında yakalanır. Etkin bir bağlantıyla ilgili performans sorunları için, etkinliğin KIMLIĞINI istemcinin veri erişimi izleme (`ActivityID` alanından) alabilir ve ardından genişletilmiş olaylar çıkışında etkinlik KIMLIĞINI bulabilirsiniz. Genişletilmiş olaylardaki etkinlik KIMLIĞI, dört baytlık bir sıra numarasıyla birlikte bir 16 baytlık GUID 'dir (istemci bağlantı KIMLIĞI GUID 'SI ile aynı değildir). Sıra numarası bir iş parçacığı içindeki bir isteğin sırasını temsil eder ve iş parçacığı için Batch ve RPC deyimlerinin göreli sıralamasını gösterir. `ActivityID` Şu anda SQL Batch deyimleri ve RPC istekleri için veri erişimi izleme etkin olduğunda ve veri erişimi izleme yapılandırma sözcüğünün 18 biti açık olduğunda, isteğe bağlı olarak gönderilir.

Aşağıda, bir halka arabelleğinde depolanacak bir genişletilmiş olaylar oturumu başlatmak için Transact-SQL kullanan bir örnek verilmiştir ve bir istemciden RPC ve Batch işlemlerinde gönderilen etkinlik KIMLIĞI kaydedilir.

```sql
create event session MySession on server
add event connectivity_ring_buffer_recorded,
add event sql_statement_starting (action (client_connection_id)),
add event sql_statement_completed (action (client_connection_id)),
add event rpc_starting (action (client_connection_id)),
add event rpc_completed (action (client_connection_id))
add target ring_buffer with (track_causality=on)
```

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework'te Ağ İzleme](../../network-programming/network-tracing.md)
- [İzleme ve İşaretleme Uygulamaları](../../debug-trace-profile/tracing-and-instrumenting-applications.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
