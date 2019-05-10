---
title: Federasyon
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation [WCF]
ms.assetid: 2f1e646f-8361-48d4-9d5d-1b961f31ede4
ms.openlocfilehash: baf65340e390c7439e8639e334819fb0bf60f952
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64662623"
---
# <a name="federation"></a><span data-ttu-id="2de39-102">Federasyon</span><span class="sxs-lookup"><span data-stu-id="2de39-102">Federation</span></span>
<span data-ttu-id="2de39-103">Bu konuda birleşik güvenliği kavramını kısa bir genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="2de39-103">This topic provides a brief overview of the concept of federated security.</span></span> <span data-ttu-id="2de39-104">Ayrıca, Federasyon güvenlik mimariyi dağıtmak için Windows Communication Foundation (WCF) desteği açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2de39-104">It also describes Windows Communication Foundation (WCF) support for deploying federated security architectures.</span></span> <span data-ttu-id="2de39-105">Federasyon gösteren örnek bir uygulama için bkz. [Federasyon örneği](../../../../docs/framework/wcf/samples/federation-sample.md).</span><span class="sxs-lookup"><span data-stu-id="2de39-105">For a sample application that demonstrates federation, see [Federation Sample](../../../../docs/framework/wcf/samples/federation-sample.md).</span></span>  
  
## <a name="definition-of-federated-security"></a><span data-ttu-id="2de39-106">Federasyon güvenlik tanımı</span><span class="sxs-lookup"><span data-stu-id="2de39-106">Definition of Federated Security</span></span>  
 <span data-ttu-id="2de39-107">Birleşik güvenliği bir istemci erişim hizmeti ve ilişkili kimlik doğrulama ve yetkilendirme yordamları arasında ayrım sağlar.</span><span class="sxs-lookup"><span data-stu-id="2de39-107">Federated security allows for clean separation between the service a client is accessing and the associated authentication and authorization procedures.</span></span> <span data-ttu-id="2de39-108">Birleşik güvenliği ayrıca birden fazla sistemler, ağlar ve farklı güven bölgelerinde kuruluşta işbirliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="2de39-108">Federated security also enables collaboration across multiple systems, networks, and organizations in different trust realms.</span></span>  
  
 <span data-ttu-id="2de39-109">WCF oluştururken ve dağıtırken, Federasyon güvenlik kullanan dağıtılmış sistemler için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="2de39-109">WCF provides support for building and deploying distributed systems that employ federated security.</span></span>  
  
### <a name="elements-of-a-federated-security-architecture"></a><span data-ttu-id="2de39-110">Öğeleri bir Federasyon güvenlik mimarisi</span><span class="sxs-lookup"><span data-stu-id="2de39-110">Elements of a Federated Security Architecture</span></span>  
 <span data-ttu-id="2de39-111">Birleşik güvenliği mimari, aşağıdaki tabloda açıklandığı gibi üç anahtar öğelerin sahiptir.</span><span class="sxs-lookup"><span data-stu-id="2de39-111">The federated security architecture has three key elements, as described in the following table.</span></span>  
  
|<span data-ttu-id="2de39-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="2de39-112">Element</span></span>|<span data-ttu-id="2de39-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2de39-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2de39-114">Domain/realm</span><span class="sxs-lookup"><span data-stu-id="2de39-114">Domain/realm</span></span>|<span data-ttu-id="2de39-115">Güvenlik yönetimi ya da güven tek bir birim.</span><span class="sxs-lookup"><span data-stu-id="2de39-115">A single unit of security administration or trust.</span></span> <span data-ttu-id="2de39-116">Tipik bir etki alanı, tek bir kuruma içerebilir.</span><span class="sxs-lookup"><span data-stu-id="2de39-116">A typical domain might include a single organization.</span></span>|  
|<span data-ttu-id="2de39-117">Federasyon</span><span class="sxs-lookup"><span data-stu-id="2de39-117">Federation</span></span>|<span data-ttu-id="2de39-118">Güveni olan etki alanları koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="2de39-118">A collection of domains that have established trust.</span></span> <span data-ttu-id="2de39-119">Güven düzeyi farklılık gösterebilir, ancak genellikle kimlik doğrulaması içerir ve hemen her zaman yetkilendirme içerir.</span><span class="sxs-lookup"><span data-stu-id="2de39-119">The level of trust may vary, but typically includes authentication and almost always includes authorization.</span></span> <span data-ttu-id="2de39-120">Tipik bir federasyon güveni için bir kaynak kümesi için paylaşılan erişim kuruluşların sayısı içerebilir.</span><span class="sxs-lookup"><span data-stu-id="2de39-120">A typical federation might include a number of organizations that have established trust for shared access to a set of resources.</span></span>|  
|<span data-ttu-id="2de39-121">Güvenlik Belirteci Hizmeti (STS)</span><span class="sxs-lookup"><span data-stu-id="2de39-121">Security Token Service (STS)</span></span>|<span data-ttu-id="2de39-122">Güvenlik belirteçleri bir Web hizmeti; diğer bir deyişle, onaylamalar yanınızda güvendiği, çok güvendiği kanıta göre yapar.</span><span class="sxs-lookup"><span data-stu-id="2de39-122">A Web service that issues security tokens; that is, it makes assertions based on evidence that it trusts, to whomever trusts it.</span></span> <span data-ttu-id="2de39-123">Bu, etki alanı arasında güven aracılığı yapmaktan'ın temelini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2de39-123">This forms the basis of trust brokering between domains.</span></span>|  
  
