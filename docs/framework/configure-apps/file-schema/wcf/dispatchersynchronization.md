---
title: <dispatcherSynchronization>
ms.date: 03/30/2017
ms.assetid: cc030f9c-4e38-4b14-94dc-9a0e41ec8e2d
ms.openlocfilehash: 6be9752e8102a5d4db4fed31aae8ff6d56fdd24e
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55273338"
---
# <a name="dispatchersynchronization"></a>\<dispatcherSynchronization >
  
Zaman uyumsuz yanıtlar göndermek bir hizmet sağlayan bir uç nokta davranışı belirtir.  
  
\<system.serviceModel>  
\<davranışlar >  
\<endpointBehaviors>  
\<davranışı >  
  
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
| `maxPendingReceives`    | Kanal sayısı eşzamanlı alımların belirten bir tamsayı verilebilir.<br /><br /> Bu değer yalnızca doğru hizmet azaltma davranışı yapılandırdıktan sonra yapılandırılmalıdır. |

### <a name="child-elements"></a>Alt öğeleri

Yok.

### <a name="parent-elements"></a>Üst öğeler

| Öğe | Açıklama |  
| ------- | ----------- |  
| [\<davranışı >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Bir uç nokta davranışı belirtir. |

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.DispatcherSynchronizationElement>
- <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior>
