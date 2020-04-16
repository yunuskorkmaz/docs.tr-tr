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
ms.openlocfilehash: 9616a5afb88e46bb5d69f1cd253c854cc1684d9f
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81464178"
---
# <a name="federation"></a><span data-ttu-id="b222c-102">Federasyon</span><span class="sxs-lookup"><span data-stu-id="b222c-102">Federation</span></span>
<span data-ttu-id="b222c-103">Bu konu federe güvenlik kavramına kısa bir genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="b222c-103">This topic provides a brief overview of the concept of federated security.</span></span> <span data-ttu-id="b222c-104">Ayrıca, Windows Communication Foundation (WCF) federe güvenlik mimarilerinin dağıtılması için destek açıklar.</span><span class="sxs-lookup"><span data-stu-id="b222c-104">It also describes Windows Communication Foundation (WCF) support for deploying federated security architectures.</span></span> <span data-ttu-id="b222c-105">Federasyonu gösteren örnek bir uygulama için [Federasyon Örneği'ne](../../../../docs/framework/wcf/samples/federation-sample.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="b222c-105">For a sample application that demonstrates federation, see [Federation Sample](../../../../docs/framework/wcf/samples/federation-sample.md).</span></span>  
  
## <a name="definition-of-federated-security"></a><span data-ttu-id="b222c-106">Federe Güvenliğin Tanımı</span><span class="sxs-lookup"><span data-stu-id="b222c-106">Definition of Federated Security</span></span>  
 <span data-ttu-id="b222c-107">Federe güvenlik, istemcinin eriştisi olduğu hizmet ile ilişkili kimlik doğrulama ve yetkilendirme yordamları arasında temiz ayrım yapılmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="b222c-107">Federated security allows for clean separation between the service a client is accessing and the associated authentication and authorization procedures.</span></span> <span data-ttu-id="b222c-108">Federe güvenlik, farklı güven bölgelerindeki birden çok sistem, ağ ve kuruluş arasında işbirliğine de olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="b222c-108">Federated security also enables collaboration across multiple systems, networks, and organizations in different trust realms.</span></span>  
  
 <span data-ttu-id="b222c-109">WCF, federe güvenlik kullanan dağıtılmış sistemlerin oluşturulması ve dağıtılması için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="b222c-109">WCF provides support for building and deploying distributed systems that employ federated security.</span></span>  
  
### <a name="elements-of-a-federated-security-architecture"></a><span data-ttu-id="b222c-110">Federe Güvenlik Mimarisinin Unsurları</span><span class="sxs-lookup"><span data-stu-id="b222c-110">Elements of a Federated Security Architecture</span></span>  
 <span data-ttu-id="b222c-111">Federe güvenlik mimarisi, aşağıdaki tabloda açıklandığı gibi üç temel öğeye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="b222c-111">The federated security architecture has three key elements, as described in the following table.</span></span>  
  
|<span data-ttu-id="b222c-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="b222c-112">Element</span></span>|<span data-ttu-id="b222c-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b222c-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b222c-114">Etki alanı/bölge</span><span class="sxs-lookup"><span data-stu-id="b222c-114">Domain/realm</span></span>|<span data-ttu-id="b222c-115">Güvenlik yönetimi veya güven tek bir birim.</span><span class="sxs-lookup"><span data-stu-id="b222c-115">A single unit of security administration or trust.</span></span> <span data-ttu-id="b222c-116">Tipik bir etki alanı tek bir kuruluş içerebilir.</span><span class="sxs-lookup"><span data-stu-id="b222c-116">A typical domain might include a single organization.</span></span>|  
|<span data-ttu-id="b222c-117">Federasyon</span><span class="sxs-lookup"><span data-stu-id="b222c-117">Federation</span></span>|<span data-ttu-id="b222c-118">Güven oluşturmuş etki alanları topluluğu.</span><span class="sxs-lookup"><span data-stu-id="b222c-118">A collection of domains that have established trust.</span></span> <span data-ttu-id="b222c-119">Güven düzeyi değişebilir, ancak genellikle kimlik doğrulaması içerir ve hemen hemen her zaman yetkilendirme içerir.</span><span class="sxs-lookup"><span data-stu-id="b222c-119">The level of trust may vary, but typically includes authentication and almost always includes authorization.</span></span> <span data-ttu-id="b222c-120">Tipik bir federasyon, bir dizi kaynağa paylaşılan erişim için güven oluşturmuş bir dizi kuruluş içerebilir.</span><span class="sxs-lookup"><span data-stu-id="b222c-120">A typical federation might include a number of organizations that have established trust for shared access to a set of resources.</span></span>|  
|<span data-ttu-id="b222c-121">Güvenlik Belirteci Hizmeti (STS)</span><span class="sxs-lookup"><span data-stu-id="b222c-121">Security Token Service (STS)</span></span>|<span data-ttu-id="b222c-122">Güvenlik belirteçleri veren bir Web hizmeti; diğer bir şey, güvendiği kanıtlara dayanarak iddialarda yer almakta, kime güvenirse güvensin.</span><span class="sxs-lookup"><span data-stu-id="b222c-122">A Web service that issues security tokens; that is, it makes assertions based on evidence that it trusts, to whomever trusts it.</span></span> <span data-ttu-id="b222c-123">Bu, etki alanları arasında güven aracılığı temelini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b222c-123">This forms the basis of trust brokering between domains.</span></span>|  
  
### <a name="example-scenario"></a><span data-ttu-id="b222c-124">Örnek Senaryo</span><span class="sxs-lookup"><span data-stu-id="b222c-124">Example Scenario</span></span>  
 <span data-ttu-id="b222c-125">Aşağıdaki resimde federe güvenlik bir örnek gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="b222c-125">The following illustration shows an example of federated security:</span></span>  
  
 ![Tipik bir federe güvenlik senaryosu gösteren diyagram.](./media/federation/typical-federated-security-scenario.gif)  
  
 <span data-ttu-id="b222c-127">Bu senaryo iki kuruluş içerir: A ve B Organizasyonu B'nin A organizasyonundaki bazı kullanıcıların değerli bulduğu bir Web kaynağı (Web hizmeti) vardır.</span><span class="sxs-lookup"><span data-stu-id="b222c-127">This scenario includes two organizations: A and B. Organization B has a Web resource (a Web service) that some users in organization A find valuable.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b222c-128">Bu bölümde *kaynak,* *hizmet*ve *Web hizmeti* terimleri birbirinin yerine kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b222c-128">This section uses the terms *resource*, *service*, and *Web service* interchangeably.</span></span>  
  
 <span data-ttu-id="b222c-129">Genellikle, B kuruluşu, A kuruluşundaki bir kullanıcının hizmete erişmeden önce geçerli bir kimlik doğrulama biçimi sağlamasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="b222c-129">Typically, organization B requires that a user from organization A provide some valid form of authentication before accessing the service.</span></span> <span data-ttu-id="b222c-130">Buna ek olarak, kuruluş kullanıcısöz konusu belirli kaynağa erişmek için yetkili olmasını da gerektirebilir.</span><span class="sxs-lookup"><span data-stu-id="b222c-130">In addition, the organization may also require that the user be authorized to access the specific resource in question.</span></span> <span data-ttu-id="b222c-131">Bu sorunu gidermenin ve A organizasyonundaki kullanıcıların B organizasyonundaki kaynağa erişmesini sağlamanın bir yolu aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="b222c-131">One way to address this problem and enable users in organization A to access the resource in organization B is as follows:</span></span>  
  
- <span data-ttu-id="b222c-132">A kuruluşunun kullanıcıları kimlik bilgilerini (kullanıcı adı ve parola) B kuruluşuna kaydeder.</span><span class="sxs-lookup"><span data-stu-id="b222c-132">Users from organization A register their credentials (a user name and password) with organization B.</span></span>  
  
- <span data-ttu-id="b222c-133">Kaynak erişimi sırasında, A organizasyonundaki kullanıcılar kimlik bilgilerini B kuruluşuna sunar ve kaynağa erişmeden önce kimlik doğrulaması yapılır.</span><span class="sxs-lookup"><span data-stu-id="b222c-133">During the resource access, users from organization A present their credentials to organization B and are authenticated before accessing the resource.</span></span>  
  
 <span data-ttu-id="b222c-134">Bu yaklaşımın üç önemli dezavantajı vardır:</span><span class="sxs-lookup"><span data-stu-id="b222c-134">This approach has three significant drawbacks:</span></span>  
  
- <span data-ttu-id="b222c-135">B organizasyonu, yerel kullanıcılarının kimlik bilgilerini yönetmeye ek olarak A organizasyonundaki kullanıcıların kimlik bilgilerini yönetmek zorundadır.</span><span class="sxs-lookup"><span data-stu-id="b222c-135">Organization B has to manage the credentials for users from organization A in addition to managing the credentials of its local users.</span></span>  
  
- <span data-ttu-id="b222c-136">Kuruluştaki kullanıcılar A, a organizasyonu içindeki kaynaklara erişmek için normalde kullandıkları kimlik bilgilerinin dışında ek bir kimlik bilgileri kümesi (diğer bir deyişle ek bir kullanıcı adı ve parolayı hatırlayın) tutmanız gerekir. Bu genellikle zayıf bir güvenlik önlemi olan birden çok hizmet sitelerinde aynı kullanıcı adı ve parolayı kullanma pratiğini teşvik eder.</span><span class="sxs-lookup"><span data-stu-id="b222c-136">Users in organization A need to maintain an additional set of credentials (that is, remember an additional user name and password) apart from the credentials they normally use to gain access to resources within organization A. This usually encourages the practice of using the same user name and password at multiple service sites, which is a weak security measure.</span></span>  
  
- <span data-ttu-id="b222c-137">Daha fazla kuruluş B organizasyonundaki kaynağı bir değerolarak algıladığı için mimari ölçeklenmez.</span><span class="sxs-lookup"><span data-stu-id="b222c-137">The architecture does not scale as more organizations perceive the resource at organization B as being of some value.</span></span>  
  
 <span data-ttu-id="b222c-138">Daha önce bahsedilen sakıncaları gideren alternatif bir yaklaşım, federe güvenlik istihdam etmektir.</span><span class="sxs-lookup"><span data-stu-id="b222c-138">An alternative approach, which addresses the previously mentioned drawbacks, is to employ federated security.</span></span> <span data-ttu-id="b222c-139">Bu yaklaşımda, A ve B kuruluşları bir güven ilişkisi kurar ve kurulan güvenin aracılık etmesini sağlamak için Güvenlik Belirteci Hizmeti (STS) kullanır.</span><span class="sxs-lookup"><span data-stu-id="b222c-139">In this approach, organizations A and B establish a trust relationship and employ Security Token Service (STS) to enable brokering of the established trust.</span></span>  
  
 <span data-ttu-id="b222c-140">Federe güvenlik mimarisinde, A kuruluşunun kullanıcıları B organizasyonunda Web hizmetine erişmek istiyorlarsa, belirli bir hizmete erişimlerini doğrulayan ve yetkilendirilen B organizasyonunda STS'den geçerli bir güvenlik belirteci sunmaları gerektiğini bilirler.</span><span class="sxs-lookup"><span data-stu-id="b222c-140">In a federated security architecture, users from organization A know that if they want to access the Web service in organization B that they must present a valid security token from the STS at organization B, which authenticates and authorizes their access to the specific service.</span></span>  
  
 <span data-ttu-id="b222c-141">STS B ile iletişime geçerek, kullanıcılar STS ile ilişkili ilkeden başka bir yönlendirme düzeyi alır.</span><span class="sxs-lookup"><span data-stu-id="b222c-141">On contacting the STS B, the users receive another level of indirection from the policy associated with the STS.</span></span> <span data-ttu-id="b222c-142">STS B'nin onlara bir güvenlik belirteci verabilmesi için STS A'dan (diğer bir şekilde istemci güven diyarı) geçerli bir güvenlik belirteci sunmaları gerekir.</span><span class="sxs-lookup"><span data-stu-id="b222c-142">They must present a valid security token from the STS A (that is, the client trust realm) before the STS B can issue them a security token.</span></span> <span data-ttu-id="b222c-143">Bu, iki kuruluş arasında kurulan güven ilişkisinin bir sonucudur ve B kuruluşunun A organizasyonundaki kullanıcılar için kimlikleri yönetmesi gerekmediğini ima eder. Uygulamada, STS B genellikle bir `issuerAddress` `issuerMetadataAddress`null ve .</span><span class="sxs-lookup"><span data-stu-id="b222c-143">This is a corollary of the trust relationship established between the two organizations and implies that organization B does not have to manage identities for users from organization A. In practice, STS B typically has a null `issuerAddress` and `issuerMetadataAddress`.</span></span> <span data-ttu-id="b222c-144">Daha fazla bilgi için [bkz: Yerel İhraççı'yı yapılandırma.](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)</span><span class="sxs-lookup"><span data-stu-id="b222c-144">For more information, see [How to: Configure a Local Issuer](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).</span></span> <span data-ttu-id="b222c-145">Bu durumda, istemci STS A'yı bulmak için yerel bir ilkeden başvurur. STS B STS A hakkında bilgi korumak zorunda değildir, çünkü bu yapılandırma *ev bölge federasyonu* denir ve daha iyi ölçekler.</span><span class="sxs-lookup"><span data-stu-id="b222c-145">In that case, the client consults a local policy to locate STS A. This configuration is called *home realm federation* and it scales better because STS B does not have to maintain information about STS A.</span></span>  
  
 <span data-ttu-id="b222c-146">Kullanıcılar daha sonra A organizasyonundaki STS ile iletişime geçer ve normalde A kuruluşundaki herhangi bir kaynağa erişmek için kullandıkları kimlik doğrulama kimlik bilgilerini sunarak bir güvenlik belirteci elde eder. Bu, kullanıcıların birden çok kimlik belgesi kümesini korumak veya birden çok hizmet sitesinde aynı kimlik bilgileri kümesini kullanmak zorunda kalma sorununu da hafifletir.</span><span class="sxs-lookup"><span data-stu-id="b222c-146">The users then contact the STS at organization A and obtain a security token by presenting authentication credentials that they normally use to gain access to any other resource within organization A. This also alleviates the problem of users having to maintain multiple sets of credentials or using the same set of credentials at multiple service sites.</span></span>  
  
 <span data-ttu-id="b222c-147">Kullanıcılar STS A'dan bir güvenlik belirteci aldıktan sonra, belirteci STS B. Organization B'ye sunarlar ve kullanıcıların isteklerinin yetkilendirmesini gerçekleştirmek için gelirler ve kendi güvenlik belirteçleri kümesinden kullanıcılara bir güvenlik belirteci verir.</span><span class="sxs-lookup"><span data-stu-id="b222c-147">Once the users obtain a security token from the STS A, they present the token to the STS B. Organization B proceeds to perform authorization of the users' requests and issues a security token to the users from its own set of security tokens.</span></span> <span data-ttu-id="b222c-148">Kullanıcılar daha sonra belirteçlerini B kuruluşundaki kaynağa sunabilir ve hizmete erişebilir.</span><span class="sxs-lookup"><span data-stu-id="b222c-148">The users can then present their token to the resource at organization B and access the service.</span></span>  
  
## <a name="support-for-federated-security-in-wcf"></a><span data-ttu-id="b222c-149">WCF'de Federe Güvenliğe Destek</span><span class="sxs-lookup"><span data-stu-id="b222c-149">Support for Federated Security in WCF</span></span>  
 <span data-ttu-id="b222c-150">WCF [ \<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)aracılığıyla federe güvenlik mimarileri dağıtmak için anahtar teslimi destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="b222c-150">WCF provides turnkey support for deploying federated security architectures through the [\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span></span>  
  
 <span data-ttu-id="b222c-151">wsFederationHttpBinding>öğesi, http'nin istek yanıtı iletişim stili için temel aktarım mekanizması olarak kullanılmasını gerektiren güvenli, güvenilir ve birlikte çalışabilir bir bağlama sağlar ve kodkodlama için tel biçimi olarak metin ve XML kullanır. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="b222c-151">The [\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) element provides for a secure, reliable, interoperable binding that entails the use of HTTP as the underlying transport mechanism for request-reply communication style, employing text and XML as the wire format for encoding.</span></span>  
  
 <span data-ttu-id="b222c-152">bir federe güvenlik senaryosunda wsFederationHttpBinding>kullanımı, aşağıdaki bölümlerde açıklandığı gibi, mantıksal olarak bağımsız iki aşamaya ayrıştırılabilir. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="b222c-152">The use of [\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) in a federated security scenario can be decoupled into two logically independent phases, as described in the following sections.</span></span>  
  
### <a name="phase-1-design-phase"></a><span data-ttu-id="b222c-153">Faz 1: Tasarım Aşaması</span><span class="sxs-lookup"><span data-stu-id="b222c-153">Phase 1: Design Phase</span></span>  
 <span data-ttu-id="b222c-154">Tasarım aşamasında istemci [ServiceModel Metadata Utility Tool'u (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) hizmet bitiş noktasının ortaya çıkardığı ilkeyi okumak ve hizmetin kimlik doğrulama ve yetkilendirme gereksinimlerini toplamak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="b222c-154">During the design phase, the client uses the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to read the policy the service endpoint exposes and to collect the service's authentication and authorization requirements.</span></span> <span data-ttu-id="b222c-155">Uygun vekiller, istemcide aşağıdaki federe güvenlik iletişimi deseni oluşturmak için oluşturulur:</span><span class="sxs-lookup"><span data-stu-id="b222c-155">The appropriate proxies are constructed to create the following federated security communication pattern at the client:</span></span>  
  
- <span data-ttu-id="b222c-156">İstemci güven alanında STS'den bir güvenlik belirteci edinin.</span><span class="sxs-lookup"><span data-stu-id="b222c-156">Obtain a security token from the STS in the client trust realm.</span></span>  
  
- <span data-ttu-id="b222c-157">Belirteci hizmet güven alanında STS'ye sunun.</span><span class="sxs-lookup"><span data-stu-id="b222c-157">Present the token to the STS in the service trust realm.</span></span>  
  
- <span data-ttu-id="b222c-158">Hizmet güven alanında STS'den bir güvenlik belirteci edinin.</span><span class="sxs-lookup"><span data-stu-id="b222c-158">Obtain a security token from the STS in the service trust realm.</span></span>  
  
- <span data-ttu-id="b222c-159">Hizmete erişmek için belirteci hizmete sunun.</span><span class="sxs-lookup"><span data-stu-id="b222c-159">Present the token to the service to access the service.</span></span>  
  
### <a name="phase-2-run-time-phase"></a><span data-ttu-id="b222c-160">Aşama 2: Çalışma Zamanı Aşaması</span><span class="sxs-lookup"><span data-stu-id="b222c-160">Phase 2: Run-Time Phase</span></span>  
 <span data-ttu-id="b222c-161">Çalışma süresi aşamasında, istemci WCF istemci sınıfının bir nesnesini anında alar ve WCF istemcisini kullanarak arama yapar.</span><span class="sxs-lookup"><span data-stu-id="b222c-161">During the run-time phase, the client instantiates an object of the WCF client class and makes a call using the WCF client.</span></span> <span data-ttu-id="b222c-162">WCF'nin temel çerçevesi, federe güvenlik iletişimi modelinde daha önce belirtilen adımları işler ve istemcinin hizmeti sorunsuz bir şekilde tüketmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="b222c-162">The underlying framework of WCF handles the previously mentioned steps in the federated security communication pattern and enables the client to seamlessly consume the service.</span></span>  
  
## <a name="sample-implementation-using-wcf"></a><span data-ttu-id="b222c-163">WCF kullanarak örnek uygulama</span><span class="sxs-lookup"><span data-stu-id="b222c-163">Sample Implementation Using WCF</span></span>  
 <span data-ttu-id="b222c-164">Aşağıdaki resimde, WCF'nin yerel desteğini kullanarak federe bir güvenlik mimarisi için örnek bir uygulama gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b222c-164">The following illustration shows a sample implementation for a federated security architecture using native support from WCF.</span></span>  
  
 ![Örnek bir Federasyon güvenlik uygulamasını gösteren diyagram.](./media/federation/federated-security-implementation.gif)  
  
### <a name="example-myservice"></a><span data-ttu-id="b222c-166">Örnek MyService</span><span class="sxs-lookup"><span data-stu-id="b222c-166">Example MyService</span></span>  
 <span data-ttu-id="b222c-167">`MyService` Hizmet, tek bir bitiş `MyServiceEndpoint`noktasını .</span><span class="sxs-lookup"><span data-stu-id="b222c-167">The service `MyService` exposes a single endpoint through `MyServiceEndpoint`.</span></span> <span data-ttu-id="b222c-168">Aşağıdaki resimde bitiş noktasıile ilişkili adres, bağlama ve sözleşme gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b222c-168">The following illustration shows the address, binding, and contract associated with the endpoint.</span></span>  
  
 ![MyServiceEndpoint ayrıntılarını gösteren diyagram.](./media/federation/myserviceendpoint-details.gif)  
  
 <span data-ttu-id="b222c-170">Hizmet bitiş `MyServiceEndpoint` noktası [ \<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) kullanır ve STS B tarafından verilen bir talep `accessAuthorized` ile geçerli bir Güvenlik İddiaları İşaretleme Dili (SAML) belirteci gerektirir. Bu, hizmet yapılandırmasında bildirimsel olarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="b222c-170">The service endpoint `MyServiceEndpoint` uses the [\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) and requires a valid Security Assertions Markup Language (SAML) token with an `accessAuthorized` claim issued by STS B. This is declaratively specified in the service configuration.</span></span>  
  
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
> <span data-ttu-id="b222c-171">İnce bir nokta tarafından `MyService`gerekli iddiaları hakkında dikkat edilmelidir.</span><span class="sxs-lookup"><span data-stu-id="b222c-171">A subtle point should be noted about the claims required by `MyService`.</span></span> <span data-ttu-id="b222c-172">İkinci şekil, `MyService` iddiaile bir SAML `accessAuthorized` belirteci gerektirdiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="b222c-172">The second figure indicates that `MyService` requires a SAML token with the `accessAuthorized` claim.</span></span> <span data-ttu-id="b222c-173">Daha kesin olmak gerekirse, bu `MyService` talep türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="b222c-173">To be more precise, this specifies the claim type that `MyService` requires.</span></span> <span data-ttu-id="b222c-174">Bu talep türünün `http://tempuri.org:accessAuthorized` tam nitelikli adı ( ilişkili ad alanı ile birlikte), hizmet yapılandırma dosyasında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b222c-174">The fully-qualified name of this claim type is `http://tempuri.org:accessAuthorized` (along with the associated namespace), which is used in the service configuration file.</span></span> <span data-ttu-id="b222c-175">Bu talebin değeri bu talebin varlığını gösterir ve `true` STS B tarafından ayarlanır varsayılır.</span><span class="sxs-lookup"><span data-stu-id="b222c-175">The value of this claim indicates the presence of this claim and is assumed to be set to `true` by STS B.</span></span>  
  
 <span data-ttu-id="b222c-176">Çalışma zamanında, bu ilke `MyServiceOperationRequirement` bir parçası olarak uygulanan sınıf `MyService`tarafından zorlanır.</span><span class="sxs-lookup"><span data-stu-id="b222c-176">At runtime, this policy is enforced by the `MyServiceOperationRequirement` class that is implemented as part of the `MyService`.</span></span>  
  
 [!code-csharp[C_Federation#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#0)]
 [!code-vb[C_Federation#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#0)]  
[!code-csharp[C_Federation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#1)]
[!code-vb[C_Federation#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#1)]  
  
#### <a name="sts-b"></a><span data-ttu-id="b222c-177">STS B</span><span class="sxs-lookup"><span data-stu-id="b222c-177">STS B</span></span>  
 <span data-ttu-id="b222c-178">Aşağıdaki resimde STS B gösterilmektedir. Daha önce de belirtildiği gibi, bir güvenlik belirteç hizmeti (STS) aynı zamanda bir Web hizmetidir ve ilişkili uç noktalarına, ilkeye vb. sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="b222c-178">The following illustration shows the STS B. As stated earlier, a security token service (STS) is also a Web service and can have its associated endpoints, policy, and so on.</span></span>  
  
 ![Güvenlik belirteci hizmetini gösteren diyagram B.](./media/federation/myservice-security-token-service-b.gif)  
  
 <span data-ttu-id="b222c-180">STS B, `STSEndpoint` güvenlik belirteçleri istemek için kullanilebilen tek bir uç noktayı ortaya çıkarır.</span><span class="sxs-lookup"><span data-stu-id="b222c-180">STS B exposes a single endpoint, called `STSEndpoint` that can be use to request security tokens.</span></span> <span data-ttu-id="b222c-181">Özellikle, STS B, hizmete erişmek `accessAuthorized` için `MyService` hizmet yerinde sunulabilecek olan saml belirteçlerini taleple birlikte verir.</span><span class="sxs-lookup"><span data-stu-id="b222c-181">Specifically, STS B issues SAML tokens with the `accessAuthorized` claim, which can be presented at the `MyService` service site for accessing the service.</span></span> <span data-ttu-id="b222c-182">Ancak, STS B, kullanıcıların `userAuthenticated` STS A tarafından verilen ve talebi içeren geçerli bir SAML belirteci sunmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="b222c-182">However, STS B requires users to present a valid SAML token issued by STS A that contains the `userAuthenticated` claim.</span></span> <span data-ttu-id="b222c-183">Bu, STS yapılandırmasında bildirimsel olarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="b222c-183">This is declaratively specified in the STS configuration.</span></span>  
  
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
> <span data-ttu-id="b222c-184">Yine, `userAuthenticated` talep STS B tarafından gerekli olan talep türüdür. Bu talep türünün tam nitelikli `http://tempuri.org:userAuthenticated` adı (ilişkili ad alanı ile birlikte) STS yapılandırma dosyasında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b222c-184">Again, the `userAuthenticated` claim is the claim type that is required by STS B. The fully-qualified name of this claim type is `http://tempuri.org:userAuthenticated` (along with the associated namespace), which is used in the STS configuration file.</span></span> <span data-ttu-id="b222c-185">Bu talebin değeri bu talebin varlığını gösterir ve `true` STS A tarafından ayarlanır varsayılır.</span><span class="sxs-lookup"><span data-stu-id="b222c-185">The value of this claim indicates the presence of this claim and is assumed to be set to `true` by STS A.</span></span>  
  
 <span data-ttu-id="b222c-186">Çalışma zamanında, `STS_B_OperationRequirement` sınıf STS B'nin bir parçası olarak uygulanan bu ilkeyi zorlar.</span><span class="sxs-lookup"><span data-stu-id="b222c-186">At runtime, the `STS_B_OperationRequirement` class enforces this policy, which is implemented as part of STS B.</span></span>  
  
 [!code-csharp[C_Federation#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#2)]
 [!code-vb[C_Federation#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#2)]  
  
 <span data-ttu-id="b222c-187">Erişim denetimi açıksa, `accessAuthorized` STS B taleple birlikte bir SAML belirteci yayınlar.</span><span class="sxs-lookup"><span data-stu-id="b222c-187">If the access check is clear, STS B issues a SAML token with the `accessAuthorized` claim.</span></span>  
  
 [!code-csharp[C_Federation#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#3)]
 [!code-vb[C_Federation#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#3)]  
  
#### <a name="sts-a"></a><span data-ttu-id="b222c-188">STS A</span><span class="sxs-lookup"><span data-stu-id="b222c-188">STS A</span></span>  
 <span data-ttu-id="b222c-189">Aşağıdaki resimde STS A gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b222c-189">The following illustration shows the STS A.</span></span>  
  
 <span data-ttu-id="b222c-190">![Federasyon](../../../../docs/framework/wcf/feature-details/media/sts-b.gif "STS_B")</span><span class="sxs-lookup"><span data-stu-id="b222c-190">![Federation](../../../../docs/framework/wcf/feature-details/media/sts-b.gif "STS_B")</span></span>  
  
 <span data-ttu-id="b222c-191">STS B'ye benzer şekilde, STS A da güvenlik belirteçleri veren ve bu amaç için tek bir bitiş noktasını ortaya çıkaran bir Web hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="b222c-191">Similar to the STS B, the STS A is also a Web service that issues security tokens and exposes a single endpoint for this purpose.</span></span> <span data-ttu-id="b222c-192">Ancak, farklı bir bağlama`wsHttpBinding`kullanır ( ) ve kullanıcıların bir `emailAddress` talep ile geçerli bir CardSpace sunmak için gerektirir.</span><span class="sxs-lookup"><span data-stu-id="b222c-192">However, it uses a different binding (`wsHttpBinding`) and requires users to present a valid CardSpace with an `emailAddress` claim.</span></span> <span data-ttu-id="b222c-193">Yanıt olarak, `userAuthenticated` iddia ile SAML belirteçleri sorunları.</span><span class="sxs-lookup"><span data-stu-id="b222c-193">In response, it issues SAML tokens with the `userAuthenticated` claim.</span></span> <span data-ttu-id="b222c-194">Bu, hizmet yapılandırmasında bildirimsel olarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="b222c-194">This is declaratively specified in the service configuration.</span></span>  
  
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
    </endpoint>  
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
  
 <span data-ttu-id="b222c-195">Çalışma zamanında sınıf, `STS_A_OperationRequirement` STS A'nın bir parçası olarak uygulanan bu ilkeyi zorlar.</span><span class="sxs-lookup"><span data-stu-id="b222c-195">At runtime, the `STS_A_OperationRequirement` class enforces this policy, which is implemented as part of STS A.</span></span>  
  
 [!code-csharp[C_Federation#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#4)]
 [!code-vb[C_Federation#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#4)]  
  
 <span data-ttu-id="b222c-196">Erişim ise, `true`STS A talep ile `userAuthenticated` bir SAML belirteci sorunları.</span><span class="sxs-lookup"><span data-stu-id="b222c-196">If the access is `true`, STS A issues a SAML token with `userAuthenticated` claim.</span></span>  
  
 [!code-csharp[C_Federation#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#5)]
 [!code-vb[C_Federation#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#5)]  
  
### <a name="client-at-organization-a"></a><span data-ttu-id="b222c-197">A Organizasyonunda İstemci</span><span class="sxs-lookup"><span data-stu-id="b222c-197">Client at Organization A</span></span>  
 <span data-ttu-id="b222c-198">Aşağıdaki resimde, A organizasyonundaki istemci ve bir `MyService` servis çağrısı yapma yla ilgili adımlar gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b222c-198">The following illustration shows the client at organization A, along with the steps involved in making a `MyService` service call.</span></span> <span data-ttu-id="b222c-199">Diğer fonksiyonel bileşenler de bütünlük için dahildir.</span><span class="sxs-lookup"><span data-stu-id="b222c-199">The other functional components are also included for completeness.</span></span>  
  
 ![MyService servis çağrısındaki adımları gösteren diyagram.](./media/federation/federation-myservice-service-call-process.gif)  
  
## <a name="summary"></a><span data-ttu-id="b222c-201">Özet</span><span class="sxs-lookup"><span data-stu-id="b222c-201">Summary</span></span>  
 <span data-ttu-id="b222c-202">Federe güvenlik, temiz bir sorumluluk bölümü sağlar ve güvenli, ölçeklenebilir hizmet mimarileri oluşturmaya yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="b222c-202">Federated security provides a clean division of responsibility and helps to build secure, scalable service architectures.</span></span> <span data-ttu-id="b222c-203">Dağıtılmış uygulamalar oluşturmak ve dağıtmak için bir platform olarak WCF, federe güvenliğin uygulanması için yerel destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="b222c-203">As a platform for building and deploying distributed applications, WCF provides native support for implementing federated security.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b222c-204">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b222c-204">See also</span></span>

- [<span data-ttu-id="b222c-205">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="b222c-205">Security</span></span>](../../../../docs/framework/wcf/feature-details/security.md)