### <a name="example-scenario"></a><span data-ttu-id="2de39-124">Örnek senaryo</span><span class="sxs-lookup"><span data-stu-id="2de39-124">Example Scenario</span></span>  
 <span data-ttu-id="2de39-125">Birleşik güvenliği örneği aşağıda gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="2de39-125">The following illustration shows an example of federated security:</span></span>  
  
 ![Tipik birleşik güvenliği senaryoyu gösteren diyagram.](./media/federation/typical-federated-security-scenario.gif)  
  
 <span data-ttu-id="2de39-127">Bu senaryo, iki kuruluş içerir: A ve b kuruluş, bir kuruluştaki bazı kullanıcılar değerli bulduğunuz bir Web kaynağı (bir Web hizmeti) sahip.</span><span class="sxs-lookup"><span data-stu-id="2de39-127">This scenario includes two organizations: A and B. Organization B has a Web resource (a Web service) that some users in organization A find valuable.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2de39-128">Bu bölümde terimler kullanılmaktadır *kaynak*, *hizmet*, ve *Web hizmeti* birbirinin yerine.</span><span class="sxs-lookup"><span data-stu-id="2de39-128">This section uses the terms *resource*, *service*, and *Web service* interchangeably.</span></span>  
  
 <span data-ttu-id="2de39-129">Genellikle, kuruluş B, A kuruluştan bir kullanıcı geçerli çeşit hizmet erişmeden önce kimlik doğrulaması sağlaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="2de39-129">Typically, organization B requires that a user from organization A provide some valid form of authentication before accessing the service.</span></span> <span data-ttu-id="2de39-130">Ayrıca, kuruluş Ayrıca kullanıcı söz konusu belirli kaynağa erişim yetkisi olması gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="2de39-130">In addition, the organization may also require that the user be authorized to access the specific resource in question.</span></span> <span data-ttu-id="2de39-131">Bu sorunu gidermek ve kuruluştaki B kaynağa erişmek için bir kuruluştaki kullanıcılara etkinleştirmek için bir yol aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="2de39-131">One way to address this problem and enable users in organization A to access the resource in organization B is as follows:</span></span>  
  
- <span data-ttu-id="2de39-132">Bir kuruluşun kullanıcıları, kimlik bilgilerini (kullanıcı adı ve parola) kuruluş b ile kaydedin.</span><span class="sxs-lookup"><span data-stu-id="2de39-132">Users from organization A register their credentials (a user name and password) with organization B.</span></span>  
  
- <span data-ttu-id="2de39-133">Kaynak erişim sırasında bir kuruluşun kullanıcıları kuruluş B için kimlik bilgilerini sunmak ve kaynağa erişmeden önce kimlikleri doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="2de39-133">During the resource access, users from organization A present their credentials to organization B and are authenticated before accessing the resource.</span></span>  
  
 <span data-ttu-id="2de39-134">Bu yaklaşım, üç önemli engelleri vardır:</span><span class="sxs-lookup"><span data-stu-id="2de39-134">This approach has three significant drawbacks:</span></span>  
  
- <span data-ttu-id="2de39-135">Yerel kullanıcı kimlik bilgilerini yönetmenin yanı sıra bir kuruluştan kullanıcılar için kimlik bilgilerini yönetmek B kuruluş var.</span><span class="sxs-lookup"><span data-stu-id="2de39-135">Organization B has to manage the credentials for users from organization A in addition to managing the credentials of its local users.</span></span>  
  
- <span data-ttu-id="2de39-136">Bir kuruluştaki kullanıcılara ek bir kimlik bilgileri kümesini bulundurmak gerekir (diğer bir deyişle, bir ek kullanıcı adınızı ve parolanızı hatırlayacağınızdan) dışında normalde A. kuruluşundaki kaynaklara erişmek için kullandıkları kimlik bilgileri Bu genellikle zayıf güvenlik önlemi olduğu birden çok hizmet sitede aynı kullanıcı adı ve parola kullanarak uygulama teşvik eder.</span><span class="sxs-lookup"><span data-stu-id="2de39-136">Users in organization A need to maintain an additional set of credentials (that is, remember an additional user name and password) apart from the credentials they normally use to gain access to resources within organization A. This usually encourages the practice of using the same user name and password at multiple service sites, which is a weak security measure.</span></span>  
  
