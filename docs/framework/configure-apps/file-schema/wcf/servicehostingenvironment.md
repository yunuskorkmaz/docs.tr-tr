---
description: 'Hakkında daha fazla bilgi edinin: <serviceHostingEnvironment>'
title: <serviceHostingEnvironment>
ms.date: 03/30/2017
ms.assetid: 4f8a7c4f-e735-4987-979a-b74fcdae2652
ms.openlocfilehash: 95243a1cf9cea734b7f35a1400a8b5b865767976
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786726"
---
# \<serviceHostingEnvironment>

<span data-ttu-id="91fdd-102">Bu öğe, belirli bir aktarım için hizmet barındırma ortamının örneklenme türünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="91fdd-102">This element defines the type the service hosting environment instantiates for a particular transport.</span></span> <span data-ttu-id="91fdd-103">Bu öğe boşsa, varsayılan tür kullanılır.</span><span class="sxs-lookup"><span data-stu-id="91fdd-103">If this element is empty, the default type is used.</span></span> <span data-ttu-id="91fdd-104">Bu öğe, yalnızca uygulama veya makine düzeyinde yapılandırma dosyalarında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="91fdd-104">This element can only be used at the application or machine level configuration files.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceHostingEnvironment>**  
  
## <a name="syntax"></a><span data-ttu-id="91fdd-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="91fdd-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="91fdd-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="91fdd-106">Attributes and Elements</span></span>  

 <span data-ttu-id="91fdd-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="91fdd-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="91fdd-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="91fdd-108">Attributes</span></span>  
  
