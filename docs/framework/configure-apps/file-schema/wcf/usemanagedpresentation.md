---
title: '&lt;useManagedPresentation&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 17a0dd77-af54-41db-a9d0-4b17ff42878f
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ae9851794d77972066fb897aa76528fec86fd6f0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltusemanagedpresentationgt"></a>&lt;useManagedPresentation&gt;
CardSpace güvenlik belirteci, WS-Trust CardSpace profilini destekleyen hizmeti ile iletişim kurmak için kullanılan bir bağlama öğesi. Bu öğe hiçbir özniteliği var ve boş bir anahtar yok.  
  
 \<system.serviceModel >  
\<bağlamaları >  
\<customBinding >  
\<bağlama >  
\<useManagedPresentation >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<useManagedPresentation/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
 Yok.  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<bağlama >](../../../../../docs/framework/misc/binding.md)|Özel bağlama tüm bağlama özelliklerini tanımlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu öğe, WS-Trust CardSpace profilini destekleyen olgu kendi ilkesinde ifade etmek için bir kimlik sağlayıcısı tarafından kullanılır. Bu tür bir ilke onaylama yayımlama kimlik sağlayıcıları bu CardSpace profilini temel sorunu belirteçleri saptayabilmelisiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Configuration.UseManagedPresentationElement>  
 <xref:System.ServiceModel.Channels.UseManagedPresentationBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [Bağlamalar](../../../../../docs/framework/wcf/bindings.md)  
 [Bağlamaları Genişletme](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Özel Bağlamalar](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
