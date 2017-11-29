---
title: '&lt;callbackDebug&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4073feda-1857-4be4-9947-227afb847ced
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 93b89787795cb58644b79ae4795e7a036741e138
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltcallbackdebuggt"></a>&lt;callbackDebug&gt;
Hizmeti için hata ayıklama belirten bir [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] geri çağırma nesnesi.  
  
 \<Sistem. ServiceModel >  
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
