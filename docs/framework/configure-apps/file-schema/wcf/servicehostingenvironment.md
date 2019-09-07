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
# <a name="servicehostingenvironment"></a><span data-ttu-id="1a568-101">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="1a568-101">\<serviceHostingEnvironment></span></span>
<span data-ttu-id="1a568-102">Bu öğe, belirli bir aktarım için hizmet barındırma ortamının örneklenme türünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1a568-102">This element defines the type the service hosting environment instantiates for a particular transport.</span></span> <span data-ttu-id="1a568-103">Bu öğe boşsa, varsayılan tür kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1a568-103">If this element is empty, the default type is used.</span></span> <span data-ttu-id="1a568-104">Bu öğe, yalnızca uygulama veya makine düzeyinde yapılandırma dosyalarında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1a568-104">This element can only be used at the application or machine level configuration files.</span></span>  
  
<span data-ttu-id="1a568-105">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="1a568-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="1a568-106">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="1a568-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="1a568-107">&nbsp;&nbsp;&nbsp;&nbsp; **\<serviceHostingEnvironment >**</span><span class="sxs-lookup"><span data-stu-id="1a568-107">&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceHostingEnvironment>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a568-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1a568-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1a568-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="1a568-109">Attributes and Elements</span></span>  
 <span data-ttu-id="1a568-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1a568-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1a568-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="1a568-111">Attributes</span></span>  
  
