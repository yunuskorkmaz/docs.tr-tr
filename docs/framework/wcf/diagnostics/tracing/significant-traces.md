---
title: Önemli İzlemeler
ms.date: 03/30/2017
ms.assetid: 40a1770e-3b09-4142-b0dd-f9ef73642074
ms.openlocfilehash: 2dc5010874285ba14dae625fcbf92740eb1707b0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="significant-traces"></a>Önemli İzlemeler
Bu konu Windows Communication Foundation (WCF) tarafından gösterilen önemli izlemeler bazıları listeler.  
  
## <a name="significant-traces"></a>Önemli İzlemeler  
  
|İzleme|Açıklama|  
|-----------|-----------------|  
|İleti günlüğü izleme|İzleme yayılan olduğunda bir [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] ileti ileti günlüğü tarafından günlüğe özelliği `System.ServiceModel.MessageLogging` izleme kaynağını etkindir. Bu izleme tıklatarak iletisi görüntülenir. Bir ileti için dört yapılandırılabilir günlüğe kaydetme noktası vardır: `ServiceLevelSendRequest`, `TransportSend`, `TransportReceive`, `ServiceLevelReceiveRequest`, ileti günlüğü izleme iletisi kaynak öznitelikte belirttiği.|  
|Alınan ileti izleme|Bu izleme yayılan olduğunda bir [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] varsa iletisi aldı `System.ServiceModel` izleme kaynağını bilgi veya ayrıntılı düzeyinde etkinleştirilir. Bu izleme iletisi bağıntı oku etkinliği Grafik görünümünde görmek gereklidir.|  
|Gönderilen ileti izleme|Bu izleme yayılan olduğunda bir [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] , iletinin gönderildiği `System.ServiceModel` izleme kaynağını bilgi veya ayrıntılı düzeyinde etkinleştirilir. Bu izleme iletisi bağıntı oku etkinliği Grafik görünümünde görmek gereklidir.|  
|ChannelEndpointElement öğesini Al|Bu izleme bilgileri düzeyinde yapı kanal fabrikası yayınlanır. Bu, istemci uç nokta açıklamasını Konuşmayı (uzak adres, bağlama, sözleşme adı) sağlar.|  
|ServiceElement öğesini Al|Bu izleme, bilgi düzeyinde yapı hizmeti ana bilgisayarı yayınlanır. Bağlama ve hizmet sözleşmesini açıklamasını sağlar.|  
|SocketConnection oluşturma|Bu izleme, istemci tarafından gerçekleştirilen ilk işlem eylem ve hizmet alma bayt faaliyete yayınlanır. Yerel ve uzak IP adresleri sağlar. Bilgi düzeyinde yayınlanır.|
