---
title: <applicationPool> Öğesi (Web Ayarları)
ms.date: 03/30/2017
helpviewer_keywords:
- applicationPool element
- <applicationPool> element
ms.assetid: 46d1baaa-e343-4639-b70d-2a43a9f62b2a
ms.openlocfilehash: 6feaa801610fa0ffbbf47575f25aff29fa46a66c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152860"
---
# <a name="applicationpool-element-web-settings"></a>\<applicationPool> Elemanı (Web Ayarları)
ASP.NET tarafından, bir ASP.NET uygulaması IIS 7.0 veya daha sonraki bir sürümde Tümleşik modda çalışırken, işlem genelindeki davranışı yönetmek için kullanılan yapılandırma ayarlarını belirtir.  
  
> [!IMPORTANT]
> Bu öğe ve desteklediği özellik yalnızca ASP.NET uygulamanız IIS 7.0 veya sonraki sürümlerinde barındırılırsa çalışır.  
  
[**\<yapılandırma>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.web>**](system-web-element-web-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<uygulamaHavuz>**  
  
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
|`maxConcurrentRequestsPerCPU`|CPU başına kaç eşzamanlı istek ASP.NET izin verdiğini belirtir.|  
|`maxConcurrentThreadsPerCPU`|Her CPU için bir uygulama havuzu için kaç eşzamanlı iş parçacığının çalıştığını belirtir. Bu, istekleri sunmak için CPU başına kullanılabilecek yönetilen iş parçacığı sayısını sınırlayabilirsiniz, çünkü ASP.NET eşzamanlılık denetlemek için alternatif bir yol sağlar. Varsayılan olarak bu ayar 0'dır, bu da ASP.NET CPU başına oluşturulabilecek iş parçacığı sayısını sınırlamadığı anlamına gelir, ancak CLR iş parçacığı havuzu oluşturulabilecek iş parçacığı sayısını da sınırlar.|  
|`requestQueueLimit`|Tek bir işlemde ASP.NET için sıraya alınabilecek en fazla istek sayısını belirtir. İki veya daha fazla ASP.NET uygulama tek bir uygulama havuzunda çalıştırıldığında, uygulama havuzundaki herhangi bir uygulamaya yapılan toplu istek kümesi bu ayara tabidir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<system.web>](system-web-element-web-settings.md)|ASP.NET'nin ana bilgisayar uygulamasıyla nasıl etkileşimde bulunduğuhakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  

IIS 7.0 veya daha sonraki bir sürümü Tümleşik modunda çalıştırdığınızda, bu öğe birleşimi, uygulama bir IIS uygulama havuzunda barındırıldığında iş parçacığı ve kuyruk isteklerini nasıl ASP.NET yapılandırmanızı sağlar. IIS 6 çalıştırırsanız veya IIS 7.0'ı Klasik modda veya ISAPI modunda çalıştırırsanız, bu ayarlar yoksayılır.  
  
Ayarlar,.NET `applicationPool` Framework'ün belirli bir sürümünde çalışan tüm uygulama havuzları için geçerlidir. Ayarlar bir aspnet.config dosyasında bulunur. Bu dosyanın .NET Framework'ün 2.0 ve 4.0 sürümleri için bir sürümü vardır. (.NET Framework'ün 3.0 ve 3.5 sürümleri aspnet.config dosyasını sürüm 2.0 ile paylaşır.)  
  
> [!IMPORTANT]
> Windows 7'de IIS 7.0 çalıştırıyorsanız, her uygulama havuzu için ayrı bir aspnet.config dosyası yapılandırabilirsiniz. Bu, her uygulama havuzu için iş parçacıklarının performansını uyarlamanızı sağlar.  
  
Ayar `maxConcurrentRequestsPerCPU` için, .NET Framework 4'teki varsayılan "5000" ayarı, CPU başına 5000 veya daha fazla isteğiniz yoksa, ASP.NET tarafından denetlenir olan istek azaltmayı etkin bir şekilde kapatır. Varsayılan ayar, bunun yerine CPU başına eşzamanlılık otomatik olarak yönetmek için CLR iş parçacığı havuzuna bağlıdır. Eşzamanlı istek işlemeyi kapsamlı olarak kullanan veya ağ I/O'da uzun süreli istekleri engellenen uygulamalar,.NET Framework 4'teki artan varsayılan sınırdan yararlanır. Sıfıra ayar, `maxConcurrentRequestsPerCPU` ASP.NET isteklerini işlemek için yönetilen iş parçacıklarının kullanımını kapatır. Bir uygulama bir IIS uygulama havuzunda çalıştığında, istekler IIS G/Ç iş parçacığında kalır ve bu nedenle eşzamanlılık IIS iş parçacığı ayarları tarafından daraltılır.  
  
Ayar, `requestQueueLimit` ASP.NET uygulamalar için `requestQueueLimit` Web.config dosyalarında ayarlanan [işlemModel](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7w2sway1(v=vs.100)) öğesinin özniteliğiyle aynı şekilde çalışır. Ancak, `requestQueueLimit` aspnet.config dosyasındaki ayar, `requestQueueLimit` Web.config dosyasındaki ayarı geçersiz kılar. Başka bir deyişle, her iki öznitelik de ayarlanmışsa (varsayılan olarak bu doğrudur), aspnet.config dosyasındaki `requestQueueLimit` ayar önceliklidir.  
  
## <a name="example"></a>Örnek  

Aşağıdaki örnek, aşağıdaki durumlarda aspnet.config dosyasındaki ASP.NET işlem genelindedavranışın nasıl yapılandırılabildiğini gösterir:  
  
- Uygulama, IIS 7.0 uygulama havuzunda barındırılır.  
  
- IIS 7.0 Tümleşik modda çalışıyor.  
  
- Uygulama .NET Framework 3.5 SP1 veya daha sonraki bir sürümü kullanıyor.  
  
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
|Şema Adı||  
|Doğrulama Dosyası||  
|Boş Olabilir||  
  
## <a name="see-also"></a>Ayrıca bkz.

- [\<system.web> Element (Web Ayarları)](system-web-element-web-settings.md)
