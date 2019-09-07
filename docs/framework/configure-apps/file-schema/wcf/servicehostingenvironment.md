---
title: <serviceHostingEnvironment>
ms.date: 03/30/2017
ms.assetid: 4f8a7c4f-e735-4987-979a-b74fcdae2652
ms.openlocfilehash: 165dbed1b78d00f8d4dd3e482b9fee8a23db60da
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399622"
---
# <a name="servicehostingenvironment"></a>\<serviceHostingEnvironment >
Bu öğe, belirli bir aktarım için hizmet barındırma ortamının örneklenme türünü tanımlar. Bu öğe boşsa, varsayılan tür kullanılır. Bu öğe, yalnızca uygulama veya makine düzeyinde yapılandırma dosyalarında kullanılabilir.  
  
[ **\<Yapılandırma >** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<serviceHostingEnvironment >**  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<serviceHostingEnvironment aspNetCompatibilityEnabled="Boolean"
                           minFreeMemoryPercentageToActivateService="Integer"
                           multipleSiteBindingsEnabled="Boolean">
  <baseAddressPrefixFilters>
    <add prefix="string" />
  </baseAddressPrefixFilters>
  <serviceActivations>
    <add factory="String"
         service="String" />
  </serviceActivations>
  <transportConfigurationTypes>
    <add name="String"
         transportConfigurationType="String" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|aspNetCompatibilityEnabled|Geçerli uygulama için ASP.NET uyumluluk modunun açık olup olmadığını gösteren bir Boole değeri. Varsayılan, `false` değeridir.<br /><br /> Bu öznitelik olarak `true`ayarlandığında, ASP.NET HTTP işlem hattı aracılığıyla Windows Communication Foundation (WCF) Hizmetleri akışına ve http olmayan protokoller üzerinden iletişime izin verilmez. Daha fazla bilgi için bkz. [WCF Hizmetleri ve ASP.net](../../../wcf/feature-details/wcf-services-and-aspnet.md).|  
|Minfreememoryyüztagetoactivateservice|Bir WCF hizmeti etkinleştirilmeden önce, sistem için kullanılabilir olması gereken minimum boş bellek miktarını belirten bir tamsayı. **Dikkatli**  Bu özniteliği bir WCF hizmetinin Web. config dosyasında kısmi güven ile birlikte belirtmek, hizmet çalıştırıldığında bir <xref:System.Security.SecurityException> ile sonuçlanır.|  
|multipleSiteBindingsEnabled|Site başına birden fazla IIS bağlaması etkinleştirilip etkinleştirilmeyeceğini belirten bir Boole değeri.<br /><br /> IIS, sanal dizinleri içeren sanal uygulamalara yönelik kapsayıcılar olan Web sitelerinden oluşur. Bir sitedeki uygulamaya bir veya daha fazla IIS bağlaması aracılığıyla erişilebilir. IIS bağlama iki bilgi parçası sağlar: bağlama protokolü ve bağlama bilgileri. Bağlama protokolü, iletişimin gerçekleştiği düzeni tanımlar ve bağlama bilgileri siteye erişmek için kullanılan bilgiler. Bağlama protokolüne bir örnek HTTP olabilir, ancak bağlama bilgileri bir IP adresi, bağlantı noktası, ana bilgisayar üstbilgisi vb. içerebilir.<br /><br /> IIS, her site için birden çok IIS bağlaması belirtmeyi destekler ve bu, her şema için birden çok temel adrese neden Ancak, bir site altında barındırılan bir Windows Communication Foundation (WCF) hizmeti, her şema için yalnızca bir baseAddress 'e bağlamaya izin verir.<br /><br /> Windows Communication Foundation (WCF) hizmeti için site başına birden çok IIS bağlamasını etkinleştirmek için, bu özniteliği olarak `true`ayarlayın. Birden çok site bağlamasının yalnızca HTTP protokolü için desteklendiğine dikkat edin. Yapılandırma dosyasındaki uç noktaların adresi, tüm URI olmalıdır.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<baseAddressPrefixFilters >](baseaddressprefixfilters.md)|Hizmet ana bilgisayarı tarafından kullanılan taban adresler için ön ek filtrelerini belirten yapılandırma öğeleri koleksiyonu.|  
|[\<Serviceetkinleştirmeleri >](serviceactivations.md)|Etkinleştirme ayarlarını açıklayan bir yapılandırma bölümü.|  
|[\<transportConfigurationTypes >](transportconfigurationtypes.md)|Belirli bir taşımanın türünü tanımlayan yapılandırma öğelerinin koleksiyonu.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|serviceModel|Tüm Windows Communication Foundation (WCF) yapılandırma öğelerinin kök öğesi.|  
  
## <a name="remarks"></a>Açıklamalar  
 Varsayılan olarak, WCF Hizmetleri barındırılan uygulama etki alanlarında (AppDomain) ASP.NET ile yan yana çalışır. WCF ve ASP.NET aynı AppDomain içinde bulunabilir olsa da, WCF istekleri varsayılan olarak ASP.NET HTTP işlem hattı tarafından işlenmez. Sonuç olarak, ASP.NET uygulama platformunun birkaç öğesi WCF Hizmetleri için kullanılamaz. Bunlar şunlardır  
  
- ASP.NET dosyası/URL yetkilendirmesi  
  
- ASP.NET Kimliğe bürünme  
  
- Tanımlama bilgisi tabanlı oturum durumu  
  
- HttpContext. Current  
  
- Özel HttpModule aracılığıyla işlem hattı genişletilebilirliği  
  
 WCF hizmetlerinizin ASP.NET bağlamında çalışması ve yalnızca HTTP üzerinden iletişim kurması gerekiyorsa, WCF 'nin ASP.NET uyumluluk modunu kullanabilirsiniz. `aspNetCompatibilityEnabled` Özniteliği uygulama düzeyinde olarak `true` ayarlandığında bu mod açıktır. Hizmet uygulamaları, <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> sınıfını kullanarak uyumluluk modunda çalıştırma imkanlarını bildirmelidir. Uyumluluk modu etkinleştirildiğinde,  
  
- ASP.NET dosya/URL yetkilendirmesi, WCF yetkilendirmesi öncesinde zorlanır. Yetkilendirme kararı, isteğin aktarım düzeyi kimliğine göre belirlenir. İleti düzeyindeki kimlikler yok sayılır.  
  
- WCF hizmeti işlemleri ASP.NET Kimliğe bürünme bağlamında yürütülmeye başlar. Belirli bir hizmet için hem ASP.NET Kimliğe bürünme hem de WCF kimliğe bürünme etkinleştirilirse, WCF kimliğe bürünme bağlamı geçerlidir.  
  
- HttpContext. Current, WCF hizmet kodundan kullanılabilir ve hizmetlerin HTTP olmayan uç noktaları kullanıma sunmasının engellenmektedir.  
  
- WCF istekleri ASP.NET işlem hattı tarafından işlenir. Gelen istekler üzerinde çalışacak şekilde yapılandırılmış HttpModules, WCF isteklerini de işleyebilir. Bunlar, ASP.NET Platform bileşenlerini (ör. <xref:System.Web.SessionState.SessionStateModule>) ve özel üçüncü taraf modüllerini içerebilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde, ASP uyumluluk modunun nasıl etkinleştirileceği gösterilmektedir.  
  
## <a name="code"></a>Kod  
  
```xml  
<serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [Barındırma](../../../wcf/feature-details/hosting.md)
- [WCF Hizmetleri ve ASP.NET](../../../wcf/feature-details/wcf-services-and-aspnet.md)
