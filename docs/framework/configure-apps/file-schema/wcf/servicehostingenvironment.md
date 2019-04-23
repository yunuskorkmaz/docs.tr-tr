---
title: <serviceHostingEnvironment>
ms.date: 03/30/2017
ms.assetid: 4f8a7c4f-e735-4987-979a-b74fcdae2652
ms.openlocfilehash: 24cf36aba81b5bb31eaac475361e2d07bc6f8b12
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59215995"
---
# <a name="servicehostingenvironment"></a><span data-ttu-id="f3f7e-101">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="f3f7e-101">\<serviceHostingEnvironment></span></span>
<span data-ttu-id="f3f7e-102">Bu öğe, belirli taşıma için hizmet barındırma ortamını gösteren türü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f3f7e-102">This element defines the type the service hosting environment instantiates for a particular transport.</span></span> <span data-ttu-id="f3f7e-103">Bu öğe boş ise, varsayılan türü kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f3f7e-103">If this element is empty, the default type is used.</span></span> <span data-ttu-id="f3f7e-104">Bu öğe yalnızca uygulama veya makine düzeyinde yapılandırma dosyalarını kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f3f7e-104">This element can only be used at the application or machine level configuration files.</span></span>  
  
 <span data-ttu-id="f3f7e-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="f3f7e-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="f3f7e-106">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="f3f7e-106">\<ServiceHostingEnvironment></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3f7e-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f3f7e-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f3f7e-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f3f7e-108">Attributes and Elements</span></span>  
 <span data-ttu-id="f3f7e-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f3f7e-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f3f7e-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f3f7e-110">Attributes</span></span>  
  
