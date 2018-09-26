---
title: '&lt;System.Web&gt; öğesi (Web Ayarları)'
ms.date: 03/30/2017
helpviewer_keywords:
- Web.config configuration file [ASP.NET]
- system.Web element
- <system.Web> element
- ASP.NET configuration system
- configuration files [ASP.NET]
ms.assetid: 24c4cf4f-ad32-42b2-b040-8e4549e2855e
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 39d305d429490380c76e15bdcdde434f0d75457b
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47083143"
---
# <a name="ltsystemwebgt-element-web-settings"></a>&lt;System.Web&gt; öğesi (Web Ayarları)
ASP.NET barındırma katman işlem geneline yönelik davranışını nasıl yönettiği hakkında bilgi içerir.  
  
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
|[\<ApplicationPool >](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)|IIS uygulama havuzları için yapılandırma ayarlarını bir aspnet.config dosyasını belirtir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Yapılandırma >](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|Her yapılandırma dosyasında ortak dil çalışma zamanı tarafından kullanılan kök öğesini belirtir ve [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] uygulamalar.|  
  
## <a name="remarks"></a>Açıklamalar  
 `system.web` Öğesi ve kendi alt `applicationPool` öğesi eklendi [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] sürümünden [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)]. Çalıştırdığınızda [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] veya tümleşik modu sonraki sürümlerde, bu öğe birleşim ASP.NET iş parçacıkları nasıl yönettiğini ve nasıl Bu istekler kuyruğa bir IIS uygulama havuzunda ASP.NET barındırıldığında yapılandırmanıza sağlar. Çalıştırırsanız [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] veya sonraki sürümleri bu ayarları Klasik veya ISAPI modunda yoksayılır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir IIS uygulama havuzunda ASP.NET barındırıldığında aspnet.config dosyasında ASP.NET işlem geneline yönelik davranışını yapılandırma gösterilmektedir. Örnek IIS içinde tümleşik çalıştığını varsayar modu ve uygulama kullanıyor [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)] veya sonraki bir sürümü. Bu davranış sürümlerinde oluşmaz [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] öncesi [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)]. Varsayılan değerleri örnekte değerlerdir.  
  
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
|Doğrulama dosyası||  
|Boş olabilir.||  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [\<applicationPool > öğesi (Web Ayarları)](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)