|<span data-ttu-id="1a568-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="1a568-112">Attribute</span></span>|<span data-ttu-id="1a568-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1a568-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1a568-114">aspNetCompatibilityEnabled</span><span class="sxs-lookup"><span data-stu-id="1a568-114">aspNetCompatibilityEnabled</span></span>|<span data-ttu-id="1a568-115">Geçerli uygulama için ASP.NET uyumluluk modunun açık olup olmadığını gösteren bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="1a568-115">A Boolean value indicating whether the ASP.NET compatibility mode has been turned on for the current application.</span></span> <span data-ttu-id="1a568-116">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="1a568-116">The default is `false`.</span></span><br /><br /> <span data-ttu-id="1a568-117">Bu öznitelik olarak `true`ayarlandığında, ASP.NET HTTP işlem hattı aracılığıyla Windows Communication Foundation (WCF) Hizmetleri akışına ve http olmayan protokoller üzerinden iletişime izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="1a568-117">When this attribute is set to `true`, requests to Windows Communication Foundation (WCF) services flow through the ASP.NET HTTP pipeline, and communication over non-HTTP protocols is prohibited.</span></span> <span data-ttu-id="1a568-118">Daha fazla bilgi için bkz. [WCF Hizmetleri ve ASP.net](../../../wcf/feature-details/wcf-services-and-aspnet.md).</span><span class="sxs-lookup"><span data-stu-id="1a568-118">For more information, see [WCF Services and ASP.NET](../../../wcf/feature-details/wcf-services-and-aspnet.md).</span></span>|  
|<span data-ttu-id="1a568-119">Minfreememoryyüztagetoactivateservice</span><span class="sxs-lookup"><span data-stu-id="1a568-119">minFreeMemoryPercentageToActivateService</span></span>|<span data-ttu-id="1a568-120">Bir WCF hizmeti etkinleştirilmeden önce, sistem için kullanılabilir olması gereken minimum boş bellek miktarını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="1a568-120">An integer that specifies the minimum amount of free memory that should be available to the system, before a WCF service can be activated.</span></span> <span data-ttu-id="1a568-121">**Dikkatli**  Bu özniteliği bir WCF hizmetinin Web. config dosyasında kısmi güven ile birlikte belirtmek, hizmet çalıştırıldığında bir <xref:System.Security.SecurityException> ile sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="1a568-121">**Caution:**  Specifying this attribute along with partial trust in the web.config file of a WCF service will result in a <xref:System.Security.SecurityException> when the service is run.</span></span>|  
|<span data-ttu-id="1a568-122">multipleSiteBindingsEnabled</span><span class="sxs-lookup"><span data-stu-id="1a568-122">multipleSiteBindingsEnabled</span></span>|<span data-ttu-id="1a568-123">Site başına birden fazla IIS bağlaması etkinleştirilip etkinleştirilmeyeceğini belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="1a568-123">A Boolean value that specifies whether multiple IIS bindings per site is enabled.</span></span><br /><br /> <span data-ttu-id="1a568-124">IIS, sanal dizinleri içeren sanal uygulamalara yönelik kapsayıcılar olan Web sitelerinden oluşur.</span><span class="sxs-lookup"><span data-stu-id="1a568-124">IIS consists of web sites, which are containers for virtual applications containing virtual directories.</span></span> <span data-ttu-id="1a568-125">Bir sitedeki uygulamaya bir veya daha fazla IIS bağlaması aracılığıyla erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="1a568-125">The application in a site can be accessed through one or more IIS binding.</span></span> <span data-ttu-id="1a568-126">IIS bağlama iki bilgi parçası sağlar: bağlama protokolü ve bağlama bilgileri.</span><span class="sxs-lookup"><span data-stu-id="1a568-126">An IIS binding provides two pieces of information: a binding protocol and binding information.</span></span> <span data-ttu-id="1a568-127">Bağlama protokolü, iletişimin gerçekleştiği düzeni tanımlar ve bağlama bilgileri siteye erişmek için kullanılan bilgiler.</span><span class="sxs-lookup"><span data-stu-id="1a568-127">Binding protocol defines the scheme over which communication occurs, and binding information is the information used to access the site.</span></span> <span data-ttu-id="1a568-128">Bağlama protokolüne bir örnek HTTP olabilir, ancak bağlama bilgileri bir IP adresi, bağlantı noktası, ana bilgisayar üstbilgisi vb. içerebilir.</span><span class="sxs-lookup"><span data-stu-id="1a568-128">An example of a binding protocol can be HTTP, whereas binding information can contain an IP address, Port, host header, etc.</span></span><br /><br /> <span data-ttu-id="1a568-129">IIS, her site için birden çok IIS bağlaması belirtmeyi destekler ve bu, her şema için birden çok temel adrese neden</span><span class="sxs-lookup"><span data-stu-id="1a568-129">IIS supports specifying multiple IIS bindings per site, which results in multiple base addresses per scheme.</span></span> <span data-ttu-id="1a568-130">Ancak, bir site altında barındırılan bir Windows Communication Foundation (WCF) hizmeti, her şema için yalnızca bir baseAddress 'e bağlamaya izin verir.</span><span class="sxs-lookup"><span data-stu-id="1a568-130">However, a Windows Communication Foundation (WCF) service hosted under a site allows binding to only one baseAddress per scheme.</span></span><br /><br /> <span data-ttu-id="1a568-131">Windows Communication Foundation (WCF) hizmeti için site başına birden çok IIS bağlamasını etkinleştirmek için, bu özniteliği olarak `true`ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="1a568-131">To enable multiple IIS bindings per site for a Windows Communication Foundation (WCF) service, set this attribute to `true`.</span></span> <span data-ttu-id="1a568-132">Birden çok site bağlamasının yalnızca HTTP protokolü için desteklendiğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="1a568-132">Notice that multiple site binding is supported only for the HTTP protocol.</span></span> <span data-ttu-id="1a568-133">Yapılandırma dosyasındaki uç noktaların adresi, tüm URI olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1a568-133">The address of endpoints in the configuration file needs to be a complete URI.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1a568-134">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="1a568-134">Child Elements</span></span>  
  
|<span data-ttu-id="1a568-135">Öğe</span><span class="sxs-lookup"><span data-stu-id="1a568-135">Element</span></span>|<span data-ttu-id="1a568-136">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1a568-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1a568-137">\<baseAddressPrefixFilters ></span><span class="sxs-lookup"><span data-stu-id="1a568-137">\<baseAddressPrefixFilters></span></span>](baseaddressprefixfilters.md)|<span data-ttu-id="1a568-138">Hizmet ana bilgisayarı tarafından kullanılan taban adresler için ön ek filtrelerini belirten yapılandırma öğeleri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="1a568-138">A collection of configuration elements that specify prefix filters for the base addresses used by the service host.</span></span>|  
|[<span data-ttu-id="1a568-139">\<Serviceetkinleştirmeleri ></span><span class="sxs-lookup"><span data-stu-id="1a568-139">\<serviceActivations></span></span>](serviceactivations.md)|<span data-ttu-id="1a568-140">Etkinleştirme ayarlarını açıklayan bir yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="1a568-140">A configuration section that describes activation settings.</span></span>|  
|[<span data-ttu-id="1a568-141">\<transportConfigurationTypes ></span><span class="sxs-lookup"><span data-stu-id="1a568-141">\<transportConfigurationTypes></span></span>](transportconfigurationtypes.md)|<span data-ttu-id="1a568-142">Belirli bir taşımanın türünü tanımlayan yapılandırma öğelerinin koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="1a568-142">A collection of configuration elements that identify the type of a particular transport.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1a568-143">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="1a568-143">Parent Elements</span></span>  
  