|<span data-ttu-id="f3f7e-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f3f7e-111">Attribute</span></span>|<span data-ttu-id="f3f7e-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f3f7e-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f3f7e-113">aspNetCompatibilityEnabled</span><span class="sxs-lookup"><span data-stu-id="f3f7e-113">aspNetCompatibilityEnabled</span></span>|<span data-ttu-id="f3f7e-114">ASP.NET uyumluluk modunun geçerli uygulama için açık durumda olup olmadığını gösteren bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="f3f7e-114">A Boolean value indicating whether the ASP.NET compatibility mode has been turned on for the current application.</span></span> <span data-ttu-id="f3f7e-115">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="f3f7e-115">The default is `false`.</span></span><br /><br /> <span data-ttu-id="f3f7e-116">Bu öznitelik ayarlandığında `true`, Windows Communication Foundation (WCF) hizmetlere yönelik istekler ASP.NET HTTP ardışık düzende akış ve HTTP olmayan protokolleri üzerinden iletişim kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="f3f7e-116">When this attribute is set to `true`, requests to Windows Communication Foundation (WCF) services flow through the ASP.NET HTTP pipeline, and communication over non-HTTP protocols is prohibited.</span></span> <span data-ttu-id="f3f7e-117">Daha fazla bilgi için [WCF hizmetleri ve ASP.NET](../../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md).</span><span class="sxs-lookup"><span data-stu-id="f3f7e-117">For more information, see [WCF Services and ASP.NET](../../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md).</span></span>|  
|<span data-ttu-id="f3f7e-118">minFreeMemoryPercentageToActivateService</span><span class="sxs-lookup"><span data-stu-id="f3f7e-118">minFreeMemoryPercentageToActivateService</span></span>|<span data-ttu-id="f3f7e-119">Bir tamsayı en az bir WCF hizmet aktif edilmeden önce sistemde kullanılabilir olması gereken boş bellek miktarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="f3f7e-119">An integer that specifies the minimum amount of free memory that should be available to the system, before a WCF service can be activated.</span></span> <span data-ttu-id="f3f7e-120">**Dikkat:**  Kısmi güven web.config dosyasındaki bir WCF Hizmeti ile birlikte bu öznitelik belirtmemeye sonuçlanır bir <xref:System.Security.SecurityException> hizmeti ne zaman çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="f3f7e-120">**Caution:**  Specifying this attribute along with partial trust in the web.config file of a WCF service will result in a <xref:System.Security.SecurityException> when the service is run.</span></span>|  
|<span data-ttu-id="f3f7e-121">multipleSiteBindingsEnabled</span><span class="sxs-lookup"><span data-stu-id="f3f7e-121">multipleSiteBindingsEnabled</span></span>|<span data-ttu-id="f3f7e-122">Çoklu IIS bağlamalarının her site etkin olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="f3f7e-122">A Boolean value that specifies whether multiple IIS bindings per site is enabled.</span></span><br /><br /> <span data-ttu-id="f3f7e-123">IIS web siteleri, sanal dizinler içeren sanal uygulamaların kapsayıcılarıdır oluşur.</span><span class="sxs-lookup"><span data-stu-id="f3f7e-123">IIS consists of web sites, which are containers for virtual applications containing virtual directories.</span></span> <span data-ttu-id="f3f7e-124">Uygulama bir sitedeki bir veya daha fazla IIS bağlama aracılığıyla erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="f3f7e-124">The application in a site can be accessed through one or more IIS binding.</span></span> <span data-ttu-id="f3f7e-125">Bir IIS bağlaması iki bilgi parçasını sağlar: bağlama protokolü ve bağlama bilgileri.</span><span class="sxs-lookup"><span data-stu-id="f3f7e-125">An IIS binding provides two pieces of information: a binding protocol and binding information.</span></span> <span data-ttu-id="f3f7e-126">Bağlama Protokolü iletişim oluştuğu düzenini tanımlar ve bağlama bilgileri siteye erişmek için kullanılan bilgiler bunlardır.</span><span class="sxs-lookup"><span data-stu-id="f3f7e-126">Binding protocol defines the scheme over which communication occurs, and binding information is the information used to access the site.</span></span> <span data-ttu-id="f3f7e-127">Bağlama Protokolü örneği HTTP olabilir, bu IP adresi, bağlama bilgileri içerebilir ancak bağlantı noktası, ana bilgisayar üstbilgisi.</span><span class="sxs-lookup"><span data-stu-id="f3f7e-127">An example of a binding protocol can be HTTP, whereas binding information can contain an IP address, Port, host header, etc.</span></span><br /><br /> <span data-ttu-id="f3f7e-128">Çoklu IIS bağlamalarının her Düzen başına birden çok taban adresi sonuçlanır site belirtme IIS destekler.</span><span class="sxs-lookup"><span data-stu-id="f3f7e-128">IIS supports specifying multiple IIS bindings per site, which results in multiple base addresses per scheme.</span></span> <span data-ttu-id="f3f7e-129">Ancak, bir site altında barındırılan Windows Communication Foundation (WCF) hizmet şeması başına yalnızca bir baseAddress bağlama sağlar.</span><span class="sxs-lookup"><span data-stu-id="f3f7e-129">However, a Windows Communication Foundation (WCF) service hosted under a site allows binding to only one baseAddress per scheme.</span></span><br /><br /> <span data-ttu-id="f3f7e-130">Çoklu IIS bağlamalarının her site için bir Windows Communication Foundation (WCF) hizmetini etkinleştirmek için bu öznitelik ayarlanan `true`.</span><span class="sxs-lookup"><span data-stu-id="f3f7e-130">To enable multiple IIS bindings per site for a Windows Communication Foundation (WCF) service, set this attribute to `true`.</span></span> <span data-ttu-id="f3f7e-131">Birden çok site bağlaması yalnızca HTTP protokolü için desteklenip desteklenmediğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="f3f7e-131">Notice that multiple site binding is supported only for the HTTP protocol.</span></span> <span data-ttu-id="f3f7e-132">Yapılandırma dosyasındaki uç nokta adresi, tam bir URI olması gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="f3f7e-132">The address of endpoints in the configuration file needs to be a complete URI.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f3f7e-133">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f3f7e-133">Child Elements</span></span>  
  
|<span data-ttu-id="f3f7e-134">Öğe</span><span class="sxs-lookup"><span data-stu-id="f3f7e-134">Element</span></span>|<span data-ttu-id="f3f7e-135">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f3f7e-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f3f7e-136">\<baseAddressPrefixFilters></span><span class="sxs-lookup"><span data-stu-id="f3f7e-136">\<baseAddressPrefixFilters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddressprefixfilters.md)|<span data-ttu-id="f3f7e-137">Ön ek filtreler için hizmet ana bilgisayarı tarafından kullanılan tabanı belirten yapılandırma öğelerinin koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="f3f7e-137">A collection of configuration elements that specify prefix filters for the base addresses used by the service host.</span></span>|  
|[<span data-ttu-id="f3f7e-138">\<serviceActivations ></span><span class="sxs-lookup"><span data-stu-id="f3f7e-138">\<serviceActivations></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/serviceactivations.md)|<span data-ttu-id="f3f7e-139">Aktivasyon ayarlarını tanımlayan bir yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="f3f7e-139">A configuration section that describes activation settings.</span></span>|  
|[<span data-ttu-id="f3f7e-140">\<transportConfigurationTypes ></span><span class="sxs-lookup"><span data-stu-id="f3f7e-140">\<transportConfigurationTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transportconfigurationtypes.md)|<span data-ttu-id="f3f7e-141">Belirli bir türünü belirleyen yapılandırma öğelerinin koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="f3f7e-141">A collection of configuration elements that identify the type of a particular transport.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f3f7e-142">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f3f7e-142">Parent Elements</span></span>  
  
