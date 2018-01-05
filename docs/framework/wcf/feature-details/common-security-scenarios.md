---
title: "Ortak Güvenlik Senaryoları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: security [WCF], scenarios
ms.assetid: 201923b5-5162-4a8a-8d4c-e7bd242748d5
caps.latest.revision: "18"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: d8881768d66e95ce1391ce1be1663bdc3107a347
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="common-security-scenarios"></a><span data-ttu-id="8780f-102">Ortak Güvenlik Senaryoları</span><span class="sxs-lookup"><span data-stu-id="8780f-102">Common Security Scenarios</span></span>
<span data-ttu-id="8780f-103">Bu bölümdeki konular, bir dizi olası istemci ve hizmet güvenlik yapılandırması katalog.</span><span class="sxs-lookup"><span data-stu-id="8780f-103">The topics in this section catalog a number of possible client and service security configurations.</span></span> <span data-ttu-id="8780f-104">Yapılandırmalarını bir dizi etkene göre farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="8780f-104">Configurations vary according to a number of factors.</span></span> <span data-ttu-id="8780f-105">Örneğin, bir hizmet veya istemci intranet üzerinde olup ya da güvenlik olup Windows veya taşıma (Örneğin HTTPS) tarafından sağlanır.</span><span class="sxs-lookup"><span data-stu-id="8780f-105">For example, whether a service or client is on an intranet, or whether the security is provided by Windows or transport (such as HTTPS).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8780f-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="8780f-106">In This Section</span></span>  
 [<span data-ttu-id="8780f-107">İnternet Güvenli Olmayan Hizmet ve İstemci</span><span class="sxs-lookup"><span data-stu-id="8780f-107">Internet Unsecured Client and Service</span></span>](../../../../docs/framework/wcf/feature-details/internet-unsecured-client-and-service.md)  
 <span data-ttu-id="8780f-108">Bir ortak, güvenli olmayan bir istemci ve hizmet örneği.</span><span class="sxs-lookup"><span data-stu-id="8780f-108">An example of a public, unsecured client and service.</span></span>  
  
 [<span data-ttu-id="8780f-109">İntranet Güvenli Olmayan Hizmet ve İstemci</span><span class="sxs-lookup"><span data-stu-id="8780f-109">Intranet Unsecured Client and Service</span></span>](../../../../docs/framework/wcf/feature-details/intranet-unsecured-client-and-service.md)  
 <span data-ttu-id="8780f-110">Temel bir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] hizmet geliştirilen özel bir ağda güvenli için bilgi sağlamak için bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uygulama.</span><span class="sxs-lookup"><span data-stu-id="8780f-110">A basic [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service developed to provide information on a secure private network to a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] application.</span></span>  
  
 [<span data-ttu-id="8780f-111">Temel Kimlik Doğrulama ile Aktarım Güvenliği</span><span class="sxs-lookup"><span data-stu-id="8780f-111">Transport Security with Basic Authentication</span></span>](../../../../docs/framework/wcf/feature-details/transport-security-with-basic-authentication.md)  
 <span data-ttu-id="8780f-112">Uygulama istemcilerinin özel kimlik doğrulaması kullanarak oturum olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="8780f-112">The application allows clients to log on using custom authentication.</span></span>  
  
 [<span data-ttu-id="8780f-113">Windows Kimlik Doğrulaması ile Aktarım Güvenliği</span><span class="sxs-lookup"><span data-stu-id="8780f-113">Transport Security with Windows Authentication</span></span>](../../../../docs/framework/wcf/feature-details/transport-security-with-windows-authentication.md)  
 <span data-ttu-id="8780f-114">Bir istemci ve hizmet Windows security tarafından korunan gösterir.</span><span class="sxs-lookup"><span data-stu-id="8780f-114">Shows a client and service secured by Windows security.</span></span>  
  
 [<span data-ttu-id="8780f-115">Anonim İstemci ile Aktarım Güvenliği</span><span class="sxs-lookup"><span data-stu-id="8780f-115">Transport Security with an Anonymous Client</span></span>](../../../../docs/framework/wcf/feature-details/transport-security-with-an-anonymous-client.md)  
 <span data-ttu-id="8780f-116">Bu senaryo, gizliliği ve bütünlük sağlamak için Aktarım güvenliği (Örneğin HTTPS) kullanır.</span><span class="sxs-lookup"><span data-stu-id="8780f-116">This scenario uses transport security (such as HTTPS) to ensure confidentiality and integrity.</span></span>  
  
 [<span data-ttu-id="8780f-117">Sertifika Kimlik Doğrulama ile Aktarım Güvenliği</span><span class="sxs-lookup"><span data-stu-id="8780f-117">Transport Security with Certificate Authentication</span></span>](../../../../docs/framework/wcf/feature-details/transport-security-with-certificate-authentication.md)  
 <span data-ttu-id="8780f-118">Bir istemci ve hizmet sertifikası ile güvenli gösterir.</span><span class="sxs-lookup"><span data-stu-id="8780f-118">Shows a client and service secured by a certificate.</span></span>  
  
 [<span data-ttu-id="8780f-119">Anonim İstemci ile İleti Güvenliği</span><span class="sxs-lookup"><span data-stu-id="8780f-119">Message Security with an Anonymous Client</span></span>](../../../../docs/framework/wcf/feature-details/message-security-with-an-anonymous-client.md)  
 <span data-ttu-id="8780f-120">Bir istemci ve hizmet tarafından güvenli hale getirilmiş gösterir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ileti güvenlik.</span><span class="sxs-lookup"><span data-stu-id="8780f-120">Shows a client and service secured by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] message security.</span></span>  
  
 [<span data-ttu-id="8780f-121">Kullanıcı Adı İstemcisi ile İleti Güvenliği</span><span class="sxs-lookup"><span data-stu-id="8780f-121">Message Security with a User Name Client</span></span>](../../../../docs/framework/wcf/feature-details/message-security-with-a-user-name-client.md)  
 <span data-ttu-id="8780f-122">İstemci, bir etki alanı kullanıcı adı ve parola kullanarak oturum istemcilerin bir Windows Forms uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="8780f-122">The client is a Windows Forms application that allows clients to log on using a domain user name and password.</span></span>  
  
 [<span data-ttu-id="8780f-123">Sertifika İstemcisi ile İleti Güvenliği</span><span class="sxs-lookup"><span data-stu-id="8780f-123">Message Security with a Certificate Client</span></span>](../../../../docs/framework/wcf/feature-details/message-security-with-a-certificate-client.md)  
 <span data-ttu-id="8780f-124">Sunucu sertifikalarına sahip olduğunu ve her bir istemci bir sertifikaya sahip.</span><span class="sxs-lookup"><span data-stu-id="8780f-124">Servers have certificates, and each client has a certificate.</span></span> <span data-ttu-id="8780f-125">Bir güvenlik bağlamı, Aktarım Katmanı Güvenliği (TLS) anlaşması ile kurulur.</span><span class="sxs-lookup"><span data-stu-id="8780f-125">A security context is established through Transport Layer Security (TLS) negotiation.</span></span>  
  
 [<span data-ttu-id="8780f-126">Windows İstemcisi ile İleti Güvenliği</span><span class="sxs-lookup"><span data-stu-id="8780f-126">Message Security with a Windows Client</span></span>](../../../../docs/framework/wcf/feature-details/message-security-with-a-windows-client.md)  
 <span data-ttu-id="8780f-127">Sertifika istemcisi çeşidi.</span><span class="sxs-lookup"><span data-stu-id="8780f-127">A variation of the certificate client.</span></span> <span data-ttu-id="8780f-128">Sunucu sertifikalarına sahip olduğunu ve her bir istemci bir sertifikaya sahip.</span><span class="sxs-lookup"><span data-stu-id="8780f-128">Servers have certificates, and each client has a certificate.</span></span> <span data-ttu-id="8780f-129">Bir güvenlik bağlamı TLS anlaşması ile kurulur.</span><span class="sxs-lookup"><span data-stu-id="8780f-129">A security context is established through TLS negotiation.</span></span>  
  
 [<span data-ttu-id="8780f-130">Windows İstemcisi ile Kimlik Bilgileri Görüşmesi Olmadan İleti Güvenliği</span><span class="sxs-lookup"><span data-stu-id="8780f-130">Message Security with a Windows Client without Credential Negotiation</span></span>](../../../../docs/framework/wcf/feature-details/message-security-with-a-windows-client-without-credential-negotiation.md)  
 <span data-ttu-id="8780f-131">Bir istemci ve Kerberos etki alanı tarafından güvenli hale getirilmiş hizmet gösterir.</span><span class="sxs-lookup"><span data-stu-id="8780f-131">Shows a client and service secured by a Kerberos domain.</span></span>  
  
 [<span data-ttu-id="8780f-132">Karşılıklı Sertifikalar ile İleti Güvenliği</span><span class="sxs-lookup"><span data-stu-id="8780f-132">Message Security with Mutual Certificates</span></span>](../../../../docs/framework/wcf/feature-details/message-security-with-mutual-certificates.md)  
 <span data-ttu-id="8780f-133">Sunucu sertifikalarına sahip olduğunu ve her bir istemci bir sertifikaya sahip.</span><span class="sxs-lookup"><span data-stu-id="8780f-133">Servers have certificates, and each client has a certificate.</span></span> <span data-ttu-id="8780f-134">Sunucu sertifikası uygulama ile dağıtılmış ve bant dışı kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8780f-134">The server certificate is distributed with the application and is available out of band.</span></span>  
  
 [<span data-ttu-id="8780f-135">Verilen Belirteçlerle İleti Güvenliği</span><span class="sxs-lookup"><span data-stu-id="8780f-135">Message Security with Issued Tokens</span></span>](../../../../docs/framework/wcf/feature-details/message-security-with-issued-tokens.md)  
 <span data-ttu-id="8780f-136">Bağımsız etki alanları arasında güven kurulması etkinleştirir federe güvenlik.</span><span class="sxs-lookup"><span data-stu-id="8780f-136">Federated security that enables the establishment of trust between independent domains.</span></span>  
  
 [<span data-ttu-id="8780f-137">Güvenilir Alt Sistem</span><span class="sxs-lookup"><span data-stu-id="8780f-137">Trusted Subsystem</span></span>](../../../../docs/framework/wcf/feature-details/trusted-subsystem.md)  
 <span data-ttu-id="8780f-138">Bir istemci bir ağ üzerinden dağıtılan bir veya daha fazla Web Hizmetleri erişir.</span><span class="sxs-lookup"><span data-stu-id="8780f-138">A client accesses one or more Web services that are distributed across a network.</span></span> <span data-ttu-id="8780f-139">Web Hizmetleri güvenli hale getirilmelidir ek kaynaklar (örneğin, veritabanları veya diğer Web Hizmetleri) erişin.</span><span class="sxs-lookup"><span data-stu-id="8780f-139">The Web services access additional resources (such as databases or other Web services) that must be secured.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="8780f-140">Başvuru</span><span class="sxs-lookup"><span data-stu-id="8780f-140">Reference</span></span>  
 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a><span data-ttu-id="8780f-141">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="8780f-141">Related Sections</span></span>  
 [<span data-ttu-id="8780f-142">Yetkilendirme</span><span class="sxs-lookup"><span data-stu-id="8780f-142">Authorization</span></span>](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
  
 [<span data-ttu-id="8780f-143">Güvenliğe Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="8780f-143">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
  
 [<span data-ttu-id="8780f-144">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="8780f-144">Security</span></span>](../../../../docs/framework/wcf/feature-details/security.md)  
  
 [<span data-ttu-id="8780f-145">Bağlamalar ve Güvenlik</span><span class="sxs-lookup"><span data-stu-id="8780f-145">Bindings and Security</span></span>](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)  
  
 [<span data-ttu-id="8780f-146">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="8780f-146">Securing Services and Clients</span></span>](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
  
 [<span data-ttu-id="8780f-147">Kimlik Doğrulaması</span><span class="sxs-lookup"><span data-stu-id="8780f-147">Authentication</span></span>](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)  
  
 [<span data-ttu-id="8780f-148">Yetkilendirme</span><span class="sxs-lookup"><span data-stu-id="8780f-148">Authorization</span></span>](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
  
 [<span data-ttu-id="8780f-149">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="8780f-149">Federation and Issued Tokens</span></span>](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
  
 [<span data-ttu-id="8780f-150">Denetim</span><span class="sxs-lookup"><span data-stu-id="8780f-150">Auditing</span></span>](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)  
  
## <a name="see-also"></a><span data-ttu-id="8780f-151">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8780f-151">See Also</span></span>  
 [<span data-ttu-id="8780f-152">Güvenlik Kılavuzu ve En İyi Uygulamalar</span><span class="sxs-lookup"><span data-stu-id="8780f-152">Security Guidance and Best Practices</span></span>](../../../../docs/framework/wcf/feature-details/security-guidance-and-best-practices.md)  
 [<span data-ttu-id="8780f-153">Windows Server App Fabric için güvenlik modeli</span><span class="sxs-lookup"><span data-stu-id="8780f-153">Security Model for Windows Server App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
