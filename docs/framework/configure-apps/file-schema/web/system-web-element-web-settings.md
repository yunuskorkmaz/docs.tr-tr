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
ms.openlocfilehash: b37b05bdf90630251cbfcf86751243a3a8b77663
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152847"
---
# <a name="systemweb-element-web-settings"></a>\<system.web> Element (Web Ayarları)
ASP.NET barındırma katmanının işlem genelindeki davranışı nasıl yönettiği hakkında bilgi içerir.  
  
[**\<yapılandırma>**](../configuration-element.md)  
&nbsp;&nbsp;**\<system.web>**  
  
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
|[\<uygulamaHavuz>](applicationpool-element-web-settings.md)|Aspnet.config dosyasında IIS uygulama havuzları için yapılandırma ayarlarını belirtir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<yapılandırma>](../configuration-element.md)|Ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan her yapılandırma dosyasındaki kök öğeyi belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  

.NET `system.web` Framework `applicationPool` 3.5 SP1 itibariyle eleman ve alt öğesi .NET Çerçevesi'ne eklendi. Tümleşik modda IIS 7.0 veya daha sonraki sürümleri çalıştırdığınızda, bu öğe birleşimi iş parçacıklarını nasıl ASP.NET ve ASP.NET bir IIS uygulama havuzunda barındırıldığında istekleri nasıl sıraya oluşturduğunu yapılandırmanıza olanak tanır. Klasik veya ISAPI modunda IIS 7.0 veya daha sonraki sürümleri çalıştırırsanız, bu ayarlar yoksayılır.  
  
## <a name="example"></a>Örnek  

Aşağıdaki örnek, ASP.NET bir IIS uygulama havuzunda barındırıldığında aspnet.config dosyasındaki işlem genelindeASP.NET davranışın nasıl yapılandırılabildiğini gösterir. Örnek, IIS'nin Tümleşik modda çalıştığını ve uygulamanın .NET Framework 3.5 SP1 veya daha sonraki bir sürümü kullandığını varsayar. Bu davranış.NET Framework 3.5 SP1'den önceki .NET Framework sürümlerinde oluşmaz. Örnekteki değerler varsayılan değerlerdir.  
  
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
|Şema Adı||  
|Doğrulama Dosyası||  
|Boş Olabilir||  
  
## <a name="see-also"></a>Ayrıca bkz.

- [\<applicationPool> Elemanı (Web Ayarları)](applicationpool-element-web-settings.md)
