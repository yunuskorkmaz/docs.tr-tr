---
title: Önemli İzlemeler
ms.date: 03/30/2017
ms.assetid: 40a1770e-3b09-4142-b0dd-f9ef73642074
ms.openlocfilehash: c230c65b4d3fd45c4905d4ae5f4cbbf90e10faad
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61784969"
---
# <a name="significant-traces"></a>Önemli İzlemeler
Bu konu, Windows Communication Foundation (WCF) tarafından yayılan ana izlemeler bazıları listelenmiştir.  
  
## <a name="significant-traces"></a>Önemli İzlemeler  
  
|İzleme|Açıklama|  
|-----------|-----------------|  
|İleti günlüğü izleme|Bir WCF ileti ileti günlüğü tarafından günlüğe kaydedildiğinde, izleme yayıldığını özelliği `System.ServiceModel.MessageLogging` izleme kaynağı etkinleştirilir. Bu izleme tıklayarak iletisi görüntülenir. Bir ileti için dört yapılandırılabilir günlüğe kaydetme noktası vardır: `ServiceLevelSendRequest`, `TransportSend`, `TransportReceive`, `ServiceLevelReceiveRequest`, ayrıca ileti günlüğü izleme iletisi kaynak özniteliği tarafından belirtilen.|  
|Alınan ileti izleme|Bu izleme, bir WCF ileti alındığında yayıldığını `System.ServiceModel` izleme kaynağı bilgi veya ayrıntılı düzeyinde etkinleştirilir. Bu izleme iletisi bağıntı oku etkinliği graf görünümünü görmek gereklidir.|  
|Gönderilen ileti izleme|Bu izleme, bir WCF ileti gönderildiğinde yayıldığını `System.ServiceModel` izleme kaynağı bilgi veya ayrıntılı düzeyinde etkinleştirilir. Bu izleme iletisi bağıntı oku etkinliği graf görünümünü görmek gereklidir.|  
|Get ChannelEndpointElement|Bu izleme, bilgi düzeyinde yapısı kanal fabrikası yayınlanır. Bu, istemci uç noktası açıklamasını Bahsediyor (uzak adres, bağlama, anlaşma adı) sağlar.|  
|ServiceElement öğesini Al|Bu izleme, bilgi düzeyinde yapı hizmeti ana bilgisayarı olarak yayınlanır. Bu hizmet sözleşmesini ve bağlama açıklamasını sağlar.|  
|SocketConnection oluşturma|Bu izleme, istemci tarafından gerçekleştirilen ilk işlem eylemi ve alma bayt etkinliğini hizmette yayınlanır. Bu, yerel ve uzak IP adreslerini sağlar. Bilgi düzeyinde yayılır.|
