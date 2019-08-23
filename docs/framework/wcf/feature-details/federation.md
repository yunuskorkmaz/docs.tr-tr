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
ms.openlocfilehash: 2331e484f22be7e3154a4cff981ee320a9b143a5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69948155"
---
# <a name="federation"></a><span data-ttu-id="bbf6e-102">Federasyon</span><span class="sxs-lookup"><span data-stu-id="bbf6e-102">Federation</span></span>
<span data-ttu-id="bbf6e-103">Bu konuda, Federe güvenlik kavramıyla ilgili kısa bir genel bakış sunulmaktadır.</span><span class="sxs-lookup"><span data-stu-id="bbf6e-103">This topic provides a brief overview of the concept of federated security.</span></span> <span data-ttu-id="bbf6e-104">Federasyon güvenlik mimarilerini dağıtmaya yönelik Windows Communication Foundation (WCF) desteğini de açıklar.</span><span class="sxs-lookup"><span data-stu-id="bbf6e-104">It also describes Windows Communication Foundation (WCF) support for deploying federated security architectures.</span></span> <span data-ttu-id="bbf6e-105">Federasyonu gösteren örnek bir uygulama için bkz. [Federasyon örneği](../../../../docs/framework/wcf/samples/federation-sample.md).</span><span class="sxs-lookup"><span data-stu-id="bbf6e-105">For a sample application that demonstrates federation, see [Federation Sample](../../../../docs/framework/wcf/samples/federation-sample.md).</span></span>  
  
## <a name="definition-of-federated-security"></a><span data-ttu-id="bbf6e-106">Federal Güvenlik tanımı</span><span class="sxs-lookup"><span data-stu-id="bbf6e-106">Definition of Federated Security</span></span>  
 <span data-ttu-id="bbf6e-107">Federasyon güvenliği, bir istemcinin eriştiği hizmet ile ilişkili kimlik doğrulama ve yetkilendirme yordamlarına kadar temiz ayrım sağlar.</span><span class="sxs-lookup"><span data-stu-id="bbf6e-107">Federated security allows for clean separation between the service a client is accessing and the associated authentication and authorization procedures.</span></span> <span data-ttu-id="bbf6e-108">Federasyon güvenliği, farklı güven bölgelerinde birden fazla sistem, ağ ve kuruluşta işbirliği yapılmasını de mümkün.</span><span class="sxs-lookup"><span data-stu-id="bbf6e-108">Federated security also enables collaboration across multiple systems, networks, and organizations in different trust realms.</span></span>  
  
 <span data-ttu-id="bbf6e-109">WCF, Federasyon güvenliği kullanan dağıtılmış sistemler oluşturmak ve dağıtmak için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="bbf6e-109">WCF provides support for building and deploying distributed systems that employ federated security.</span></span>  
  
### <a name="elements-of-a-federated-security-architecture"></a><span data-ttu-id="bbf6e-110">Federasyon güvenlik mimarisinin öğeleri</span><span class="sxs-lookup"><span data-stu-id="bbf6e-110">Elements of a Federated Security Architecture</span></span>  
 <span data-ttu-id="bbf6e-111">Federasyon güvenlik mimarisinin aşağıdaki tabloda açıklandığı gibi üç anahtar öğesi vardır.</span><span class="sxs-lookup"><span data-stu-id="bbf6e-111">The federated security architecture has three key elements, as described in the following table.</span></span>  
  
