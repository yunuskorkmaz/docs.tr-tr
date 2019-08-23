---
title: <dispatcherSynchronization>
ms.date: 03/30/2017
ms.assetid: cc030f9c-4e38-4b14-94dc-9a0e41ec8e2d
ms.openlocfilehash: 7336c9f7d8a117f9a9bfd338e47941eeb648fa51
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925851"
---
# <a name="dispatchersynchronization"></a>\<dispatcherSynchronization >
  
Bir hizmetin yanıtları zaman uyumsuz olarak göndermesini sağlayan bir uç nokta davranışı belirtir.  
  
\<system.serviceModel>  
\<davranışlar >  
\<Endpointdavranışlar >  
\<davranış >  
  
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
| asynchronousSendEnabled | Zaman uyumsuz gönderme davranışının etkin olup olmadığını belirten bir Boole değeri. |
| `maxPendingReceives`    | Kanalda verilebilirler eşzamanlı alma sayısını belirten bir tamsayı.<br /><br /> Bu değer, hizmet azaltma davranışını doğru şekilde yapılandırdıktan sonra yapılandırılmalıdır. |

### <a name="child-elements"></a>Alt öğeleri

Yok.

### <a name="parent-elements"></a>Üst öğeler

| Öğe | Açıklama |  
| ------- | ----------- |  
| [\<davranış >](behavior-of-endpointbehaviors.md)|Bir uç nokta davranışı belirtir. |

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.DispatcherSynchronizationElement>
- <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior>
