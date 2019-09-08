---
title: ADO.NET’te Veri İzleme
ms.date: 03/30/2017
ms.assetid: a6a752a5-d2a9-4335-a382-b58690ccb79f
ms.openlocfilehash: 1b2ee679ce4b0d39b993b9081f428fe585ef7d92
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784893"
---
# <a name="data-tracing-in-adonet"></a>ADO.NET’te Veri İzleme

ADO.net, SQL Server, Oracle, OLE DB ve ODBC için .NET veri sağlayıcılarının yanı sıra ADO.net <xref:System.Data.DataSet>ve SQL Server ağ protokollerini destekleyen yerleşik veri izleme işlevselliğine sahiptir.

Veri erişimi API 'SI çağrılarını izlemek, aşağıdaki sorunları tanılamanıza yardımcı olabilir:

- İstemci programı ile veritabanı arasında şema uyumsuzluğu.

- Veritabanı kullanım dışı veya ağ kitaplığı sorunları.

- Bir uygulama tarafından sabit olarak kodlanmış veya üretilen hatalı SQL.

- Yanlış programlama mantığı.

- Birden çok ADO.NET bileşeni veya ADO.NET ile kendi bileşenleriniz arasındaki etkileşimden kaynaklanan sorunlar.

Farklı izleme teknolojilerini desteklemek için, izleme Genişletilebilir olduğundan, geliştirici bir sorunu uygulama yığınının herhangi bir düzeyinde izleyebilir. İzleme yalnızca ADO.NET özelliği olmamasına karşın, Microsoft sağlayıcıları Genelleştirilmiş izleme ve araç API 'Lerinden yararlanır.

ADO.NET ' de yönetilen izlemeyi ayarlama ve yapılandırma hakkında daha fazla bilgi için bkz. [veri erişimini izleme](https://docs.microsoft.com/previous-versions/sql/sql-server-2012/hh880086(v=msdn.10)).

## <a name="accessing-diagnostic-information-in-the-extended-events-log"></a>Genişletilmiş olaylar günlüğündeki tanılama bilgilerine erişme

SQL Server için .NET Framework Veri Sağlayıcısı, veri erişimi izleme ([veri erişimi izleme](https://docs.microsoft.com/previous-versions/sql/sql-server-2012/hh880086(v=msdn.10))), istemci olaylarının bağlantı hatalarıyla, sunucu bağlantısının bağlantısının daha kolay bir şekilde ilişkilendirilmesi daha kolay hale getirmek için güncelleştirilmiştir. genişletilmiş olaylar günlüğündeki halka arabelleği ve uygulama performansı bilgileri. Genişletilmiş olaylar günlüğünü okuma hakkında daha fazla bilgi için bkz. [olay oturumu verilerini görüntüleme](https://docs.microsoft.com/previous-versions/sql/sql-server-2012/hh710068(v=sql.110)).

Bağlantı işlemleri için, ADO.NET bir istemci bağlantı KIMLIĞI gönderir. Bağlantı başarısız olursa, bağlantı halkası arabelleğine (bağlantı[sorunlarını SQL Server 2008 ' de bağlantı sorunlarını giderme](https://go.microsoft.com/fwlink/?LinkId=207752)) erişebilir ve bu `ClientConnectionID` alanı bulabilir ve bağlantı hatası hakkında tanılama bilgileri edinebilirsiniz. İstemci bağlantı kimlikleri, yalnızca bir hata oluşursa halka arabelleğine kaydedilir. (Ön oturum açma paketini göndermeden önce bir bağlantı başarısız olursa, bir istemci bağlantı KIMLIĞI oluşturulmaz.) İstemci bağlantı KIMLIĞI, 16 baytlık bir GUID 'dir. Ayrıca, bir genişletilmiş olaylar oturumunda olaylara eklenirse, `client_connection_id` istemci bağlantı kimliğini genişletilmiş olaylar hedef çıktısında bulabilirsiniz. Veri erişimi izlemeyi etkinleştirebilir ve bağlantı komutunu yeniden çalıştırabilir ve daha fazla istemci sürücü `ClientConnectionID` tanılama yardımına ihtiyacınız varsa veri erişim izleme içindeki alanı gözlemleyebilirsiniz.

`SqlConnection.ClientConnectionID` Özelliğini kullanarak istemci bağlantı kimliğini programlı bir şekilde alabilirsiniz.

, `ClientConnectionID` Başarıyla bağlantı kuran bir <xref:System.Data.SqlClient.SqlConnection> nesne için kullanılabilir. Bir bağlantı girişimi başarısız olursa, `ClientConnectionID` aracılığıyla `SqlException.ToString`bulunabilir.

ADO.NET ayrıca iş parçacığına özgü etkinlik KIMLIĞI gönderir. Oturumlar TRACK_CAUSALITY seçeneği etkin olarak başlatılırsa, etkinlik KIMLIĞI genişletilmiş olaylar oturumlarında yakalanır. Etkin bir bağlantıyla ilgili performans sorunları için, etkinliğin kimliğini istemcinin veri erişimi izleme (`ActivityID` alan) ' dan alabilir ve sonra genişletilmiş olaylar çıkışında etkinlik kimliğini bulabilirsiniz. Genişletilmiş olaylardaki etkinlik KIMLIĞI, dört baytlık bir sıra numarasıyla birlikte bir 16 baytlık GUID 'dir (istemci bağlantı KIMLIĞI GUID 'SI ile aynı değildir). Sıra numarası bir iş parçacığı içindeki bir isteğin sırasını temsil eder ve iş parçacığı için Batch ve RPC deyimlerinin göreli sıralamasını gösterir. Şu `ActivityID` anda, veri erişimi izleme etkinleştirildiğinde SQL Batch deyimleri ve RPC istekleri için isteğe bağlı olarak gönderilir ve veri erişimi izleme yapılandırma sözcüğünün 18 biti açıktır.

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