|<span data-ttu-id="bbf6e-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="bbf6e-112">Element</span></span>|<span data-ttu-id="bbf6e-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bbf6e-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bbf6e-114">Etki alanı/bölge</span><span class="sxs-lookup"><span data-stu-id="bbf6e-114">Domain/realm</span></span>|<span data-ttu-id="bbf6e-115">Tek bir güvenlik yönetimi veya güven birimi.</span><span class="sxs-lookup"><span data-stu-id="bbf6e-115">A single unit of security administration or trust.</span></span> <span data-ttu-id="bbf6e-116">Tipik bir etki alanı tek bir kuruluş içerebilir.</span><span class="sxs-lookup"><span data-stu-id="bbf6e-116">A typical domain might include a single organization.</span></span>|  
|<span data-ttu-id="bbf6e-117">Federasyon</span><span class="sxs-lookup"><span data-stu-id="bbf6e-117">Federation</span></span>|<span data-ttu-id="bbf6e-118">Güvenine sahip bir etki alanı koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="bbf6e-118">A collection of domains that have established trust.</span></span> <span data-ttu-id="bbf6e-119">Güven düzeyi farklılık gösterebilir, ancak genellikle kimlik doğrulaması içerir ve hemen her zaman yetkilendirme içerir.</span><span class="sxs-lookup"><span data-stu-id="bbf6e-119">The level of trust may vary, but typically includes authentication and almost always includes authorization.</span></span> <span data-ttu-id="bbf6e-120">Tipik bir federasyon güveni için bir kaynak kümesi için paylaşılan erişim kuruluşların sayısı içerebilir.</span><span class="sxs-lookup"><span data-stu-id="bbf6e-120">A typical federation might include a number of organizations that have established trust for shared access to a set of resources.</span></span>|  
|<span data-ttu-id="bbf6e-121">Güvenlik Belirteci Hizmeti (STS)</span><span class="sxs-lookup"><span data-stu-id="bbf6e-121">Security Token Service (STS)</span></span>|<span data-ttu-id="bbf6e-122">Güvenlik belirteçleri veren bir Web hizmeti; diğer bir deyişle, bu, güvendiğini ve güvenmesini sağlayan kanıtları temel alarak onaylamaları yapar.</span><span class="sxs-lookup"><span data-stu-id="bbf6e-122">A Web service that issues security tokens; that is, it makes assertions based on evidence that it trusts, to whomever trusts it.</span></span> <span data-ttu-id="bbf6e-123">Bu, etki alanları arasındaki güven aracılığı temelini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bbf6e-123">This forms the basis of trust brokering between domains.</span></span>|  
  
### <a name="example-scenario"></a><span data-ttu-id="bbf6e-124">Örnek senaryo</span><span class="sxs-lookup"><span data-stu-id="bbf6e-124">Example Scenario</span></span>  
 <span data-ttu-id="bbf6e-125">Aşağıdaki çizimde bir Federasyon güvenliği örneği gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="bbf6e-125">The following illustration shows an example of federated security:</span></span>  
  
 ![Tipik bir Federasyon güvenlik senaryosunu gösteren diyagram.](./media/federation/typical-federated-security-scenario.gif)  
  
 <span data-ttu-id="bbf6e-127">Bu senaryo iki kuruluş içerir: A ve B. kuruluş B, kuruluşlardaki bazı kullanıcıların önemli bulabileceği bir web kaynağına (Web hizmeti) sahiptir.</span><span class="sxs-lookup"><span data-stu-id="bbf6e-127">This scenario includes two organizations: A and B. Organization B has a Web resource (a Web service) that some users in organization A find valuable.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bbf6e-128">Bu bölümde, *kaynak*, *hizmet*ve *Web hizmeti* 'nin birbirlerinin yerine kullanıldığı terimler kullanılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="bbf6e-128">This section uses the terms *resource*, *service*, and *Web service* interchangeably.</span></span>  
  
 <span data-ttu-id="bbf6e-129">Genellikle kuruluş B, bir kullanıcının, hizmet erişmeden önce geçerli bir kimlik doğrulama biçimi sağlamasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="bbf6e-129">Typically, organization B requires that a user from organization A provide some valid form of authentication before accessing the service.</span></span> <span data-ttu-id="bbf6e-130">Ayrıca, kuruluş, kullanıcının söz konusu kaynağa erişmek için yetkilendirilmesini de gerektirebilir.</span><span class="sxs-lookup"><span data-stu-id="bbf6e-130">In addition, the organization may also require that the user be authorized to access the specific resource in question.</span></span> <span data-ttu-id="bbf6e-131">Bu sorunu ele almanın ve kuruluşlardaki kullanıcıların B kuruluşunda kaynağa erişmesi için bir yol aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="bbf6e-131">One way to address this problem and enable users in organization A to access the resource in organization B is as follows:</span></span>  
  
- <span data-ttu-id="bbf6e-132">Kuruluştaki kullanıcılar, kimlik bilgilerini (Kullanıcı adı ve parola) B kuruluşuna kaydeder.</span><span class="sxs-lookup"><span data-stu-id="bbf6e-132">Users from organization A register their credentials (a user name and password) with organization B.</span></span>  
  
