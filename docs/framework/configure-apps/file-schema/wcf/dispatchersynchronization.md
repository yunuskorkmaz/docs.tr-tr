---
title: '&lt;dispatcherSynchronization&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cc030f9c-4e38-4b14-94dc-9a0e41ec8e2d
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 57477ea60337e5032b80bd9ae8da850099dd08f7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltdispatchersynchronizationgt"></a>&lt;dispatcherSynchronization&gt;

Yanıtı zaman uyumsuz olarak göndermek bir hizmet sağlayan bir uç nokta davranışını belirtir.

\<system.serviceModel > \<davranışları > \<endpointBehaviors > \<davranışı >

## <a name="syntax"></a>Sözdizimi

```xml
<dispatcherSynchronizationBehavior asynchronousSendEnabled="Boolean" 
                                   maxPendingReceives="Integer" />
```

## <a name="type"></a>Tür

`Type`

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler

Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

| Öznitelik               | Açıklama       |
| ----------------------- | ----------------- |
| asynchronousSendEnabled | Zaman uyumsuz gönderme davranışının etkinleştirilip etkinleştirilmediğini belirten bir Boole değeri. |
| `maxPendingReceives`    | Eşzamanlı sayısını alır belirten bir tamsayı kanalda verilebilir.<br /><br /> Yalnızca doğru hizmet azaltma davranışı yapılandırdıktan sonra bu değeri yapılandırılması gerekir. |

### <a name="child-elements"></a>Alt öğeleri

Yok.

### <a name="parent-elements"></a>Üst öğeler

| Öğe | Açıklama |  
| ------- | ----------- |  
| [\<davranışı >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Bir uç nokta davranışını belirtir. |

## <a name="see-also"></a>Ayrıca bkz.

 <xref:System.ServiceModel.Configuration.DispatcherSynchronizationElement><xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior>
