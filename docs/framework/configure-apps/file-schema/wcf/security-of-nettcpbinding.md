---
description: 'Hakkında daha fazla bilgi <security> edinin: <netTcpBinding>'
title: <security> / <netTcpBinding>
ms.date: 03/30/2017
ms.assetid: 286cd191-4fd5-4c4e-a223-9c71cf7fdead
ms.openlocfilehash: ad924f5a6ea9e003f6427ee76d3aef3afde9d083
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99683079"
---
# <a name="security-of-nettcpbinding"></a><span data-ttu-id="1b71a-103">\<security> / \<netTcpBinding></span><span class="sxs-lookup"><span data-stu-id="1b71a-103">\<security> of \<netTcpBinding></span></span>

<span data-ttu-id="1b71a-104">Bağlama için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1b71a-104">Defines the security settings for a binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netTcpBinding>**](nettcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="1b71a-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="1b71a-105">Syntax</span></span>  
  
```xml  
<security mode="Message/None/Transport/TransportWithCredential">
  <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             protectionLevel="None/Sign/EncryptAndSign" />
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1b71a-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="1b71a-106">Attributes and Elements</span></span>  

 <span data-ttu-id="1b71a-107">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="1b71a-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1b71a-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="1b71a-108">Attributes</span></span>  
  
|<span data-ttu-id="1b71a-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="1b71a-109">Attribute</span></span>|<span data-ttu-id="1b71a-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1b71a-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1b71a-111">mod</span><span class="sxs-lookup"><span data-stu-id="1b71a-111">mode</span></span>|<span data-ttu-id="1b71a-112">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="1b71a-112">Optional.</span></span> <span data-ttu-id="1b71a-113">Uygulanan güvenlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="1b71a-113">Specifies the type of security that is applied.</span></span> <span data-ttu-id="1b71a-114">Geçerli değerler aşağıda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="1b71a-114">Valid values are shown below.</span></span> <span data-ttu-id="1b71a-115">`Transport` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="1b71a-115">The default value is `Transport`.</span></span><br /><br /> <span data-ttu-id="1b71a-116">Bu öznitelik türü <xref:System.ServiceModel.SecurityMode> .</span><span class="sxs-lookup"><span data-stu-id="1b71a-116">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="1b71a-117">mode özniteliği</span><span class="sxs-lookup"><span data-stu-id="1b71a-117">mode Attribute</span></span>  
  
|<span data-ttu-id="1b71a-118">Değer</span><span class="sxs-lookup"><span data-stu-id="1b71a-118">Value</span></span>|<span data-ttu-id="1b71a-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1b71a-119">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1b71a-120">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="1b71a-120">None</span></span>|<span data-ttu-id="1b71a-121">Güvenlik devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="1b71a-121">Security is disabled.</span></span>|  
|<span data-ttu-id="1b71a-122">Aktarım</span><span class="sxs-lookup"><span data-stu-id="1b71a-122">Transport</span></span>|<span data-ttu-id="1b71a-123">Aktarım güvenliği TCP veya SPNego üzerinden TLS kullanılarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="1b71a-123">Transport security is provided using TLS over TCP or SPNego.</span></span> <span data-ttu-id="1b71a-124">Hizmetin SSL sertifikalarıyla yapılandırılması gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="1b71a-124">The service may need to be configured with SSL certificates.</span></span> <span data-ttu-id="1b71a-125">Koruma düzeyini Bu modla denetlemek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="1b71a-125">It is possible to control the protection level with this mode.</span></span>|  
|<span data-ttu-id="1b71a-126">İleti</span><span class="sxs-lookup"><span data-stu-id="1b71a-126">Message</span></span>|<span data-ttu-id="1b71a-127">Güvenlik, SOAP iletisi güvenliği kullanılarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="1b71a-127">Security is provided using SOAP message security.</span></span> <span data-ttu-id="1b71a-128">Varsayılan olarak, SOAP gövdesi şifrelenir ve imzalanır.</span><span class="sxs-lookup"><span data-stu-id="1b71a-128">By default, the SOAP body is encrypted and signed.</span></span> <span data-ttu-id="1b71a-129">Bu mod, hizmet kimlik bilgilerinin, istemci bant dışı, kullanılacak algoritma paketini ve ileti gövdesine uygulanacak koruma düzeyini belirtir gibi çeşitli özellikler sunar.</span><span class="sxs-lookup"><span data-stu-id="1b71a-129">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body.</span></span> <span data-ttu-id="1b71a-130">Oturum başına istemci kimlik doğrulaması gerçekleştirilir ve kimlik doğrulama sonuçları oturum süresince önbelleğe alınır.</span><span class="sxs-lookup"><span data-stu-id="1b71a-130">Client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
|<span data-ttu-id="1b71a-131">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="1b71a-131">TransportWithMessageCredential</span></span>|<span data-ttu-id="1b71a-132">Aktarım güvenliği, ileti güvenliği ile birlikte gönderilir.</span><span class="sxs-lookup"><span data-stu-id="1b71a-132">Transport security is coupled with message security.</span></span> <span data-ttu-id="1b71a-133">Aktarım güvenliği TCP veya SPNego üzerinden TLS tarafından sağlanır ve bütünlük, gizlilik ve sunucu kimlik doğrulamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="1b71a-133">Transport security is provided by TLS over TCP, or SPNego, and ensures integrity, confidentiality, and server authentication.</span></span> <span data-ttu-id="1b71a-134">SOAP iletisi güvenliği istemci kimlik doğrulaması sağlar.</span><span class="sxs-lookup"><span data-stu-id="1b71a-134">SOAP message security provides client authentication.</span></span> <span data-ttu-id="1b71a-135">Varsayılan olarak, oturum başına istemci kimlik doğrulaması gerçekleştirilir ve kimlik doğrulama sonuçları oturum süresince önbelleğe alınır.</span><span class="sxs-lookup"><span data-stu-id="1b71a-135">By default, client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1b71a-136">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="1b71a-136">Child Elements</span></span>  
  
|<span data-ttu-id="1b71a-137">Öğe</span><span class="sxs-lookup"><span data-stu-id="1b71a-137">Element</span></span>|<span data-ttu-id="1b71a-138">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1b71a-138">Description</span></span>|  
|-------------|-----------------|  
|[\<transport>](transport-of-nettcpbinding.md)|<span data-ttu-id="1b71a-139">Taşımanın güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1b71a-139">Defines the security settings for the transport.</span></span> <span data-ttu-id="1b71a-140">Bu öğe türündedir <xref:System.ServiceModel.Configuration.TcpTransportSecurityElement> .</span><span class="sxs-lookup"><span data-stu-id="1b71a-140">This element is of type <xref:System.ServiceModel.Configuration.TcpTransportSecurityElement>.</span></span>|  
|[\<message>](message-element-of-nettcpbinding.md)|<span data-ttu-id="1b71a-141">İleti için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1b71a-141">Defines the security settings for the message.</span></span> <span data-ttu-id="1b71a-142">Bu öğe türündedir <xref:System.ServiceModel.Configuration.MessageSecurityOverTcpElement> .</span><span class="sxs-lookup"><span data-stu-id="1b71a-142">This element is of type <xref:System.ServiceModel.Configuration.MessageSecurityOverTcpElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1b71a-143">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="1b71a-143">Parent Elements</span></span>  
  
|<span data-ttu-id="1b71a-144">Öğe</span><span class="sxs-lookup"><span data-stu-id="1b71a-144">Element</span></span>|<span data-ttu-id="1b71a-145">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1b71a-145">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1b71a-146">bağlama</span><span class="sxs-lookup"><span data-stu-id="1b71a-146">binding</span></span>|<span data-ttu-id="1b71a-147">Öğesinin bağlama öğesi [\<netTcpBinding>](nettcpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="1b71a-147">The binding element of the [\<netTcpBinding>](nettcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1b71a-148">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1b71a-148">Remarks</span></span>  

 <span data-ttu-id="1b71a-149">Standart bağlamaların her biri, aktarım güvenliği gereksinimlerini denetlemek için parametreler sağlar.</span><span class="sxs-lookup"><span data-stu-id="1b71a-149">Each of the standard bindings provides parameters for controlling the transfer security requirements.</span></span> <span data-ttu-id="1b71a-150">Bu parametreler genellikle ileti düzeyi veya aktarım düzeyi güvenliğin kullanılıp kullanılmadığını ve istemci kimlik bilgisi türünü seçmesini belirten güvenlik modunu içerir.</span><span class="sxs-lookup"><span data-stu-id="1b71a-150">These parameters typically include the security mode that specified whether message-level or transport-level security is used and the choice of client credential type.</span></span> <span data-ttu-id="1b71a-151">Bu parametrelerin mevcut seçeneklerinin seçimine bağlı olarak, uygun güvenlik ile bir kanal yığını oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="1b71a-151">Based on the choice of options these parameters present, a channel stack is constructed with appropriate security.</span></span>  
  
 <span data-ttu-id="1b71a-152">Windows Communication Foundation (WCF) tarafından sağlanan sistem tarafından sağlanan bağlamalar, en yaygın senaryo gereksinimlerinin bazılarını karşılayacak şekilde tasarlanan bir kümesidir.</span><span class="sxs-lookup"><span data-stu-id="1b71a-152">The system-provided bindings supplied by Windows Communication Foundation (WCF) are a set designed to meet some of the most common scenario requirements.</span></span> <span data-ttu-id="1b71a-153">Bu bağlamalardan her biri, belirli bir hedeflenmiş senaryolar için güvenlik gereksinimlerinin belirtilede olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="1b71a-153">Each of these bindings allows the specification of security requirements for some specific targeted scenarios.</span></span>  
  
 <span data-ttu-id="1b71a-154">Bu yapılandırma öğesi için güvenlik belirtimleri sağlar `netTcpBinding` .</span><span class="sxs-lookup"><span data-stu-id="1b71a-154">This configuration element provides the security specifications for `netTcpBinding`.</span></span> <span data-ttu-id="1b71a-155">Bu, makineler arası iletişim için uygun, güvenli, güvenilir ve iyileştirilmiş bir bağlamadır.</span><span class="sxs-lookup"><span data-stu-id="1b71a-155">This is a secure, reliable, optimized binding suitable for cross-machine communication.</span></span> <span data-ttu-id="1b71a-156">Varsayılan olarak, ileti teslimi ve ileti güvenliği ve kimlik doğrulaması için Windows güvenliği, güvenilirlik için WS-ReliableMessaging ve ikili ileti kodlaması için TCP destekleyen bir çalışma zamanı iletişim yığını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1b71a-156">By default it generates a runtime communication stack supporting TCP for message delivery and Windows Security for message security and authentication, WS-ReliableMessaging for reliability, and binary message encoding.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b71a-157">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1b71a-157">See also</span></span>

- <xref:System.ServiceModel.NetTcpSecurity>
- <xref:System.ServiceModel.NetTcpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetTcpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>
- [<span data-ttu-id="1b71a-158">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="1b71a-158">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="1b71a-159">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="1b71a-159">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="1b71a-160">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="1b71a-160">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="1b71a-161">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="1b71a-161">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
