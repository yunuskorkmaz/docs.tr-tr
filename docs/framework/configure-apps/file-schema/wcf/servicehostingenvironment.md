---
title: <serviceHostingEnvironment>
ms.date: 03/30/2017
ms.assetid: 4f8a7c4f-e735-4987-979a-b74fcdae2652
ms.openlocfilehash: 16dacee89576b4ede0f2f80255ba8a0dcbc8c0dc
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64610181"
---
# <a name="servicehostingenvironment"></a>\<serviceHostingEnvironment >
Bu öğe, belirli taşıma için hizmet barındırma ortamını gösteren türü tanımlar. Bu öğe boş ise, varsayılan türü kullanılır. Bu öğe yalnızca uygulama veya makine düzeyinde yapılandırma dosyalarını kullanılabilir.  
  
 \<system.ServiceModel>  
\<serviceHostingEnvironment >  
  
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
|aspNetCompatibilityEnabled|ASP.NET uyumluluk modunun geçerli uygulama için açık durumda olup olmadığını gösteren bir Boole değeri. Varsayılan, `false` değeridir.<br /><br /> Bu öznitelik ayarlandığında `true`, Windows Communication Foundation (WCF) hizmetlere yönelik istekler ASP.NET HTTP ardışık düzende akış ve HTTP olmayan protokolleri üzerinden iletişim kullanılamaz. Daha fazla bilgi için [WCF hizmetleri ve ASP.NET](../../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md).|  
|minFreeMemoryPercentageToActivateService|Bir tamsayı en az bir WCF hizmet aktif edilmeden önce sistemde kullanılabilir olması gereken boş bellek miktarını belirtir. **Dikkat:**  Kısmi güven web.config dosyasındaki bir WCF Hizmeti ile birlikte bu öznitelik belirtmemeye sonuçlanır bir <xref:System.Security.SecurityException> hizmeti ne zaman çalıştırılır.|  
|multipleSiteBindingsEnabled|Çoklu IIS bağlamalarının her site etkin olup olmadığını belirten bir Boole değeri.<br /><br /> IIS web siteleri, sanal dizinler içeren sanal uygulamaların kapsayıcılarıdır oluşur. Uygulama bir sitedeki bir veya daha fazla IIS bağlama aracılığıyla erişilebilir. Bir IIS bağlaması iki bilgi parçasını sağlar: bağlama protokolü ve bağlama bilgileri. Bağlama Protokolü iletişim oluştuğu düzenini tanımlar ve bağlama bilgileri siteye erişmek için kullanılan bilgiler bunlardır. Bağlama Protokolü örneği HTTP olabilir, bu IP adresi, bağlama bilgileri içerebilir ancak bağlantı noktası, ana bilgisayar üstbilgisi.<br /><br /> Çoklu IIS bağlamalarının her Düzen başına birden çok taban adresi sonuçlanır site belirtme IIS destekler. Ancak, bir site altında barındırılan Windows Communication Foundation (WCF) hizmet şeması başına yalnızca bir baseAddress bağlama sağlar.<br /><br /> Çoklu IIS bağlamalarının her site için bir Windows Communication Foundation (WCF) hizmetini etkinleştirmek için bu öznitelik ayarlanan `true`. Birden çok site bağlaması yalnızca HTTP protokolü için desteklenip desteklenmediğini unutmayın. Yapılandırma dosyasındaki uç nokta adresi, tam bir URI olması gerekiyor.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<baseAddressPrefixFilters>](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddressprefixfilters.md)|Ön ek filtreler için hizmet ana bilgisayarı tarafından kullanılan tabanı belirten yapılandırma öğelerinin koleksiyonu.|  
|[\<serviceActivations >](../../../../../docs/framework/configure-apps/file-schema/wcf/serviceactivations.md)|Aktivasyon ayarlarını tanımlayan bir yapılandırma bölümü.|  
|[\<transportConfigurationTypes >](../../../../../docs/framework/configure-apps/file-schema/wcf/transportconfigurationtypes.md)|Belirli bir türünü belirleyen yapılandırma öğelerinin koleksiyonu.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|serviceModel|Tüm Windows Communication Foundation (WCF) yapılandırma öğelerinin kök öğe.|  
  
## <a name="remarks"></a>Açıklamalar  
 Varsayılan olarak, çalışma yan yana barındırılan uygulama etki alanı (AppDomain) içinde ASP.NET ile WCF hizmetleri. WCF ve ASP.NET aynı AppDomain içinde bulunabilir olsa da, WCF istekleri varsayılan olarak ASP.NET HTTP ardışık düzeni tarafından işlenmez. Sonuç olarak, ASP.NET uygulama platformu çeşitli öğeleri, WCF hizmetleri için kullanılamaz. Bunlar  
  
- ASP.NET dosya/URL yetkilendirmesi  
  
- ASP.NET kimliğe bürünme  
  
- Tanımlama bilgisi tabanlı oturum durumu  
  
- HttpContext.Current  
  
- Özel HTTP aracılığıyla işlem hattı genişletilebilirliği  
  
 WCF hizmetlerinizi ASP.NET bağlamda işlev ve yalnızca HTTP üzerinden iletişim kurması gerekiyorsa, WCF'ın ASP.NET uyumluluk modunun kullanabilirsiniz. Bu mod üzerinde ne zaman etkin `aspNetCompatibilityEnabled` özniteliği `true` uygulama düzeyinde. Hizmet uygulamaları, uyumluluk modu kullanarak çalıştırmak için kendi yeteneği bildirmelidir <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> sınıfı. Uyumluluk modu etkinleştirildiğinde  
  
- ASP.NET dosya/URL yetkilendirmesi, WCF yetkilendirme önce uygulanır. Bir yetkilendirme kararı, aktarım düzeyinde isteğin kimliğini temel alır. İleti düzeyinde kimlikleri yok sayılır.  
  
- ASP.NET kimliğe bürünme bağlamda yürütülecek WCF Hizmeti işlemlerini başlatın. ASP.NET kimliğe bürünme hem de WCF kimliğe bürünme belirli bir hizmet için etkinleştirilip etkinleştirilmediğini WCF kimliğe bürünülmüş bağlamdaki geçerlidir.  
  
- WCF hizmet kodundan HttpContext.Current kullanılabilir ve HTTP olmayan uç noktaları açıklamanızı hizmetler engellenir.  
  
- WCF istekleri ASP.NET işlem hattı tarafından işlenir. Gelen istekleri davranacak şekilde yapılandırılmış HttpModules işlem WCF istekleri de olabilir. Bunlar, ASP.NET platform bileşenleri içerebilir (örneğin, <xref:System.Web.SessionState.SessionStateModule>), üçüncü taraf özel modüller yanı sıra.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, ASP uyumluluk modunu etkinleştirmek gösterilmektedir.  
  
## <a name="code"></a>Kod  
  
```xml  
<serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [Barındırma](../../../../../docs/framework/wcf/feature-details/hosting.md)
- [WCF Hizmetleri ve ASP.NET](../../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)
