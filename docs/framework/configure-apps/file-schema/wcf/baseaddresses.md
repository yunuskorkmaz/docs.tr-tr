---
title: '&lt;baseAddresses&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 78918102-2898-46e0-9ea8-6b8afe65603e
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 69a049e1daacce901685050ab9fbe99a9c4d3428
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltbaseaddressesgt"></a>&lt;baseAddresses&gt;
Bir koleksiyonunu temsil eder `baseAddress` otomatik olarak barındırılan bir ortamda hizmet ana bilgisayarı için temel adresler öğeleri. Taban adresi varsa, taban adresi göre adresleriyle uç noktaları yapılandırılabilir.  
  
 \<Sistem. ServiceModel >  
\<İstemci >  
\<uç noktası >  
\<ana bilgisayar >  
\<baseAddresses >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<baseAddresses>  
   <add baseAddress="string" />  
</baseAddresses>  
```  
  
## <a name="type"></a>Tür  
 `Type`  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
 Yok.  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<ekleme >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-baseaddresses.md)|Hizmet ana bilgisayar tarafından kullanılan temel adres belirtir bir yapılandırma öğesi.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<ana bilgisayar >](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|Hizmet ana bilgisayarı ayarlarını belirtir. bir yapılandırma öğesi.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>  
 [Barındırma](../../../../../docs/framework/wcf/feature-details/hosting.md)
