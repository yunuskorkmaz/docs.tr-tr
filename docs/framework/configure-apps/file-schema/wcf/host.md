---
title: '&lt;ana bilgisayar&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: be566d55-9d50-4b2e-985d-52a5cc26cbbb
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d498190e7d7c3a6e879c50324e3b973f0f8e8fa6
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="lthostgt"></a>&lt;ana bilgisayar&gt;
Hizmet ana bilgisayarı ayarlarını belirtir.  
  
 \<Sistem. ServiceModel >  
\<Hizmetleri >  
\<Hizmet >  
\<ana bilgisayar >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<host>  
      <baseAddresses>  
         <baseAddress baseAddress="string" />  
      </baseAddresses>  
      <timeOuts closeTimeout="TimeSpan"  
         openTimeout="TimeSpan" >  
</host>  
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
|[\<baseAddresses >](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md)|Bir koleksiyonu `baseAddress` hizmeti ana bilgisayar tarafından kullanılan temel adres belirtir öğeleri.|  
|[\<zaman aşımı >](../../../../../docs/framework/configure-apps/file-schema/wcf/timeouts.md)|Hizmet ana bilgisayarı açmak veya kapatmak izin verilen zaman aralığını belirtir bir yapılandırma öğesi.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Hizmet >](../../../../../docs/framework/configure-apps/file-schema/wcf/service.md)|Ayarlarını belirten bir [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] hizmet.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 [Barındırma](../../../../../docs/framework/wcf/feature-details/hosting.md)
