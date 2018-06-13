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
ms.openlocfilehash: d69de8c01a23eff5314220a10a51f6487080df41
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33496775"
---
# <a name="federation"></a><span data-ttu-id="e48fb-102">Federasyon</span><span class="sxs-lookup"><span data-stu-id="e48fb-102">Federation</span></span>
<span data-ttu-id="e48fb-103">Bu konu, Federasyon güvenlik kavramı kısa bir genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="e48fb-103">This topic provides a brief overview of the concept of federated security.</span></span> <span data-ttu-id="e48fb-104">Ayrıca, Federasyon güvenlik mimarileri dağıtmak için Windows Communication Foundation (WCF) destek açıklanır.</span><span class="sxs-lookup"><span data-stu-id="e48fb-104">It also describes Windows Communication Foundation (WCF) support for deploying federated security architectures.</span></span> <span data-ttu-id="e48fb-105">Federasyon gösteren örnek bir uygulama için bkz: [Federasyon örnek](../../../../docs/framework/wcf/samples/federation-sample.md).</span><span class="sxs-lookup"><span data-stu-id="e48fb-105">For a sample application that demonstrates federation, see [Federation Sample](../../../../docs/framework/wcf/samples/federation-sample.md).</span></span>  
  
## <a name="definition-of-federated-security"></a><span data-ttu-id="e48fb-106">Federasyon güvenlik tanımı</span><span class="sxs-lookup"><span data-stu-id="e48fb-106">Definition of Federated Security</span></span>  
 <span data-ttu-id="e48fb-107">Bir istemci erişim hizmeti ile ilişkili kimlik doğrulama ve yetkilendirme yordamları arasında temiz ayırmayı federe güvenlik sağlar.</span><span class="sxs-lookup"><span data-stu-id="e48fb-107">Federated security allows for clean separation between the service a client is accessing and the associated authentication and authorization procedures.</span></span> <span data-ttu-id="e48fb-108">Federasyon güvenlik işbirliği birden çok sistemler, ağlar ve farklı güven bölgelerinde kuruluşlarda üzerinden de sağlar.</span><span class="sxs-lookup"><span data-stu-id="e48fb-108">Federated security also enables collaboration across multiple systems, networks, and organizations in different trust realms.</span></span>  
  
 <span data-ttu-id="e48fb-109">WCF oluşturma ve dağıtma federe güvenlik işe dağıtılmış sistemler için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="e48fb-109">WCF provides support for building and deploying distributed systems that employ federated security.</span></span>  
  
### <a name="elements-of-a-federated-security-architecture"></a><span data-ttu-id="e48fb-110">Öğeleri bir federe güvenlik mimarisi</span><span class="sxs-lookup"><span data-stu-id="e48fb-110">Elements of a Federated Security Architecture</span></span>  
 <span data-ttu-id="e48fb-111">Federasyon güvenlik mimarisi aşağıdaki tabloda açıklandığı gibi üç temel öğeleri vardır.</span><span class="sxs-lookup"><span data-stu-id="e48fb-111">The federated security architecture has three key elements, as described in the following table.</span></span>  
  
|<span data-ttu-id="e48fb-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="e48fb-112">Element</span></span>|<span data-ttu-id="e48fb-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e48fb-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e48fb-114">Etki alanı/bölge</span><span class="sxs-lookup"><span data-stu-id="e48fb-114">Domain/realm</span></span>|<span data-ttu-id="e48fb-115">Güvenlik yönetimi ya da güven tek bir birimi.</span><span class="sxs-lookup"><span data-stu-id="e48fb-115">A single unit of security administration or trust.</span></span> <span data-ttu-id="e48fb-116">Tipik bir etki alanı tek bir kurumun içerebilir.</span><span class="sxs-lookup"><span data-stu-id="e48fb-116">A typical domain might include a single organization.</span></span>|  
|<span data-ttu-id="e48fb-117">Federasyon</span><span class="sxs-lookup"><span data-stu-id="e48fb-117">Federation</span></span>|<span data-ttu-id="e48fb-118">Güven etki alanı topluluğu.</span><span class="sxs-lookup"><span data-stu-id="e48fb-118">A collection of domains that have established trust.</span></span> <span data-ttu-id="e48fb-119">Güven düzeyi farklılık gösterebilir, ancak genellikle kimlik doğrulaması içerir ve neredeyse her zaman yetkilendirme içerir.</span><span class="sxs-lookup"><span data-stu-id="e48fb-119">The level of trust may vary, but typically includes authentication and almost always includes authorization.</span></span> <span data-ttu-id="e48fb-120">Tipik bir federasyon güveni bir kaynak kümesi için paylaşılan erişim için kuruluş sayısı içerebilir.</span><span class="sxs-lookup"><span data-stu-id="e48fb-120">A typical federation might include a number of organizations that have established trust for shared access to a set of resources.</span></span>|  
|<span data-ttu-id="e48fb-121">Güvenlik Belirteci Hizmeti (STS)</span><span class="sxs-lookup"><span data-stu-id="e48fb-121">Security Token Service (STS)</span></span>|<span data-ttu-id="e48fb-122">Güvenlik belirteçleri Web hizmeti; diğer bir deyişle, sağlanmayacağını güvendiği, çok güvendiği kanıt üzerinde temel onaylar kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="e48fb-122">A Web service that issues security tokens; that is, it makes assertions based on evidence that it trusts, to whomever trusts it.</span></span> <span data-ttu-id="e48fb-123">Bu, etki alanı arasında güven aracılığı yapmaktan temelini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e48fb-123">This forms the basis of trust brokering between domains.</span></span>|  
  
