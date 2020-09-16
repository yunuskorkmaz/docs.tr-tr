---
title: Veri Izleme
ms.date: 03/30/2017
ms.assetid: a6a752a5-d2a9-4335-a382-b58690ccb79f
ms.openlocfilehash: 5fe04d6b6146079db7d4e110a94ced361949998c
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557116"
---
# <a name="data-tracing-in-adonet"></a>ADO.NET’te Veri İzleme

ADO.NET, SQL Server, Oracle, OLE DB ve ODBC için .NET veri sağlayıcılarının yanı sıra ADO.NET <xref:System.Data.DataSet> ve SQL Server ağ protokollerini destekleyen yerleşik veri izleme işlevselliğine sahiptir.

Veri erişimi API 'SI çağrılarını izlemek, aşağıdaki sorunları tanılamanıza yardımcı olabilir:

- İstemci programı ile veritabanı arasında şema uyumsuzluğu.

- Veritabanı kullanım dışı veya ağ kitaplığı sorunları.

- Bir uygulama tarafından sabit olarak kodlanmış veya üretilen hatalı SQL.

- Yanlış programlama mantığı.

- Birden çok ADO.NET bileşeni veya ADO.NET ile kendi bileşenleriniz arasındaki etkileşimden kaynaklanan sorunlar.

Farklı izleme teknolojilerini desteklemek için, izleme Genişletilebilir olduğundan, geliştirici bir sorunu uygulama yığınının herhangi bir düzeyinde izleyebilir. İzleme yalnızca ADO.NET özelliği olmamasına karşın, Microsoft sağlayıcıları Genelleştirilmiş izleme ve araç API 'Lerinden yararlanır.

ADO.NET ' de yönetilen izlemeyi ayarlama ve yapılandırma hakkında daha fazla bilgi için bkz. [veri erişimini izleme](/previous-versions/sql/sql-server-2012/hh880086(v=msdn.10)).

## <a name="accessing-diagnostic-information-in-the-extended-events-log"></a>Genişletilmiş olaylar günlüğündeki tanılama bilgilerine erişme

SQL Server için .NET Framework Veri Sağlayıcısı, veri erişimi izleme ([veri erişimi izleme](/previous-versions/sql/sql-server-2012/hh880086(v=msdn.10))), istemci olaylarının bağlantı hatalarıyla, sunucunun bağlantı halkası arabelleği ve genişletilmiş olaylar günlüğündeki uygulama performansı bilgileri gibi tanılama bilgileriyle ilişkilendirilmesi daha kolay hale getirmek için güncelleştirilmiştir. Genişletilmiş olaylar günlüğünü okuma hakkında daha fazla bilgi için bkz. [olay oturumu verilerini görüntüleme](/previous-versions/sql/sql-server-2012/hh710068(v=sql.110)).

Bağlantı işlemleri için, ADO.NET bir istemci bağlantı KIMLIĞI gönderir. Bağlantı başarısız olursa, bağlantı halkası arabelleğine (bağlantı[sorunlarını SQL Server 2008 ' de bağlantı sorunlarını giderme](/archive/blogs/sql_protocols/connectivity-troubleshooting-in-sql-server-2008-with-the-connectivity-ring-buffer)) erişebilir ve bu `ClientConnectionID` alanı bulabilir ve bağlantı hatası hakkında tanılama bilgileri edinebilirsiniz. İstemci bağlantı kimlikleri, yalnızca bir hata oluşursa halka arabelleğine kaydedilir. (Ön oturum açma paketini göndermeden önce bir bağlantı başarısız olursa, bir istemci bağlantı KIMLIĞI oluşturulmaz.) İstemci bağlantı KIMLIĞI, 16 baytlık bir GUID 'dir. Ayrıca, `client_connection_id` bir genişletilmiş olaylar oturumunda olaylara eklenirse, istemci bağlantı kimliğini genişletilmiş olaylar hedef çıktısında bulabilirsiniz. Veri erişimi izlemeyi etkinleştirebilir ve bağlantı komutunu yeniden çalıştırabilir ve `ClientConnectionID` daha fazla istemci sürücü tanılama yardımına ihtiyacınız varsa veri erişim izleme içindeki alanı gözlemleyebilirsiniz.

Özelliğini kullanarak istemci bağlantı KIMLIĞINI programlı bir şekilde alabilirsiniz `SqlConnection.ClientConnectionID` .

, `ClientConnectionID` <xref:System.Data.SqlClient.SqlConnection> Başarıyla bağlantı kuran bir nesne için kullanılabilir. Bir bağlantı girişimi başarısız olursa, `ClientConnectionID` aracılığıyla bulunabilir `SqlException.ToString` .

ADO.NET ayrıca iş parçacığına özgü etkinlik KIMLIĞI gönderir. Oturumlar TRACK_CAUSALITY seçeneği etkin olarak başlatılırsa, etkinlik KIMLIĞI genişletilmiş olaylar oturumlarında yakalanır. Etkin bir bağlantıyla ilgili performans sorunları için, etkinliğin KIMLIĞINI istemcinin veri erişimi izleme (alan) ' dan alabilir `ActivityID` ve sonra genişletilmiş olaylar çıkışında etkınlık kimliğini bulabilirsiniz. Genişletilmiş olaylardaki etkinlik KIMLIĞI, dört baytlık bir sıra numarasıyla birlikte bir 16 baytlık GUID 'dir (istemci bağlantı KIMLIĞI GUID 'SI ile aynı değildir). Sıra numarası bir iş parçacığı içindeki bir isteğin sırasını temsil eder ve iş parçacığı için Batch ve RPC deyimlerinin göreli sıralamasını gösterir. `ActivityID`Şu anda, veri erişimi izleme etkinleştirildiğinde SQL Batch deyimleri ve RPC istekleri için isteğe bağlı olarak gönderilir ve veri erişimi izleme yapılandırma sözcüğünün 18 biti açıktır.

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
- [Uygulamaları izleme ve İşaretleme](../../debug-trace-profile/tracing-and-instrumenting-applications.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
