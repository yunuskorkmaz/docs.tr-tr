---
title: "&lt;applicationPool&gt; öğesi (Web Ayarları)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- applicationPool element
- <applicationPool> element
ms.assetid: 46d1baaa-e343-4639-b70d-2a43a9f62b2a
caps.latest.revision: "12"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 70119b3067342dc9bc93e0fb8a43a3242f2dacc8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltapplicationpoolgt-element-web-settings"></a>&lt;applicationPool&gt; öğesi (Web Ayarları)
Bir ASP.NET uygulaması Tümleşik modunda çalışan işlem genelinde yönetmek için ASP.NET tarafından kullanılan yapılandırma ayarlarını belirtir [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] veya sonraki bir sürümü.  
  
> [!IMPORTANT]
>  ASP.NET uygulamanızın üzerinde barındırılıyorsa, bu öğeyi ve bu özellik yalnızca iş desteklediği [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] veya sonraki sürümler.  
  
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
|`maxConcurrentRequestsPerCPU`|Kaç tane eşzamanlı istek CPU ASP.NET verir belirtir.|  
|`maxConcurrentThreadsPerCPU`|Kaç tane eşzamanlı iş parçacıklarının her CPU için bir uygulama havuzu için çalışabilir belirtir. CPU isteklere hizmet için kullanılabilir yönetilen iş parçacığı sayısını sınırlamak için bu ASP.NET eşzamanlılık denetlemek için alternatif bir yol sağlar. Varsayılan olarak bu ayarı CLR iş parçacığı havuzu da oluşturulabilir iş parçacığı sayısını sınırlar rağmen ASP.NET CPU oluşturulan iş parçacığı sayısını sınırlamaz anlamına gelir 0'dır.|  
|`requestQueueLimit`|ASP.NET için tek bir işlemde sıraya alınabilecek istekleri en fazla sayısını belirtir. İki veya daha fazla ASP.NET uygulamaları tek bir uygulama havuzunda çalıştırdığınızda, toplu uygulama havuzundaki herhangi bir uygulama için yapılan istekleri bu ayar tabi kümesidir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<System.Web >](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md)|ASP.NET ana bilgisayar uygulaması ile nasıl etkileşim kurduğunu hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Çalıştırdığınızda [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] veya sonraki bir sürümünü tümleşik modda bu öğe birleşimi, bir IIS uygulama havuzunda uygulama barındırıldığında ASP.NET iş parçacıkları ve Kuyruklar istekleri nasıl yönettiğini yapılandırmanıza olanak sağlar. IIS 6 çalıştırmak veya çalıştırdığınız [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] bu ayarlar, Klasik modda veya ISAPI modunu göz ardı edilir.  
  
 `applicationPool` Ayarları belirli bir .NET Framework sürümü üzerinde çalışan tüm uygulama havuzları için geçerlidir. Ayarları bir aspnet.config dosyasında bulunur. Bu dosyayı sürüm 2.0 ve .NET Framework 4.0 sürümü yok. (Sürüm 3.0 ve 3.5, .NET Framework sürüm 2.0 aspnet.config dosya paylaşımı.)  
  
> [!IMPORTANT]
>  Çalıştırırsanız [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] üzerinde [!INCLUDE[win7](../../../../../includes/win7-md.md)], her uygulama havuzu için ayrı aspnet.config dosyası yapılandırabilirsiniz. Bu, iş parçacıklarının her uygulama havuzu için performans uyarlamak sağlar.  
  
 İçin `maxConcurrentRequestsPerCPU` ayarı, varsayılan ayarı "5000" olan [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] CPU başına 5000 veya daha fazla isteği gerçekte yoksa etkili bir şekilde isteği başka bir deyişle azaltma devre dışı bırakır ASP.NET tarafından denetlenir. Varsayılan ayar yerine CLR iş parçacığı başına CPU eşzamanlılık otomatik olarak yönetmek için havuz bağlıdır. Zaman uyumsuz istek işlemeye kapsamlı kullanımını olun veya ağ g/ç üzerinde engellenen pek çok uzun süre çalışan istekleri sahip uygulamalar artan varsayılan sınır gelen yararlanacaktır [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]. Ayarı `maxConcurrentRequestsPerCPU` için ASP.NET isteklerini işlemek için yönetilen iş parçacığı kullanımını sıfır kapatır. Bir uygulama bir IIS uygulama havuzunda çalıştığında, istekleri IIS g/ç iş parçacığı üzerinde kalır ve bu nedenle eşzamanlılık IIS iş parçacığı ayarları tarafından kısıtlanıyor.  
  
 `requestQueueLimit` Ayarı aynı şekilde çalışır `requestQueueLimit` özniteliği [processModel](http://msdn.microsoft.com/en-us/4b8fe20e-74c8-4566-b72c-ce5f83c8e32d) ASP.NET uygulamaları için Web.config dosyalarında ayarlanan öğesi. Ancak, `requestQueueLimit` aspnet.config dosyasındaki ayarı geçersiz kılar `requestQueueLimit` Web.config dosyasındaki ayarlama. Diğer bir deyişle, her iki öznitelik ayarlarsanız (varsayılan olarak, bu doğrudur), `requestQueueLimit` aspnet.config dosyasındaki ayarı önceliklidir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, aşağıdaki durumlarda aspnet.config dosyasındaki ASP.NET işlem genelinde davranışı yapılandırmak gösterilmektedir:  
  
-   Uygulama içinde barındırılan bir [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] uygulama havuzu.  
  
-   [!INCLUDE[iisver](../../../../../includes/iisver-md.md)]Tümleşik modda çalışıyor.  
  
-   Uygulamayı kullanarak [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)] veya sonraki bir sürümü.  
  
 Örnek değerler varsayılan değerlerdir.  
  
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
 [\<System.Web > öğesi (Web Ayarları)](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md)
