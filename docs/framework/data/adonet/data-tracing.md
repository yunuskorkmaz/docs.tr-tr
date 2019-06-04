---
title: ADO.NET’te Veri İzleme
ms.date: 03/30/2017
ms.assetid: a6a752a5-d2a9-4335-a382-b58690ccb79f
ms.openlocfilehash: 120a9e2a817401ba04e0dce8052caecb83115e0e
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489526"
---
# <a name="data-tracing-in-adonet"></a>ADO.NET’te Veri İzleme

ADO.NET .NET veri sağlayıcıları tarafından desteklenen SQL Server, Oracle, OLE DB ve ODBC yanı için ADO.NET yerleşik veri izleme işlevselliği özellikleri <xref:System.Data.DataSet>ve SQL Server ağ protokolleri.

Veri izleme erişim API çağrıları aşağıdaki sorunları tanılamanıza yardımcı olabilir:

- İstemci programı ve veritabanı arasındaki şeması uyuşmazlığı.

- Veritabanı kullanım dışı kalması veya ağ kitaplığı sorunları.

- Hatalı SQL sabit kodlanmış ya da bir uygulama tarafından üretilen.

- Hatalı programlama mantığı.

- ADO.NET ve kendi bileşenler arasındaki etkileşimi veya birden çok ADO.NET bileşenleri arasında kaynaklanan sorunları.

Bir geliştirici herhangi bir düzeyde uygulama yığınının bir sorunu izlemek için farklı izleme teknolojilerini desteklemek için izleme genişletilebilir. İzleme, bir yalnızca ADO.NET özelliği olmamasına karşın, Microsoft sağlayıcıları genelleştirilmiş izleme ve ölçümlü izleme API'leri yararlanın.

Ayarlama ve ADO.NET yönetilen izlemeyi yapılandırma hakkında daha fazla bilgi için bkz. [izleme veri erişimi](https://docs.microsoft.com/previous-versions/sql/sql-server-2012/hh880086(v=msdn.10)).

## <a name="accessing-diagnostic-information-in-the-extended-events-log"></a>Genişletilmiş olaylar günlüğünde tanılama bilgilerine erişme

SQL Server için .NET Framework veri sağlayıcısı veri erişim izleme ([veri erişimini izlemeye](https://docs.microsoft.com/previous-versions/sql/sql-server-2012/hh880086(v=msdn.10))) daha kolay gelen bağlantı hataları gibi tanılama bilgileri ile istemci olayları ilişkilendirmek daha kolay hale getirmek için güncelleştirildi sunucunun bağlantı halka arabelleği ve uygulama performans bilgilerini genişletilmiş olaylar günlüğünde. Genişletilmiş olay günlüğünü okuma hakkında daha fazla bilgi için bkz: [görünümü olay oturumu verileri](https://docs.microsoft.com/previous-versions/sql/sql-server-2012/hh710068(v=sql.110)).

Bağlantı işlemleri için bir istemci ADO.NET gönderir bağlantı kimliği. Bağlantı başarısız olursa bağlantı halka arabelleği erişebilirsiniz ([bağlantı halka arabelleği ile SQL Server 2008'deki bağlantı sorunlarını giderme](https://go.microsoft.com/fwlink/?LinkId=207752)) ve bulma `ClientConnectionID` alan ve tanı bilgilerini almak bağlantı hatası. İstemci bağlantı kimlikleri, bir hata oluşursa halka arabelleği günlüğe kaydedilir. (Oturum açma öncesi paket göndermeden önce bir bağlantı başarısız olursa, istemci bağlantı kimliği üretilmez.) İstemci bağlantı kimliği 16 baytlık bir GUID'dir. İstemci bağlantısı da bulabilirsiniz genişletilmiş olaylar hedef çıkışında kimliği `client_connection_id` eylemi için olayları bir genişletilmiş olaylar oturumunda eklenir. Veri erişim izlemeyi etkinleştirebilir ve bağlantı komutu yeniden çalıştırın ve gözlemleyin `ClientConnectionID` daha fazla istemci sürücü tanılama yardıma ihtiyacınız varsa veri erişimi izleme alan.

İstemci alabilir kullanarak program aracılığıyla bağlantı kimliği `SqlConnection.ClientConnectionID` özelliği.

`ClientConnectionID` İçin kullanılabilir bir <xref:System.Data.SqlClient.SqlConnection> nesnesini başarıyla bir bağlantı kurar. Bağlantı denemesi başarısız olursa `ClientConnectionID` aracılığıyla kullanılabilir olan `SqlException.ToString`.

ADO.NET bir iş parçacığına özgü etkinlik kimliğini de gönderir. TRACK_CAUSALITY seçeneği etkin oturumları başlattıysanız, etkinlik kimliği genişletilmiş olaylar oturumunda yakalanır. Etkin bir bağlantı ile performans sorunlarını için istemcinin veri erişim izlemesinden etkinlik kimliği alabilirsiniz (`ActivityID` alan) ve etkinlik kimliği genişletilmiş olaylar çıktısında bulun. Genişletilmiş olaylar etkinlik Kimliğini dört bayt sıralı numara ekli bir 16 baytlık (değil GUID istemci bağlantı kimliği aynı) GUID'dir. Sıra numarası, bir isteğin bir iş parçacığından sırayı temsil eder ve toplu işlem ve iş parçacığı için RPC deyimleri göreli sıralamasını belirtir. `ActivityID` SQL toplu deyimleri ve RPC istekleri için veri erişimini izlemeye etkinleştirilir ve yapılandırma word izleme veri erişimi 18 bit açık olduğunda şu anda isteğe bağlı olarak gönderilir.

Bir halka arabelleği içinde depolanır ve RPC ve toplu işlemler bir istemciye gönderilen etkinlik kimliği kaydedilecek bir genişletilmiş olaylar oturumu başlatmak için Transact-SQL kullanan bir örnek verilmiştir.

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

- [.NET Framework'te Ağ İzleme](../../../../docs/framework/network-programming/network-tracing.md)
- [İzleme ve İşaretleme Uygulamaları](../../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
