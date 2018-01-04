---
title: '&lt;persistenceProvider&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a37049c5-a7ea-4519-94f2-912eeb010380
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 447384ef34c1ca2c7e641f0ba0d3d3718139e579
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltpersistenceprovidergt"></a>&lt;persistenceProvider&gt;
Kalıcılık işlemleri için zaman aşımı yanı sıra kullanmak için Kalıcılık sağlayıcı uygulaması türünü belirtir.  
  
 \<Sistem. ServiceModel >  
\<davranışları >  
\<serviceBehaviors >  
\<davranışı >  
\<persistenceProvider >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<persistenceProvider persistenceOperationTimeout="TimeSpan"  
   type="String" />  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|persistenceOperationTimeout|A <xref:System.TimeSpan> Kalıcılık işlemleri için kullanılan zaman aşımı belirten değer. Varsayılan değer "00: 00:30".|  
|türü|Kullanılacak Kalıcılık sağlayıcı üreteci türünü belirten bir dize.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<davranışı >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Bir davranış öğesi belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu öğe bir WCF Hizmeti durumunu serileştirmek için kullanılacak Kalıcılık sağlayıcıyı belirtir. İle birlikte kullanılmalıdır `wsHttpContextBinding` HTTP üstbilgilerinde durum bilgilerini geçirir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Configuration.PersistenceProviderElement>  
 <xref:System.ServiceModel.Persistence.PersistenceProvider>