|<span data-ttu-id="1a568-144">Öğe</span><span class="sxs-lookup"><span data-stu-id="1a568-144">Element</span></span>|<span data-ttu-id="1a568-145">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1a568-145">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1a568-146">serviceModel</span><span class="sxs-lookup"><span data-stu-id="1a568-146">serviceModel</span></span>|<span data-ttu-id="1a568-147">Tüm Windows Communication Foundation (WCF) yapılandırma öğelerinin kök öğesi.</span><span class="sxs-lookup"><span data-stu-id="1a568-147">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1a568-148">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1a568-148">Remarks</span></span>  
 <span data-ttu-id="1a568-149">Varsayılan olarak, WCF Hizmetleri barındırılan uygulama etki alanlarında (AppDomain) ASP.NET ile yan yana çalışır.</span><span class="sxs-lookup"><span data-stu-id="1a568-149">By default, WCF services run side-by-side with ASP.NET in hosted Application Domains (AppDomain).</span></span> <span data-ttu-id="1a568-150">WCF ve ASP.NET aynı AppDomain içinde bulunabilir olsa da, WCF istekleri varsayılan olarak ASP.NET HTTP işlem hattı tarafından işlenmez.</span><span class="sxs-lookup"><span data-stu-id="1a568-150">Even though WCF and ASP.NET can coexist in the same AppDomain, WCF requests are not processed by the ASP.NET HTTP Pipeline by default.</span></span> <span data-ttu-id="1a568-151">Sonuç olarak, ASP.NET uygulama platformunun birkaç öğesi WCF Hizmetleri için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="1a568-151">As a result, several elements of the ASP.NET application platform are not available to WCF services.</span></span> <span data-ttu-id="1a568-152">Bunlar şunlardır</span><span class="sxs-lookup"><span data-stu-id="1a568-152">These include</span></span>  
  
- <span data-ttu-id="1a568-153">ASP.NET dosyası/URL yetkilendirmesi</span><span class="sxs-lookup"><span data-stu-id="1a568-153">ASP.NET File/URL Authorization</span></span>  
  
- <span data-ttu-id="1a568-154">ASP.NET Kimliğe bürünme</span><span class="sxs-lookup"><span data-stu-id="1a568-154">ASP.NET Impersonation</span></span>  
  
- <span data-ttu-id="1a568-155">Tanımlama bilgisi tabanlı oturum durumu</span><span class="sxs-lookup"><span data-stu-id="1a568-155">Cookie-based Session State</span></span>  
  
- <span data-ttu-id="1a568-156">HttpContext. Current</span><span class="sxs-lookup"><span data-stu-id="1a568-156">HttpContext.Current</span></span>  
  
- <span data-ttu-id="1a568-157">Özel HttpModule aracılığıyla işlem hattı genişletilebilirliği</span><span class="sxs-lookup"><span data-stu-id="1a568-157">Pipeline Extensibility via custom HttpModule</span></span>  
  
 <span data-ttu-id="1a568-158">WCF hizmetlerinizin ASP.NET bağlamında çalışması ve yalnızca HTTP üzerinden iletişim kurması gerekiyorsa, WCF 'nin ASP.NET uyumluluk modunu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1a568-158">If your WCF services need to function in the ASP.NET context, and communicate only over HTTP, you can use WCF’s ASP.NET compatibility mode.</span></span> <span data-ttu-id="1a568-159">`aspNetCompatibilityEnabled` Özniteliği uygulama düzeyinde olarak `true` ayarlandığında bu mod açıktır.</span><span class="sxs-lookup"><span data-stu-id="1a568-159">This mode is turned on when the `aspNetCompatibilityEnabled` attribute is set to `true` at the application level.</span></span> <span data-ttu-id="1a568-160">Hizmet uygulamaları, <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> sınıfını kullanarak uyumluluk modunda çalıştırma imkanlarını bildirmelidir.</span><span class="sxs-lookup"><span data-stu-id="1a568-160">Service implementations must declare their ability to run in compatibility mode using the <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> class.</span></span> <span data-ttu-id="1a568-161">Uyumluluk modu etkinleştirildiğinde,</span><span class="sxs-lookup"><span data-stu-id="1a568-161">When the compatibility mode is enabled,</span></span>  
  
