---
title: <applicationPool> Öğesi (Web Ayarları)
ms.date: 03/30/2017
helpviewer_keywords:
- applicationPool element
- <applicationPool> element
ms.assetid: 46d1baaa-e343-4639-b70d-2a43a9f62b2a
ms.openlocfilehash: 963b25e57ae8c2cc59dcc3e50ae2a52cc04f54a8
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91185645"
---
# <a name="applicationpool-element-web-settings"></a>\<applicationPool> Öğesi (Web Ayarları)

Bir ASP.NET uygulaması IIS 7,0 veya sonraki bir sürümde tümleşik modda çalışırken, işlem genelinde davranışı yönetmek için ASP.NET tarafından kullanılan yapılandırma ayarlarını belirtir.  
  
> [!IMPORTANT]
> Bu öğe ve özellik yalnızca ASP.NET uygulamanız IIS 7,0 veya sonraki sürümlerde barındırılıyorsa çalışmayı destekler.  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.web>**](system-web-element-web-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<applicationPool>**  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<applicationPool
    maxConcurrentRequestsPerCPU="5000"
    maxConcurrentThreadsPerCPU="0"
    requestQueueLimit="5000" />  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  

Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`maxConcurrentRequestsPerCPU`|CPU başına kaç tane eş zamanlı istek ASP.NET izin verdiğini belirtir.|  
|`maxConcurrentThreadsPerCPU`|Her CPU için bir uygulama havuzu için kaç tane eş zamanlı iş parçacığının çalıştığını belirtir. Bu, isteklere hizmeti sağlamak için CPU başına kullanılabilecek yönetilen iş parçacıklarının sayısını sınırlayabilmeniz için ASP.NET eşzamanlılık denetiminin alternatif bir yolunu sağlar. Varsayılan olarak, bu ayar 0 ' dır, yani CLR iş parçacığı havuzu oluşturulabilen iş parçacığı sayısını da sınırladığından, bu ayar, ASP.NET CPU başına oluşturulabilen iş parçacığı sayısını sınırlamaz.|  
|`requestQueueLimit`|Tek bir işlemde ASP.NET için sıraya alınabilen en fazla istek sayısını belirtir. İki veya daha fazla ASP.NET uygulaması tek bir uygulama havuzunda çalıştığında, uygulama havuzundaki herhangi bir uygulamaya yapılan toplam istek kümesi bu ayara tabidir.|  
  
### <a name="child-elements"></a>Alt Öğeler  

 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<system.web>](system-web-element-web-settings.md)|ASP.NET 'in bir konak uygulamasıyla nasıl etkileşime girdiği hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  

IIS 7,0 veya sonraki bir sürümü tümleşik modda çalıştırdığınızda, bu öğe birleşimi, uygulamanın bir IIS uygulama havuzunda barındırıldığı zaman iş parçacıklarını ve sıra isteklerini nasıl yönettiğini ASP.NET yapılandırmanıza olanak tanır. IIS 6 veya IIS 7,0 'yi Klasik modda veya ISAPI modunda çalıştırırsanız, bu ayarlar yok sayılır.  
  
`applicationPool`Ayarlar .NET Framework belirli bir sürümünde çalışan tüm uygulama havuzları için geçerlidir. Ayarlar bir aspnet.config dosyasında bulunur. .NET Framework 2,0 ve 4,0 sürümleri için bu dosyanın bir sürümü vardır. (.NET Framework 3,0 sürümleri ve 3,5 sürümü aspnet.config dosyayı sürüm 2,0 ile paylaşır.)  
  
> [!IMPORTANT]
> IIS 7,0 'yi Windows 7 üzerinde çalıştırırsanız, her uygulama havuzu için ayrı bir aspnet.config dosyası yapılandırabilirsiniz. Bu, her uygulama havuzu için iş parçacıklarının performansını uyarlamanızı sağlar.  
  
Bu `maxConcurrentRequestsPerCPU` ayar için, "5000 .NET Framework" varsayılan ayarı, ASP.NET tarafından denetlenen istek azaltmasını etkin bir şekilde devre dışı bırakır, ancak CPU başına 5000 veya daha fazla istek olmadığı müddetçe. Varsayılan ayar, CLR iş parçacığı havuzuna CPU başına otomatik olarak yönetilecek şekilde değişir. Zaman uyumsuz istek işlemenin çok fazla kullanımını veya ağ g/ç 'de engellenen çok uzun süreli istekleri olan uygulamalar, .NET Framework 4 ' te artan varsayılan sınırdan faydalanır. Sıfıra ayarlandığında, `maxConcurrentRequestsPerCPU` ASP.net isteklerini işlemek için yönetilen iş parçacıklarının kullanımını devre dışı bırakır. Bir uygulama bir IIS uygulama havuzunda çalıştığında, istekler IIS g/ç iş parçacığında kalır ve bu nedenle eşzamanlılık IIS iş parçacığı ayarları tarafından kısıtlanır.  
  
`requestQueueLimit`Ayar, `requestQueueLimit` ASP.NET uygulamaları için Web.config dosyalarında ayarlanan [processModel](/previous-versions/dotnet/netframework-4.0/7w2sway1(v=vs.100)) öğesinin özniteliğiyle aynı şekilde çalışıyor. Ancak, `requestQueueLimit` bir aspnet.config dosyadaki ayar, `requestQueueLimit` Web.config bir dosyadaki ayarı geçersiz kılar. Diğer bir deyişle, her iki öznitelik de ayarlanırsa (varsayılan olarak, bu true ise) `requestQueueLimit` aspnet.config dosyadaki ayar önceliklidir.  
  
## <a name="example"></a>Örnek  

Aşağıdaki örnekte, aşağıdaki durumlarda aspnet.config dosyasında ASP.NET işlem genelinde davranışın nasıl yapılandırılacağı gösterilmektedir:  
  
- Uygulama bir IIS 7,0 uygulama havuzunda barındırılır.  
  
- IIS 7,0, tümleşik modda çalışıyor.  
  
- Uygulama .NET Framework 3,5 SP1 veya sonraki bir sürümünü kullanıyor.  
  
Örnekteki değerler varsayılan değerlerdir.  
  
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

- [\<system.web> Öğesi (Web ayarları)](system-web-element-web-settings.md)