- <span data-ttu-id="bbf6e-133">Kaynak erişimi sırasında, kuruluşlardaki kullanıcılar kimlik bilgilerini B kuruluşuna sunmadan, kaynağa erişmeden önce kimlik doğrulamasından geçer.</span><span class="sxs-lookup"><span data-stu-id="bbf6e-133">During the resource access, users from organization A present their credentials to organization B and are authenticated before accessing the resource.</span></span>  
  
 <span data-ttu-id="bbf6e-134">Bu yaklaşım üç önemli dezavantaja sahiptir:</span><span class="sxs-lookup"><span data-stu-id="bbf6e-134">This approach has three significant drawbacks:</span></span>  
  
- <span data-ttu-id="bbf6e-135">B kuruluşunun, yerel kullanıcılarının kimlik bilgilerini yönetmeye ek olarak, kuruluşlarındaki kullanıcıların kimlik bilgilerini yönetmesi vardır.</span><span class="sxs-lookup"><span data-stu-id="bbf6e-135">Organization B has to manage the credentials for users from organization A in addition to managing the credentials of its local users.</span></span>  
  
- <span data-ttu-id="bbf6e-136">Kuruluştaki kullanıcıların, normalde bir kuruluş içindeki kaynaklara erişim kazanmak için kullandıkları kimlik bilgilerinden ayrı bir ek kimlik bilgileri (yani, ek Kullanıcı adı ve parola hatırlamaları) olması gerekir. Bu genellikle, çok sayıda hizmet sitesinde aynı Kullanıcı adı ve parolayı kullanma ve zayıf bir güvenlik ölçüsü olan uygulamayı teşvik eder.</span><span class="sxs-lookup"><span data-stu-id="bbf6e-136">Users in organization A need to maintain an additional set of credentials (that is, remember an additional user name and password) apart from the credentials they normally use to gain access to resources within organization A. This usually encourages the practice of using the same user name and password at multiple service sites, which is a weak security measure.</span></span>  
  
