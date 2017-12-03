---
title: '&lt;serviceHostingEnvironment&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4f8a7c4f-e735-4987-979a-b74fcdae2652
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e3951c52a5bc510cc288b1289f2f6cc9c39255db
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltservicehostingenvironmentgt"></a><span data-ttu-id="40906-102">&lt;serviceHostingEnvironment&gt;</span><span class="sxs-lookup"><span data-stu-id="40906-102">&lt;serviceHostingEnvironment&gt;</span></span>
<span data-ttu-id="40906-103">Bu öğe için belirli bir barındırma ortamı hizmeti başlatır türü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="40906-103">This element defines the type the service hosting environment instantiates for a particular transport.</span></span> <span data-ttu-id="40906-104">Bu öğe boş ise, varsayılan türü kullanılır.</span><span class="sxs-lookup"><span data-stu-id="40906-104">If this element is empty, the default type is used.</span></span> <span data-ttu-id="40906-105">Bu öğe yalnızca uygulama veya makine düzeyi yapılandırma dosyaları kullanılır.</span><span class="sxs-lookup"><span data-stu-id="40906-105">This element can only be used at the application or machine level configuration files.</span></span>  
  
 <span data-ttu-id="40906-106">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="40906-106">\<system.ServiceModel></span></span>  
<span data-ttu-id="40906-107">\<ServiceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="40906-107">\<ServiceHostingEnvironment></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40906-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="40906-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="40906-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="40906-109">Attributes and Elements</span></span>  
 <span data-ttu-id="40906-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="40906-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="40906-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="40906-111">Attributes</span></span>  
  
