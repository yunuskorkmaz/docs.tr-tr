---
title: '&lt;callbackDebug&gt;'
ms.date: 03/30/2017
ms.assetid: 4073feda-1857-4be4-9947-227afb847ced
ms.openlocfilehash: 2103c32112b6c5554d7b510f486d4cbb1349f35d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltcallbackdebuggt"></a>&lt;callbackDebug&gt;
Hizmet için bir Windows Communication Foundation (WCF) geri çağırma nesnesi hata ayıklama belirtir.  
  
 \<system.ServiceModel>  
\<davranışları >  
\<endpointBehaviors >  
\<davranışı >  
\<callbackDebug >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<callbackDebug  includeExceptionDetailInFaults="Boolean" />  
```  
  
## <a name="type"></a>Tür  
 `Type`  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`includeExceptionDetailInFaults`|İstemci geri araması nesneleri yönetilen özel durum bilgilerini SOAP hataları hizmete geri döndürme olup olmadığını belirten bir değer.<br /><br /> Bu öznitelik ayarlanırsa, `true` tekrar hata ayıklama amacıyla hizmet için bir istemci geri çağırma nesnesindeki yönetilen özel durum bilgi akışını programlı olarak etkinleştirebilirsiniz. **Dikkat:** döndürme istemcilere yönetilen özel durum bilgileri, bir güvenlik riski olabilir. Özel durum ayrıntıları yetkisiz istemcileri tarafından kullanılan iç hizmet uygulaması hakkında bilgi kullanıma olmasıdır.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<davranışı >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Bir uç nokta davranışını belirtir.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Configuration.CallbackDebugElement>  
 <xref:System.ServiceModel.Description.CallbackDebugBehavior>
