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
ms.openlocfilehash: 5c5c857d4494b6d78b819e56bae4213abc5e2035
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699098"
---
# <a name="systemweb-element-web-settings"></a>@no__t -0system. Web > öğesi (Web ayarları)
ASP.NET barındırma katmanının işlem genelinde davranışı nasıl yönettiği hakkında bilgi içerir.  
  
[ **\<Yapılandırma >** ](../configuration-element.md)  
&nbsp; @ no__t-1 **@no__t -3system. web >**  
  
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
|[\<applicationPool >](applicationpool-element-web-settings.md)|ASPNET. config dosyasındaki IIS uygulama havuzlarının yapılandırma ayarlarını belirtir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<yapılandırma >](../configuration-element.md)|Ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan her yapılandırma dosyasında kök öğesini belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  

@No__t-0 öğesi ve onun alt `applicationPool` öğesi .NET Framework 3,5 SP1 itibariyle .NET Framework eklenmiştir. IIS 7,0 veya sonraki sürümlerini tümleşik modda çalıştırdığınızda, bu öğe birleşimi ASP.NET 'in iş parçacıklarını nasıl yönettiğini ve ASP.NET 'in bir IIS uygulama havuzunda barındırıldığında istekleri nasıl sıraya yazacağını yapılandırmanıza olanak tanır. IIS 7,0 veya sonraki sürümlerini klasik veya ISAPI modunda çalıştırırsanız, bu ayarlar yok sayılır.  
  
## <a name="example"></a>Örnek  

Aşağıdaki örnek, ASP.NET bir IIS uygulama havuzunda barındırıldığında Aspnet. config dosyasında ASP.NET işlem genelindeki davranışın nasıl yapılandırılacağını gösterir. Örnekte IIS 'nin tümleşik modda çalıştığı ve uygulamanın .NET Framework 3,5 SP1 veya sonraki bir sürümü kullanıldığı varsayılır. Bu davranış, .NET Framework .NET Framework 3,5 SP1 'den önceki sürümlerinde oluşmaz. Örnekteki değerler varsayılan değerlerdir.  
  
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
|Boş olabilir||  
  
## <a name="see-also"></a>Ayrıca bkz.

- [\<applicationPool > öğesi (Web ayarları)](applicationpool-element-web-settings.md)
