---
title: Etkinlik Kimliği Yayma
ms.date: 03/30/2017
ms.assetid: cd1c1ae5-cc8a-4f51-90c9-f7b476bcfe70
ms.openlocfilehash: 642d4da49f90d3fc6f2b0dfc9896d724acb075b5
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64651816"
---
# <a name="activity-id-propagation"></a>Etkinlik Kimliği Yayma
ServiceModel Etkinlik izleme etkin (ServiceModel yayma) veya devre dışı (kullanıcı için Etkinlik yayma) olduğunda yayma olur.  
  
## <a name="servicemodel-activity-tracing-is-enabled"></a>ServiceModel Etkinlik izleme etkin  
 ServiceModel ActivityTracing etkinleştirilirse, yayma ProcessAction etkinlikler arasında gerçekleşir.  
  
### <a name="server"></a>Sunucu  
 Zaman `propagateActivity` özniteliği `true` hem istemci hem de sunucu kimliği `ProcessAction` sunucudaki etkinlik kimliği yayılan aynı `ActivityId` ileti üst bilgisi.  
  
 Hiçbir `ActivityId` başlığıdır iletide (diğer bir deyişle, `propagateActivity` = `false` istemci üzerinde), veya `propagateActivity` = `false` sunucuda, sunucunun yeni bir etkinlik kimliği oluşturur.  
  
### <a name="client"></a>İstemci  
 İstemcinin zaman uyumlu olarak tek iş parçacıklı olup olmadığını, istemci, herhangi bir ayarı yok sayar `propagateActivity` istemci veya sunucu. Bunun yerine, yanıt isteği etkinliğini ele alınır. İstemci zaman uyumlu veya zaman uyumsuz olması durumunda birden çok iş parçacıklı, `propagateActivity` = `true` istemci ve sunucu tarafından gönderilen ileti içinde bir etkinlik kimliği üst bilgisi yoktur, istemci etkinlik kimliği gelen iletiyi alır ve aktarır Yayılan etkinlik kimliğini içeren bir işlem eylem etkinliği Aksi takdirde istemci iletiyi işle etkinliği için yeni bir işlem eylem etkinliği aktarır. Bu ek aktarım için yeni bir işlem eylem etkinliği tutarlılık sağlamak için gerçekleştirilir. İş parçacığının yanıt ileti işleme için tahsis edildiğinde bu etkinliği içinde istemci yerel iş parçacığı bağlamından BeginCall etkinliğin etkinlik kimliği alır. Ardından, ilk işlem eylem etkinliği aktarır.  
  
 İstemci, istemci çift yönlü ise, iletiyi almak için sunucuda görür.  
  
### <a name="propagation-in-fault-messages"></a>Hata iletileri yayma  
 Geçerli işleme ve hata iletileri fark yoktur. Varsa `propagateActivity` = `true`, SOAP hatası ileti üstbilgilerini eklenen etkinlik kimliği ortam etkinlik için aynıdır.  
  
## <a name="servicemodel-activity-tracing-is-disabled"></a>ServiceModel etkinliği izleme devre dışı bırakıldı  
 ServiceModel ActivityTracing devre dışıysa, yayma ServiceModel etkinlikleri giden olmadan doğrudan kullanıcı kodu etkinlikler arasında gerçekleşir. Bir kullanıcı tanımlı etkinlik kimliği de ileti etkinlik kimliği üst bilgisi dağıtılır.  
  
 Varsa `propagateActivity` = `true` ve `ActivityTracing` = `off` ServiceModel izleme dinleyicisi (bakılmaksızın izleme ServiceModel üzerinde etkin olup olmadığı) istemci veya sunucu üzerinde şunlar:  
  
- Bir ileti biçimlendirilmiş kadar işlem istek veya yanıt göndererek, TLS etkinlik kimliği kullanıcı kodunun yayılır. Gönderilmeden önce bir etkinlik kimliği üst bilgisi da iletiye eklenir.  
  
- Alınan ileti nesne oluşturulduktan hemen sonra isteği alındığında veya yanıt alma, etkinlik kimliği ileti başlığından alınır. Kullanıcı kodu ulaşılana kadar ileti kapsamından kaybolur hemen sonra TLS etkinlik kimliği yayılır.  
  
 Bu Eylemler, kullanıcı izlemeleri yayma açıksa aynı etkinliğin görünür garanti. Ancak, üzerinde ServiceModel izlemeleri garanti etmez. ServiceModel izlemeleri kullanıcı kod etkinliğinde ortaya yalnızca izlemeleri işlenmesini kullanıcı kod etkinliği ayarlandığı aynı iş parçacığında yürütülür.  
  
 Genel olarak, aşağıdaki konumlarda ServiceModel izlemeleri gösterilebilir:  
  
- ServiceModel izlemeyi devre dışı bırakılırsa kullanıcı etkinliklerini verilmiş tüm izlemeleri görünür. Yayma hem sunucu hem de istemci sırasında etkin olduğunda bu izlemelerin aynı etkinliğin olacaktır.  
  
- Yayma iki ucu da etkinse, kullanıcı izlemeleri ServiceModel izleme etkinleştirildi, ancak ActivityTracing devre dışı bırakıldı, aynı etkinliğin görünür. Etkinlik başlangıçta ayarlandığı kullanıcı kodu işleme olarak aynı iş parçacığında ortaya sürece ServiceModel izlemeleri varsayılan 0000 etkinliğinde görüntülenir.  
  
- ServiceModel izleme hem ActivityTracing etkinleştirilirse, kullanıcının kullanıcı tanımlı etkinlikler görüntülenir ve ServiceModel izlemeleri ServiceModel tanımlı etkinlikler görünür. Yayma ServiceModel düzeyinde gerçekleşir.