- <span data-ttu-id="2de39-137">Kaynak kuruluşta B bazı değeri olarak kuruluşların algılar gibi mimarisi ölçeklenmez.</span><span class="sxs-lookup"><span data-stu-id="2de39-137">The architecture does not scale as more organizations perceive the resource at organization B as being of some value.</span></span>  
  
 <span data-ttu-id="2de39-138">Daha önce bahsedilen dezavantajları adresleri, alternatif bir yaklaşım, Federasyon güvenlik görevlendirmek sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="2de39-138">An alternative approach, which addresses the previously mentioned drawbacks, is to employ federated security.</span></span> <span data-ttu-id="2de39-139">Bu yaklaşım, kuruluşların A ve B bir güven ilişkisi kurmak ve güvenlik belirteci hizmeti (kurulan güven aracılığı yapmaktan etkinleştirmek için STS) kullanın.</span><span class="sxs-lookup"><span data-stu-id="2de39-139">In this approach, organizations A and B establish a trust relationship and employ Security Token Service (STS) to enable brokering of the established trust.</span></span>  
  
 <span data-ttu-id="2de39-140">İsterseniz kuruluşunuzdaki B kimlik doğrulamasından geçiren ve kullanıcıların erişimini yetkilendirir bir geçerli güvenlik belirtecine kuruluştaki B, STS sunması gerekir Web hizmetine erişmek birleşik güvenliği mimaride, bir kuruluşun kullanıcıları biliyor belirli hizmet.</span><span class="sxs-lookup"><span data-stu-id="2de39-140">In a federated security architecture, users from organization A know that if they want to access the Web service in organization B that they must present a valid security token from the STS at organization B, which authenticates and authorizes their access to the specific service.</span></span>  
  
 <span data-ttu-id="2de39-141">STS B başvurarak üzerinde bir STS ile ilişkili ilkeden başka bir yöneltme düzeyi kullanıcıları alır.</span><span class="sxs-lookup"><span data-stu-id="2de39-141">On contacting the STS B, the users receive another level of indirection from the policy associated with the STS.</span></span> <span data-ttu-id="2de39-142">Geçerli bir güvenlik sunması gerekir (diğer bir deyişle, istemci güven bölge) STS A'dan belirteci STS B bir güvenlik belirteci vermeden önce.</span><span class="sxs-lookup"><span data-stu-id="2de39-142">They must present a valid security token from the STS A (that is, the client trust realm) before the STS B can issue them a security token.</span></span> <span data-ttu-id="2de39-143">Bu iki kuruluş arasında bir güven ilişkisi bir corollary ve kuruluş B A. kuruluştan kullanıcılar için kimlikleri yönetme yok anlamına gelir. Uygulamada, STS B null olan `issuerAddress` ve `issuerMetadataAddress`.</span><span class="sxs-lookup"><span data-stu-id="2de39-143">This is a corollary of the trust relationship established between the two organizations and implies that organization B does not have to manage identities for users from organization A. In practice, STS B typically has a null `issuerAddress` and `issuerMetadataAddress`.</span></span> <span data-ttu-id="2de39-144">Daha fazla bilgi için [nasıl yapılır: Yerel yayımlayan yapılandırma](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).</span><span class="sxs-lookup"><span data-stu-id="2de39-144">For more information, see [How to: Configure a Local Issuer](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).</span></span> <span data-ttu-id="2de39-145">Bu durumda, istemci STS A. bulmak için yerel bir ilke başvurur Bu yapılandırma olarak adlandırılır *giriş bölge Federasyon* ve STS B STS A. hakkındaki bilgileri tutmak sahip olmadığından, daha iyi ölçeklendirir.</span><span class="sxs-lookup"><span data-stu-id="2de39-145">In that case, the client consults a local policy to locate STS A. This configuration is called *home realm federation* and it scales better because STS B does not have to maintain information about STS A.</span></span>  
  
 <span data-ttu-id="2de39-146">Kullanıcılar ardından kuruluştaki bir STS ile iletişime geçin ve normalde A. kuruluştaki herhangi bir kaynağa erişmek için kullandıkları kimlik doğrulama bilgileri sunarak bir güvenlik belirteci elde Bu, birden çok kimlik bilgileri kümesi sürdürmek zorunda veya birden çok hizmet sitede aynı kimlik bilgileri kümesini kullanarak kullanıcı sorununu da azaltır.</span><span class="sxs-lookup"><span data-stu-id="2de39-146">The users then contact the STS at organization A and obtain a security token by presenting authentication credentials that they normally use to gain access to any other resource within organization A. This also alleviates the problem of users having to maintain multiple sets of credentials or using the same set of credentials at multiple service sites.</span></span>  
  
 <span data-ttu-id="2de39-147">Kullanıcılar bir güvenlik belirteci STS A'dan edindikten sonra kullanıcıların isteklerin yetkilendirme gerçekleştirmeye STS B. kuruluş B kazançlar belirtece sunmak ve kendi güvenlik belirteçlerini kümesinden kullanıcılar için bir güvenlik belirteci verir.</span><span class="sxs-lookup"><span data-stu-id="2de39-147">Once the users obtain a security token from the STS A, they present the token to the STS B. Organization B proceeds to perform authorization of the users' requests and issues a security token to the users from its own set of security tokens.</span></span> <span data-ttu-id="2de39-148">Kullanıcılar kimliklerini belirteci kaynağa B kuruluştan sunmak ve hizmete erişim.</span><span class="sxs-lookup"><span data-stu-id="2de39-148">The users can then present their token to the resource at organization B and access the service.</span></span>  
  