|<span data-ttu-id="40906-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="40906-112">Attribute</span></span>|<span data-ttu-id="40906-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="40906-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="40906-114">aspNetCompatibilityEnabled</span><span class="sxs-lookup"><span data-stu-id="40906-114">aspNetCompatibilityEnabled</span></span>|<span data-ttu-id="40906-115">ASP.NET uyumluluğu modu geçerli uygulama için açık durumda olup olmadığını gösteren bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="40906-115">A Boolean value indicating whether the ASP.NET compatibility mode has been turned on for the current application.</span></span> <span data-ttu-id="40906-116">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="40906-116">The default is `false`.</span></span><br /><br /> <span data-ttu-id="40906-117">Bu öznitelik ayarlandığında `true`, ister [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] Hizmetleri ASP.NET HTTP kanalı yoluyla akış ve HTTP olmayan protokolleri üzerinden iletişim yasaktır.</span><span class="sxs-lookup"><span data-stu-id="40906-117">When this attribute is set to `true`, requests to [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] services flow through the ASP.NET HTTP pipeline, and communication over non-HTTP protocols is prohibited.</span></span> <span data-ttu-id="40906-118">Daha fazla bilgi için bkz: [WCF hizmetleri ve ASP.NET](../../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md).</span><span class="sxs-lookup"><span data-stu-id="40906-118">For more information, see [WCF Services and ASP.NET](../../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md).</span></span>|  
|<span data-ttu-id="40906-119">minFreeMemoryPercentageToActivateService</span><span class="sxs-lookup"><span data-stu-id="40906-119">minFreeMemoryPercentageToActivateService</span></span>|<span data-ttu-id="40906-120">En az önce sisteme kullanılabilir olması gerektiğini boş bellek miktarını belirten bir tamsayı bir [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] hizmeti etkinleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="40906-120">An integer that specifies the minimum amount of free memory that should be available to the system, before a [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] service can be activated.</span></span> <span data-ttu-id="40906-121">**Dikkat:** web.config dosyasındaki kısmi güven yanı sıra bu öznitelik belirten bir [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] hizmeti neden olur bir <xref:System.Security.SecurityException> hizmet çalıştırıldığında.</span><span class="sxs-lookup"><span data-stu-id="40906-121">**Caution:**  Specifying this attribute along with partial trust in the web.config file of a [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] service will result in a <xref:System.Security.SecurityException> when the service is run.</span></span>|  
|<span data-ttu-id="40906-122">multipleSiteBindingsEnabled</span><span class="sxs-lookup"><span data-stu-id="40906-122">multipleSiteBindingsEnabled</span></span>|<span data-ttu-id="40906-123">Site başına birden çok IIS bağlamaları etkinleştirilip etkinleştirilmediğini belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="40906-123">A Boolean value that specifies whether multiple IIS bindings per site is enabled.</span></span><br /><br /> <span data-ttu-id="40906-124">Sanal dizinler içeren sanal uygulamalar için kapsayıcılardır web siteleri, IIS oluşur.</span><span class="sxs-lookup"><span data-stu-id="40906-124">IIS consists of web sites, which are containers for virtual applications containing virtual directories.</span></span> <span data-ttu-id="40906-125">Uygulama bir sitedeki bir veya daha fazla IIS bağlama aracılığıyla erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="40906-125">The application in a site can be accessed through one or more IIS binding.</span></span> <span data-ttu-id="40906-126">Bir IIS bağlaması iki parça bilgi sağlar: bir bağlama protokolü ve bağlama bilgileri.</span><span class="sxs-lookup"><span data-stu-id="40906-126">An IIS binding provides two pieces of information: a binding protocol and binding information.</span></span> <span data-ttu-id="40906-127">Bağlama protokolü üzerinden iletişimin şeması tanımlar ve bağlama bilgileri siteye erişmek için kullanılan bilgilerdir.</span><span class="sxs-lookup"><span data-stu-id="40906-127">Binding protocol defines the scheme over which communication occurs, and binding information is the information used to access the site.</span></span> <span data-ttu-id="40906-128">Bağlama bilgileri bir IP adresi içerebilir oysa bağlama Protokolü örneği HTTP olabilir bağlantı noktası, ana bilgisayar üstbilgisi.</span><span class="sxs-lookup"><span data-stu-id="40906-128">An example of a binding protocol can be HTTP, whereas binding information can contain an IP address, Port, host header, etc.</span></span><br /><br /> <span data-ttu-id="40906-129">IIS, düzeni başına birden çok taban adresi sonuçlanır site başına birden çok IIS bağlamaları belirtmeyi destekler.</span><span class="sxs-lookup"><span data-stu-id="40906-129">IIS supports specifying multiple IIS bindings per site, which results in multiple base addresses per scheme.</span></span> <span data-ttu-id="40906-130">Ancak, bir [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] bir site altında barındırılan hizmet düzeni başına yalnızca bir baseAddress bağlamaya izin verir.</span><span class="sxs-lookup"><span data-stu-id="40906-130">However, a [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] service hosted under a site allows binding to only one baseAddress per scheme.</span></span><br /><br /> <span data-ttu-id="40906-131">Her site için birden çok IIS bağlamaları etkinleştirmek için bir [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] hizmet, bu öznitelik ayarlanırsa `true`.</span><span class="sxs-lookup"><span data-stu-id="40906-131">To enable multiple IIS bindings per site for a [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] service, set this attribute to `true`.</span></span> <span data-ttu-id="40906-132">Birden çok site bağlaması yalnızca HTTP protokolü için desteklendiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="40906-132">Notice that multiple site binding is supported only for the HTTP protocol.</span></span> <span data-ttu-id="40906-133">Uç noktaları yapılandırma dosyasındaki adresi tam bir URI olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="40906-133">The address of endpoints in the configuration file needs to be a complete URI.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="40906-134">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="40906-134">Child Elements</span></span>  
  
|<span data-ttu-id="40906-135">Öğe</span><span class="sxs-lookup"><span data-stu-id="40906-135">Element</span></span>|<span data-ttu-id="40906-136">Açıklama</span><span class="sxs-lookup"><span data-stu-id="40906-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="40906-137">\<baseAddressPrefixFilters ></span><span class="sxs-lookup"><span data-stu-id="40906-137">\<baseAddressPrefixFilters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddressprefixfilters.md)|<span data-ttu-id="40906-138">Hizmet ana bilgisayar tarafından kullanılan temel adres için önek filtreleri belirtin yapılandırma öğeleri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="40906-138">A collection of configuration elements that specify prefix filters for the base addresses used by the service host.</span></span>|  
|[<span data-ttu-id="40906-139">\<serviceActivations ></span><span class="sxs-lookup"><span data-stu-id="40906-139">\<serviceActivations></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/serviceactivations.md)|<span data-ttu-id="40906-140">Etkinleştirme ayarlarını açıklayan bir yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="40906-140">A configuration section that describes activation settings.</span></span>|  
|[<span data-ttu-id="40906-141">\<transportConfigurationTypes ></span><span class="sxs-lookup"><span data-stu-id="40906-141">\<transportConfigurationTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transportconfigurationtypes.md)|<span data-ttu-id="40906-142">Belirli bir tür belirleme yapılandırma öğeleri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="40906-142">A collection of configuration elements that identify the type of a particular transport.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="40906-143">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="40906-143">Parent Elements</span></span>  
  
