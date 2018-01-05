---
title: "&lt;System.Web&gt; öğesi (Web Ayarları)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Web.config configuration file [ASP.NET]
- system.Web element
- <system.Web> element
- ASP.NET configuration system
- configuration files [ASP.NET]
ms.assetid: 24c4cf4f-ad32-42b2-b040-8e4549e2855e
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 59899178fd9fc8da2334883ed62d9f8655eb335b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltsystemwebgt-element-web-settings"></a>&lt;System.Web&gt; öğesi (Web Ayarları)
ASP.NET barındırma katman işlem genelinde davranışı nasıl yönettiği hakkında bilgi içerir.  
  
 \<Yapılandırma >  
\<System.Web > öğesi (Web Ayarları)  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<system.web>  
</system.web>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
 Yok.  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<applicationPool >](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)|IIS uygulama havuzları için yapılandırma ayarlarını bir aspnet.config dosyasında belirtir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Yapılandırma >](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|Ortak dil çalışma zamanı tarafından kullanılan her yapılandırma dosyası kök öğesi belirtir ve [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] uygulamalar.|  
  
## <a name="remarks"></a>Açıklamalar  
 `system.web` Öğesi ve kendi alt `applicationPool` öğesi için eklendi [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] sürümünden [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)]. Çalıştırdığınızda [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] veya tümleşik mod sonraki sürümlerinde, bu öğe birleşimini ASP.NET iş parçacıklarını nasıl yönettiğini ve nasıl, kuyruklar istekleri ASP.NET bir IIS uygulama havuzunda barındırıldığında yapılandırmanıza sağlar. Çalıştırırsanız [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] veya sonraki sürümleri bu ayarları Klasik veya ISAPI modunda göz ardı edilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, ASP.NET bir IIS uygulama havuzunda barındırıldığında ASP.NET işlem genelinde davranışı aspnet.config dosyasındaki yapılandırma gösterilmektedir. Örnek IIS tümleşik çalıştığını varsayar modu ve uygulama kullanıyor [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)] veya sonraki bir sürümü. Bu davranış sürümlerinde oluşmaz [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] öncesi [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)]. Örnek değerler varsayılan değerlerdir.  
  
```xml  
<configuration>  
  <system.web>  
    <applicationPool   
        maxConcurrentRequestsPerCPU="5000"   
        maxConcurrentThreadsPerCPU="0"   
        requestQueueLimit="5000" />  
  </system.web>  
</configuration>  
```  
  
## <a name="element-information"></a>Öğe Bilgisi  
  
|||  
|-|-|  
|Ad Alanı||  
|Şema adı||  
|Dosya doğrulama||  
|Boş olabilir.||  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [\<applicationPool > öğesi (Web Ayarları)](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)