- <span data-ttu-id="bbf6e-137">Daha fazla kuruluş, B kuruluşunda kaynağı bir değer olduğu gibi algılamaz mimari ölçeklenmez.</span><span class="sxs-lookup"><span data-stu-id="bbf6e-137">The architecture does not scale as more organizations perceive the resource at organization B as being of some value.</span></span>  
  
 <span data-ttu-id="bbf6e-138">Daha önce bahsedilen dezavantajları ele veren alternatif bir yaklaşım, Federe güvenlik kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="bbf6e-138">An alternative approach, which addresses the previously mentioned drawbacks, is to employ federated security.</span></span> <span data-ttu-id="bbf6e-139">Bu yaklaşımda, A ve B kuruluşları bir güven ilişkisi kurar ve kurulan güvenin aracılı hale getirmesini sağlamak için güvenlik belirteci hizmeti (STS) benimseme.</span><span class="sxs-lookup"><span data-stu-id="bbf6e-139">In this approach, organizations A and B establish a trust relationship and employ Security Token Service (STS) to enable brokering of the established trust.</span></span>  
  
 <span data-ttu-id="bbf6e-140">Bir Federasyon güvenlik mimarisinde, kuruluşlardaki kullanıcılar b kuruluşunda Web hizmetine erişmek istiyorlarsa, b kuruluşunda bulunan STS 'den geçerli bir güvenlik belirteci sunması gerektiğini ve bunlara erişimini doğrulayan ve belirli bir hizmet.</span><span class="sxs-lookup"><span data-stu-id="bbf6e-140">In a federated security architecture, users from organization A know that if they want to access the Web service in organization B that they must present a valid security token from the STS at organization B, which authenticates and authorizes their access to the specific service.</span></span>  
  
 <span data-ttu-id="bbf6e-141">STS B ile iletişim kurulurken, kullanıcılar STS ile ilişkili ilkeden başka bir yöneltme düzeyi alır.</span><span class="sxs-lookup"><span data-stu-id="bbf6e-141">On contacting the STS B, the users receive another level of indirection from the policy associated with the STS.</span></span> <span data-ttu-id="bbf6e-142">STS B 'nin bir güvenlik belirteci vermesini gerektiren STS A 'nın (yani, istemci güven bölgesi) geçerli bir güvenlik belirteci sunması gerekir.</span><span class="sxs-lookup"><span data-stu-id="bbf6e-142">They must present a valid security token from the STS A (that is, the client trust realm) before the STS B can issue them a security token.</span></span> <span data-ttu-id="bbf6e-143">Bu, iki kuruluş arasında kurulan güven ilişkisinin bir sahibi olabilir ve B kuruluşunun, A kuruluşundan kullanıcılar için kimlikleri yönetmesi gerekmez. Pratikte STS B genellikle null `issuerAddress` ve `issuerMetadataAddress`içerir.</span><span class="sxs-lookup"><span data-stu-id="bbf6e-143">This is a corollary of the trust relationship established between the two organizations and implies that organization B does not have to manage identities for users from organization A. In practice, STS B typically has a null `issuerAddress` and `issuerMetadataAddress`.</span></span> <span data-ttu-id="bbf6e-144">Daha fazla bilgi için [nasıl yapılır: Yerel bir veren](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="bbf6e-144">For more information, see [How to: Configure a Local Issuer](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).</span></span> <span data-ttu-id="bbf6e-145">Bu durumda, istemci STS A 'nın yerini bulmak için yerel bir ilke danışmanlar. Bu yapılandırma, *Ev bölgesi Federasyonu* olarak ADLANDıRıLıR ve STS B 'nin STS hakkındaki bilgileri saklamak zorunda olmadığından daha iyi ölçeklendirilir.</span><span class="sxs-lookup"><span data-stu-id="bbf6e-145">In that case, the client consults a local policy to locate STS A. This configuration is called *home realm federation* and it scales better because STS B does not have to maintain information about STS A.</span></span>  
  
 <span data-ttu-id="bbf6e-146">Kullanıcılar A kurumunda STS ile iletişim kurun ve normal olarak kuruluş içindeki diğer kaynaklara erişim kazanmak için kullandıkları kimlik doğrulama kimlik bilgilerini sunarak bir güvenlik belirteci elde eder. Bu Ayrıca, kullanıcıların birden çok kimlik bilgisi kümesini sürdürmek veya birden çok hizmet sitesinde aynı kimlik bilgilerini kullanmasını sağlamak zorunda konuma almayı azaltır sorununu da ortadan koyar.</span><span class="sxs-lookup"><span data-stu-id="bbf6e-146">The users then contact the STS at organization A and obtain a security token by presenting authentication credentials that they normally use to gain access to any other resource within organization A. This also alleviates the problem of users having to maintain multiple sets of credentials or using the same set of credentials at multiple service sites.</span></span>  
  
 <span data-ttu-id="bbf6e-147">Kullanıcılar STS A 'dan bir güvenlik belirteci aldıktan sonra, bu belirteci STS 'ye sunar. B. kuruluş, kullanıcıların isteklerini yetkilendirmeyi gerçekleştirmeye devam eder ve kendi güvenlik belirteçleri kümesinden kullanıcılara bir güvenlik belirteci yayınlar.</span><span class="sxs-lookup"><span data-stu-id="bbf6e-147">Once the users obtain a security token from the STS A, they present the token to the STS B. Organization B proceeds to perform authorization of the users' requests and issues a security token to the users from its own set of security tokens.</span></span> <span data-ttu-id="bbf6e-148">Kullanıcılar daha sonra belirtecini B kuruluşunda kaynağa sunabilir ve hizmete erişebilir.</span><span class="sxs-lookup"><span data-stu-id="bbf6e-148">The users can then present their token to the resource at organization B and access the service.</span></span>  
  
## <a name="support-for-federated-security-in-wcf"></a><span data-ttu-id="bbf6e-149">WCF 'de Federal güvenlik desteği</span><span class="sxs-lookup"><span data-stu-id="bbf6e-149">Support for Federated Security in WCF</span></span>  
 <span data-ttu-id="bbf6e-150">WCF, [ \<WSFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)aracılığıyla Federe güvenlik mimarilerini dağıtmaya yönelik anahtar desteği sağlar.</span><span class="sxs-lookup"><span data-stu-id="bbf6e-150">WCF provides turnkey support for deploying federated security architectures through the [\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span></span>  
  
 <span data-ttu-id="bbf6e-151">WSFederationHttpBinding > öğesi, istek-yanıt iletişim stili için temel alınan aktarım mekanizması olarak http kullanımını gerektiren güvenli, güvenilir ve birlikte çalışabilen bir bağlama sağlar. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) kodlama için tel biçimlendirme.</span><span class="sxs-lookup"><span data-stu-id="bbf6e-151">The [\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) element provides for a secure, reliable, interoperable binding that entails the use of HTTP as the underlying transport mechanism for request-reply communication style, employing text and XML as the wire format for encoding.</span></span>  
  
 <span data-ttu-id="bbf6e-152">Bir Federasyon güvenlik senaryosunda [ \<WSFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) kullanımı, aşağıdaki bölümlerde açıklandığı gibi iki mantıksal bağımsız aşamaya ayrılabilir.</span><span class="sxs-lookup"><span data-stu-id="bbf6e-152">The use of [\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) in a federated security scenario can be decoupled into two logically independent phases, as described in the following sections.</span></span>  
  
### <a name="phase-1-design-phase"></a><span data-ttu-id="bbf6e-153">1\. Aşama: Tasarım aşaması</span><span class="sxs-lookup"><span data-stu-id="bbf6e-153">Phase 1: Design Phase</span></span>  
 <span data-ttu-id="bbf6e-154">Tasarım aşamasında istemci, hizmet uç noktasının açığa çıkardığı ilkeyi okumak ve hizmetin kimlik doğrulama ve yetkilendirme gereksinimlerini toplamak için [ServiceModel meta veri yardımcı programı aracını (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) kullanır.</span><span class="sxs-lookup"><span data-stu-id="bbf6e-154">During the design phase, the client uses the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to read the policy the service endpoint exposes and to collect the service's authentication and authorization requirements.</span></span> <span data-ttu-id="bbf6e-155">İstemci üzerinde aşağıdaki Federasyon güvenliği iletişim modelini oluşturmak için uygun proxy 'ler oluşturulur:</span><span class="sxs-lookup"><span data-stu-id="bbf6e-155">The appropriate proxies are constructed to create the following federated security communication pattern at the client:</span></span>  
  
- <span data-ttu-id="bbf6e-156">İstemci güven bölgesindeki STS 'den bir güvenlik belirteci alın.</span><span class="sxs-lookup"><span data-stu-id="bbf6e-156">Obtain a security token from the STS in the client trust realm.</span></span>  
  
- <span data-ttu-id="bbf6e-157">Belirteci hizmet güven bölgesindeki STS 'ye sunun.</span><span class="sxs-lookup"><span data-stu-id="bbf6e-157">Present the token to the STS in the service trust realm.</span></span>  
  
- <span data-ttu-id="bbf6e-158">Hizmet güven bölgesindeki STS 'den bir güvenlik belirteci alın.</span><span class="sxs-lookup"><span data-stu-id="bbf6e-158">Obtain a security token from the STS in the service trust realm.</span></span>  
  
- <span data-ttu-id="bbf6e-159">Hizmete erişmek için belirteci hizmete sunun.</span><span class="sxs-lookup"><span data-stu-id="bbf6e-159">Present the token to the service to access the service.</span></span>  
  
### <a name="phase-2-run-time-phase"></a><span data-ttu-id="bbf6e-160">2\. Aşama: Çalışma zamanı aşaması</span><span class="sxs-lookup"><span data-stu-id="bbf6e-160">Phase 2: Run-Time Phase</span></span>  
 <span data-ttu-id="bbf6e-161">Çalışma zamanı aşamasında istemci, WCF istemci sınıfının bir nesnesini başlatır ve WCF istemcisini kullanarak bir çağrı yapar.</span><span class="sxs-lookup"><span data-stu-id="bbf6e-161">During the run-time phase, the client instantiates an object of the WCF client class and makes a call using the WCF client.</span></span> <span data-ttu-id="bbf6e-162">WCF 'nin temel alınan çatısı, Federasyon güvenliği iletişim düzeninde daha önce bahsedilen adımları işler ve istemcinin hizmeti sorunsuz bir şekilde kullanmasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="bbf6e-162">The underlying framework of WCF handles the previously mentioned steps in the federated security communication pattern and enables the client to seamlessly consume the service.</span></span>  
  
## <a name="sample-implementation-using-wcf"></a><span data-ttu-id="bbf6e-163">WCF kullanarak örnek uygulama</span><span class="sxs-lookup"><span data-stu-id="bbf6e-163">Sample Implementation Using WCF</span></span>  
 <span data-ttu-id="bbf6e-164">Aşağıdaki çizimde, WCF 'den yerel destek kullanan bir Federasyon güvenlik mimarisine yönelik örnek bir uygulama gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="bbf6e-164">The following illustration shows a sample implementation for a federated security architecture using native support from WCF.</span></span>  
  
 ![Örnek bir Federasyon güvenlik uygulamasını gösteren diyagram.](./media/federation/federated-security-implementation.gif)  
  
### <a name="example-myservice"></a><span data-ttu-id="bbf6e-166">Örnek hizmetim</span><span class="sxs-lookup"><span data-stu-id="bbf6e-166">Example MyService</span></span>  
 <span data-ttu-id="bbf6e-167">Hizmet `MyService` aracılığıyla`MyServiceEndpoint`tek bir uç nokta sunar.</span><span class="sxs-lookup"><span data-stu-id="bbf6e-167">The service `MyService` exposes a single endpoint through `MyServiceEndpoint`.</span></span> <span data-ttu-id="bbf6e-168">Aşağıdaki çizimde bitiş noktasıyla ilişkili adres, bağlama ve anlaşma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="bbf6e-168">The following illustration shows the address, binding, and contract associated with the endpoint.</span></span>  
  
 ![MyServiceEndpoint ayrıntılarının gösterildiği diyagram.](./media/federation/myserviceendpoint-details.gif)  
  
 <span data-ttu-id="bbf6e-170">Hizmet uç noktası `MyServiceEndpoint` [ \<WSFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) kullanır ve STS B tarafından verilen `accessAuthorized` talebe sahip geçerli bir güvenlik onaylama işlemi biçimlendirme dili (SAML) belirteci gerektirir. Bu, hizmet yapılandırmasında bildirimli olarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="bbf6e-170">The service endpoint `MyServiceEndpoint` uses the [\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) and requires a valid Security Assertions Markup Language (SAML) token with an `accessAuthorized` claim issued by STS B. This is declaratively specified in the service configuration.</span></span>  
  
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
> <span data-ttu-id="bbf6e-171">İçin gereken `MyService`talepler hakkında bir hafif nokta not edilmelidir.</span><span class="sxs-lookup"><span data-stu-id="bbf6e-171">A subtle point should be noted about the claims required by `MyService`.</span></span> <span data-ttu-id="bbf6e-172">İkinci şekil, `accessAuthorized` talebe sahip `MyService` bir SAML belirteci gerektirdiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="bbf6e-172">The second figure indicates that `MyService` requires a SAML token with the `accessAuthorized` claim.</span></span> <span data-ttu-id="bbf6e-173">Daha kesin olması için bu, gereken talep türünü `MyService` belirtir.</span><span class="sxs-lookup"><span data-stu-id="bbf6e-173">To be more precise, this specifies the claim type that `MyService` requires.</span></span> <span data-ttu-id="bbf6e-174">Bu talep türünün `http://tempuri.org:accessAuthorized` tam adı, hizmet yapılandırma dosyasında kullanılan (ilişkili ad alanıyla birlikte).</span><span class="sxs-lookup"><span data-stu-id="bbf6e-174">The fully-qualified name of this claim type is `http://tempuri.org:accessAuthorized` (along with the associated namespace), which is used in the service configuration file.</span></span> <span data-ttu-id="bbf6e-175">Bu talebin değeri, bu talebin varlığını gösterir ve STS B `true` tarafından ayarlandığı varsayılır.</span><span class="sxs-lookup"><span data-stu-id="bbf6e-175">The value of this claim indicates the presence of this claim and is assumed to be set to `true` by STS B.</span></span>  
  
 <span data-ttu-id="bbf6e-176">Çalışma zamanında, bu ilke `MyServiceOperationRequirement` `MyService`öğesinin bir parçası olarak uygulanan sınıfı tarafından zorlanır.</span><span class="sxs-lookup"><span data-stu-id="bbf6e-176">At runtime, this policy is enforced by the `MyServiceOperationRequirement` class that is implemented as part of the `MyService`.</span></span>  
  
 [!code-csharp[C_Federation#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#0)]
 [!code-vb[C_Federation#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#0)]  
[!code-csharp[C_Federation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#1)]
[!code-vb[C_Federation#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#1)]  
  
#### <a name="sts-b"></a><span data-ttu-id="bbf6e-177">STS B</span><span class="sxs-lookup"><span data-stu-id="bbf6e-177">STS B</span></span>  
 <span data-ttu-id="bbf6e-178">Aşağıdaki çizimde STS B gösterilmektedir. Daha önce belirtildiği gibi, bir güvenlik belirteci hizmeti (STS) da bir Web hizmetidir ve ilişkili uç noktaları, ilkesi vb. olabilir.</span><span class="sxs-lookup"><span data-stu-id="bbf6e-178">The following illustration shows the STS B. As stated earlier, a security token service (STS) is also a Web service and can have its associated endpoints, policy, and so on.</span></span>  
  
 ![Güvenlik belirteci hizmeti B 'yi gösteren diyagram.](./media/federation/myservice-security-token-service-b.gif)  
  
 <span data-ttu-id="bbf6e-180">STS B, güvenlik belirteçleri istemek için kullanılabilecek `STSEndpoint` adlı tek bir uç nokta sunar.</span><span class="sxs-lookup"><span data-stu-id="bbf6e-180">STS B exposes a single endpoint, called `STSEndpoint` that can be use to request security tokens.</span></span> <span data-ttu-id="bbf6e-181">Özellikle STS B, servis sitesinde hizmete erişmek için `accessAuthorized` sunulabilen `MyService` , talebe sahip SAML belirteçleri verir.</span><span class="sxs-lookup"><span data-stu-id="bbf6e-181">Specifically, STS B issues SAML tokens with the `accessAuthorized` claim, which can be presented at the `MyService` service site for accessing the service.</span></span> <span data-ttu-id="bbf6e-182">Ancak STS B, kullanıcıların `userAuthenticated` talebi içeren STS tarafından verilen geçerli bir SAML belirteci sunmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="bbf6e-182">However, STS B requires users to present a valid SAML token issued by STS A that contains the `userAuthenticated` claim.</span></span> <span data-ttu-id="bbf6e-183">Bu, STS yapılandırmasında bildirimli olarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="bbf6e-183">This is declaratively specified in the STS configuration.</span></span>  
  
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
> <span data-ttu-id="bbf6e-184">Bu `userAuthenticated` talep, STS B için gereken talep türüdür. Bu talep türünün `http://tempuri.org:userAuthenticated` tam adı, STS yapılandırma dosyasında kullanılan (ilişkili ad alanıyla birlikte).</span><span class="sxs-lookup"><span data-stu-id="bbf6e-184">Again, the `userAuthenticated` claim is the claim type that is required by STS B. The fully-qualified name of this claim type is `http://tempuri.org:userAuthenticated` (along with the associated namespace), which is used in the STS configuration file.</span></span> <span data-ttu-id="bbf6e-185">Bu talebin değeri, bu talebin varlığını gösterir ve STS A `true` tarafından ayarlandığı varsayılır.</span><span class="sxs-lookup"><span data-stu-id="bbf6e-185">The value of this claim indicates the presence of this claim and is assumed to be set to `true` by STS A.</span></span>  
  
 <span data-ttu-id="bbf6e-186">Çalışma zamanında, `STS_B_OperationRequirement` sınıfı STS 'nin bir parçası olarak uygulanan bu ilkeyi zorlar.</span><span class="sxs-lookup"><span data-stu-id="bbf6e-186">At runtime, the `STS_B_OperationRequirement` class enforces this policy, which is implemented as part of STS B.</span></span>  
  
 [!code-csharp[C_Federation#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#2)]
 [!code-vb[C_Federation#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#2)]  
  
 <span data-ttu-id="bbf6e-187">Erişim denetimi net ise STS B, `accessAuthorized` talebe sahip bir SAML belirteci yayınlar.</span><span class="sxs-lookup"><span data-stu-id="bbf6e-187">If the access check is clear, STS B issues a SAML token with the `accessAuthorized` claim.</span></span>  
  
 [!code-csharp[C_Federation#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#3)]
 [!code-vb[C_Federation#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#3)]  
  
#### <a name="sts-a"></a><span data-ttu-id="bbf6e-188">STS A</span><span class="sxs-lookup"><span data-stu-id="bbf6e-188">STS A</span></span>  
 <span data-ttu-id="bbf6e-189">Aşağıdaki çizimde STS A gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="bbf6e-189">The following illustration shows the STS A.</span></span>  
  
 <span data-ttu-id="bbf6e-190">![Federasyon](../../../../docs/framework/wcf/feature-details/media/sts-b.gif "STS_B")</span><span class="sxs-lookup"><span data-stu-id="bbf6e-190">![Federation](../../../../docs/framework/wcf/feature-details/media/sts-b.gif "STS_B")</span></span>  
  
 <span data-ttu-id="bbf6e-191">STS B 'ye benzer şekilde, STS A da güvenlik belirteçleri veren ve bu amaçla tek bir uç nokta sunan bir Web hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="bbf6e-191">Similar to the STS B, the STS A is also a Web service that issues security tokens and exposes a single endpoint for this purpose.</span></span> <span data-ttu-id="bbf6e-192">Ancak, farklı bir bağlama (`wsHttpBinding`) kullanır ve kullanıcıların bir `emailAddress` talep ile geçerli bir CardSpace sunmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="bbf6e-192">However, it uses a different binding (`wsHttpBinding`) and requires users to present a valid CardSpace with an `emailAddress` claim.</span></span> <span data-ttu-id="bbf6e-193">Yanıt ' da, `userAuthenticated` talebe sahip SAML belirteçleri verir.</span><span class="sxs-lookup"><span data-stu-id="bbf6e-193">In response, it issues SAML tokens with the `userAuthenticated` claim.</span></span> <span data-ttu-id="bbf6e-194">Bu, hizmet yapılandırmasında bildirimli olarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="bbf6e-194">This is declaratively specified in the service configuration.</span></span>  
  
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
  
 <span data-ttu-id="bbf6e-195">Çalışma zamanında, `STS_A_OperationRequirement` sınıfı STS 'nin bir parçası olarak uygulanan bu ilkeyi zorlar.</span><span class="sxs-lookup"><span data-stu-id="bbf6e-195">At runtime, the `STS_A_OperationRequirement` class enforces this policy, which is implemented as part of STS A.</span></span>  
  
 [!code-csharp[C_Federation#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#4)]
 [!code-vb[C_Federation#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#4)]  
  
 <span data-ttu-id="bbf6e-196">Erişim ise `true`, STS, talebe sahip `userAuthenticated` bir SAML belirteci yayınlar.</span><span class="sxs-lookup"><span data-stu-id="bbf6e-196">If the access is `true`, STS A issues a SAML token with `userAuthenticated` claim.</span></span>  
  
 [!code-csharp[C_Federation#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#5)]
 [!code-vb[C_Federation#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#5)]  
  
### <a name="client-at-organization-a"></a><span data-ttu-id="bbf6e-197">Kuruluşunda istemci A</span><span class="sxs-lookup"><span data-stu-id="bbf6e-197">Client at Organization A</span></span>  
 <span data-ttu-id="bbf6e-198">Aşağıdaki çizimde, bir `MyService` hizmet çağrısı yapma ile ilgili adımlarla birlikte a kuruluşunda istemci gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="bbf6e-198">The following illustration shows the client at organization A, along with the steps involved in making a `MyService` service call.</span></span> <span data-ttu-id="bbf6e-199">Diğer işlevsel bileşenler de ayrıca tamamlana için de eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="bbf6e-199">The other functional components are also included for completeness.</span></span>  
  
 ![Bir hizmetim hizmeti çağrısındaki adımları gösteren diyagram.](./media/federation/federation-myservice-service-call-process.gif)  
  
## <a name="summary"></a><span data-ttu-id="bbf6e-201">Özet</span><span class="sxs-lookup"><span data-stu-id="bbf6e-201">Summary</span></span>  
 <span data-ttu-id="bbf6e-202">Federal güvenlik, daha temiz bir sorumluluk bölmesi sağlar ve güvenli, ölçeklenebilir hizmet mimarileri oluşturmaya yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="bbf6e-202">Federated security provides a clean division of responsibility and helps to build secure, scalable service architectures.</span></span> <span data-ttu-id="bbf6e-203">WCF, dağıtılmış uygulamalar oluşturmaya ve dağıtmaya yönelik bir platform olarak, Federasyon güvenliği uygulamak için yerel destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="bbf6e-203">As a platform for building and deploying distributed applications, WCF provides native support for implementing federated security.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbf6e-204">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bbf6e-204">See also</span></span>

- [<span data-ttu-id="bbf6e-205">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="bbf6e-205">Security</span></span>](../../../../docs/framework/wcf/feature-details/security.md)
