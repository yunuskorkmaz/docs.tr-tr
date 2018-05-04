---
title: '&lt;dispatcherSynchronization&gt;'
ms.date: 03/30/2017
ms.assetid: cc030f9c-4e38-4b14-94dc-9a0e41ec8e2d
ms.openlocfilehash: 34c12a05ee363df6b6cfc9ff3809bab50ee8d522
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
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
