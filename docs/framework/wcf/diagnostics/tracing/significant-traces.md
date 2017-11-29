---
title: "Önemli İzlemeler"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 40a1770e-3b09-4142-b0dd-f9ef73642074
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 58322a472a59ee9d3ac9451ff1f20ed95405ac54
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="significant-traces"></a>Önemli İzlemeler
Bu konu tarafından gösterilen önemli izlemeler bazıları listeler [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)].  
  
## <a name="significant-traces"></a>Önemli İzlemeler  
  
|İzleme|Açıklama|  
|-----------|-----------------|  
|İleti günlüğü izleme|İzleme yayılan olduğunda bir [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] ileti ileti günlüğü tarafından günlüğe özelliği `System.ServiceModel.MessageLogging` izleme kaynağını etkindir. Bu izleme tıklatarak iletisi görüntülenir. Bir ileti için dört yapılandırılabilir günlüğe kaydetme noktası vardır: `ServiceLevelSendRequest`, `TransportSend`, `TransportReceive`, `ServiceLevelReceiveRequest`, ileti günlüğü izleme iletisi kaynak öznitelikte belirttiği.|  
|Alınan ileti izleme|Bu izleme yayılan olduğunda bir [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] varsa iletisi aldı `System.ServiceModel` izleme kaynağını bilgi veya ayrıntılı düzeyinde etkinleştirilir. Bu izleme iletisi bağıntı oku etkinliği Grafik görünümünde görmek gereklidir.|  
|Gönderilen ileti izleme|Bu izleme yayılan olduğunda bir [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] , iletinin gönderildiği `System.ServiceModel` izleme kaynağını bilgi veya ayrıntılı düzeyinde etkinleştirilir. Bu izleme iletisi bağıntı oku etkinliği Grafik görünümünde görmek gereklidir.|  
|ChannelEndpointElement öğesini Al|Bu izleme bilgileri düzeyinde yapı kanal fabrikası yayınlanır. Bu, istemci uç nokta açıklamasını Konuşmayı (uzak adres, bağlama, sözleşme adı) sağlar.|  
|ServiceElement öğesini Al|Bu izleme, bilgi düzeyinde yapı hizmeti ana bilgisayarı yayınlanır. Bağlama ve hizmet sözleşmesini açıklamasını sağlar.|  
|SocketConnection oluşturma|Bu izleme, istemci tarafından gerçekleştirilen ilk işlem eylem ve hizmet alma bayt faaliyete yayınlanır. Yerel ve uzak IP adresleri sağlar. Bilgi düzeyinde yayınlanır.|
