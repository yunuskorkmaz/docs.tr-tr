---
title: <security> / <netTcpBinding>
ms.date: 03/30/2017
ms.assetid: 286cd191-4fd5-4c4e-a223-9c71cf7fdead
ms.openlocfilehash: 04e7e94f47be37dc9c4cbf404a269b9784281d7d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936615"
---
# <a name="security-of-nettcpbinding"></a><span data-ttu-id="01201-102">\<\<NetTcpBinding > Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="01201-102">\<security> of \<netTcpBinding></span></span>
<span data-ttu-id="01201-103">Bağlama için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="01201-103">Defines the security settings for a binding.</span></span>  
  
 <span data-ttu-id="01201-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="01201-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="01201-105">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="01201-105">\<bindings></span></span>  
<span data-ttu-id="01201-106">\<netTcpBinding></span><span class="sxs-lookup"><span data-stu-id="01201-106">\<netTcpBinding></span></span>  
<span data-ttu-id="01201-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="01201-107">\<binding></span></span>  
<span data-ttu-id="01201-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="01201-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01201-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="01201-109">Syntax</span></span>  
  
```xml  
<security mode="Message/None/Transport/TransportWithCredential">
  <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             protectionLevel="None/Sign/EncryptAndSign" />
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="01201-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="01201-110">Attributes and Elements</span></span>  
 <span data-ttu-id="01201-111">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="01201-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="01201-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="01201-112">Attributes</span></span>  
  
|<span data-ttu-id="01201-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="01201-113">Attribute</span></span>|<span data-ttu-id="01201-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="01201-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="01201-115">mod</span><span class="sxs-lookup"><span data-stu-id="01201-115">mode</span></span>|<span data-ttu-id="01201-116">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="01201-116">Optional.</span></span> <span data-ttu-id="01201-117">Uygulanan güvenlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="01201-117">Specifies the type of security that is applied.</span></span> <span data-ttu-id="01201-118">Geçerli değerler aşağıda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="01201-118">Valid values are shown below.</span></span> <span data-ttu-id="01201-119">Varsayılan değer `Transport` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="01201-119">The default value is `Transport`.</span></span><br /><br /> <span data-ttu-id="01201-120">Bu öznitelik türü <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="01201-120">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="01201-121">mode özniteliği</span><span class="sxs-lookup"><span data-stu-id="01201-121">mode Attribute</span></span>  
  
|<span data-ttu-id="01201-122">Değer</span><span class="sxs-lookup"><span data-stu-id="01201-122">Value</span></span>|<span data-ttu-id="01201-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="01201-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="01201-124">Yok.</span><span class="sxs-lookup"><span data-stu-id="01201-124">None</span></span>|<span data-ttu-id="01201-125">Güvenlik devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="01201-125">Security is disabled.</span></span>|  
|<span data-ttu-id="01201-126">Aktarım</span><span class="sxs-lookup"><span data-stu-id="01201-126">Transport</span></span>|<span data-ttu-id="01201-127">Aktarım güvenliği TCP veya SPNego üzerinden TLS kullanılarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="01201-127">Transport security is provided using TLS over TCP or SPNego.</span></span> <span data-ttu-id="01201-128">Hizmetin SSL sertifikalarıyla yapılandırılması gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="01201-128">The service may need to be configured with SSL certificates.</span></span> <span data-ttu-id="01201-129">Koruma düzeyini Bu modla denetlemek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="01201-129">It is possible to control the protection level with this mode.</span></span>|  
|<span data-ttu-id="01201-130">`Message`</span><span class="sxs-lookup"><span data-stu-id="01201-130">Message</span></span>|<span data-ttu-id="01201-131">Güvenlik, SOAP iletisi güvenliği kullanılarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="01201-131">Security is provided using SOAP message security.</span></span> <span data-ttu-id="01201-132">Varsayılan olarak, SOAP gövdesi şifrelenir ve imzalanır.</span><span class="sxs-lookup"><span data-stu-id="01201-132">By default, the SOAP body is encrypted and signed.</span></span> <span data-ttu-id="01201-133">Bu mod, hizmet kimlik bilgilerinin, istemci bant dışı, kullanılacak algoritma paketini ve ileti gövdesine uygulanacak koruma düzeyini belirtir gibi çeşitli özellikler sunar.</span><span class="sxs-lookup"><span data-stu-id="01201-133">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body.</span></span> <span data-ttu-id="01201-134">Oturum başına istemci kimlik doğrulaması gerçekleştirilir ve kimlik doğrulama sonuçları oturum süresince önbelleğe alınır.</span><span class="sxs-lookup"><span data-stu-id="01201-134">Client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
|<span data-ttu-id="01201-135">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="01201-135">TransportWithMessageCredential</span></span>|<span data-ttu-id="01201-136">Aktarım güvenliği, ileti güvenliği ile birlikte gönderilir.</span><span class="sxs-lookup"><span data-stu-id="01201-136">Transport security is coupled with message security.</span></span> <span data-ttu-id="01201-137">Aktarım güvenliği TCP veya SPNego üzerinden TLS tarafından sağlanır ve bütünlük, gizlilik ve sunucu kimlik doğrulamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="01201-137">Transport security is provided by TLS over TCP, or SPNego, and ensures integrity, confidentiality, and server authentication.</span></span> <span data-ttu-id="01201-138">SOAP iletisi güvenliği istemci kimlik doğrulaması sağlar.</span><span class="sxs-lookup"><span data-stu-id="01201-138">SOAP message security provides client authentication.</span></span> <span data-ttu-id="01201-139">Varsayılan olarak, oturum başına istemci kimlik doğrulaması gerçekleştirilir ve kimlik doğrulama sonuçları oturum süresince önbelleğe alınır.</span><span class="sxs-lookup"><span data-stu-id="01201-139">By default, client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="01201-140">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="01201-140">Child Elements</span></span>  
  
|<span data-ttu-id="01201-141">Öğe</span><span class="sxs-lookup"><span data-stu-id="01201-141">Element</span></span>|<span data-ttu-id="01201-142">Açıklama</span><span class="sxs-lookup"><span data-stu-id="01201-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="01201-143">\<Taşıma ></span><span class="sxs-lookup"><span data-stu-id="01201-143">\<transport></span></span>](transport-of-nettcpbinding.md)|<span data-ttu-id="01201-144">Taşımanın güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="01201-144">Defines the security settings for the transport.</span></span> <span data-ttu-id="01201-145">Bu öğe türündedir <xref:System.ServiceModel.Configuration.TcpTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="01201-145">This element is of type <xref:System.ServiceModel.Configuration.TcpTransportSecurityElement>.</span></span>|  
|[<span data-ttu-id="01201-146">\<ileti ></span><span class="sxs-lookup"><span data-stu-id="01201-146">\<message></span></span>](message-element-of-nettcpbinding.md)|<span data-ttu-id="01201-147">İleti için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="01201-147">Defines the security settings for the message.</span></span> <span data-ttu-id="01201-148">Bu öğe türündedir <xref:System.ServiceModel.Configuration.MessageSecurityOverTcpElement>.</span><span class="sxs-lookup"><span data-stu-id="01201-148">This element is of type <xref:System.ServiceModel.Configuration.MessageSecurityOverTcpElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="01201-149">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="01201-149">Parent Elements</span></span>  
  
|<span data-ttu-id="01201-150">Öğe</span><span class="sxs-lookup"><span data-stu-id="01201-150">Element</span></span>|<span data-ttu-id="01201-151">Açıklama</span><span class="sxs-lookup"><span data-stu-id="01201-151">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="01201-152">bağlama</span><span class="sxs-lookup"><span data-stu-id="01201-152">binding</span></span>|<span data-ttu-id="01201-153">NetTcpBinding > bağlama öğesi. [ \<](nettcpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="01201-153">The binding element of the [\<netTcpBinding>](nettcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="01201-154">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="01201-154">Remarks</span></span>  
 <span data-ttu-id="01201-155">Standart bağlamaların her biri, aktarım güvenliği gereksinimlerini denetlemek için parametreler sağlar.</span><span class="sxs-lookup"><span data-stu-id="01201-155">Each of the standard bindings provides parameters for controlling the transfer security requirements.</span></span> <span data-ttu-id="01201-156">Bu parametreler genellikle ileti düzeyi veya aktarım düzeyi güvenliğin kullanılıp kullanılmadığını ve istemci kimlik bilgisi türünü seçmesini belirten güvenlik modunu içerir.</span><span class="sxs-lookup"><span data-stu-id="01201-156">These parameters typically include the security mode that specified whether message-level or transport-level security is used and the choice of client credential type.</span></span> <span data-ttu-id="01201-157">Bu parametrelerin mevcut seçeneklerinin seçimine bağlı olarak, uygun güvenlik ile bir kanal yığını oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="01201-157">Based on the choice of options these parameters present, a channel stack is constructed with appropriate security.</span></span>  
  
 <span data-ttu-id="01201-158">Windows Communication Foundation (WCF) tarafından sağlanan sistem tarafından sağlanan bağlamalar, en yaygın senaryo gereksinimlerinin bazılarını karşılayacak şekilde tasarlanan bir kümesidir.</span><span class="sxs-lookup"><span data-stu-id="01201-158">The system-provided bindings supplied by Windows Communication Foundation (WCF) are a set designed to meet some of the most common scenario requirements.</span></span> <span data-ttu-id="01201-159">Bu bağlamalardan her biri, belirli bir hedeflenmiş senaryolar için güvenlik gereksinimlerinin belirtilede olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="01201-159">Each of these bindings allows the specification of security requirements for some specific targeted scenarios.</span></span>  
  
 <span data-ttu-id="01201-160">Bu yapılandırma öğesi için `netTcpBinding`güvenlik belirtimleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="01201-160">This configuration element provides the security specifications for `netTcpBinding`.</span></span> <span data-ttu-id="01201-161">Bu, makineler arası iletişim için uygun, güvenli, güvenilir ve iyileştirilmiş bir bağlamadır.</span><span class="sxs-lookup"><span data-stu-id="01201-161">This is a secure, reliable, optimized binding suitable for cross-machine communication.</span></span> <span data-ttu-id="01201-162">Varsayılan olarak, ileti teslimi için TCP ve ileti güvenliği ve kimlik doğrulaması için Windows güvenliği, güvenilirlik açısından WS-ReliableMessaging ve ikili ileti kodlaması için TCP destekleyen bir çalışma zamanı iletişim yığını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="01201-162">By default it generates a runtime communication stack supporting TCP for message delivery and Windows Security for message security and authentication, WS-ReliableMessaging for reliability, and binary message encoding.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01201-163">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="01201-163">See also</span></span>

- <xref:System.ServiceModel.NetTcpSecurity>
- <xref:System.ServiceModel.NetTcpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetTcpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>
- [<span data-ttu-id="01201-164">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="01201-164">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="01201-165">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="01201-165">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="01201-166">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="01201-166">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="01201-167">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="01201-167">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="01201-168">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="01201-168">\<binding></span></span>](../../../misc/binding.md)
