---
title: Etkinlik Kimliği Yayma
ms.date: 03/30/2017
ms.assetid: cd1c1ae5-cc8a-4f51-90c9-f7b476bcfe70
ms.openlocfilehash: e51970f693d9ca2d2f81bf4efc97969896de4828
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33474304"
---
# <a name="activity-id-propagation"></a>Etkinlik Kimliği Yayma
ServiceModel Etkinlik izleme etkin (ServiceModel yayma) ya da devre dışı (kullanıcıdan kullanıcıya Etkinlik yayma) olduğunda yayma gerçekleşir.  
  
## <a name="servicemodel-activity-tracing-is-enabled"></a>ServiceModel Etkinlik izleme etkin  
 ServiceModel ActivityTracing etkinleştirilirse, yayma ProcessAction etkinlikler arasında gerçekleşir.  
  
### <a name="server"></a>Sunucu  
 Zaman `propagateActivity` özniteliği `true` hem istemci hem de sunucu Kimliğini `ProcessAction` sunucu etkinliğinde, yayılan Kimliğinde aynıdır `ActivityId` ileti üstbilgisi.  
  
 Durumlarda `ActivityId` başlığıdır iletide (diğer bir deyişle, `propagateActivity` = `false` istemci üzerinde), veya ne zaman `propagateActivity` = `false` sunucuda, sunucunun yeni bir etkinlik kimliği oluşturur.  
  
### <a name="client"></a>İstemci  
 İstemci zaman uyumlu olarak tek iş parçacıklı ise, istemci, herhangi bir ayarı yok sayar `propagateActivity` istemci veya sunucu. Bunun yerine, yanıt isteği etkinliğinde ele alınır. İstemci zaman uyumsuz veya zaman uyumlu ise birden çok iş parçacıklı, `propagateActivity` = `true` istemci ve sunucu tarafından gönderilen ileti içinde bir etkinlik kimliği üstbilgisi yok, istemci etkinlik kimliği gelen iletiyi alır ve aktarır Yayılan etkinlik kimliğini içeren bir işlem eylem etkinliği Aksi durumda, istemci yeni bir işlem eylem etkinlik işlemi iletisi etkinliğinden aktarır. Yeni bir işlem eylem etkinlik için fazladan bu aktarım tutarlılık için yapılır. İş parçacığı yanıt iletisi işlenmek üzere atandığında bu etkinliği içinde istemci yerel iş parçacığı bağlamından BeginCall etkinliğin etkinlik kimliği alır. Ardından, ilk işlem eylem etkinlik aktarır.  
  
 İstemci, istemci çift yönlü ise, iletiyi alan sunucuda görür.  
  
### <a name="propagation-in-fault-messages"></a>Hata iletileri yayma  
 Geçerli işleme ve hata iletileri arasında fark yoktur. Varsa `propagateActivity` = `true`, SOAP hata ileti üstbilgilerini eklenen etkinlik kimliği ortam etkinlik aynıdır.  
  
## <a name="servicemodel-activity-tracing-is-disabled"></a>ServiceModel etkinliği izleme devre dışı bırakıldı  
 ServiceModel ActivityTracing devre dışıysa, yayma ServiceModel etkinlikleri giderek olmadan doğrudan kullanıcı kodu etkinlikler arasında oluşur. Kullanıcı tanımlı etkinlik kimliği de ileti etkinlik kimliği üstbilgisi dağıtılır.  
  
 Varsa `propagateActivity` = `true` ve `ActivityTracing` = `off` ServiceModel izleme dinleyicisi (bağımsız olarak izleme üzerinde ServiceModel etkinleştirilip etkinleştirilmediğini gösterir) istemci veya sunucu üzerinde aşağıdakiler:  
  
-   Bir ileti biçimlendirilmiş kadar işlem isteği veya yanıtı göndermeyi, TLS etkinlik kimliği kullanıcı kodu dışında yayılır. Gönderilmeden önce bir etkinlik kimliği üstbilgisi da iletisine eklenir.  
  
-   Alınan ileti nesne oluşturulduktan hemen sonra isteği alındığında veya yanıt alma, etkinlik kimliği ileti başlığından alınır. Kullanıcı kodu ulaşılana kadar kapsamdan ileti kaybolur hemen TLS etkinlik kimliği yayılır.  
  
 Bu eylemler güvence altına kullanıcı izleri yayma açıksa aynı etkinlik içindeki görünür. Ancak, üzerinde ServiceModel izlemeleri garanti etmez. ServiceModel izlemeleri bir kullanıcı kodu etkinliğini ortaya yalnızca bu izlemeler işlenmesini kullanıcı kodu etkinliği belirlendiği aynı iş parçacığı üzerinde yürütülür.  
  
 Genel olarak, ServiceModel izlemelerini aşağıdaki konumlarda gösterilebilir:  
  
-   ServiceModel izleme devre dışıysa, tüm verilmiş izlemeleri kullanıcı etkinlikleri görünür. Yayma hem sunucu hem de istemci etkinleştirildiğinde bu izleri aynı etkinlik içindeki olur.  
  
-   Yayma üzerindeki her iki End etkinleştirilirse ServiceModel izleme etkinleştirilir, ancak ActivityTracing devre dışı ise, kullanıcı izlemeleri aynı etkinlik içindeki görünür. İş parçacığı etkinliği başlangıçta ayarlandığı kullanıcı kodu işleme olarak da meydana gelen sürece ServiceModel izlemeleri varsayılan 0000 etkinlik görünür.  
  
-   ServiceModel izleme ve ActivityTracing etkinleştirilirse, kullanıcı tanımlı aktivitelerde kullanıcı izlemeleri görünür ve ServiceModel izlemeleri ServiceModel tanımlı etkinlikler görünür. Yayma ServiceModel düzeyinde gerçekleşir.
