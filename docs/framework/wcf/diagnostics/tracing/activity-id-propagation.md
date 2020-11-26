---
title: Etkinlik Kimliği Yayma
ms.date: 03/30/2017
ms.assetid: cd1c1ae5-cc8a-4f51-90c9-f7b476bcfe70
ms.openlocfilehash: 0f0478b16bf2ca0975ae0290a8855756ecfc383e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96236110"
---
# <a name="activity-id-propagation"></a>Etkinlik Kimliği Yayma

Bir ServiceModel (ServiceModel yayma) veya devre dışı bırakıldığında (kullanıcıdan kullanıcıya etkinlik yayma), yayma gerçekleşir.  
  
## <a name="servicemodel-activity-tracing-is-enabled"></a>ServiceModel etkinlik Izleme etkin  

 ServiceModel ActivityTracing etkinse, işlem, ProcessAction etkinlikleri arasında gerçekleşir.  
  
### <a name="server"></a>Sunucu  

 `propagateActivity`Özniteliği hem istemcide hem de sunucuda olarak ayarlandığında `true` , `ProcessAction` sunucudaki etkinliğin kimliği, YAYıLAN ileti üstbilgisindeki kimlikle aynı olur `ActivityId` .  
  
 `ActivityId`İletide (yani, `propagateActivity` = `false` istemcide) veya sunucuda bir başlık yoksa, `propagateActivity` = `false` sunucu yeni bir etkinlik kimliği oluşturur.  
  
### <a name="client"></a>İstemci  

 İstemci eşzamanlı olarak tek iş parçacıklı ise istemci, `propagateActivity` istemci veya sunucu üzerinde herhangi bir ayarı yoksayar. Bunun yerine, yanıt istek etkinliğinde işlenir. İstemci, istemcide zaman uyumsuz veya zaman uyumlu iş parçacıklı ise `propagateActivity` = `true` ve sunucu tarafından gönderilen iletide bir etkinlik kimliği üst bilgisi varsa, istemci, iletideki etkinlik kimliğini alır ve yayılan etkinlik kimliğini içeren işlem eylemi etkinliğine aktarır. Aksi halde istemci, Işlem Iletisi etkinliğinden yeni bir Işlem eylemi etkinliğine aktarır. Yeni bir Işlem eylemi etkinliğine yönelik bu ek aktarım, tutarlılık açısından yapılır. Bu etkinliğin içinde istemci, iş parçacığı yanıt iletisi işleme için ayrıldığında yerel iş parçacığı bağlamından BeginCall etkinliğinin etkinlik KIMLIĞINI alır. Ardından ilk Işlem eylemi etkinliğine aktarır.  
  
 İstemci çift yönlü ise, istemci iletiyi alırken sunucu olarak davranır.  
  
### <a name="propagation-in-fault-messages"></a>Hata Iletilerinde yayma  

 Geçerli ve hata iletilerini işlemede fark yoktur. İse `propagateActivity` = `true` , SOAP hata iletisi başlıklarına eklenen etkinlik kimliği çevresel etkinliklerle aynıdır.  
  
## <a name="servicemodel-activity-tracing-is-disabled"></a>ServiceModel etkinliği Izleme devre dışı  

 ServiceModel ActivityTracing devre dışıysa, doğrudan ServiceModel etkinliklerine geçmeden Kullanıcı kodu etkinlikleri arasında yayma yapılır. Kullanıcı tanımlı bir etkinlik KIMLIĞI de ileti etkinlik KIMLIĞI üst bilgisi aracılığıyla dağıtılır.  
  
 `propagateActivity` = `true` Ve `ActivityTracing` = `off` bir ServiceModel Trace dinleyicisi için (izlemenin ServiceModel üzerinde etkin olup olmamasına bakılmaksızın), istemci veya sunucuda aşağıdakiler gerçekleşir:  
  
- İşlem isteği veya gönderme yanıtı üzerinde, bir ileti oluşturuluncaya kadar, TLS 'deki etkinlik KIMLIĞI kullanıcı kodundan dağıtılır. Bir etkinlik KIMLIĞI üst bilgisi, gönderilmeden önce iletiye de eklenir.  
  
- İstek veya alma yanıtı alındığında, alınan ileti nesnesi oluşturulduktan hemen sonra etkinlik KIMLIĞI ileti başlığından alınır. Kullanıcı koduna ulaşılana kadar, ileti kapsamdan kaybolduktan sonra TLS 'deki etkinlik KIMLIĞI dağıtılır.  
  
 Bu eylemler, yayma açık ise Kullanıcı izlemelerinin aynı etkinlikte görüneceğini garanti eder. Ancak, ServiceModel izlemelerinde garanti vermez. Yalnızca bu izlemelerin işlenmesi Kullanıcı kodu etkinliğinin ayarlandığı iş parçacığında yürütülürse, ServiceModel izlemeleri bir Kullanıcı kodu etkinliğinde oluşur.  
  
 Genel olarak, ServiceModel izlemeleri aşağıdaki yerlerde gözlemlenebilir:  
  
- ServiceModel izleme devre dışıysa, tüm yayınlanan izlemeler Kullanıcı etkinlikleri ' nde görünür. Hem sunucu hem de istemcide yayma etkinse, bu izlemeler aynı etkinlikte olacaktır.  
  
- ServiceModel izleme etkinse ancak ActivityTracing devre dışıysa, her iki uçta de yayma etkinse kullanıcı izlemeleri aynı etkinlikte görüntülenir. ServiceModel izlemeleri, etkinliğin başlangıçta ayarlandığı Kullanıcı kodu işlemeyle aynı iş parçacığında gerçekleşmedikleri sürece varsayılan 0000 etkinliğinde görüntülenir.  
  
- Hem ServiceModel izleme hem de ActivityTracing etkinse, kullanıcı izlemeleri Kullanıcı tanımlı etkinliklerde görünür ve ServiceModel izlemeleri ServiceModel tarafından tanımlanan etkinliklerde görüntülenir. Yayma, ServiceModel düzeyinde gerçekleşir.