|<span data-ttu-id="40906-144">Öğe</span><span class="sxs-lookup"><span data-stu-id="40906-144">Element</span></span>|<span data-ttu-id="40906-145">Açıklama</span><span class="sxs-lookup"><span data-stu-id="40906-145">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="40906-146">ServiceModel</span><span class="sxs-lookup"><span data-stu-id="40906-146">serviceModel</span></span>|<span data-ttu-id="40906-147">Tüm Windows Communication Foundation (WCF) yapılandırma öğelerinin kök öğesi.</span><span class="sxs-lookup"><span data-stu-id="40906-147">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="40906-148">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="40906-148">Remarks</span></span>  
 <span data-ttu-id="40906-149">Varsayılan olarak, çalışma yan yana barındırılan uygulama etki alanları (AppDomain) ASP.NET ile WCF hizmetleri.</span><span class="sxs-lookup"><span data-stu-id="40906-149">By default, WCF services run side-by-side with ASP.NET in hosted Application Domains (AppDomain).</span></span> <span data-ttu-id="40906-150">WCF ve ASP.NET aynı AppDomain içinde bulunabilir olsa bile, WCF istekleri varsayılan olarak ASP.NET HTTP ardışık düzen tarafından işlenmez.</span><span class="sxs-lookup"><span data-stu-id="40906-150">Even though WCF and ASP.NET can coexist in the same AppDomain, WCF requests are not processed by the ASP.NET HTTP Pipeline by default.</span></span> <span data-ttu-id="40906-151">Sonuç olarak, ASP.NET uygulama platformu çeşitli öğeleri, WCF hizmetleri için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="40906-151">As a result, several elements of the ASP.NET application platform are not available to WCF services.</span></span> <span data-ttu-id="40906-152">Bunlar</span><span class="sxs-lookup"><span data-stu-id="40906-152">These include</span></span>  
  
-   <span data-ttu-id="40906-153">ASP.NET dosya/URL yetkilendirmesi</span><span class="sxs-lookup"><span data-stu-id="40906-153">ASP.NET File/URL Authorization</span></span>  
  
-   <span data-ttu-id="40906-154">ASP.NET kimliğe bürünme</span><span class="sxs-lookup"><span data-stu-id="40906-154">ASP.NET Impersonation</span></span>  
  
-   <span data-ttu-id="40906-155">Tanımlama bilgisi tabanlı oturum durumu</span><span class="sxs-lookup"><span data-stu-id="40906-155">Cookie-based Session State</span></span>  
  
-   <span data-ttu-id="40906-156">HttpContext.Current</span><span class="sxs-lookup"><span data-stu-id="40906-156">HttpContext.Current</span></span>  
  
-   <span data-ttu-id="40906-157">Özel HTTP üzerinden ardışık düzen genişletilebilirliği</span><span class="sxs-lookup"><span data-stu-id="40906-157">Pipeline Extensibility via custom HttpModule</span></span>  
  
 <span data-ttu-id="40906-158">WCF hizmetleri ASP.NET bağlamında işlev ve yalnızca HTTP üzerinden iletişim kurmak gerekiyorsa, WCF'ın ASP.NET uyumluluğu modunu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="40906-158">If your WCF services need to function in the ASP.NET context, and communicate only over HTTP, you can use WCF’s ASP.NET compatibility mode.</span></span> <span data-ttu-id="40906-159">Bu modu etkin olduğunda açılır `aspNetCompatibilityEnabled` özniteliği `true` uygulama düzeyinde.</span><span class="sxs-lookup"><span data-stu-id="40906-159">This mode is turned on when the `aspNetCompatibilityEnabled` attribute is set to `true` at the application level.</span></span> <span data-ttu-id="40906-160">Hizmet uygulamaları, uyumluluk moduyla çalıştırmak için kendi yeteneği bildirmelidir <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="40906-160">Service implementations must declare their ability to run in compatibility mode using the <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> class.</span></span> <span data-ttu-id="40906-161">Uyumluluk modu etkinleştirildiğinde</span><span class="sxs-lookup"><span data-stu-id="40906-161">When the compatibility mode is enabled,</span></span>  
  
