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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ccb48efcdd1924ade27220a685e146a7f5eeef76
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
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