### <a name="example-scenario"></a><span data-ttu-id="e48fb-124">Örnek senaryo</span><span class="sxs-lookup"><span data-stu-id="e48fb-124">Example Scenario</span></span>  
 <span data-ttu-id="e48fb-125">Aşağıdaki çizimde bir federe güvenlik örneği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="e48fb-125">The following illustration shows an example of federated security.</span></span>  
  
 <span data-ttu-id="e48fb-126">![Federasyon](../../../../docs/framework/wcf/feature-details/media/typicalfederatedsecurityscenario.gif "TypicalFederatedSecurityScenario")</span><span class="sxs-lookup"><span data-stu-id="e48fb-126">![Federation](../../../../docs/framework/wcf/feature-details/media/typicalfederatedsecurityscenario.gif "TypicalFederatedSecurityScenario")</span></span>  
  
 <span data-ttu-id="e48fb-127">Bu senaryo iki kuruluş içerir: A ve b kuruluş B sahip bir kuruluştaki bazı kullanıcılar değerli Bul bir Web kaynağını (Web hizmeti).</span><span class="sxs-lookup"><span data-stu-id="e48fb-127">This scenario includes two organizations: A and B. Organization B has a Web resource (a Web service) that some users in organization A find valuable.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e48fb-128">Bu bölümde koşullarını kullanır *kaynak*, *hizmet*, ve *Web hizmeti* birbirinin yerine.</span><span class="sxs-lookup"><span data-stu-id="e48fb-128">This section uses the terms *resource*, *service*, and *Web service* interchangeably.</span></span>  
  
 <span data-ttu-id="e48fb-129">Genellikle, kuruluş B, A kuruluştan bir kullanıcı geçerli çeşit hizmet erişmeden önce kimlik doğrulaması sağlaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e48fb-129">Typically, organization B requires that a user from organization A provide some valid form of authentication before accessing the service.</span></span> <span data-ttu-id="e48fb-130">Ayrıca, kuruluş ayrıca kullanıcının söz konusu belirli kaynağa erişmek için yetkili gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="e48fb-130">In addition, the organization may also require that the user be authorized to access the specific resource in question.</span></span> <span data-ttu-id="e48fb-131">Bu sorunu gidermek ve kuruluştaki B kaynağa erişmek için bir kuruluştaki kullanıcılar etkinleştirmek için bir yolu aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="e48fb-131">One way to address this problem and enable users in organization A to access the resource in organization B is as follows:</span></span>  
  
-   <span data-ttu-id="e48fb-132">Bir kuruluştan kullanıcıların kimlik bilgilerini (kullanıcı adı ve parola) kuruluşunuza B. kaydedin.</span><span class="sxs-lookup"><span data-stu-id="e48fb-132">Users from organization A register their credentials (a user name and password) with organization B.</span></span>  
  
-   <span data-ttu-id="e48fb-133">Kaynak erişim sırasında kullanıcıların bir kuruluştan kuruluşa B kimlik bilgilerini sunmak ve kaynağa erişmeden önce kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="e48fb-133">During the resource access, users from organization A present their credentials to organization B and are authenticated before accessing the resource.</span></span>  
  
 <span data-ttu-id="e48fb-134">Bu yaklaşımın üç önemli sakıncaları vardır:</span><span class="sxs-lookup"><span data-stu-id="e48fb-134">This approach has three significant drawbacks:</span></span>  
  
