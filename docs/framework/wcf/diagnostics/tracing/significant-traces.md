---
title: Önemli İzlemeler
ms.date: 03/30/2017
ms.assetid: 40a1770e-3b09-4142-b0dd-f9ef73642074
ms.openlocfilehash: c230c65b4d3fd45c4905d4ae5f4cbbf90e10faad
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
---
# <a name="significant-traces"></a>Önemli İzlemeler
Bu konu Windows Communication Foundation (WCF) tarafından gösterilen önemli izlemeler bazıları listeler.  
  
## <a name="significant-traces"></a>Önemli İzlemeler  
  
|İzleme|Açıklama|  
|-----------|-----------------|  
|İleti günlüğü izleme|Bir WCF ileti ileti günlüğü tarafından günlüğe kaydedildiğinde izleme yayılan özelliği `System.ServiceModel.MessageLogging` izleme kaynağını etkindir. Bu izleme tıklatarak iletisi görüntülenir. Bir ileti için dört yapılandırılabilir günlüğe kaydetme noktası vardır: `ServiceLevelSendRequest`, `TransportSend`, `TransportReceive`, `ServiceLevelReceiveRequest`, ileti günlüğü izleme iletisi kaynak öznitelikte belirttiği.|  
|Alınan ileti izleme|Bu izleme, bir WCF iletisi alındığında yayılan `System.ServiceModel` izleme kaynağını bilgi veya ayrıntılı düzeyinde etkinleştirilir. Bu izleme iletisi bağıntı oku etkinliği Grafik görünümünde görmek gereklidir.|  
|Gönderilen ileti izleme|Bu izleme, bir WCF ileti gönderildiğinde yayılan `System.ServiceModel` izleme kaynağını bilgi veya ayrıntılı düzeyinde etkinleştirilir. Bu izleme iletisi bağıntı oku etkinliği Grafik görünümünde görmek gereklidir.|  
|ChannelEndpointElement öğesini Al|Bu izleme bilgileri düzeyinde yapı kanal fabrikası yayınlanır. Bu, istemci uç nokta açıklamasını Konuşmayı (uzak adres, bağlama, sözleşme adı) sağlar.|  
|ServiceElement öğesini Al|Bu izleme, bilgi düzeyinde yapı hizmeti ana bilgisayarı yayınlanır. Bağlama ve hizmet sözleşmesini açıklamasını sağlar.|  
|SocketConnection oluşturma|Bu izleme, istemci tarafından gerçekleştirilen ilk işlem eylem ve hizmet alma bayt faaliyete yayınlanır. Yerel ve uzak IP adresleri sağlar. Bilgi düzeyinde yayınlanır.|
