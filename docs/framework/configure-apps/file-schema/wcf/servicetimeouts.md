---
title: '&lt;serviceTimeouts&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ada536cf-97dc-4cd7-89ec-ed1466c1c557
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0d8bfde535eb417614eee4ec6a2db7985152be33
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltservicetimeoutsgt"></a>&lt;serviceTimeouts&gt;
Bir hizmet için zaman aşımını belirtir.  
  
 \<Sistem. ServiceModel >  
\<davranışları >  
\<serviceBehaviors >  
\<davranışı >  
\<serviceTimeouts >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<serviceTimeouts transactionTimeout="TimeSpan" />  
```  
  
## <a name="type"></a>Tür  
 `Type`  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`transactionTimeout`|A <xref:System.TimeSpan> bir işlem istemciden sunucuya akış gerekir zaman aralığını belirten değer. Varsayılan değer "00: 00:00".|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<davranışı >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Bir davranış öğesi belirtir.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Configuration.ServiceTimeoutsElement>
