---
description: 'Hakkında daha fazla bilgi edinin: <callbackDebug>'
title: <callbackDebug>
ms.date: 03/30/2017
ms.assetid: 4073feda-1857-4be4-9947-227afb847ced
ms.openlocfilehash: 911d738764baa800831c19f4e5d181118d1d3e00
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639217"
---
# \<callbackDebug>

Windows Communication Foundation (WCF) geri çağırma nesnesi için hizmet hata ayıklamasını belirtir.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<callbackDebug>**  
  
## <a name="syntax"></a>Syntax  
  
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
|`includeExceptionDetailInFaults`|İstemci geri çağırma nesnelerinin SOAP hatalarında yönetilen özel durum bilgilerini hizmete geri döndürmeyeceğini belirten bir değer.<br /><br /> Bu özniteliği programlı olarak ayarlarsanız `true` , hata ayıklama amacıyla, istemci geri çağırma nesnesindeki yönetilen özel durum bilgileri için hizmete geri akışı sağlayabilirsiniz. **Dikkat:**  Yönetilen özel durum bilgilerini istemcilere döndürmek bir güvenlik riski oluşturabilir. Bunun nedeni, özel durum ayrıntılarının yetkisiz istemciler tarafından kullanılabilecek iç hizmet uygulamasıyla ilgili bilgileri kullanıma sunmasıdır.|  
  
### <a name="child-elements"></a>Alt Öğeler  

 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|Bir uç nokta davranışı belirtir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.CallbackDebugElement>
- <xref:System.ServiceModel.Description.CallbackDebugBehavior>
