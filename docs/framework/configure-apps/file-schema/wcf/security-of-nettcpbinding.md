---
title: <security> / <netTcpBinding>
ms.date: 03/30/2017
ms.assetid: 286cd191-4fd5-4c4e-a223-9c71cf7fdead
ms.openlocfilehash: aa01e906ddd2f15007c72bfc2a45122cfb15ba2c
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73736376"
---
# <a name="security-of-nettcpbinding"></a><span data-ttu-id="4f679-102">\<security> / \<netTcpBinding></span><span class="sxs-lookup"><span data-stu-id="4f679-102">\<security> of \<netTcpBinding></span></span>
<span data-ttu-id="4f679-103">Bağlama için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4f679-103">Defines the security settings for a binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netTcpBinding>**](nettcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="4f679-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4f679-104">Syntax</span></span>  
  
```xml  
<security mode="Message/None/Transport/TransportWithCredential">
  <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             protectionLevel="None/Sign/EncryptAndSign" />
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4f679-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="4f679-105">Attributes and Elements</span></span>  
 <span data-ttu-id="4f679-106">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="4f679-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4f679-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4f679-107">Attributes</span></span>  
  
|<span data-ttu-id="4f679-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="4f679-108">Attribute</span></span>|<span data-ttu-id="4f679-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4f679-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4f679-110">mod</span><span class="sxs-lookup"><span data-stu-id="4f679-110">mode</span></span>|<span data-ttu-id="4f679-111">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="4f679-111">Optional.</span></span> <span data-ttu-id="4f679-112">Uygulanan güvenlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="4f679-112">Specifies the type of security that is applied.</span></span> <span data-ttu-id="4f679-113">Geçerli değerler aşağıda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="4f679-113">Valid values are shown below.</span></span> <span data-ttu-id="4f679-114">Varsayılan değer: `Transport`.</span><span class="sxs-lookup"><span data-stu-id="4f679-114">The default value is `Transport`.</span></span><br /><br /> <span data-ttu-id="4f679-115">Bu öznitelik türü <xref:System.ServiceModel.SecurityMode> .</span><span class="sxs-lookup"><span data-stu-id="4f679-115">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="4f679-116">mode özniteliği</span><span class="sxs-lookup"><span data-stu-id="4f679-116">mode Attribute</span></span>  
  
|<span data-ttu-id="4f679-117">Değer</span><span class="sxs-lookup"><span data-stu-id="4f679-117">Value</span></span>|<span data-ttu-id="4f679-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4f679-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="4f679-119">Yok</span><span class="sxs-lookup"><span data-stu-id="4f679-119">None</span></span>|<span data-ttu-id="4f679-120">Güvenlik devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="4f679-120">Security is disabled.</span></span>|  
|<span data-ttu-id="4f679-121">Aktarım</span><span class="sxs-lookup"><span data-stu-id="4f679-121">Transport</span></span>|<span data-ttu-id="4f679-122">Aktarım güvenliği TCP veya SPNego üzerinden TLS kullanılarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="4f679-122">Transport security is provided using TLS over TCP or SPNego.</span></span> <span data-ttu-id="4f679-123">Hizmetin SSL sertifikalarıyla yapılandırılması gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="4f679-123">The service may need to be configured with SSL certificates.</span></span> <span data-ttu-id="4f679-124">Koruma düzeyini Bu modla denetlemek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="4f679-124">It is possible to control the protection level with this mode.</span></span>|  
|<span data-ttu-id="4f679-125">İleti</span><span class="sxs-lookup"><span data-stu-id="4f679-125">Message</span></span>|<span data-ttu-id="4f679-126">Güvenlik, SOAP iletisi güvenliği kullanılarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="4f679-126">Security is provided using SOAP message security.</span></span> <span data-ttu-id="4f679-127">Varsayılan olarak, SOAP gövdesi şifrelenir ve imzalanır.</span><span class="sxs-lookup"><span data-stu-id="4f679-127">By default, the SOAP body is encrypted and signed.</span></span> <span data-ttu-id="4f679-128">Bu mod, hizmet kimlik bilgilerinin, istemci bant dışı, kullanılacak algoritma paketini ve ileti gövdesine uygulanacak koruma düzeyini belirtir gibi çeşitli özellikler sunar.</span><span class="sxs-lookup"><span data-stu-id="4f679-128">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body.</span></span> <span data-ttu-id="4f679-129">Oturum başına istemci kimlik doğrulaması gerçekleştirilir ve kimlik doğrulama sonuçları oturum süresince önbelleğe alınır.</span><span class="sxs-lookup"><span data-stu-id="4f679-129">Client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
|<span data-ttu-id="4f679-130">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="4f679-130">TransportWithMessageCredential</span></span>|<span data-ttu-id="4f679-131">Aktarım güvenliği, ileti güvenliği ile birlikte gönderilir.</span><span class="sxs-lookup"><span data-stu-id="4f679-131">Transport security is coupled with message security.</span></span> <span data-ttu-id="4f679-132">Aktarım güvenliği TCP veya SPNego üzerinden TLS tarafından sağlanır ve bütünlük, gizlilik ve sunucu kimlik doğrulamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="4f679-132">Transport security is provided by TLS over TCP, or SPNego, and ensures integrity, confidentiality, and server authentication.</span></span> <span data-ttu-id="4f679-133">SOAP iletisi güvenliği istemci kimlik doğrulaması sağlar.</span><span class="sxs-lookup"><span data-stu-id="4f679-133">SOAP message security provides client authentication.</span></span> <span data-ttu-id="4f679-134">Varsayılan olarak, oturum başına istemci kimlik doğrulaması gerçekleştirilir ve kimlik doğrulama sonuçları oturum süresince önbelleğe alınır.</span><span class="sxs-lookup"><span data-stu-id="4f679-134">By default, client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4f679-135">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="4f679-135">Child Elements</span></span>  
  
|<span data-ttu-id="4f679-136">Öğe</span><span class="sxs-lookup"><span data-stu-id="4f679-136">Element</span></span>|<span data-ttu-id="4f679-137">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4f679-137">Description</span></span>|  
|-------------|-----------------|  
|[\<transport>](transport-of-nettcpbinding.md)|<span data-ttu-id="4f679-138">Taşımanın güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4f679-138">Defines the security settings for the transport.</span></span> <span data-ttu-id="4f679-139">Bu öğe türündedir <xref:System.ServiceModel.Configuration.TcpTransportSecurityElement> .</span><span class="sxs-lookup"><span data-stu-id="4f679-139">This element is of type <xref:System.ServiceModel.Configuration.TcpTransportSecurityElement>.</span></span>|  
|[\<message>](message-element-of-nettcpbinding.md)|<span data-ttu-id="4f679-140">İleti için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4f679-140">Defines the security settings for the message.</span></span> <span data-ttu-id="4f679-141">Bu öğe türündedir <xref:System.ServiceModel.Configuration.MessageSecurityOverTcpElement> .</span><span class="sxs-lookup"><span data-stu-id="4f679-141">This element is of type <xref:System.ServiceModel.Configuration.MessageSecurityOverTcpElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4f679-142">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="4f679-142">Parent Elements</span></span>  
  
|<span data-ttu-id="4f679-143">Öğe</span><span class="sxs-lookup"><span data-stu-id="4f679-143">Element</span></span>|<span data-ttu-id="4f679-144">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4f679-144">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4f679-145">bağlama</span><span class="sxs-lookup"><span data-stu-id="4f679-145">binding</span></span>|<span data-ttu-id="4f679-146">Öğesinin bağlama öğesi [\<netTcpBinding>](nettcpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="4f679-146">The binding element of the [\<netTcpBinding>](nettcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4f679-147">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4f679-147">Remarks</span></span>  
 <span data-ttu-id="4f679-148">Standart bağlamaların her biri, aktarım güvenliği gereksinimlerini denetlemek için parametreler sağlar.</span><span class="sxs-lookup"><span data-stu-id="4f679-148">Each of the standard bindings provides parameters for controlling the transfer security requirements.</span></span> <span data-ttu-id="4f679-149">Bu parametreler genellikle ileti düzeyi veya aktarım düzeyi güvenliğin kullanılıp kullanılmadığını ve istemci kimlik bilgisi türünü seçmesini belirten güvenlik modunu içerir.</span><span class="sxs-lookup"><span data-stu-id="4f679-149">These parameters typically include the security mode that specified whether message-level or transport-level security is used and the choice of client credential type.</span></span> <span data-ttu-id="4f679-150">Bu parametrelerin mevcut seçeneklerinin seçimine bağlı olarak, uygun güvenlik ile bir kanal yığını oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="4f679-150">Based on the choice of options these parameters present, a channel stack is constructed with appropriate security.</span></span>  
  
 <span data-ttu-id="4f679-151">Windows Communication Foundation (WCF) tarafından sağlanan sistem tarafından sağlanan bağlamalar, en yaygın senaryo gereksinimlerinin bazılarını karşılayacak şekilde tasarlanan bir kümesidir.</span><span class="sxs-lookup"><span data-stu-id="4f679-151">The system-provided bindings supplied by Windows Communication Foundation (WCF) are a set designed to meet some of the most common scenario requirements.</span></span> <span data-ttu-id="4f679-152">Bu bağlamalardan her biri, belirli bir hedeflenmiş senaryolar için güvenlik gereksinimlerinin belirtilede olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="4f679-152">Each of these bindings allows the specification of security requirements for some specific targeted scenarios.</span></span>  
  
 <span data-ttu-id="4f679-153">Bu yapılandırma öğesi için güvenlik belirtimleri sağlar `netTcpBinding` .</span><span class="sxs-lookup"><span data-stu-id="4f679-153">This configuration element provides the security specifications for `netTcpBinding`.</span></span> <span data-ttu-id="4f679-154">Bu, makineler arası iletişim için uygun, güvenli, güvenilir ve iyileştirilmiş bir bağlamadır.</span><span class="sxs-lookup"><span data-stu-id="4f679-154">This is a secure, reliable, optimized binding suitable for cross-machine communication.</span></span> <span data-ttu-id="4f679-155">Varsayılan olarak, ileti teslimi için TCP ve ileti güvenliği ve kimlik doğrulaması için Windows güvenliği, güvenilirlik açısından WS-ReliableMessaging ve ikili ileti kodlaması için TCP destekleyen bir çalışma zamanı iletişim yığını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4f679-155">By default it generates a runtime communication stack supporting TCP for message delivery and Windows Security for message security and authentication, WS-ReliableMessaging for reliability, and binary message encoding.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f679-156">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4f679-156">See also</span></span>

- <xref:System.ServiceModel.NetTcpSecurity>
- <xref:System.ServiceModel.NetTcpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetTcpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>
- [<span data-ttu-id="4f679-157">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="4f679-157">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="4f679-158">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="4f679-158">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="4f679-159">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="4f679-159">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="4f679-160">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="4f679-160">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
