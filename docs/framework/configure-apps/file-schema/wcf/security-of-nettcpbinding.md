---
title: <security> / <netTcpBinding>
ms.date: 03/30/2017
ms.assetid: 286cd191-4fd5-4c4e-a223-9c71cf7fdead
ms.openlocfilehash: d39e3e5e655817aa91c5301274a860a00a6ab7ef
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91169992"
---
# <a name="security-of-nettcpbinding"></a><span data-ttu-id="8ce1d-102">\<security> / \<netTcpBinding></span><span class="sxs-lookup"><span data-stu-id="8ce1d-102">\<security> of \<netTcpBinding></span></span>

<span data-ttu-id="8ce1d-103">Bağlama için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8ce1d-103">Defines the security settings for a binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netTcpBinding>**](nettcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="8ce1d-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="8ce1d-104">Syntax</span></span>  
  
```xml  
<security mode="Message/None/Transport/TransportWithCredential">
  <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             protectionLevel="None/Sign/EncryptAndSign" />
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8ce1d-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="8ce1d-105">Attributes and Elements</span></span>  

 <span data-ttu-id="8ce1d-106">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="8ce1d-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8ce1d-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="8ce1d-107">Attributes</span></span>  
  
|<span data-ttu-id="8ce1d-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="8ce1d-108">Attribute</span></span>|<span data-ttu-id="8ce1d-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8ce1d-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8ce1d-110">mod</span><span class="sxs-lookup"><span data-stu-id="8ce1d-110">mode</span></span>|<span data-ttu-id="8ce1d-111">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="8ce1d-111">Optional.</span></span> <span data-ttu-id="8ce1d-112">Uygulanan güvenlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="8ce1d-112">Specifies the type of security that is applied.</span></span> <span data-ttu-id="8ce1d-113">Geçerli değerler aşağıda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="8ce1d-113">Valid values are shown below.</span></span> <span data-ttu-id="8ce1d-114">Varsayılan değer: `Transport`.</span><span class="sxs-lookup"><span data-stu-id="8ce1d-114">The default value is `Transport`.</span></span><br /><br /> <span data-ttu-id="8ce1d-115">Bu öznitelik türü <xref:System.ServiceModel.SecurityMode> .</span><span class="sxs-lookup"><span data-stu-id="8ce1d-115">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="8ce1d-116">mode özniteliği</span><span class="sxs-lookup"><span data-stu-id="8ce1d-116">mode Attribute</span></span>  
  
|<span data-ttu-id="8ce1d-117">Değer</span><span class="sxs-lookup"><span data-stu-id="8ce1d-117">Value</span></span>|<span data-ttu-id="8ce1d-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8ce1d-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8ce1d-119">Yok</span><span class="sxs-lookup"><span data-stu-id="8ce1d-119">None</span></span>|<span data-ttu-id="8ce1d-120">Güvenlik devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="8ce1d-120">Security is disabled.</span></span>|  
|<span data-ttu-id="8ce1d-121">Aktarım</span><span class="sxs-lookup"><span data-stu-id="8ce1d-121">Transport</span></span>|<span data-ttu-id="8ce1d-122">Aktarım güvenliği TCP veya SPNego üzerinden TLS kullanılarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="8ce1d-122">Transport security is provided using TLS over TCP or SPNego.</span></span> <span data-ttu-id="8ce1d-123">Hizmetin SSL sertifikalarıyla yapılandırılması gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="8ce1d-123">The service may need to be configured with SSL certificates.</span></span> <span data-ttu-id="8ce1d-124">Koruma düzeyini Bu modla denetlemek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="8ce1d-124">It is possible to control the protection level with this mode.</span></span>|  
|<span data-ttu-id="8ce1d-125">İleti</span><span class="sxs-lookup"><span data-stu-id="8ce1d-125">Message</span></span>|<span data-ttu-id="8ce1d-126">Güvenlik, SOAP iletisi güvenliği kullanılarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="8ce1d-126">Security is provided using SOAP message security.</span></span> <span data-ttu-id="8ce1d-127">Varsayılan olarak, SOAP gövdesi şifrelenir ve imzalanır.</span><span class="sxs-lookup"><span data-stu-id="8ce1d-127">By default, the SOAP body is encrypted and signed.</span></span> <span data-ttu-id="8ce1d-128">Bu mod, hizmet kimlik bilgilerinin, istemci bant dışı, kullanılacak algoritma paketini ve ileti gövdesine uygulanacak koruma düzeyini belirtir gibi çeşitli özellikler sunar.</span><span class="sxs-lookup"><span data-stu-id="8ce1d-128">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body.</span></span> <span data-ttu-id="8ce1d-129">Oturum başına istemci kimlik doğrulaması gerçekleştirilir ve kimlik doğrulama sonuçları oturum süresince önbelleğe alınır.</span><span class="sxs-lookup"><span data-stu-id="8ce1d-129">Client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
|<span data-ttu-id="8ce1d-130">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="8ce1d-130">TransportWithMessageCredential</span></span>|<span data-ttu-id="8ce1d-131">Aktarım güvenliği, ileti güvenliği ile birlikte gönderilir.</span><span class="sxs-lookup"><span data-stu-id="8ce1d-131">Transport security is coupled with message security.</span></span> <span data-ttu-id="8ce1d-132">Aktarım güvenliği TCP veya SPNego üzerinden TLS tarafından sağlanır ve bütünlük, gizlilik ve sunucu kimlik doğrulamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="8ce1d-132">Transport security is provided by TLS over TCP, or SPNego, and ensures integrity, confidentiality, and server authentication.</span></span> <span data-ttu-id="8ce1d-133">SOAP iletisi güvenliği istemci kimlik doğrulaması sağlar.</span><span class="sxs-lookup"><span data-stu-id="8ce1d-133">SOAP message security provides client authentication.</span></span> <span data-ttu-id="8ce1d-134">Varsayılan olarak, oturum başına istemci kimlik doğrulaması gerçekleştirilir ve kimlik doğrulama sonuçları oturum süresince önbelleğe alınır.</span><span class="sxs-lookup"><span data-stu-id="8ce1d-134">By default, client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8ce1d-135">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="8ce1d-135">Child Elements</span></span>  
  
|<span data-ttu-id="8ce1d-136">Öğe</span><span class="sxs-lookup"><span data-stu-id="8ce1d-136">Element</span></span>|<span data-ttu-id="8ce1d-137">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8ce1d-137">Description</span></span>|  
|-------------|-----------------|  
|[\<transport>](transport-of-nettcpbinding.md)|<span data-ttu-id="8ce1d-138">Taşımanın güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8ce1d-138">Defines the security settings for the transport.</span></span> <span data-ttu-id="8ce1d-139">Bu öğe türündedir <xref:System.ServiceModel.Configuration.TcpTransportSecurityElement> .</span><span class="sxs-lookup"><span data-stu-id="8ce1d-139">This element is of type <xref:System.ServiceModel.Configuration.TcpTransportSecurityElement>.</span></span>|  
|[\<message>](message-element-of-nettcpbinding.md)|<span data-ttu-id="8ce1d-140">İleti için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8ce1d-140">Defines the security settings for the message.</span></span> <span data-ttu-id="8ce1d-141">Bu öğe türündedir <xref:System.ServiceModel.Configuration.MessageSecurityOverTcpElement> .</span><span class="sxs-lookup"><span data-stu-id="8ce1d-141">This element is of type <xref:System.ServiceModel.Configuration.MessageSecurityOverTcpElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8ce1d-142">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="8ce1d-142">Parent Elements</span></span>  
  
|<span data-ttu-id="8ce1d-143">Öğe</span><span class="sxs-lookup"><span data-stu-id="8ce1d-143">Element</span></span>|<span data-ttu-id="8ce1d-144">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8ce1d-144">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8ce1d-145">bağlama</span><span class="sxs-lookup"><span data-stu-id="8ce1d-145">binding</span></span>|<span data-ttu-id="8ce1d-146">Öğesinin bağlama öğesi [\<netTcpBinding>](nettcpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="8ce1d-146">The binding element of the [\<netTcpBinding>](nettcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8ce1d-147">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8ce1d-147">Remarks</span></span>  

 <span data-ttu-id="8ce1d-148">Standart bağlamaların her biri, aktarım güvenliği gereksinimlerini denetlemek için parametreler sağlar.</span><span class="sxs-lookup"><span data-stu-id="8ce1d-148">Each of the standard bindings provides parameters for controlling the transfer security requirements.</span></span> <span data-ttu-id="8ce1d-149">Bu parametreler genellikle ileti düzeyi veya aktarım düzeyi güvenliğin kullanılıp kullanılmadığını ve istemci kimlik bilgisi türünü seçmesini belirten güvenlik modunu içerir.</span><span class="sxs-lookup"><span data-stu-id="8ce1d-149">These parameters typically include the security mode that specified whether message-level or transport-level security is used and the choice of client credential type.</span></span> <span data-ttu-id="8ce1d-150">Bu parametrelerin mevcut seçeneklerinin seçimine bağlı olarak, uygun güvenlik ile bir kanal yığını oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="8ce1d-150">Based on the choice of options these parameters present, a channel stack is constructed with appropriate security.</span></span>  
  
 <span data-ttu-id="8ce1d-151">Windows Communication Foundation (WCF) tarafından sağlanan sistem tarafından sağlanan bağlamalar, en yaygın senaryo gereksinimlerinin bazılarını karşılayacak şekilde tasarlanan bir kümesidir.</span><span class="sxs-lookup"><span data-stu-id="8ce1d-151">The system-provided bindings supplied by Windows Communication Foundation (WCF) are a set designed to meet some of the most common scenario requirements.</span></span> <span data-ttu-id="8ce1d-152">Bu bağlamalardan her biri, belirli bir hedeflenmiş senaryolar için güvenlik gereksinimlerinin belirtilede olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="8ce1d-152">Each of these bindings allows the specification of security requirements for some specific targeted scenarios.</span></span>  
  
 <span data-ttu-id="8ce1d-153">Bu yapılandırma öğesi için güvenlik belirtimleri sağlar `netTcpBinding` .</span><span class="sxs-lookup"><span data-stu-id="8ce1d-153">This configuration element provides the security specifications for `netTcpBinding`.</span></span> <span data-ttu-id="8ce1d-154">Bu, makineler arası iletişim için uygun, güvenli, güvenilir ve iyileştirilmiş bir bağlamadır.</span><span class="sxs-lookup"><span data-stu-id="8ce1d-154">This is a secure, reliable, optimized binding suitable for cross-machine communication.</span></span> <span data-ttu-id="8ce1d-155">Varsayılan olarak, ileti teslimi için TCP ve ileti güvenliği ve kimlik doğrulaması için Windows güvenliği, güvenilirlik açısından WS-ReliableMessaging ve ikili ileti kodlaması için TCP destekleyen bir çalışma zamanı iletişim yığını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8ce1d-155">By default it generates a runtime communication stack supporting TCP for message delivery and Windows Security for message security and authentication, WS-ReliableMessaging for reliability, and binary message encoding.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ce1d-156">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8ce1d-156">See also</span></span>

- <xref:System.ServiceModel.NetTcpSecurity>
- <xref:System.ServiceModel.NetTcpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetTcpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>
- [<span data-ttu-id="8ce1d-157">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="8ce1d-157">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="8ce1d-158">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="8ce1d-158">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="8ce1d-159">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="8ce1d-159">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="8ce1d-160">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="8ce1d-160">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