-   <span data-ttu-id="40906-162">ASP.NET dosya/URL yetkilendirmesi, WCF yetkilendirme önce uygulanır.</span><span class="sxs-lookup"><span data-stu-id="40906-162">ASP.NET File/URL Authorization is enforced prior to WCF authorization.</span></span> <span data-ttu-id="40906-163">Bir yetkilendirme kararı istek aktarım düzeyinde kimliğini temel alır.</span><span class="sxs-lookup"><span data-stu-id="40906-163">An authorization decision is based on the transport-level identity of the request.</span></span> <span data-ttu-id="40906-164">İleti düzeyinde kimlikleri göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="40906-164">Identities at the message level are ignored.</span></span>  
  
-   <span data-ttu-id="40906-165">ASP.NET kimliğe bürünme bağlamda yürütmek WCF Hizmeti işlemlerini başlatın.</span><span class="sxs-lookup"><span data-stu-id="40906-165">WCF service operations start to execute in the ASP.NET impersonation context.</span></span> <span data-ttu-id="40906-166">ASP.NET kimliğe bürünme ve WCF kimliğe bürünme için belirli bir hizmet etkinleştirilirse, WCF kimliğe bürünülmüş bağlamdaki geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="40906-166">If both ASP.NET impersonation and WCF impersonation are enabled for a specific service, the WCF impersonation context applies.</span></span>  
  
-   <span data-ttu-id="40906-167">WCF hizmet kodundan HttpContext.Current kullanılabilir ve Hizmetleri HTTP olmayan uç noktalarını gösterme engellenir.</span><span class="sxs-lookup"><span data-stu-id="40906-167">HttpContext.Current can be used from WCF service code, and services are prevented from exposing non-HTTP endpoints.</span></span>  
  
-   <span data-ttu-id="40906-168">WCF istekler ASP.NET ardışık düzen tarafından işlenir.</span><span class="sxs-lookup"><span data-stu-id="40906-168">WCF requests are processed by the ASP.NET pipeline.</span></span> <span data-ttu-id="40906-169">Gelen isteklerde davranmak üzere yapılandırılmış HttpModules işlem WCF istekleri de gruplandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="40906-169">HttpModules that have been configured to act on incoming requests can also process WCF requests.</span></span> <span data-ttu-id="40906-170">Bunlar, ASP.NET platform bileşenleri içerebilir (örneğin, <xref:System.Web.SessionState.SessionStateModule>), özel üçüncü taraf modülleri yanı sıra.</span><span class="sxs-lookup"><span data-stu-id="40906-170">These can include ASP.NET platform components (e.g., <xref:System.Web.SessionState.SessionStateModule>), as well as custom third party modules.</span></span>  
  
## <a name="example"></a><span data-ttu-id="40906-171">Örnek</span><span class="sxs-lookup"><span data-stu-id="40906-171">Example</span></span>  
 <span data-ttu-id="40906-172">Aşağıdaki kod örneği, ASP uyumluluk modunu etkinleştirmek gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="40906-172">The following code sample shows how to enable ASP Compatibility Mode.</span></span>  
  
## <a name="code"></a><span data-ttu-id="40906-173">Kod</span><span class="sxs-lookup"><span data-stu-id="40906-173">Code</span></span>  
  
```xml  
<serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>  
```  
  
## <a name="see-also"></a><span data-ttu-id="40906-174">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="40906-174">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>  
 <xref:System.ServiceModel.ServiceHostingEnvironment>  
 [<span data-ttu-id="40906-175">Barındırma</span><span class="sxs-lookup"><span data-stu-id="40906-175">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)  
 [<span data-ttu-id="40906-176">WCF hizmetleri ve ASP.NET</span><span class="sxs-lookup"><span data-stu-id="40906-176">WCF Services and ASP.NET</span></span>](../../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)