|<span data-ttu-id="91fdd-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="91fdd-109">Attribute</span></span>|<span data-ttu-id="91fdd-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="91fdd-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="91fdd-111">aspNetCompatibilityEnabled</span><span class="sxs-lookup"><span data-stu-id="91fdd-111">aspNetCompatibilityEnabled</span></span>|<span data-ttu-id="91fdd-112">Geçerli uygulama için ASP.NET uyumluluk modunun açık olup olmadığını gösteren bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="91fdd-112">A Boolean value indicating whether the ASP.NET compatibility mode has been turned on for the current application.</span></span> <span data-ttu-id="91fdd-113">Varsayılan değer: `false`.</span><span class="sxs-lookup"><span data-stu-id="91fdd-113">The default is `false`.</span></span><br /><br /> <span data-ttu-id="91fdd-114">Bu öznitelik olarak ayarlandığında `true` , ASP.NET HTTP işlem hattı aracılığıyla Windows Communication Foundation (WCF) Hizmetleri akışına ve http olmayan protokoller üzerinden iletişime izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="91fdd-114">When this attribute is set to `true`, requests to Windows Communication Foundation (WCF) services flow through the ASP.NET HTTP pipeline, and communication over non-HTTP protocols is prohibited.</span></span> <span data-ttu-id="91fdd-115">Daha fazla bilgi için bkz. [WCF Hizmetleri ve ASP.net](../../../wcf/feature-details/wcf-services-and-aspnet.md).</span><span class="sxs-lookup"><span data-stu-id="91fdd-115">For more information, see [WCF Services and ASP.NET](../../../wcf/feature-details/wcf-services-and-aspnet.md).</span></span>|  
|<span data-ttu-id="91fdd-116">Minfreememoryyüztagetoactivateservice</span><span class="sxs-lookup"><span data-stu-id="91fdd-116">minFreeMemoryPercentageToActivateService</span></span>|<span data-ttu-id="91fdd-117">Bir WCF hizmeti etkinleştirilmeden önce, sistem için kullanılabilir olması gereken minimum boş bellek miktarını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="91fdd-117">An integer that specifies the minimum amount of free memory that should be available to the system, before a WCF service can be activated.</span></span> <span data-ttu-id="91fdd-118">**Dikkat:**  Bu özniteliği bir WCF hizmetinin web.config dosyasında kısmi güvenle belirtmek <xref:System.Security.SecurityException> , hizmet çalıştırıldığında bir ile sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="91fdd-118">**Caution:**  Specifying this attribute along with partial trust in the web.config file of a WCF service will result in a <xref:System.Security.SecurityException> when the service is run.</span></span>|  
|<span data-ttu-id="91fdd-119">multipleSiteBindingsEnabled</span><span class="sxs-lookup"><span data-stu-id="91fdd-119">multipleSiteBindingsEnabled</span></span>|<span data-ttu-id="91fdd-120">Site başına birden fazla IIS bağlaması etkinleştirilip etkinleştirilmeyeceğini belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="91fdd-120">A Boolean value that specifies whether multiple IIS bindings per site is enabled.</span></span><br /><br /> <span data-ttu-id="91fdd-121">IIS, sanal dizinleri içeren sanal uygulamalara yönelik kapsayıcılar olan Web sitelerinden oluşur.</span><span class="sxs-lookup"><span data-stu-id="91fdd-121">IIS consists of web sites, which are containers for virtual applications containing virtual directories.</span></span> <span data-ttu-id="91fdd-122">Bir sitedeki uygulamaya bir veya daha fazla IIS bağlaması aracılığıyla erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="91fdd-122">The application in a site can be accessed through one or more IIS binding.</span></span> <span data-ttu-id="91fdd-123">IIS bağlama iki bilgi parçası sağlar: bağlama protokolü ve bağlama bilgileri.</span><span class="sxs-lookup"><span data-stu-id="91fdd-123">An IIS binding provides two pieces of information: a binding protocol and binding information.</span></span> <span data-ttu-id="91fdd-124">Bağlama protokolü, iletişimin gerçekleştiği düzeni tanımlar ve bağlama bilgileri siteye erişmek için kullanılan bilgiler.</span><span class="sxs-lookup"><span data-stu-id="91fdd-124">Binding protocol defines the scheme over which communication occurs, and binding information is the information used to access the site.</span></span> <span data-ttu-id="91fdd-125">Bağlama protokolüne bir örnek HTTP olabilir, ancak bağlama bilgileri bir IP adresi, bağlantı noktası, ana bilgisayar üstbilgisi vb. içerebilir.</span><span class="sxs-lookup"><span data-stu-id="91fdd-125">An example of a binding protocol can be HTTP, whereas binding information can contain an IP address, Port, host header, etc.</span></span><br /><br /> <span data-ttu-id="91fdd-126">IIS, her site için birden çok IIS bağlaması belirtmeyi destekler ve bu, her şema için birden çok temel adrese neden</span><span class="sxs-lookup"><span data-stu-id="91fdd-126">IIS supports specifying multiple IIS bindings per site, which results in multiple base addresses per scheme.</span></span> <span data-ttu-id="91fdd-127">Ancak, bir site altında barındırılan bir Windows Communication Foundation (WCF) hizmeti, her şema için yalnızca bir baseAddress 'e bağlamaya izin verir.</span><span class="sxs-lookup"><span data-stu-id="91fdd-127">However, a Windows Communication Foundation (WCF) service hosted under a site allows binding to only one baseAddress per scheme.</span></span><br /><br /> <span data-ttu-id="91fdd-128">Windows Communication Foundation (WCF) hizmeti için site başına birden çok IIS bağlamasını etkinleştirmek için, bu özniteliği olarak ayarlayın `true` .</span><span class="sxs-lookup"><span data-stu-id="91fdd-128">To enable multiple IIS bindings per site for a Windows Communication Foundation (WCF) service, set this attribute to `true`.</span></span> <span data-ttu-id="91fdd-129">Birden çok site bağlamasının yalnızca HTTP protokolü için desteklendiğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="91fdd-129">Notice that multiple site binding is supported only for the HTTP protocol.</span></span> <span data-ttu-id="91fdd-130">Yapılandırma dosyasındaki uç noktaların adresi, tüm URI olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="91fdd-130">The address of endpoints in the configuration file needs to be a complete URI.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="91fdd-131">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="91fdd-131">Child Elements</span></span>  
  
|<span data-ttu-id="91fdd-132">Öğe</span><span class="sxs-lookup"><span data-stu-id="91fdd-132">Element</span></span>|<span data-ttu-id="91fdd-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="91fdd-133">Description</span></span>|  
|-------------|-----------------|  
|[\<baseAddressPrefixFilters>](baseaddressprefixfilters.md)|<span data-ttu-id="91fdd-134">Hizmet ana bilgisayarı tarafından kullanılan taban adresler için ön ek filtrelerini belirten yapılandırma öğeleri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="91fdd-134">A collection of configuration elements that specify prefix filters for the base addresses used by the service host.</span></span>|  
|[\<serviceActivations>](serviceactivations.md)|<span data-ttu-id="91fdd-135">Etkinleştirme ayarlarını açıklayan bir yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="91fdd-135">A configuration section that describes activation settings.</span></span>|  
|[\<transportConfigurationTypes>](transportconfigurationtypes.md)|<span data-ttu-id="91fdd-136">Belirli bir taşımanın türünü tanımlayan yapılandırma öğelerinin koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="91fdd-136">A collection of configuration elements that identify the type of a particular transport.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="91fdd-137">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="91fdd-137">Parent Elements</span></span>  
  