## <a name="support-for-federated-security-in-wcf"></a><span data-ttu-id="2de39-149">Wcf'de güvenlik için destek</span><span class="sxs-lookup"><span data-stu-id="2de39-149">Support for Federated Security in WCF</span></span>  
 <span data-ttu-id="2de39-150">WCF güvenlik mimariler aracılığıyla dağıtmaya yönelik kullanıma hazır destek sağlar [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="2de39-150">WCF provides turnkey support for deploying federated security architectures through the [\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span></span>  
  
 <span data-ttu-id="2de39-151">[ \<WsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) istek-yanıt iletişim stil temelindeki iletim mekanizması olarak HTTP kullanımını gerektirir güvenli, güvenilir ve birlikte çalışabilen bir bağlama öğesi sağlar metin ve XML olarak kodlamak için kablo biçimini kullanan.</span><span class="sxs-lookup"><span data-stu-id="2de39-151">The [\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) element provides for a secure, reliable, interoperable binding that entails the use of HTTP as the underlying transport mechanism for request-reply communication style, employing text and XML as the wire format for encoding.</span></span>  
  
 <span data-ttu-id="2de39-152">Kullanımını [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) Federasyon security'de senaryo iki mantıksal olarak bağımsızdır aşamaya, aşağıdaki bölümlerde açıklandığı gibi ölçeklendirilebilmeleri.</span><span class="sxs-lookup"><span data-stu-id="2de39-152">The use of [\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) in a federated security scenario can be decoupled into two logically independent phases, as described in the following sections.</span></span>  
  
### <a name="phase-1-design-phase"></a><span data-ttu-id="2de39-153">1. Aşama: Tasarım aşaması</span><span class="sxs-lookup"><span data-stu-id="2de39-153">Phase 1: Design Phase</span></span>  
 <span data-ttu-id="2de39-154">Tasarım aşamasında, istemcinin kullandığı [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) hizmet uç noktasını kullanıma sunar politikasını okuyun ve hizmetin kimlik doğrulaması ve yetkilendirme gereksinimlerine toplanacak.</span><span class="sxs-lookup"><span data-stu-id="2de39-154">During the design phase, the client uses the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to read the policy the service endpoint exposes and to collect the service's authentication and authorization requirements.</span></span> <span data-ttu-id="2de39-155">İstemcide aşağıdaki güvenlik iletişim düzeni oluşturmak için uygun proxy oluşturulur:</span><span class="sxs-lookup"><span data-stu-id="2de39-155">The appropriate proxies are constructed to create the following federated security communication pattern at the client:</span></span>  
  
- <span data-ttu-id="2de39-156">Bir güvenlik belirteci istemcisinin güven içinde STS almak.</span><span class="sxs-lookup"><span data-stu-id="2de39-156">Obtain a security token from the STS in the client trust realm.</span></span>  
  
- <span data-ttu-id="2de39-157">Belirteç sts'ye hizmet güven bölgedeki sunar.</span><span class="sxs-lookup"><span data-stu-id="2de39-157">Present the token to the STS in the service trust realm.</span></span>  
  
- <span data-ttu-id="2de39-158">Bir güvenlik belirteci hizmeti güven bölge içinde STS almak.</span><span class="sxs-lookup"><span data-stu-id="2de39-158">Obtain a security token from the STS in the service trust realm.</span></span>  
  
- <span data-ttu-id="2de39-159">Hizmete erişmek için hizmet belirteci sunar.</span><span class="sxs-lookup"><span data-stu-id="2de39-159">Present the token to the service to access the service.</span></span>  
  
### <a name="phase-2-run-time-phase"></a><span data-ttu-id="2de39-160">2. Aşama: Çalışma zamanı aşaması</span><span class="sxs-lookup"><span data-stu-id="2de39-160">Phase 2: Run-Time Phase</span></span>  
 <span data-ttu-id="2de39-161">Çalıştırma aşamasında, istemci bir WCF istemcisi sınıfı nesnesinin örneğini oluşturur ve WCF istemcisi kullanarak bir çağrı yapar.</span><span class="sxs-lookup"><span data-stu-id="2de39-161">During the run-time phase, the client instantiates an object of the WCF client class and makes a call using the WCF client.</span></span> <span data-ttu-id="2de39-162">WCF temel çerçevesinde, Federasyon güvenlik iletişim deseni yukarıda açıklanan adımları işler ve sorunsuz bir şekilde hizmeti kullanmak ve istemcinin sağlar.</span><span class="sxs-lookup"><span data-stu-id="2de39-162">The underlying framework of WCF handles the previously mentioned steps in the federated security communication pattern and enables the client to seamlessly consume the service.</span></span>  
  
## <a name="sample-implementation-using-wcf"></a><span data-ttu-id="2de39-163">WCF kullanan örnek uygulama</span><span class="sxs-lookup"><span data-stu-id="2de39-163">Sample Implementation Using WCF</span></span>  
 <span data-ttu-id="2de39-164">Aşağıdaki çizim bir örnek uygulama için yerel destek WCF kullanarak Federasyon güvenlik mimarisi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2de39-164">The following illustration shows a sample implementation for a federated security architecture using native support from WCF.</span></span>  
  
 ![Örnek Federasyon güvenlik uygulama gösteren diyagram.](./media/federation/federated-security-implementation.gif)  
  
### <a name="example-myservice"></a><span data-ttu-id="2de39-166">Örnek MyService</span><span class="sxs-lookup"><span data-stu-id="2de39-166">Example MyService</span></span>  
 <span data-ttu-id="2de39-167">Hizmet `MyService` tek bir uç nokta aracılığıyla kullanıma sunan `MyServiceEndpoint`.</span><span class="sxs-lookup"><span data-stu-id="2de39-167">The service `MyService` exposes a single endpoint through `MyServiceEndpoint`.</span></span> <span data-ttu-id="2de39-168">Aşağıdaki çizim, adres, bağlamayı ve uç noktası ile ilişkili sözleşme gösterir.</span><span class="sxs-lookup"><span data-stu-id="2de39-168">The following illustration shows the address, binding, and contract associated with the endpoint.</span></span>  
  
 ![MyServiceEndpoint ayrıntılarını gösteren diyagram.](./media/federation/myserviceendpoint-details.gif)  
  
 <span data-ttu-id="2de39-170">Hizmet uç noktası `MyServiceEndpoint` kullanır [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) ve geçerli bir güvenlik onaylama işaretleme dili (SAML) belirteçle gerektiren bir `accessAuthorized` STS b tarafından verilen talep Bu, hizmet yapılandırmasında bildirimli olarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="2de39-170">The service endpoint `MyServiceEndpoint` uses the [\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) and requires a valid Security Assertions Markup Language (SAML) token with an `accessAuthorized` claim issued by STS B. This is declaratively specified in the service configuration.</span></span>  
  
```xml  
<system.serviceModel>  
  <services>  
    <service type="FederationSample.MyService"      
        behaviorConfiguration='MyServiceBehavior'>  
        <endpoint address=""  
            binding=" wsFederationHttpBinding"  
            bindingConfiguration='MyServiceBinding'  
            contract="Federation.IMyService" />  
   </service>  
  </services>  
  
  <bindings>  
    <wsFederationHttpBinding>  
    <!-- This is the binding used by MyService. It redirects   
    clients to STS-B. -->  
      <binding name='MyServiceBinding'>  
        <security mode="Message">  
           <message issuedTokenType=  
"http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1">  
           <issuer address="http://localhost/FederationSample/STS-B/STS.svc" />  
            <issuerMetadata   
           address=  
"http://localhost/FederationSample/STS-B/STS.svc/mex" />  
         <requiredClaimTypes>  
            <add claimType="http://tempuri.org:accessAuthorized" />  
         </requiredClaimTypes>  
        </message>  
      </security>  
      </binding>  
    </wsFederationHttpBinding>  
  </bindings>  
  
  <behaviors>  
    <behavior name='MyServiceBehavior'>  
      <serviceAuthorization   
operationRequirementType="FederationSample.MyServiceOperationRequirement, MyService" />  
       <serviceCredentials>  
         <serviceCertificate findValue="CN=FederationSample.com"  
         x509FindType="FindBySubjectDistinguishedName"  
         storeLocation='LocalMachine'  
         storeName='My' />  
      </serviceCredentials>  
    </behavior>  
  </behaviors>  
</system.serviceModel>  
```  
  
> [!NOTE]
>  <span data-ttu-id="2de39-171">Bir ince noktası gerektirdiği taleplerle ilgili unutulmamalıdır `MyService`.</span><span class="sxs-lookup"><span data-stu-id="2de39-171">A subtle point should be noted about the claims required by `MyService`.</span></span> <span data-ttu-id="2de39-172">İkinci şekil belirten `MyService` bir SAML belirteci gerektirir `accessAuthorized` talep.</span><span class="sxs-lookup"><span data-stu-id="2de39-172">The second figure indicates that `MyService` requires a SAML token with the `accessAuthorized` claim.</span></span> <span data-ttu-id="2de39-173">Daha kesin olacak şekilde bu talep türü belirtir `MyService` gerektirir.</span><span class="sxs-lookup"><span data-stu-id="2de39-173">To be more precise, this specifies the claim type that `MyService` requires.</span></span> <span data-ttu-id="2de39-174">Bu talep türü tam adı `http://tempuri.org:accessAuthorized` (ilişkili ad alanı ile birlikte), hizmet yapılandırma dosyasında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2de39-174">The fully-qualified name of this claim type is `http://tempuri.org:accessAuthorized` (along with the associated namespace), which is used in the service configuration file.</span></span> <span data-ttu-id="2de39-175">Bu talep değerini bu talep varlığını gösterir ve ayarlanması varsayılır `true` STS b tarafından</span><span class="sxs-lookup"><span data-stu-id="2de39-175">The value of this claim indicates the presence of this claim and is assumed to be set to `true` by STS B.</span></span>  
  
 <span data-ttu-id="2de39-176">Çalışma zamanında Bu ilke tarafından zorunlu `MyServiceOperationRequirement` parçası olarak uygulanan sınıfı `MyService`.</span><span class="sxs-lookup"><span data-stu-id="2de39-176">At runtime, this policy is enforced by the `MyServiceOperationRequirement` class that is implemented as part of the `MyService`.</span></span>  
  
 [!code-csharp[C_Federation#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#0)]
 [!code-vb[C_Federation#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#0)]  
[!code-csharp[C_Federation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#1)]
[!code-vb[C_Federation#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#1)]  
  
#### <a name="sts-b"></a><span data-ttu-id="2de39-177">STS B</span><span class="sxs-lookup"><span data-stu-id="2de39-177">STS B</span></span>  
 <span data-ttu-id="2de39-178">Aşağıdaki çizim STS b gösterir Daha önce belirtildiği gibi bir güvenlik belirteci hizmeti (STS) de bir Web hizmetidir ve kendi ilişkili uç noktaları, ilke ve benzeri olabilir.</span><span class="sxs-lookup"><span data-stu-id="2de39-178">The following illustration shows the STS B. As stated earlier, a security token service (STS) is also a Web service and can have its associated endpoints, policy, and so on.</span></span>  
  
 ![Güvenlik belirteci hizmeti b gösteren diyagram](./media/federation/myservice-security-token-service-b.gif)  
  
 <span data-ttu-id="2de39-180">STS B adlı tek bir uç noktasını kullanıma sunar `STSEndpoint` isteği güvenlik belirteçleri kullanmak olabilir.</span><span class="sxs-lookup"><span data-stu-id="2de39-180">STS B exposes a single endpoint, called `STSEndpoint` that can be use to request security tokens.</span></span> <span data-ttu-id="2de39-181">Özellikle, STS B SAML ile belirteçleri `accessAuthorized` talep, hangi konumunda sunulabilir `MyService` hizmete erişmek için hizmet sitesi.</span><span class="sxs-lookup"><span data-stu-id="2de39-181">Specifically, STS B issues SAML tokens with the `accessAuthorized` claim, which can be presented at the `MyService` service site for accessing the service.</span></span> <span data-ttu-id="2de39-182">Ancak, kullanıcıların içeren STS A verilen geçerli bir SAML belirteç sunmasını STS B gerektirir `userAuthenticated` talep.</span><span class="sxs-lookup"><span data-stu-id="2de39-182">However, STS B requires users to present a valid SAML token issued by STS A that contains the `userAuthenticated` claim.</span></span> <span data-ttu-id="2de39-183">Bu, STS yapılandırmada bildirimli olarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="2de39-183">This is declaratively specified in the STS configuration.</span></span>  
  
```xml  
<system.serviceModel>  
  <services>  
    <service type="FederationSample.STS_B" behaviorConfiguration=  
     "STS-B_Behavior">  
    <endpoint address=""  
              binding="wsFederationHttpBinding"  
              bindingConfiguration='STS-B_Binding'  
      contract="FederationSample.ISts" />  
    </service>  
  </services>  
  <bindings>  
    <wsFederationHttpBinding>  
    <!-- This is the binding used by STS-B. It redirects clients to   
         STS-A. -->  
      <binding name='STS-B_Binding'>  
        <security mode='Message'>  
          <message issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1">  
          <issuer address='http://localhost/FederationSample/STS-A/STS.svc' />  
          <issuerMetadata address='http://localhost/FederationSample/STS-A/STS.svc/mex'/>  
          <requiredClaimTypes>  
            <add claimType='http://tempuri.org:userAuthenticated'/>  
          </requiredClaimTypes>  
          </message>  
        </security>  
    </binding>  
   </wsFederationHttpBinding>  
  </bindings>  
  <behaviors>  
  <behavior name='STS-B_Behavior'>  
    <serviceAuthorization   operationRequirementType='FederationSample.STS_B_OperationRequirement, STS_B' />  
    <serviceCredentials>  
      <serviceCertificate findValue='CN=FederationSample.com'  
      x509FindType='FindBySubjectDistinguishedName'  
       storeLocation='LocalMachine'  
       storeName='My' />  
     </serviceCredentials>  
   </behavior>  
  </behaviors>  
</system.serviceModel>  
```  
  
> [!NOTE]
>  <span data-ttu-id="2de39-184">Yeniden `userAuthenticated` talep olduğunu STS b tarafından gerekli talep türü Bu talep türü tam adı `http://tempuri.org:userAuthenticated` (ilişkili ad alanı ile birlikte), STS'ye yapılandırma dosyasında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2de39-184">Again, the `userAuthenticated` claim is the claim type that is required by STS B. The fully-qualified name of this claim type is `http://tempuri.org:userAuthenticated` (along with the associated namespace), which is used in the STS configuration file.</span></span> <span data-ttu-id="2de39-185">Bu talep değerini bu talep varlığını gösterir ve ayarlanması varsayılır `true` STS a tarafından</span><span class="sxs-lookup"><span data-stu-id="2de39-185">The value of this claim indicates the presence of this claim and is assumed to be set to `true` by STS A.</span></span>  
  
 <span data-ttu-id="2de39-186">Çalışma zamanında, `STS_B_OperationRequirement` sınıfı STS b bir parçası olarak uygulanan bu ilkeyi zorlar</span><span class="sxs-lookup"><span data-stu-id="2de39-186">At runtime, the `STS_B_OperationRequirement` class enforces this policy, which is implemented as part of STS B.</span></span>  
  
 [!code-csharp[C_Federation#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#2)]
 [!code-vb[C_Federation#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#2)]  
  
 <span data-ttu-id="2de39-187">Erişim denetimi açık ise, STS B ile bir SAML belirteci verir. `accessAuthorized` talep.</span><span class="sxs-lookup"><span data-stu-id="2de39-187">If the access check is clear, STS B issues a SAML token with the `accessAuthorized` claim.</span></span>  
  
 [!code-csharp[C_Federation#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#3)]
 [!code-vb[C_Federation#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#3)]  
  
#### <a name="sts-a"></a><span data-ttu-id="2de39-188">STS A</span><span class="sxs-lookup"><span data-stu-id="2de39-188">STS A</span></span>  
 <span data-ttu-id="2de39-189">Aşağıdaki çizim STS A. gösterir</span><span class="sxs-lookup"><span data-stu-id="2de39-189">The following illustration shows the STS A.</span></span>  
  
 <span data-ttu-id="2de39-190">![Federasyon](../../../../docs/framework/wcf/feature-details/media/sts-b.gif "STS_B")</span><span class="sxs-lookup"><span data-stu-id="2de39-190">![Federation](../../../../docs/framework/wcf/feature-details/media/sts-b.gif "STS_B")</span></span>  
  
 <span data-ttu-id="2de39-191">STS B, STS A de güvenlik belirteçleri sağlar ve bu amaç için tek bir uç noktayı kullanıma sunan bir Web hizmeti benzer.</span><span class="sxs-lookup"><span data-stu-id="2de39-191">Similar to the STS B, the STS A is also a Web service that issues security tokens and exposes a single endpoint for this purpose.</span></span> <span data-ttu-id="2de39-192">Ancak, farklı bir bağlama kullanır (`wsHttpBinding`) ve geçerli bir sunmak kullanıcıların gerektirir [!INCLUDE[infocard](../../../../includes/infocard-md.md)] ile bir `emailAddress` talep.</span><span class="sxs-lookup"><span data-stu-id="2de39-192">However, it uses a different binding (`wsHttpBinding`) and requires users to present a valid [!INCLUDE[infocard](../../../../includes/infocard-md.md)] with an `emailAddress` claim.</span></span> <span data-ttu-id="2de39-193">İsteğe bağlı olarak yanıtta ile SAML belirteçlerini çıkartan `userAuthenticated` talep.</span><span class="sxs-lookup"><span data-stu-id="2de39-193">In response, it issues SAML tokens with the `userAuthenticated` claim.</span></span> <span data-ttu-id="2de39-194">Bu, hizmet yapılandırmasında bildirimli olarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="2de39-194">This is declaratively specified in the service configuration.</span></span>  
  
```xml  
<system.serviceModel>  
  <services>  
    <service type="FederationSample.STS_A" behaviorConfiguration="STS-A_Behavior">  
      <endpoint address=""  
                binding="wsHttpBinding"  
                bindingConfiguration="STS-A_Binding"  
                contract="FederationSample.ISts">  
       <identity>  
       <certificateReference findValue="CN=FederationSample.com"    
                       x509FindType="FindBySubjectDistinguishedName"  
                       storeLocation="LocalMachine"   
                       storeName="My" />  
       </identity>  
    <endpoint>  
  </service>  
</services>  
  
<bindings>  
  <wsHttpBinding>  
  <!-- This is the binding used by STS-A. It requires users to present  
   a CardSpace. -->  
    <binding name='STS-A_Binding'>  
      <security mode='Message'>  
        <message clientCredentialType="CardSpace" />  
      </security>  
    </binding>  
  </wsHttpBinding>  
</bindings>  
  
<behaviors>  
  <behavior name='STS-A_Behavior'>  
    <serviceAuthorization operationRequirementType=  
     "FederationSample.STS_A_OperationRequirement, STS_A" />  
      <serviceCredentials>  
  <serviceCertificate findValue="CN=FederationSample.com"  
                     x509FindType='FindBySubjectDistinguishedName'  
                     storeLocation='LocalMachine'  
                     storeName='My' />  
      </serviceCredentials>  
    </behavior>  
  </behaviors>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="2de39-195">Çalışma zamanında, `STS_A_OperationRequirement` sınıfı STS a'nın bir parçası olarak uygulanan bu ilkeyi zorlar</span><span class="sxs-lookup"><span data-stu-id="2de39-195">At runtime, the `STS_A_OperationRequirement` class enforces this policy, which is implemented as part of STS A.</span></span>  
  
 [!code-csharp[C_Federation#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#4)]
 [!code-vb[C_Federation#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#4)]  
  
 <span data-ttu-id="2de39-196">Erişim ise `true`, STS bir SAML belirteci ile sorunları `userAuthenticated` talep.</span><span class="sxs-lookup"><span data-stu-id="2de39-196">If the access is `true`, STS A issues a SAML token with `userAuthenticated` claim.</span></span>  
  
 [!code-csharp[C_Federation#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#5)]
 [!code-vb[C_Federation#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#5)]  
  
### <a name="client-at-organization-a"></a><span data-ttu-id="2de39-197">Bir kuruluştaki istemci</span><span class="sxs-lookup"><span data-stu-id="2de39-197">Client at Organization A</span></span>  
 <span data-ttu-id="2de39-198">Aşağıdaki çizimde istemci kuruluşta A yer alan adımların yanı sıra yapma gösterir bir `MyService` hizmet çağrısı.</span><span class="sxs-lookup"><span data-stu-id="2de39-198">The following illustration shows the client at organization A, along with the steps involved in making a `MyService` service call.</span></span> <span data-ttu-id="2de39-199">İşlev diğer bileşenleri de bütünlük açısından dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="2de39-199">The other functional components are also included for completeness.</span></span>  
  
 ![Showwing MyService hizmet çağrısı adımları diyagram.](./media/federation/federation-myservice-service-call-process.gif)  
  
## <a name="summary"></a><span data-ttu-id="2de39-201">Özet</span><span class="sxs-lookup"><span data-stu-id="2de39-201">Summary</span></span>  
 <span data-ttu-id="2de39-202">Birleşik güvenliği sorumluluk temiz bir bölme sağlar ve güvenli, ölçeklenebilir hizmet mimarisi oluşturmak için yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="2de39-202">Federated security provides a clean division of responsibility and helps to build secure, scalable service architectures.</span></span> <span data-ttu-id="2de39-203">Dağıtılmış uygulama oluşturup dağıtırken için bir platform, WCF, Federasyon güvenlik uygulamak için yerel destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="2de39-203">As a platform for building and deploying distributed applications, WCF provides native support for implementing federated security.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2de39-204">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2de39-204">See also</span></span>

- [<span data-ttu-id="2de39-205">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="2de39-205">Security</span></span>](../../../../docs/framework/wcf/feature-details/security.md)