- <span data-ttu-id="1a568-162">ASP.NET dosya/URL yetkilendirmesi, WCF yetkilendirmesi öncesinde zorlanır.</span><span class="sxs-lookup"><span data-stu-id="1a568-162">ASP.NET File/URL Authorization is enforced prior to WCF authorization.</span></span> <span data-ttu-id="1a568-163">Yetkilendirme kararı, isteğin aktarım düzeyi kimliğine göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="1a568-163">An authorization decision is based on the transport-level identity of the request.</span></span> <span data-ttu-id="1a568-164">İleti düzeyindeki kimlikler yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="1a568-164">Identities at the message level are ignored.</span></span>  
  
- <span data-ttu-id="1a568-165">WCF hizmeti işlemleri ASP.NET Kimliğe bürünme bağlamında yürütülmeye başlar.</span><span class="sxs-lookup"><span data-stu-id="1a568-165">WCF service operations start to execute in the ASP.NET impersonation context.</span></span> <span data-ttu-id="1a568-166">Belirli bir hizmet için hem ASP.NET Kimliğe bürünme hem de WCF kimliğe bürünme etkinleştirilirse, WCF kimliğe bürünme bağlamı geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="1a568-166">If both ASP.NET impersonation and WCF impersonation are enabled for a specific service, the WCF impersonation context applies.</span></span>  
  
- <span data-ttu-id="1a568-167">HttpContext. Current, WCF hizmet kodundan kullanılabilir ve hizmetlerin HTTP olmayan uç noktaları kullanıma sunmasının engellenmektedir.</span><span class="sxs-lookup"><span data-stu-id="1a568-167">HttpContext.Current can be used from WCF service code, and services are prevented from exposing non-HTTP endpoints.</span></span>  
  
- <span data-ttu-id="1a568-168">WCF istekleri ASP.NET işlem hattı tarafından işlenir.</span><span class="sxs-lookup"><span data-stu-id="1a568-168">WCF requests are processed by the ASP.NET pipeline.</span></span> <span data-ttu-id="1a568-169">Gelen istekler üzerinde çalışacak şekilde yapılandırılmış HttpModules, WCF isteklerini de işleyebilir.</span><span class="sxs-lookup"><span data-stu-id="1a568-169">HttpModules that have been configured to act on incoming requests can also process WCF requests.</span></span> <span data-ttu-id="1a568-170">Bunlar, ASP.NET Platform bileşenlerini (ör. <xref:System.Web.SessionState.SessionStateModule>) ve özel üçüncü taraf modüllerini içerebilir.</span><span class="sxs-lookup"><span data-stu-id="1a568-170">These can include ASP.NET platform components (e.g., <xref:System.Web.SessionState.SessionStateModule>), as well as custom third party modules.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1a568-171">Örnek</span><span class="sxs-lookup"><span data-stu-id="1a568-171">Example</span></span>  
 <span data-ttu-id="1a568-172">Aşağıdaki kod örneğinde, ASP uyumluluk modunun nasıl etkinleştirileceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1a568-172">The following code sample shows how to enable ASP Compatibility Mode.</span></span>  
  
## <a name="code"></a><span data-ttu-id="1a568-173">Kod</span><span class="sxs-lookup"><span data-stu-id="1a568-173">Code</span></span>  
  
```xml  
<serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>
```  
  
## <a name="see-also"></a><span data-ttu-id="1a568-174">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1a568-174">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [<span data-ttu-id="1a568-175">Barındırma</span><span class="sxs-lookup"><span data-stu-id="1a568-175">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
- [<span data-ttu-id="1a568-176">WCF Hizmetleri ve ASP.NET</span><span class="sxs-lookup"><span data-stu-id="1a568-176">WCF Services and ASP.NET</span></span>](../../../wcf/feature-details/wcf-services-and-aspnet.md)
