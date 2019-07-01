---
title: <system.web> Öğesi (Web Ayarları)
ms.date: 03/30/2017
helpviewer_keywords:
- Web.config configuration file [ASP.NET]
- system.Web element
- <system.Web> element
- ASP.NET configuration system
- configuration files [ASP.NET]
ms.assetid: 24c4cf4f-ad32-42b2-b040-8e4549e2855e
ms.openlocfilehash: b9a43c5f5141e364ab9aac1cfdff577a8fb8a161
ms.sourcegitcommit: 2d42b7ae4252cfe1232777f501ea9ac97df31b63
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2019
ms.locfileid: "67486674"
---
# <a name="systemweb-element-web-settings"></a>\<System.Web > öğesi (Web Ayarları)
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
|[\<Yapılandırma >](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|Her yapılandırma dosyasında ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğesini belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 `system.web` Öğesi ve kendi alt `applicationPool` öğesi .NET Framework 3.5 SP1 itibariyle .NET Framework eklendi. IIS 7.0 veya üzeri sürümler tümleşik modda çalıştırdığınızda, bu öğe birleşim ASP.NET iş parçacıkları nasıl yönettiğini ve nasıl Bu istekler kuyruğa bir IIS uygulama havuzunda ASP.NET barındırıldığında yapılandırmanıza olanak sağlar. IIS 7.0 veya üzeri sürümler Klasik veya ISAPI modunu çalıştırırsanız, bu ayarları göz ardı edilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir IIS uygulama havuzunda ASP.NET barındırıldığında aspnet.config dosyasında ASP.NET işlem geneline yönelik davranışını yapılandırma gösterilmektedir. Örnek IIS içinde tümleşik çalıştığını varsayar modu ve uygulama .NET Framework 3.5 SP1 veya sonraki bir sürümünü kullanıyor. Bu davranış, .NET Framework 3.5 SP1'den önceki .NET Framework sürümlerinde gerçekleşmez. Varsayılan değerleri örnekte değerlerdir.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [\<applicationPool > öğesi (Web Ayarları)](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)