-   <span data-ttu-id="e48fb-135">Kullanıcılar için kimlik bilgilerini yerel kullanıcı kimlik bilgilerini yönetmeye ek olarak bir kuruluştan yönetmek kuruluşun B vardır.</span><span class="sxs-lookup"><span data-stu-id="e48fb-135">Organization B has to manage the credentials for users from organization A in addition to managing the credentials of its local users.</span></span>  
  
-   <span data-ttu-id="e48fb-136">Bir kuruluştaki kullanıcılar gereken ek bir kimlik bilgileri kümesini korumak (diğer bir deyişle, bir ek kullanıcı adı ve parola unutmayın) normalde A. kuruluşunuzdaki kaynaklara erişmek için kullandıkları kimlik dışında Bu genellikle zayıf güvenlik önlemi olduğu birden çok hizmet sitede aynı kullanıcı adı ve parola kullanarak uygulama teşvik eder.</span><span class="sxs-lookup"><span data-stu-id="e48fb-136">Users in organization A need to maintain an additional set of credentials (that is, remember an additional user name and password) apart from the credentials they normally use to gain access to resources within organization A. This usually encourages the practice of using the same user name and password at multiple service sites, which is a weak security measure.</span></span>  
  
-   <span data-ttu-id="e48fb-137">Daha fazla kuruluşlar bazı değeri olarak B kuruluşu kaynak bakışını gibi mimarisi ölçeklenmez.</span><span class="sxs-lookup"><span data-stu-id="e48fb-137">The architecture does not scale as more organizations perceive the resource at organization B as being of some value.</span></span>  
  
 <span data-ttu-id="e48fb-138">Yukarıda açıklanan belirli sakıncaları adresleri, alternatif bir yaklaşım federe güvenlik kullanmayı ' dir.</span><span class="sxs-lookup"><span data-stu-id="e48fb-138">An alternative approach, which addresses the previously mentioned drawbacks, is to employ federated security.</span></span> <span data-ttu-id="e48fb-139">Bu yaklaşımda kuruluşlar A ve B bir güven ilişkisi oluşturmak ve güvenlik belirteci hizmeti (oluşturulan güven aracılığı yapmaktan etkinleştirmek için STS) kullanan.</span><span class="sxs-lookup"><span data-stu-id="e48fb-139">In this approach, organizations A and B establish a trust relationship and employ Security Token Service (STS) to enable brokering of the established trust.</span></span>  
  
 <span data-ttu-id="e48fb-140">B kuruluştaki kimliğini doğrular ve kendi erişimini yetkilendirir geçerli güvenlik uygulamasından bir belirteç kuruluştaki B STS sunmalıdır Web hizmeti erişim vermek istiyorsanız bir federe güvenlik mimaride kullanıcılar bir kuruluştan biliyor belirli hizmet.</span><span class="sxs-lookup"><span data-stu-id="e48fb-140">In a federated security architecture, users from organization A know that if they want to access the Web service in organization B that they must present a valid security token from the STS at organization B, which authenticates and authorizes their access to the specific service.</span></span>  
  
 <span data-ttu-id="e48fb-141">STS B başvurarak üzerinde kullanıcılar yöneltmesi başka bir düzeyi STS ile ilişkili ilkesinden alır.</span><span class="sxs-lookup"><span data-stu-id="e48fb-141">On contacting the STS B, the users receive another level of indirection from the policy associated with the STS.</span></span> <span data-ttu-id="e48fb-142">Geçerli bir güvenlik sunması gerekir (yani, güven istemcisinin) STS A'dan belirteci STS B bunları bir güvenlik belirteci yayımlayabilmesi.</span><span class="sxs-lookup"><span data-stu-id="e48fb-142">They must present a valid security token from the STS A (that is, the client trust realm) before the STS B can issue them a security token.</span></span> <span data-ttu-id="e48fb-143">Bu iki kuruluş arasında bir güven ilişkisi corollary ve kuruluş B A. kuruluştan kullanıcılar için kimlikleri yönetme yok anlamına gelir Uygulamada, STS B null sahip `issuerAddress` ve `issuerMetadataAddress`.</span><span class="sxs-lookup"><span data-stu-id="e48fb-143">This is a corollary of the trust relationship established between the two organizations and implies that organization B does not have to manage identities for users from organization A. In practice, STS B typically has a null `issuerAddress` and `issuerMetadataAddress`.</span></span> <span data-ttu-id="e48fb-144">Daha fazla bilgi için bkz: [nasıl yapılır: yerel yayımlayan yapılandırma](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).</span><span class="sxs-lookup"><span data-stu-id="e48fb-144">For more information, see [How to: Configure a Local Issuer](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).</span></span> <span data-ttu-id="e48fb-145">Bu durumda, istemci STS A. bulmak için bir yerel ilke başvurur Bu yapılandırma olarak adlandırılır *giriş bölgesi Federasyon* ve STS B STS A. hakkındaki bilgileri tutmak sahip olmadığından daha iyi ölçeklenir</span><span class="sxs-lookup"><span data-stu-id="e48fb-145">In that case, the client consults a local policy to locate STS A. This configuration is called *home realm federation* and it scales better because STS B does not have to maintain information about STS A.</span></span>  
  
 <span data-ttu-id="e48fb-146">Kullanıcıların sonra kuruluştaki bir STS başvurun ve normalde A. kuruluştaki herhangi bir kaynağa erişmek için kullandıkları kimlik doğrulama bilgilerini sunarak bir güvenlik belirteci alın Bu aynı zamanda birden çok kimlik bilgileri kümesi bakımını yapmak zorunda veya birden çok hizmet sitede aynı kimlik bilgileri kümesini kullanarak kullanıcı sorununu ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="e48fb-146">The users then contact the STS at organization A and obtain a security token by presenting authentication credentials that they normally use to gain access to any other resource within organization A. This also alleviates the problem of users having to maintain multiple sets of credentials or using the same set of credentials at multiple service sites.</span></span>  
  
 <span data-ttu-id="e48fb-147">Kullanıcılar bir güvenlik belirteci STS A'dan edindikten sonra kullanıcıların isteklerin yetkilendirme gerçekleştirmek üzere STS B. kuruluş B kazançlar belirtece sunmak ve kullanıcılara kendi güvenlik belirteçlerini kümesinden bir güvenlik belirteci verir.</span><span class="sxs-lookup"><span data-stu-id="e48fb-147">Once the users obtain a security token from the STS A, they present the token to the STS B. Organization B proceeds to perform authorization of the users' requests and issues a security token to the users from its own set of security tokens.</span></span> <span data-ttu-id="e48fb-148">Kullanıcılar kendi belirteci kaynağa B kuruluştan sunmak ve hizmete erişim.</span><span class="sxs-lookup"><span data-stu-id="e48fb-148">The users can then present their token to the resource at organization B and access the service.</span></span>  
  