|<span data-ttu-id="91fdd-138">Öğe</span><span class="sxs-lookup"><span data-stu-id="91fdd-138">Element</span></span>|<span data-ttu-id="91fdd-139">Açıklama</span><span class="sxs-lookup"><span data-stu-id="91fdd-139">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="91fdd-140">serviceModel</span><span class="sxs-lookup"><span data-stu-id="91fdd-140">serviceModel</span></span>|<span data-ttu-id="91fdd-141">Tüm Windows Communication Foundation (WCF) yapılandırma öğelerinin kök öğesi.</span><span class="sxs-lookup"><span data-stu-id="91fdd-141">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="91fdd-142">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="91fdd-142">Remarks</span></span>  

 <span data-ttu-id="91fdd-143">Varsayılan olarak, WCF Hizmetleri barındırılan uygulama etki alanlarında (AppDomain) ASP.NET ile yan yana çalışır.</span><span class="sxs-lookup"><span data-stu-id="91fdd-143">By default, WCF services run side-by-side with ASP.NET in hosted Application Domains (AppDomain).</span></span> <span data-ttu-id="91fdd-144">WCF ve ASP.NET aynı AppDomain içinde bulunabilir olsa da, WCF istekleri varsayılan olarak ASP.NET HTTP işlem hattı tarafından işlenmez.</span><span class="sxs-lookup"><span data-stu-id="91fdd-144">Even though WCF and ASP.NET can coexist in the same AppDomain, WCF requests are not processed by the ASP.NET HTTP Pipeline by default.</span></span> <span data-ttu-id="91fdd-145">Sonuç olarak, ASP.NET uygulama platformunun birkaç öğesi WCF Hizmetleri için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="91fdd-145">As a result, several elements of the ASP.NET application platform are not available to WCF services.</span></span> <span data-ttu-id="91fdd-146">Bunlar şunlardır</span><span class="sxs-lookup"><span data-stu-id="91fdd-146">These include</span></span>  
  
- <span data-ttu-id="91fdd-147">ASP.NET dosyası/URL yetkilendirmesi</span><span class="sxs-lookup"><span data-stu-id="91fdd-147">ASP.NET File/URL Authorization</span></span>  
  
- <span data-ttu-id="91fdd-148">ASP.NET Kimliğe Bürünme</span><span class="sxs-lookup"><span data-stu-id="91fdd-148">ASP.NET Impersonation</span></span>  
  
- <span data-ttu-id="91fdd-149">Tanımlama bilgisi tabanlı oturum durumu</span><span class="sxs-lookup"><span data-stu-id="91fdd-149">Cookie-based Session State</span></span>  
  
- <span data-ttu-id="91fdd-150">HttpContext. Current</span><span class="sxs-lookup"><span data-stu-id="91fdd-150">HttpContext.Current</span></span>  
  
- <span data-ttu-id="91fdd-151">Özel HttpModule aracılığıyla işlem hattı genişletilebilirliği</span><span class="sxs-lookup"><span data-stu-id="91fdd-151">Pipeline Extensibility via custom HttpModule</span></span>  
  
 <span data-ttu-id="91fdd-152">WCF hizmetlerinizin ASP.NET bağlamında çalışması ve yalnızca HTTP üzerinden iletişim kurması gerekiyorsa, WCF 'nin ASP.NET uyumluluk modunu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="91fdd-152">If your WCF services need to function in the ASP.NET context, and communicate only over HTTP, you can use WCF’s ASP.NET compatibility mode.</span></span> <span data-ttu-id="91fdd-153">`aspNetCompatibilityEnabled`Özniteliği uygulama düzeyinde olarak ayarlandığında bu mod açıktır `true` .</span><span class="sxs-lookup"><span data-stu-id="91fdd-153">This mode is turned on when the `aspNetCompatibilityEnabled` attribute is set to `true` at the application level.</span></span> <span data-ttu-id="91fdd-154">Hizmet uygulamaları, sınıfını kullanarak uyumluluk modunda çalıştırma imkanlarını bildirmelidir <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> .</span><span class="sxs-lookup"><span data-stu-id="91fdd-154">Service implementations must declare their ability to run in compatibility mode using the <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> class.</span></span> <span data-ttu-id="91fdd-155">Uyumluluk modu etkinleştirildiğinde,</span><span class="sxs-lookup"><span data-stu-id="91fdd-155">When the compatibility mode is enabled,</span></span>  
  
