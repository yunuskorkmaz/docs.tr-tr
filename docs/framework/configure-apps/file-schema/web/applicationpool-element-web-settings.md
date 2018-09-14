---
title: '&lt;applicationPool&gt; öğesi (Web Ayarları)'
ms.date: 03/30/2017
helpviewer_keywords:
- applicationPool element
- <applicationPool> element
ms.assetid: 46d1baaa-e343-4639-b70d-2a43a9f62b2a
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 1a129abca5888120d03c42689ac825d768733a9d
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45515645"
---
# <a name="ltapplicationpoolgt-element-web-settings"></a>&lt;applicationPool&gt; öğesi (Web Ayarları)
Bir ASP.NET uygulaması tümleşik modda çalıştırılan işlem genelinde yönetmesi için ASP.NET tarafından kullanılan yapılandırma ayarlarını belirten [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] veya sonraki bir sürümü.  
  
> [!IMPORTANT]
>  ASP.NET uygulamanızı üzerinde barındırılıyorsa bu öğeyi ve bu özellik yalnızca iş desteklediği [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] veya sonraki sürümler.  
  
 \<Yapılandırma >  
\<System.Web > öğesi (Web Ayarları)  
\<applicationPool > öğesi (Web Ayarları)  
  
## <a name="syntax"></a>Sözdizimi  
  
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
|`maxConcurrentRequestsPerCPU`|CPU ASP.NET sağlayan kaç tane eş zamanlı istek belirtir.|  
|`maxConcurrentThreadsPerCPU`|Kaç tane eşzamanlı iş parçacığı her CPU için bir uygulama havuzu için çalışabilir belirtir. CPU isteklere hizmet için kullanılabilir yönetilen iş parçacığı sayısı sınırı, çünkü bu ASP.NET eşzamanlılık denetimi için alternatif bir yol sağlar. Varsayılan olarak bu ayar, CLR iş parçacığı havuzu da oluşturulabilir iş parçacığı sayısını sınırlar olsa da ASP.NET CPU oluşturulan iş parçacığı sayısını sınırlamaz anlamına gelen 0 ' dır.|  
|`requestQueueLimit`|ASP.NET için tek bir işlemde sıraya alınabilecek istekleri en yüksek sayısını belirtir. İki veya daha fazla ASP.NET uygulamaları tek bir uygulama havuzunda çalıştırdığınızda, toplu uygulama havuzundaki herhangi bir uygulama için yapılan istekleri bu ayar tabi kümesidir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<System.Web >](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md)|ASP.NET bir ana bilgisayar uygulaması ile nasıl etkileşim kurduğunu hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Çalıştırdığınızda [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] veya sonraki bir sürümünü tümleşik modunda bu öğe birleşimi, nasıl ASP.NET iş parçacıkları ve Kuyruklar isteklerini yöneten bir IIS uygulama havuzunda uygulama barındırıldığında yapılandırmanıza olanak sağlar. IIS 6 çalıştırın ya da çalıştırdığınız [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] Klasik modda veya ISAPI modunu, bu ayarları göz ardı edilir.  
  
 `applicationPool` .NET Framework'ün belirli bir sürümü çalıştıran tüm uygulama havuzları için ayarlar uygulanır. Ayarları bir aspnet.config dosyasında bulunur. Bu dosya sürümleri 2.0 ve .NET Framework 4.0 sürümü yoktur. (Sürüm 3.0 ve 3.5 .NET Framework sürüm 2.0 ile aspnet.config dosyayı paylaşın.)  
  
> [!IMPORTANT]
>  Çalıştırırsanız [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] üzerinde [!INCLUDE[win7](../../../../../includes/win7-md.md)], ayrı aspnet.config dosyası her bir uygulama havuzu için yapılandırabilirsiniz. Bu, her bir uygulama havuzu için bir iş parçacığı performansını uyumlu hale getirmenizi sağlar.  
  
 İçin `maxConcurrentRequestsPerCPU` ayarı, varsayılan ayar "5000" [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] gerçekten CPU başına 5000 veya daha fazla istek olmadığı sürece etkili bir şekilde başka bir deyişle, istek azaltma devre dışı bırakır ASP.NET tarafından denetlenir. Varsayılan ayar yerine CLR iş parçacığı eşzamanlılık CPU başına otomatik olarak yönetmek için havuzu bağlıdır. Zaman uyumsuz istek işlemeye kapsamlı kullanımını olun veya ağ g/ç üzerinde engellendi çok uzun süre çalışan istekleri olan uygulamaların, artırılmış varsayılan sınırı'ndan yararlanacaktır [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]. Ayar `maxConcurrentRequestsPerCPU` için ASP.NET isteklerini işlemek için yönetilen iş parçacığı kullanımı sıfır kapatır. Bir IIS uygulama havuzunda uygulama çalıştığında, istekleri IIS g/ç iş parçacığı üzerinde kalır ve bu nedenle eşzamanlılık IIS iş parçacığı ayarları tarafından kısıtlanmış.  
  
 `requestQueueLimit` Ayarını aynı şekilde çalışır `requestQueueLimit` özniteliği [processModel](https://msdn.microsoft.com/library/4b8fe20e-74c8-4566-b72c-ce5f83c8e32d) ASP.NET uygulamaları için Web.config dosyalarında ayarlanan öğesi. Ancak, `requestQueueLimit` aspnet.config dosyasındaki ayarını geçersiz kılar `requestQueueLimit` Web.config dosyasında ayarı. Diğer bir deyişle, her iki öznitelik ayarlarsanız (varsayılan olarak true budur), `requestQueueLimit` aspnet.config dosyasındaki ayarı öncelik alır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, aşağıdaki koşullarda aspnet.config dosyasında ASP.NET işlem geneline yönelik davranışını yapılandırmak gösterilmektedir:  
  
-   Uygulama içinde barındırılan bir [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] uygulama havuzu.  
  
-   [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] Tümleşik modda çalışıyor.  
  
-   Uygulamayı kullanarak [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)] veya sonraki bir sürümü.  
  
 Varsayılan değerleri örnekte değerlerdir.  
  
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
 [\<System.Web > öğesi (Web Ayarları)](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md)
