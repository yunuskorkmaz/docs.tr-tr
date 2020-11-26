---
title: Önemli İzlemeler
ms.date: 03/30/2017
ms.assetid: 40a1770e-3b09-4142-b0dd-f9ef73642074
ms.openlocfilehash: 9ad7c217b528cb2ad22169c1aea6391462bab1ae
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96248676"
---
# <a name="significant-traces"></a>Önemli İzlemeler

Bu konuda Windows Communication Foundation (WCF) tarafından oluşturulan bazı önemli izlemeler listelenmiştir.  
  
## <a name="significant-traces"></a>Önemli İzlemeler  
  
|İzleme|Açıklama|  
|-----------|-----------------|  
|İleti günlüğü izleme|İzleme kaynağı etkinleştirildiğinde, ileti günlüğü özelliği tarafından bir WCF iletisi günlüğe kaydedildiğinde izleme yayınlanır `System.ServiceModel.MessageLogging` . Bu izlemeye tıkladığınızda ileti görüntülenir. İleti için dört yapılandırılabilir günlüğe yazma noktası vardır:,,,, `ServiceLevelSendRequest` `TransportSend` Ayrıca ileti `TransportReceive` `ServiceLevelReceiveRequest` günlüğü izlemesinde ileti kaynağı özniteliğiyle gösterilir.|  
|İleti alındı izlemesi|Bu izleme, `System.ServiceModel` bilgi veya ayrıntılı düzeyde izleme kaynağı etkinse BIR WCF iletisi alındığında yayınlanır. Bu izleme, Etkinlik Grafiği görünümünde ileti bağıntı okuna bakmak için gereklidir.|  
|İleti gönderme izlemesi|Bu izleme, `System.ServiceModel` bilgi veya ayrıntılı düzeyde izleme kaynağı etkinse BIR WCF iletisi gönderildiğinde yayınlanır. Bu izleme, Etkinlik Grafiği görünümünde ileti bağıntı okuna bakmak için gereklidir.|  
|ChannelEndpointElement al|Bu izleme, bilgi düzeyinde, kanal fabrikası oluşturma içinde yayınlanır. İstemcinin konuştuğu uç noktanın açıklamasını (uzak adres, bağlama, anlaşma adı) sağlar.|  
|ServiceElement al|Bu izleme, bilgi düzeyinde hizmet ana bilgisayarı oluşturma bölümünde yayınlanır. Hizmet sözleşmesinin ve bağlamanın bir açıklamasını sağlar.|  
|SocketConnection oluşturma|Bu izleme, istemci tarafından gerçekleştirilen ilk Işlem eyleminde ve hizmet üzerindeki baytları al etkinliğinde yayınlanır. Yerel ve uzak IP adreslerini sağlar. Bilgi düzeyinde yayınlanır.|
