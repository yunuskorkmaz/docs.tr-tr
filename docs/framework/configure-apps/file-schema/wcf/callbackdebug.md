---
title: <callbackDebug>
ms.date: 03/30/2017
ms.assetid: 4073feda-1857-4be4-9947-227afb847ced
ms.openlocfilehash: 62ce1bc179c7215d4988e4c6bda08025c3d3e5de
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55286318"
---
# <a name="callbackdebug"></a>\<callbackDebug >
Bir Windows Communication Foundation (WCF) geri çağırma nesnesi için hizmet hata ayıklamasını belirtir.  
  
 \<system.ServiceModel>  
\<davranışlar >  
\<endpointBehaviors>  
\<davranışı >  
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
|`includeExceptionDetailInFaults`|İstemci geri çağırma nesnelerinin SOAP hataları içerisinde yönetilen özel durum bilgilerini hizmete döndürüp belirtir bir değeri.<br /><br /> Bu öznitelik ayarlanırsa verilen `true` programlı olarak hata ayıklama amacıyla yeniden hizmetine istemci geri çağırma nesnesinde yönetilen özel durum bilgilerinin akışını etkinleştirebilirsiniz. **Dikkat:**  İstemcilere döndüren yönetilen özel durum bilgilerini bir güvenlik riski olabilir. Özel durum ayrıntıları yetkisiz istemciler tarafından kullanılabilecek iç hizmet uygulaması hakkında bilgi açığa olmasıdır.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<davranışı >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Bir uç nokta davranışı belirtir.|  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.ServiceModel.Configuration.CallbackDebugElement>
- <xref:System.ServiceModel.Description.CallbackDebugBehavior>
