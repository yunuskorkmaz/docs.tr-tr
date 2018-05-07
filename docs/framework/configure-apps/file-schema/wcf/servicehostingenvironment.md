---
title: '&lt;serviceHostingEnvironment&gt;'
ms.date: 03/30/2017
ms.assetid: 4f8a7c4f-e735-4987-979a-b74fcdae2652
ms.openlocfilehash: 1d9edec2c5bbddefe575952d591416353d603d33
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="ltservicehostingenvironmentgt"></a>&lt;serviceHostingEnvironment&gt;
Bu öğe için belirli bir barındırma ortamı hizmeti başlatır türü tanımlar. Bu öğe boş ise, varsayılan türü kullanılır. Bu öğe yalnızca uygulama veya makine düzeyi yapılandırma dosyaları kullanılır.  
  
 \<system.ServiceModel>  
\<ServiceHostingEnvironment >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<serviceHostingEnvironment aspNetCompatibilityEnabled="Boolean" 
                           minFreeMemoryPercentageToActivateService="Integer" 
                           multipleSiteBindingsEnabled="Boolean">
  <baseAddressPrefixFilters>
    <add prefix="string" />
  </baseAddressPrefixFilters>
  <serviceActivations>
    <add factory="String" service="String" />
  </serviceActivations>
  <transportConfigurationTypes>
    <add name="String" transportConfigurationType="String" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|aspNetCompatibilityEnabled|ASP.NET uyumluluğu modu geçerli uygulama için açık durumda olup olmadığını gösteren bir Boole değeri. Varsayılan, `false` değeridir.<br /><br /> Bu öznitelik ayarlandığında `true`, Windows Communication Foundation (WCF) hizmetlerini isteklerine ASP.NET HTTP ardışık düzen üzerinden akış ve HTTP olmayan protokolleri üzerinden iletişim yasaktır. Daha fazla bilgi için bkz: [WCF hizmetleri ve ASP.NET](../../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md).|  
|minFreeMemoryPercentageToActivateService|En az bir WCF hizmeti etkin hale getirilmeden önce sistemi için kullanılabilir olması gereken boş bellek miktarını belirten bir tamsayı. **Dikkat:** bu öznitelik bir WCF Hizmeti web.config dosyasında kısmi güven birlikte belirtme neden olur bir <xref:System.Security.SecurityException> hizmet çalıştırıldığında.|  
|multipleSiteBindingsEnabled|Site başına birden çok IIS bağlamaları etkinleştirilip etkinleştirilmediğini belirten bir Boole değeri.<br /><br /> Sanal dizinler içeren sanal uygulamalar için kapsayıcılardır web siteleri, IIS oluşur. Uygulama bir sitedeki bir veya daha fazla IIS bağlama aracılığıyla erişilebilir. Bir IIS bağlaması iki parça bilgi sağlar: bir bağlama protokolü ve bağlama bilgileri. Bağlama protokolü üzerinden iletişimin şeması tanımlar ve bağlama bilgileri siteye erişmek için kullanılan bilgilerdir. Bağlama bilgileri bir IP adresi içerebilir oysa bağlama Protokolü örneği HTTP olabilir bağlantı noktası, ana bilgisayar üstbilgisi.<br /><br /> IIS, düzeni başına birden çok taban adresi sonuçlanır site başına birden çok IIS bağlamaları belirtmeyi destekler. Ancak, bir site altında barındırılan bir Windows Communication Foundation (WCF) hizmetini düzeni başına yalnızca bir baseAddress bağlama sağlar.<br /><br /> Site başına birden çok IIS bağlamaları Windows Communication Foundation (WCF) hizmetini etkinleştirmek için bu öznitelik ayarlamak `true`. Birden çok site bağlaması yalnızca HTTP protokolü için desteklendiğini unutmayın. Uç noktaları yapılandırma dosyasındaki adresi tam bir URI olması gerekir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<baseAddressPrefixFilters >](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddressprefixfilters.md)|Hizmet ana bilgisayar tarafından kullanılan temel adres için önek filtreleri belirtin yapılandırma öğeleri koleksiyonu.|  
|[\<serviceActivations >](../../../../../docs/framework/configure-apps/file-schema/wcf/serviceactivations.md)|Etkinleştirme ayarlarını açıklayan bir yapılandırma bölümü.|  
|[\<transportConfigurationTypes >](../../../../../docs/framework/configure-apps/file-schema/wcf/transportconfigurationtypes.md)|Belirli bir tür belirleme yapılandırma öğeleri koleksiyonu.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|ServiceModel|Tüm Windows Communication Foundation (WCF) yapılandırma öğelerinin kök öğesi.|  
  
## <a name="remarks"></a>Açıklamalar  
 Varsayılan olarak, çalışma yan yana barındırılan uygulama etki alanları (AppDomain) ASP.NET ile WCF hizmetleri. WCF ve ASP.NET aynı AppDomain içinde bulunabilir olsa bile, WCF istekleri varsayılan olarak ASP.NET HTTP ardışık düzen tarafından işlenmez. Sonuç olarak, ASP.NET uygulama platformu çeşitli öğeleri, WCF hizmetleri için kullanılamaz. Bunlar  
  
-   ASP.NET dosya/URL yetkilendirmesi  
  
-   ASP.NET kimliğe bürünme  
  
-   Tanımlama bilgisi tabanlı oturum durumu  
  
-   HttpContext.Current  
  
-   Özel HTTP üzerinden ardışık düzen genişletilebilirliği  
  
 WCF hizmetleri ASP.NET bağlamında işlev ve yalnızca HTTP üzerinden iletişim kurmak gerekiyorsa, WCF'ın ASP.NET uyumluluğu modunu kullanabilirsiniz. Bu modu etkin olduğunda açılır `aspNetCompatibilityEnabled` özniteliği `true` uygulama düzeyinde. Hizmet uygulamaları, uyumluluk moduyla çalıştırmak için kendi yeteneği bildirmelidir <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> sınıfı. Uyumluluk modu etkinleştirildiğinde  
  
-   ASP.NET dosya/URL yetkilendirmesi, WCF yetkilendirme önce uygulanır. Bir yetkilendirme kararı istek aktarım düzeyinde kimliğini temel alır. İleti düzeyinde kimlikleri göz ardı edilir.  
  
-   ASP.NET kimliğe bürünme bağlamda yürütmek WCF Hizmeti işlemlerini başlatın. ASP.NET kimliğe bürünme ve WCF kimliğe bürünme için belirli bir hizmet etkinleştirilirse, WCF kimliğe bürünülmüş bağlamdaki geçerlidir.  
  
-   WCF hizmet kodundan HttpContext.Current kullanılabilir ve Hizmetleri HTTP olmayan uç noktalarını gösterme engellenir.  
  
-   WCF istekler ASP.NET ardışık düzen tarafından işlenir. Gelen isteklerde davranmak üzere yapılandırılmış HttpModules işlem WCF istekleri de gruplandırabilirsiniz. Bunlar, ASP.NET platform bileşenleri içerebilir (örneğin, <xref:System.Web.SessionState.SessionStateModule>), özel üçüncü taraf modülleri yanı sıra.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, ASP uyumluluk modunu etkinleştirmek gösterilmiştir.  
  
## <a name="code"></a>Kod  
  
```xml  
<serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>  
 <xref:System.ServiceModel.ServiceHostingEnvironment>  
 [Barındırma](../../../../../docs/framework/wcf/feature-details/hosting.md)  
 [WCF Hizmetleri ve ASP.NET](../../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)
