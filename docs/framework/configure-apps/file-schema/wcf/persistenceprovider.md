---
title: <persistenceProvider>
ms.date: 03/30/2017
ms.assetid: a37049c5-a7ea-4519-94f2-912eeb010380
ms.openlocfilehash: 054991687a54ecbf95cc18f58717a4ed3e36f050
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55260807"
---
# <a name="persistenceprovider"></a>\<persistenceProvider >
Kullanılacak Kalıcılık sağlayıcı uygulanması yanı sıra Kalıcılık işlemleri için kullanılacak zaman aşımını türünü belirtir.  
  
 \<system.ServiceModel>  
\<davranışlar >  
\<serviceBehaviors>  
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
|persistenceOperationTimeout|A <xref:System.TimeSpan> Kalıcılık işlemleri için kullanılan zaman aşımını belirten bir değer. Varsayılan değer "00: 00:30".|  
|türü|Kullanılacak Kalıcılık sağlayıcı üreteci türünü belirten bir dize.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<davranışı >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Bir davranış öğesi belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu öğe bir WCF Hizmeti durumunu serileştirmek için kullanılacak Kalıcılık sağlayıcı belirtir. İle birlikte kullanılmalıdır `wsHttpContextBinding` HTTP üst bilgilerinde durum bilgilerini geçirir.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.ServiceModel.Configuration.PersistenceProviderElement>
- <xref:System.ServiceModel.Persistence.PersistenceProvider>
