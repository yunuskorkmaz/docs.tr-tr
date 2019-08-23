---
title: <callbackDebug>
ms.date: 03/30/2017
ms.assetid: 4073feda-1857-4be4-9947-227afb847ced
ms.openlocfilehash: 91e7bd63bf496f2c38776d88173ed2ac12a3b888
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926316"
---
# <a name="callbackdebug"></a>\<callbackDebug >
Windows Communication Foundation (WCF) geri çağırma nesnesi için hizmet hata ayıklamasını belirtir.  
  
 \<system.ServiceModel>  
\<davranışlar >  
\<Endpointdavranışlar >  
\<davranış >  
\<callbackDebug >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<callbackDebug includeExceptionDetailInFaults="Boolean" />
```  
  
## <a name="type"></a>Tür  
 `Type`  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`includeExceptionDetailInFaults`|İstemci geri çağırma nesnelerinin SOAP hatalarında yönetilen özel durum bilgilerini hizmete geri döndürmeyeceğini belirten bir değer.<br /><br /> Bu özniteliği `true` programlı olarak ayarlarsanız, hata ayıklama amacıyla, istemci geri çağırma nesnesindeki yönetilen özel durum bilgileri için hizmete geri akışı sağlayabilirsiniz. **Dikkatli**  Yönetilen özel durum bilgilerini istemcilere döndürmek bir güvenlik riski oluşturabilir. Bunun nedeni, özel durum ayrıntılarının yetkisiz istemciler tarafından kullanılabilecek iç hizmet uygulamasıyla ilgili bilgileri kullanıma sunmasıdır.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<davranış >](behavior-of-endpointbehaviors.md)|Bir uç nokta davranışı belirtir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.CallbackDebugElement>
- <xref:System.ServiceModel.Description.CallbackDebugBehavior>