## <a name="support-for-federated-security-in-wcf"></a><span data-ttu-id="e48fb-149">Wcf'de güvenlik desteği</span><span class="sxs-lookup"><span data-stu-id="e48fb-149">Support for Federated Security in WCF</span></span>  
 <span data-ttu-id="e48fb-150">WCF federe güvenlik mimarileri üzerinden dağıtmak için anahtar teslimi desteği sağlar [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="e48fb-150">WCF provides turnkey support for deploying federated security architectures through the [\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span></span>  
  
 <span data-ttu-id="e48fb-151">[ \<WsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) istek-yanıt iletişim stili temelindeki iletim mekanizması olarak HTTP kullanımını kapsar güvenli, güvenilir ve birlikte çalışabilir bağlama öğesi sağlar metin ve XML kodlama için kablo biçimi olarak kullanan.</span><span class="sxs-lookup"><span data-stu-id="e48fb-151">The [\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) element provides for a secure, reliable, interoperable binding that entails the use of HTTP as the underlying transport mechanism for request-reply communication style, employing text and XML as the wire format for encoding.</span></span>  
  
 <span data-ttu-id="e48fb-152">Kullanımını [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) Federasyon güvenliğinde senaryo iki mantıksal olarak bağımsızdır aşamaya, aşağıdaki bölümlerde açıklandığı gibi ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="e48fb-152">The use of [\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) in a federated security scenario can be decoupled into two logically independent phases, as described in the following sections.</span></span>  
  
### <a name="phase-1-design-phase"></a><span data-ttu-id="e48fb-153">1. Aşama: Tasarım aşaması</span><span class="sxs-lookup"><span data-stu-id="e48fb-153">Phase 1: Design Phase</span></span>  
 <span data-ttu-id="e48fb-154">Tasarım aşamasında, istemcinin kullandığı [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) hizmet uç noktasını kullanıma sunar ilkesini okuyun ve hizmetin kimlik doğrulama ve yetkilendirme gereksinimlerine toplamak için.</span><span class="sxs-lookup"><span data-stu-id="e48fb-154">During the design phase, the client uses the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to read the policy the service endpoint exposes and to collect the service's authentication and authorization requirements.</span></span> <span data-ttu-id="e48fb-155">Uygun proxy'leri istemcide aşağıdaki federe güvenlik iletişim düzeni oluşturmak üzere oluşturulur:</span><span class="sxs-lookup"><span data-stu-id="e48fb-155">The appropriate proxies are constructed to create the following federated security communication pattern at the client:</span></span>  
  
-   <span data-ttu-id="e48fb-156">İstemci güven bölge içinde STS ile bir güvenlik belirteci alın.</span><span class="sxs-lookup"><span data-stu-id="e48fb-156">Obtain a security token from the STS in the client trust realm.</span></span>  
  
-   <span data-ttu-id="e48fb-157">Belirteç Hizmeti güven bölge içinde STS sunar.</span><span class="sxs-lookup"><span data-stu-id="e48fb-157">Present the token to the STS in the service trust realm.</span></span>  
  
-   <span data-ttu-id="e48fb-158">Bir güvenlik belirteci hizmeti güven bölge içinde STS almak.</span><span class="sxs-lookup"><span data-stu-id="e48fb-158">Obtain a security token from the STS in the service trust realm.</span></span>  
  
-   <span data-ttu-id="e48fb-159">Belirteç hizmetine erişmek için hizmet sunar.</span><span class="sxs-lookup"><span data-stu-id="e48fb-159">Present the token to the service to access the service.</span></span>  
  
### <a name="phase-2-run-time-phase"></a><span data-ttu-id="e48fb-160">2. Aşama: Çalışma zamanında aşaması</span><span class="sxs-lookup"><span data-stu-id="e48fb-160">Phase 2: Run-Time Phase</span></span>  
 <span data-ttu-id="e48fb-161">Çalışma zamanı aşamasında, istemci WCF istemci sınıfın bir nesnesi oluşturur ve WCF istemcisi kullanarak bir çağrı yapar.</span><span class="sxs-lookup"><span data-stu-id="e48fb-161">During the run-time phase, the client instantiates an object of the WCF client class and makes a call using the WCF client.</span></span> <span data-ttu-id="e48fb-162">WCF temel çerçevesinde federe güvenlik iletişim düzeni yukarıda açıklanan adımları işler ve sorunsuz bir şekilde hizmeti kullanmak istemci sağlar.</span><span class="sxs-lookup"><span data-stu-id="e48fb-162">The underlying framework of WCF handles the previously mentioned steps in the federated security communication pattern and enables the client to seamlessly consume the service.</span></span>  
  
## <a name="sample-implementation-using-wcf"></a><span data-ttu-id="e48fb-163">WCF kullanarak örnek uygulama</span><span class="sxs-lookup"><span data-stu-id="e48fb-163">Sample Implementation Using WCF</span></span>  
 <span data-ttu-id="e48fb-164">Aşağıdaki çizimde WCF yerel Destek'ten kullanarak bir Federasyon güvenlik mimarisi için bir örnek uygulama gösterir.</span><span class="sxs-lookup"><span data-stu-id="e48fb-164">The following illustration shows a sample implementation for a federated security architecture using native support from WCF.</span></span>  
  
 <span data-ttu-id="e48fb-165">![WCF güvenliğinde Federasyon](../../../../docs/framework/wcf/feature-details/media/federatedsecurityinwcf.gif "FederatedSecurityInWCF")</span><span class="sxs-lookup"><span data-stu-id="e48fb-165">![Federation security in WCF](../../../../docs/framework/wcf/feature-details/media/federatedsecurityinwcf.gif "FederatedSecurityInWCF")</span></span>  
  
### <a name="example-myservice"></a><span data-ttu-id="e48fb-166">Örnek MyService</span><span class="sxs-lookup"><span data-stu-id="e48fb-166">Example MyService</span></span>  
 <span data-ttu-id="e48fb-167">Hizmet `MyService` tek bir uç noktası aracılığıyla kullanıma sunan `MyServiceEndpoint`.</span><span class="sxs-lookup"><span data-stu-id="e48fb-167">The service `MyService` exposes a single endpoint through `MyServiceEndpoint`.</span></span> <span data-ttu-id="e48fb-168">Aşağıdaki çizimde, adresi, bağlama ve uç noktasıyla ilişkili sözleşme gösterir.</span><span class="sxs-lookup"><span data-stu-id="e48fb-168">The following illustration shows the address, binding, and contract associated with the endpoint.</span></span>  
  
 <span data-ttu-id="e48fb-169">![Federasyon](../../../../docs/framework/wcf/feature-details/media/myservice.gif "MyService")</span><span class="sxs-lookup"><span data-stu-id="e48fb-169">![Federation](../../../../docs/framework/wcf/feature-details/media/myservice.gif "MyService")</span></span>  
  
 <span data-ttu-id="e48fb-170">Hizmet uç noktası `MyServiceEndpoint` kullanan [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) ve geçerli bir güvenlik onaylar biçimlendirme dili (SAML) belirteci ile gerektiren bir `accessAuthorized` STS B. tarafından verilen talep Bu hizmet yapılandırmasında bildirimli olarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="e48fb-170">The service endpoint `MyServiceEndpoint` uses the [\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) and requires a valid Security Assertions Markup Language (SAML) token with an `accessAuthorized` claim issued by STS B. This is declaratively specified in the service configuration.</span></span>  
  
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
>  <span data-ttu-id="e48fb-171">Bir ince noktası gerektirdiği talepler hakkında unutulmamalıdır `MyService`.</span><span class="sxs-lookup"><span data-stu-id="e48fb-171">A subtle point should be noted about the claims required by `MyService`.</span></span> <span data-ttu-id="e48fb-172">İkinci şekil belirten `MyService` bir SAML belirteci gerektirir `accessAuthorized` talep.</span><span class="sxs-lookup"><span data-stu-id="e48fb-172">The second figure indicates that `MyService` requires a SAML token with the `accessAuthorized` claim.</span></span> <span data-ttu-id="e48fb-173">Daha kesin olacak şekilde bu talep türü belirtir `MyService` gerektirir.</span><span class="sxs-lookup"><span data-stu-id="e48fb-173">To be more precise, this specifies the claim type that `MyService` requires.</span></span> <span data-ttu-id="e48fb-174">Bu talep türü tam adı http://tempuri.org:accessAuthorized (ilişkili ad alanı ile birlikte), hangi hizmet yapılandırma dosyasında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e48fb-174">The fully-qualified name of this claim type is http://tempuri.org:accessAuthorized (along with the associated namespace), which is used in the service configuration file.</span></span> <span data-ttu-id="e48fb-175">Bu talep değerini bu talep durumunu gösteren ve ayarlamak için kabul `true` STS B. tarafından</span><span class="sxs-lookup"><span data-stu-id="e48fb-175">The value of this claim indicates the presence of this claim and is assumed to be set to `true` by STS B.</span></span>  
  
 <span data-ttu-id="e48fb-176">Çalışma zamanında, bu ilke tarafından uygulanan `MyServiceOperationRequirement` parçası olarak uygulanan sınıfı `MyService`.</span><span class="sxs-lookup"><span data-stu-id="e48fb-176">At runtime, this policy is enforced by the `MyServiceOperationRequirement` class that is implemented as part of the `MyService`.</span></span>  
  
 [!code-csharp[C_Federation#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#0)]
 [!code-vb[C_Federation#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#0)]  
[!code-csharp[C_Federation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#1)]
[!code-vb[C_Federation#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#1)]  
  
#### <a name="sts-b"></a><span data-ttu-id="e48fb-177">STS B</span><span class="sxs-lookup"><span data-stu-id="e48fb-177">STS B</span></span>  
 <span data-ttu-id="e48fb-178">STS B. aşağıda gösterilmektedir Daha önce belirtildiği gibi bir güvenlik belirteci hizmeti (STS) de bir Web hizmetidir ve ilişkili uç noktaları, ilke ve benzeri olabilir.</span><span class="sxs-lookup"><span data-stu-id="e48fb-178">The following illustration shows the STS B. As stated earlier, a security token service (STS) is also a Web service and can have its associated endpoints, policy, and so on.</span></span>  
  
 <span data-ttu-id="e48fb-179">![Federasyon](../../../../docs/framework/wcf/feature-details/media/msservicestsb.gif "MsServiceSTSB")</span><span class="sxs-lookup"><span data-stu-id="e48fb-179">![Federation](../../../../docs/framework/wcf/feature-details/media/msservicestsb.gif "MsServiceSTSB")</span></span>  
  
 <span data-ttu-id="e48fb-180">STS B adlı tek bir uç noktasını kullanıma sunar `STSEndpoint` isteği güvenlik belirteçleri kullanımına olabilir.</span><span class="sxs-lookup"><span data-stu-id="e48fb-180">STS B exposes a single endpoint, called `STSEndpoint` that can be use to request security tokens.</span></span> <span data-ttu-id="e48fb-181">Özellikle, STS B SAML ile belirteçleri `accessAuthorized` talep, hangi konumunda sunulabilir `MyService` hizmete erişim için hizmet sitesi.</span><span class="sxs-lookup"><span data-stu-id="e48fb-181">Specifically, STS B issues SAML tokens with the `accessAuthorized` claim, which can be presented at the `MyService` service site for accessing the service.</span></span> <span data-ttu-id="e48fb-182">Ancak, STS B içeren STS A verilen geçerli bir SAML belirteci sunmak kullanıcılara gerektirir `userAuthenticated` talep.</span><span class="sxs-lookup"><span data-stu-id="e48fb-182">However, STS B requires users to present a valid SAML token issued by STS A that contains the `userAuthenticated` claim.</span></span> <span data-ttu-id="e48fb-183">Bu STS yapılandırmasında bildirimli olarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="e48fb-183">This is declaratively specified in the STS configuration.</span></span>  
  
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
>  <span data-ttu-id="e48fb-184">Yeniden `userAuthenticated` talep olduğu STS B. tarafından gerekli talep türü Bu talep türü tam adı http://tempuri.org:userAuthenticated (ilişkili ad alanı ile birlikte), hangi STS yapılandırma dosyasında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e48fb-184">Again, the `userAuthenticated` claim is the claim type that is required by STS B. The fully-qualified name of this claim type is http://tempuri.org:userAuthenticated (along with the associated namespace), which is used in the STS configuration file.</span></span> <span data-ttu-id="e48fb-185">Bu talep değerini bu talep durumunu gösteren ve ayarlamak için kabul `true` STS A. tarafından</span><span class="sxs-lookup"><span data-stu-id="e48fb-185">The value of this claim indicates the presence of this claim and is assumed to be set to `true` by STS A.</span></span>  
  
 <span data-ttu-id="e48fb-186">Çalışma zamanında `STS_B_OperationRequirement` sınıfı STS B. bir parçası olarak uygulanan bu ilkeyi zorlar</span><span class="sxs-lookup"><span data-stu-id="e48fb-186">At runtime, the `STS_B_OperationRequirement` class enforces this policy, which is implemented as part of STS B.</span></span>  
  
 [!code-csharp[C_Federation#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#2)]
 [!code-vb[C_Federation#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#2)]  
  
 <span data-ttu-id="e48fb-187">Erişim denetimi boş olduğunda, bir SAML belirteci STS B sorunları `accessAuthorized` talep.</span><span class="sxs-lookup"><span data-stu-id="e48fb-187">If the access check is clear, STS B issues a SAML token with the `accessAuthorized` claim.</span></span>  
  
 [!code-csharp[C_Federation#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#3)]
 [!code-vb[C_Federation#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#3)]  
  
#### <a name="sts-a"></a><span data-ttu-id="e48fb-188">STS A</span><span class="sxs-lookup"><span data-stu-id="e48fb-188">STS A</span></span>  
 <span data-ttu-id="e48fb-189">STS A. aşağıda gösterilmektedir</span><span class="sxs-lookup"><span data-stu-id="e48fb-189">The following illustration shows the STS A.</span></span>  
  
 <span data-ttu-id="e48fb-190">![Federasyon](../../../../docs/framework/wcf/feature-details/media/sts-b.gif "STS_B")</span><span class="sxs-lookup"><span data-stu-id="e48fb-190">![Federation](../../../../docs/framework/wcf/feature-details/media/sts-b.gif "STS_B")</span></span>  
  
 <span data-ttu-id="e48fb-191">STS B, STS A Ayrıca güvenlik belirteçleri sağlar ve bu amaç için tek bir uç nokta gösteren bir Web hizmeti benzer.</span><span class="sxs-lookup"><span data-stu-id="e48fb-191">Similar to the STS B, the STS A is also a Web service that issues security tokens and exposes a single endpoint for this purpose.</span></span> <span data-ttu-id="e48fb-192">Ancak, başka bir bağlama kullanır (`wsHttpBinding`) ve geçerli bir sunmak kullanıcıların gerektiren [!INCLUDE[infocard](../../../../includes/infocard-md.md)] ile bir `emailAddress` talep.</span><span class="sxs-lookup"><span data-stu-id="e48fb-192">However, it uses a different binding (`wsHttpBinding`) and requires users to present a valid [!INCLUDE[infocard](../../../../includes/infocard-md.md)] with an `emailAddress` claim.</span></span> <span data-ttu-id="e48fb-193">SAML belirteçleri ile verdiği yanıt olarak `userAuthenticated` talep.</span><span class="sxs-lookup"><span data-stu-id="e48fb-193">In response, it issues SAML tokens with the `userAuthenticated` claim.</span></span> <span data-ttu-id="e48fb-194">Bu hizmet yapılandırmasında bildirimli olarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="e48fb-194">This is declaratively specified in the service configuration.</span></span>  
  
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
  
 <span data-ttu-id="e48fb-195">Çalışma zamanında `STS_A_OperationRequirement` sınıfı STS A. bir parçası olarak uygulanan bu ilkeyi zorlar</span><span class="sxs-lookup"><span data-stu-id="e48fb-195">At runtime, the `STS_A_OperationRequirement` class enforces this policy, which is implemented as part of STS A.</span></span>  
  
 [!code-csharp[C_Federation#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#4)]
 [!code-vb[C_Federation#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#4)]  
  
 <span data-ttu-id="e48fb-196">Erişim ise `true`, STS A sorunları SAML belirteci ile `userAuthenticated` talep.</span><span class="sxs-lookup"><span data-stu-id="e48fb-196">If the access is `true`, STS A issues a SAML token with `userAuthenticated` claim.</span></span>  
  
 [!code-csharp[C_Federation#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#5)]
 [!code-vb[C_Federation#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#5)]  
  
### <a name="client-at-organization-a"></a><span data-ttu-id="e48fb-197">Kuruluşun bir istemcide</span><span class="sxs-lookup"><span data-stu-id="e48fb-197">Client at Organization A</span></span>  
 <span data-ttu-id="e48fb-198">Aşağıdaki çizimde istemci kuruluşta A adımlarını birlikte yapma gösterir bir `MyService` hizmet çağrısı.</span><span class="sxs-lookup"><span data-stu-id="e48fb-198">The following illustration shows the client at organization A, along with the steps involved in making a `MyService` service call.</span></span> <span data-ttu-id="e48fb-199">Bir işlev bileşenleri de bütünlük açısından dahil edilmiştir.</span><span class="sxs-lookup"><span data-stu-id="e48fb-199">The other functional components are also included for completeness.</span></span>  
  
 <span data-ttu-id="e48fb-200">![Federasyon](../../../../docs/framework/wcf/feature-details/media/federationclienta.gif "FederationClientA")</span><span class="sxs-lookup"><span data-stu-id="e48fb-200">![Federation](../../../../docs/framework/wcf/feature-details/media/federationclienta.gif "FederationClientA")</span></span>  
  
## <a name="summary"></a><span data-ttu-id="e48fb-201">Özet</span><span class="sxs-lookup"><span data-stu-id="e48fb-201">Summary</span></span>  
 <span data-ttu-id="e48fb-202">Federasyon güvenlik sorumluluk temiz bölme sağlar ve güvenli, ölçeklenebilir hizmet mimarileri oluşturmaya yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="e48fb-202">Federated security provides a clean division of responsibility and helps to build secure, scalable service architectures.</span></span> <span data-ttu-id="e48fb-203">Dağıtılmış uygulamaları geliştirmek ve dağıtılmak için platform WCF federe güvenlik uygulamak için yerel destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="e48fb-203">As a platform for building and deploying distributed applications, WCF provides native support for implementing federated security.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e48fb-204">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e48fb-204">See Also</span></span>  
 [<span data-ttu-id="e48fb-205">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="e48fb-205">Security</span></span>](../../../../docs/framework/wcf/feature-details/security.md)