- <span data-ttu-id="91fdd-156">ASP.NET dosya/URL yetkilendirmesi, WCF yetkilendirmesi öncesinde zorlanır.</span><span class="sxs-lookup"><span data-stu-id="91fdd-156">ASP.NET File/URL Authorization is enforced prior to WCF authorization.</span></span> <span data-ttu-id="91fdd-157">Yetkilendirme kararı, isteğin aktarım düzeyi kimliğine göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="91fdd-157">An authorization decision is based on the transport-level identity of the request.</span></span> <span data-ttu-id="91fdd-158">İleti düzeyindeki kimlikler yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="91fdd-158">Identities at the message level are ignored.</span></span>  
  
- <span data-ttu-id="91fdd-159">WCF hizmeti işlemleri ASP.NET Kimliğe bürünme bağlamında yürütülmeye başlar.</span><span class="sxs-lookup"><span data-stu-id="91fdd-159">WCF service operations start to execute in the ASP.NET impersonation context.</span></span> <span data-ttu-id="91fdd-160">Belirli bir hizmet için hem ASP.NET Kimliğe bürünme hem de WCF kimliğe bürünme etkinleştirilirse, WCF kimliğe bürünme bağlamı geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="91fdd-160">If both ASP.NET impersonation and WCF impersonation are enabled for a specific service, the WCF impersonation context applies.</span></span>  
  
- <span data-ttu-id="91fdd-161">HttpContext. Current, WCF hizmet kodundan kullanılabilir ve hizmetlerin HTTP olmayan uç noktaları kullanıma sunmasının engellenmektedir.</span><span class="sxs-lookup"><span data-stu-id="91fdd-161">HttpContext.Current can be used from WCF service code, and services are prevented from exposing non-HTTP endpoints.</span></span>  
  
- <span data-ttu-id="91fdd-162">WCF istekleri ASP.NET işlem hattı tarafından işlenir.</span><span class="sxs-lookup"><span data-stu-id="91fdd-162">WCF requests are processed by the ASP.NET pipeline.</span></span> <span data-ttu-id="91fdd-163">Gelen istekler üzerinde çalışacak şekilde yapılandırılmış HttpModules, WCF isteklerini de işleyebilir.</span><span class="sxs-lookup"><span data-stu-id="91fdd-163">HttpModules that have been configured to act on incoming requests can also process WCF requests.</span></span> <span data-ttu-id="91fdd-164">Bunlar, ASP.NET Platform bileşenlerini (ör. <xref:System.Web.SessionState.SessionStateModule> ) ve özel üçüncü taraf modüllerini içerebilir.</span><span class="sxs-lookup"><span data-stu-id="91fdd-164">These can include ASP.NET platform components (e.g., <xref:System.Web.SessionState.SessionStateModule>), as well as custom third party modules.</span></span>  
  
## <a name="example"></a><span data-ttu-id="91fdd-165">Örnek</span><span class="sxs-lookup"><span data-stu-id="91fdd-165">Example</span></span>  

 <span data-ttu-id="91fdd-166">Aşağıdaki kod örneğinde, ASP uyumluluk modunun nasıl etkinleştirileceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="91fdd-166">The following code sample shows how to enable ASP Compatibility Mode.</span></span>  
  
## <a name="code"></a><span data-ttu-id="91fdd-167">Kod</span><span class="sxs-lookup"><span data-stu-id="91fdd-167">Code</span></span>  
  
```xml  
<serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>
```  
  
## <a name="see-also"></a><span data-ttu-id="91fdd-168">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="91fdd-168">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [<span data-ttu-id="91fdd-169">Hosting</span><span class="sxs-lookup"><span data-stu-id="91fdd-169">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
- [<span data-ttu-id="91fdd-170">WCF Hizmetleri ve ASP.NET</span><span class="sxs-lookup"><span data-stu-id="91fdd-170">WCF Services and ASP.NET</span></span>](../../../wcf/feature-details/wcf-services-and-aspnet.md)