|<span data-ttu-id="f3f7e-143">Öğe</span><span class="sxs-lookup"><span data-stu-id="f3f7e-143">Element</span></span>|<span data-ttu-id="f3f7e-144">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f3f7e-144">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f3f7e-145">serviceModel</span><span class="sxs-lookup"><span data-stu-id="f3f7e-145">serviceModel</span></span>|<span data-ttu-id="f3f7e-146">Tüm Windows Communication Foundation (WCF) yapılandırma öğelerinin kök öğe.</span><span class="sxs-lookup"><span data-stu-id="f3f7e-146">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f3f7e-147">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f3f7e-147">Remarks</span></span>  
 <span data-ttu-id="f3f7e-148">Varsayılan olarak, çalışma yan yana barındırılan uygulama etki alanı (AppDomain) içinde ASP.NET ile WCF hizmetleri.</span><span class="sxs-lookup"><span data-stu-id="f3f7e-148">By default, WCF services run side-by-side with ASP.NET in hosted Application Domains (AppDomain).</span></span> <span data-ttu-id="f3f7e-149">WCF ve ASP.NET aynı AppDomain içinde bulunabilir olsa da, WCF istekleri varsayılan olarak ASP.NET HTTP ardışık düzeni tarafından işlenmez.</span><span class="sxs-lookup"><span data-stu-id="f3f7e-149">Even though WCF and ASP.NET can coexist in the same AppDomain, WCF requests are not processed by the ASP.NET HTTP Pipeline by default.</span></span> <span data-ttu-id="f3f7e-150">Sonuç olarak, ASP.NET uygulama platformu çeşitli öğeleri, WCF hizmetleri için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="f3f7e-150">As a result, several elements of the ASP.NET application platform are not available to WCF services.</span></span> <span data-ttu-id="f3f7e-151">Bunlar</span><span class="sxs-lookup"><span data-stu-id="f3f7e-151">These include</span></span>  
  
-   <span data-ttu-id="f3f7e-152">ASP.NET dosya/URL yetkilendirmesi</span><span class="sxs-lookup"><span data-stu-id="f3f7e-152">ASP.NET File/URL Authorization</span></span>  
  
-   <span data-ttu-id="f3f7e-153">ASP.NET kimliğe bürünme</span><span class="sxs-lookup"><span data-stu-id="f3f7e-153">ASP.NET Impersonation</span></span>  
  
-   <span data-ttu-id="f3f7e-154">Tanımlama bilgisi tabanlı oturum durumu</span><span class="sxs-lookup"><span data-stu-id="f3f7e-154">Cookie-based Session State</span></span>  
  
-   <span data-ttu-id="f3f7e-155">HttpContext.Current</span><span class="sxs-lookup"><span data-stu-id="f3f7e-155">HttpContext.Current</span></span>  
  
-   <span data-ttu-id="f3f7e-156">Özel HTTP aracılığıyla işlem hattı genişletilebilirliği</span><span class="sxs-lookup"><span data-stu-id="f3f7e-156">Pipeline Extensibility via custom HttpModule</span></span>  
  
 <span data-ttu-id="f3f7e-157">WCF hizmetlerinizi ASP.NET bağlamda işlev ve yalnızca HTTP üzerinden iletişim kurması gerekiyorsa, WCF'ın ASP.NET uyumluluk modunun kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f3f7e-157">If your WCF services need to function in the ASP.NET context, and communicate only over HTTP, you can use WCF’s ASP.NET compatibility mode.</span></span> <span data-ttu-id="f3f7e-158">Bu mod üzerinde ne zaman etkin `aspNetCompatibilityEnabled` özniteliği `true` uygulama düzeyinde.</span><span class="sxs-lookup"><span data-stu-id="f3f7e-158">This mode is turned on when the `aspNetCompatibilityEnabled` attribute is set to `true` at the application level.</span></span> <span data-ttu-id="f3f7e-159">Hizmet uygulamaları, uyumluluk modu kullanarak çalıştırmak için kendi yeteneği bildirmelidir <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="f3f7e-159">Service implementations must declare their ability to run in compatibility mode using the <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> class.</span></span> <span data-ttu-id="f3f7e-160">Uyumluluk modu etkinleştirildiğinde</span><span class="sxs-lookup"><span data-stu-id="f3f7e-160">When the compatibility mode is enabled,</span></span>  
  
