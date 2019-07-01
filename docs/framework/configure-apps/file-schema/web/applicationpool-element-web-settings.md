---
title: <applicationPool> Öğesi (Web Ayarları)
ms.date: 03/30/2017
helpviewer_keywords:
- applicationPool element
- <applicationPool> element
ms.assetid: 46d1baaa-e343-4639-b70d-2a43a9f62b2a
ms.openlocfilehash: d6c931ec904e9a7e58d5b747c74898208863b8e9
ms.sourcegitcommit: 2d42b7ae4252cfe1232777f501ea9ac97df31b63
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2019
ms.locfileid: "67486731"
---
# <a name="applicationpool-element-web-settings"></a>\<applicationPool > öğesi (Web Ayarları)
Bir ASP.NET uygulamasını IIS 7.0 veya sonraki bir sürümü üzerinde tümleşik modunda çalışırken işlem geneline yönelik davranışını yönetmek için ASP.NET tarafından kullanılan yapılandırma ayarlarını belirtir.  
  
> [!IMPORTANT]
>  ASP.NET uygulamanızı IIS 7.0 veya üzeri sürümleri üzerinde barındırılıyorsa bu öğeyi ve bu özellik yalnızca iş destekler.  
  
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
 IIS 7.0 veya üzeri bir sürüm tümleşik modda çalıştırdığınızda, bu öğe birleşim nasıl ASP.NET iş parçacıkları ve Kuyruklar isteklerini yöneten bir IIS uygulama havuzunda uygulama barındırıldığında yapılandırmanıza olanak verir. IIS 6 Çalıştır veya Klasik modda veya ISAPI modunu IIS 7.0 çalıştırmak, bu ayarları göz ardı edilir.  
  
 `applicationPool` .NET Framework'ün belirli bir sürümü çalıştıran tüm uygulama havuzları için ayarlar uygulanır. Ayarları bir aspnet.config dosyasında bulunur. Bu dosya sürümleri 2.0 ve .NET Framework 4.0 sürümü yoktur. (Sürüm 3.0 ve 3.5 .NET Framework sürüm 2.0 ile aspnet.config dosyayı paylaşın.)  
  
> [!IMPORTANT]
>  IIS 7.0 çalıştırırsanız, [!INCLUDE[win7](../../../../../includes/win7-md.md)], ayrı aspnet.config dosyası her bir uygulama havuzu için yapılandırabilirsiniz. Bu, her bir uygulama havuzu için bir iş parçacığı performansını uyumlu hale getirmenizi sağlar.  
  
 İçin `maxConcurrentRequestsPerCPU` ayarı varsayılan ayar "5000".NET Framework 4'te etkili bir şekilde ASP.NET tarafından denetlenen istek azaltma devre dışı bırakır gerçekten CPU başına 5000 veya daha fazla istek yoksa. Varsayılan ayar yerine CLR iş parçacığı eşzamanlılık CPU başına otomatik olarak yönetmek için havuzu bağlıdır. Zaman uyumsuz istek işlemeye kapsamlı kullanımını olun veya ağ g/ç üzerinde engellendi çok uzun süre çalışan istekleri olan uygulamaları .NET Framework 4'te artan varsayılan sınır yararlı olacaktır. Ayar `maxConcurrentRequestsPerCPU` için ASP.NET isteklerini işlemek için yönetilen iş parçacığı kullanımı sıfır kapatır. Bir IIS uygulama havuzunda uygulama çalıştığında, istekleri IIS g/ç iş parçacığı üzerinde kalır ve bu nedenle eşzamanlılık IIS iş parçacığı ayarları tarafından kısıtlanmış.  
  
 `requestQueueLimit` Ayarını aynı şekilde çalışır `requestQueueLimit` özniteliği [processModel](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7w2sway1(v=vs.100)) ASP.NET uygulamaları için Web.config dosyalarında ayarlanan öğesi. Ancak, `requestQueueLimit` aspnet.config dosyasındaki ayarını geçersiz kılar `requestQueueLimit` Web.config dosyasında ayarı. Diğer bir deyişle, her iki öznitelik ayarlarsanız (varsayılan olarak true budur), `requestQueueLimit` aspnet.config dosyasındaki ayarı öncelik alır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, aşağıdaki koşullarda aspnet.config dosyasında ASP.NET işlem geneline yönelik davranışını yapılandırmak gösterilmektedir:  
  
- Uygulama, IIS 7.0 uygulama havuzu içinde barındırılır.  
  
- IIS 7.0, tümleşik modunda çalışıyor.  
  
- Uygulama, .NET Framework 3.5 SP1 veya sonraki bir sürümünü kullanıyor.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [\<System.Web > öğesi (Web Ayarları)](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md)