-   <span data-ttu-id="f3f7e-161">ASP.NET dosya/URL yetkilendirmesi, WCF yetkilendirme önce uygulanır.</span><span class="sxs-lookup"><span data-stu-id="f3f7e-161">ASP.NET File/URL Authorization is enforced prior to WCF authorization.</span></span> <span data-ttu-id="f3f7e-162">Bir yetkilendirme kararı, aktarım düzeyinde isteğin kimliğini temel alır.</span><span class="sxs-lookup"><span data-stu-id="f3f7e-162">An authorization decision is based on the transport-level identity of the request.</span></span> <span data-ttu-id="f3f7e-163">İleti düzeyinde kimlikleri yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="f3f7e-163">Identities at the message level are ignored.</span></span>  
  
-   <span data-ttu-id="f3f7e-164">ASP.NET kimliğe bürünme bağlamda yürütülecek WCF Hizmeti işlemlerini başlatın.</span><span class="sxs-lookup"><span data-stu-id="f3f7e-164">WCF service operations start to execute in the ASP.NET impersonation context.</span></span> <span data-ttu-id="f3f7e-165">ASP.NET kimliğe bürünme hem de WCF kimliğe bürünme belirli bir hizmet için etkinleştirilip etkinleştirilmediğini WCF kimliğe bürünülmüş bağlamdaki geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="f3f7e-165">If both ASP.NET impersonation and WCF impersonation are enabled for a specific service, the WCF impersonation context applies.</span></span>  
  
-   <span data-ttu-id="f3f7e-166">WCF hizmet kodundan HttpContext.Current kullanılabilir ve HTTP olmayan uç noktaları açıklamanızı hizmetler engellenir.</span><span class="sxs-lookup"><span data-stu-id="f3f7e-166">HttpContext.Current can be used from WCF service code, and services are prevented from exposing non-HTTP endpoints.</span></span>  
  
-   <span data-ttu-id="f3f7e-167">WCF istekleri ASP.NET işlem hattı tarafından işlenir.</span><span class="sxs-lookup"><span data-stu-id="f3f7e-167">WCF requests are processed by the ASP.NET pipeline.</span></span> <span data-ttu-id="f3f7e-168">Gelen istekleri davranacak şekilde yapılandırılmış HttpModules işlem WCF istekleri de olabilir.</span><span class="sxs-lookup"><span data-stu-id="f3f7e-168">HttpModules that have been configured to act on incoming requests can also process WCF requests.</span></span> <span data-ttu-id="f3f7e-169">Bunlar, ASP.NET platform bileşenleri içerebilir (örneğin, <xref:System.Web.SessionState.SessionStateModule>), üçüncü taraf özel modüller yanı sıra.</span><span class="sxs-lookup"><span data-stu-id="f3f7e-169">These can include ASP.NET platform components (e.g., <xref:System.Web.SessionState.SessionStateModule>), as well as custom third party modules.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f3f7e-170">Örnek</span><span class="sxs-lookup"><span data-stu-id="f3f7e-170">Example</span></span>  
 <span data-ttu-id="f3f7e-171">Aşağıdaki kod örneği, ASP uyumluluk modunu etkinleştirmek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f3f7e-171">The following code sample shows how to enable ASP Compatibility Mode.</span></span>  
  
## <a name="code"></a><span data-ttu-id="f3f7e-172">Kod</span><span class="sxs-lookup"><span data-stu-id="f3f7e-172">Code</span></span>  
  
```xml  
<serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>
```  
  
## <a name="see-also"></a><span data-ttu-id="f3f7e-173">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f3f7e-173">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [<span data-ttu-id="f3f7e-174">Barındırma</span><span class="sxs-lookup"><span data-stu-id="f3f7e-174">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
- [<span data-ttu-id="f3f7e-175">WCF Hizmetleri ve ASP.NET</span><span class="sxs-lookup"><span data-stu-id="f3f7e-175">WCF Services and ASP.NET</span></span>](../../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)
