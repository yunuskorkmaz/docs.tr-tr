---
title: Ortak Güvenlik Senaryoları
ms.date: 03/30/2017
helpviewer_keywords:
- security [WCF], scenarios
ms.assetid: 201923b5-5162-4a8a-8d4c-e7bd242748d5
ms.openlocfilehash: 21c8279890d1d1cf746e98f875efb6b1ff869c73
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96295086"
---
# <a name="common-security-scenarios"></a><span data-ttu-id="c9650-102">Ortak Güvenlik Senaryoları</span><span class="sxs-lookup"><span data-stu-id="c9650-102">Common Security Scenarios</span></span>

<span data-ttu-id="c9650-103">Bu bölümdeki konularda, bir dizi olası istemci ve hizmet güvenlik yapılandırması kataloglayın.</span><span class="sxs-lookup"><span data-stu-id="c9650-103">The topics in this section catalog a number of possible client and service security configurations.</span></span> <span data-ttu-id="c9650-104">Konfigürasyonlar bir dizi etkene göre farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="c9650-104">Configurations vary according to a number of factors.</span></span> <span data-ttu-id="c9650-105">Örneğin, bir hizmet veya istemcinin intranette olup olmadığı ya da güvenliğin Windows ya da taşıma (HTTPS gibi) tarafından sağlandığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c9650-105">For example, whether a service or client is on an intranet, or whether the security is provided by Windows or transport (such as HTTPS).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c9650-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="c9650-106">In This Section</span></span>  

 [<span data-ttu-id="c9650-107">İnternet Güvenli Olmayan Hizmet ve İstemci</span><span class="sxs-lookup"><span data-stu-id="c9650-107">Internet Unsecured Client and Service</span></span>](internet-unsecured-client-and-service.md)  
 <span data-ttu-id="c9650-108">Ortak, güvenli olmayan bir istemci ve hizmet örneği.</span><span class="sxs-lookup"><span data-stu-id="c9650-108">An example of a public, unsecured client and service.</span></span>  
  
 [<span data-ttu-id="c9650-109">Intranet Güvenli Olmayan Hizmet ve İstemci</span><span class="sxs-lookup"><span data-stu-id="c9650-109">Intranet Unsecured Client and Service</span></span>](intranet-unsecured-client-and-service.md)  
 <span data-ttu-id="c9650-110">Bir WCF uygulamasına güvenli bir özel ağ hakkında bilgi sağlamak için geliştirilen temel bir Windows Communication Foundation (WCF) hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="c9650-110">A basic Windows Communication Foundation (WCF) service developed to provide information on a secure private network to a WCF application.</span></span>  
  
 [<span data-ttu-id="c9650-111">Temel Kimlik Doğrulama ile Taşıma Güvenliği</span><span class="sxs-lookup"><span data-stu-id="c9650-111">Transport Security with Basic Authentication</span></span>](transport-security-with-basic-authentication.md)  
 <span data-ttu-id="c9650-112">Uygulama, istemcilerin özel kimlik doğrulaması kullanarak oturum açmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="c9650-112">The application allows clients to log on using custom authentication.</span></span>  
  
 [<span data-ttu-id="c9650-113">Windows Kimlik Doğrulama ile Taşıma Güvenliği</span><span class="sxs-lookup"><span data-stu-id="c9650-113">Transport Security with Windows Authentication</span></span>](transport-security-with-windows-authentication.md)  
 <span data-ttu-id="c9650-114">Windows güvenliği tarafından güvenliği sağlanmış bir istemciyi ve hizmeti gösterir.</span><span class="sxs-lookup"><span data-stu-id="c9650-114">Shows a client and service secured by Windows security.</span></span>  
  
 [<span data-ttu-id="c9650-115">Anonim İstemci ile Aktarım Güvenliği</span><span class="sxs-lookup"><span data-stu-id="c9650-115">Transport Security with an Anonymous Client</span></span>](transport-security-with-an-anonymous-client.md)  
 <span data-ttu-id="c9650-116">Bu senaryo gizlilik ve bütünlüğü sağlamak için taşıma güvenliği (HTTPS gibi) kullanır.</span><span class="sxs-lookup"><span data-stu-id="c9650-116">This scenario uses transport security (such as HTTPS) to ensure confidentiality and integrity.</span></span>  
  
 [<span data-ttu-id="c9650-117">Sertifika Kimlik Doğrulama ile Taşıma Güvenliği</span><span class="sxs-lookup"><span data-stu-id="c9650-117">Transport Security with Certificate Authentication</span></span>](transport-security-with-certificate-authentication.md)  
 <span data-ttu-id="c9650-118">Bir sertifika tarafından güvenliği sağlanmış bir istemciyi ve hizmeti gösterir.</span><span class="sxs-lookup"><span data-stu-id="c9650-118">Shows a client and service secured by a certificate.</span></span>  
  
 [<span data-ttu-id="c9650-119">Anonim İstemci ile İleti Güvenliği</span><span class="sxs-lookup"><span data-stu-id="c9650-119">Message Security with an Anonymous Client</span></span>](message-security-with-an-anonymous-client.md)  
 <span data-ttu-id="c9650-120">WCF ileti güvenliği tarafından güvenli hale getirilmiş bir istemciyi ve hizmeti gösterir.</span><span class="sxs-lookup"><span data-stu-id="c9650-120">Shows a client and service secured by WCF message security.</span></span>  
  
 [<span data-ttu-id="c9650-121">Kullaıcı Adı İstemcisi ile İleti Güvenliği</span><span class="sxs-lookup"><span data-stu-id="c9650-121">Message Security with a User Name Client</span></span>](message-security-with-a-user-name-client.md)  
 <span data-ttu-id="c9650-122">İstemci, istemcilerin bir etki alanı Kullanıcı adı ve parola kullanarak oturum açmasına izin veren bir Windows Forms uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="c9650-122">The client is a Windows Forms application that allows clients to log on using a domain user name and password.</span></span>  
  
 [<span data-ttu-id="c9650-123">Sertifika İstemcisi ile İleti Güvenliği</span><span class="sxs-lookup"><span data-stu-id="c9650-123">Message Security with a Certificate Client</span></span>](message-security-with-a-certificate-client.md)  
 <span data-ttu-id="c9650-124">Sunucularda sertifikalar vardır ve her bir istemcinin sertifikası vardır.</span><span class="sxs-lookup"><span data-stu-id="c9650-124">Servers have certificates, and each client has a certificate.</span></span> <span data-ttu-id="c9650-125">Aktarım Katmanı Güvenliği (TLS) anlaşması aracılığıyla bir güvenlik bağlamı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="c9650-125">A security context is established through Transport Layer Security (TLS) negotiation.</span></span>  
  
 [<span data-ttu-id="c9650-126">Windows İstemcisi ile İleti Güvenliği</span><span class="sxs-lookup"><span data-stu-id="c9650-126">Message Security with a Windows Client</span></span>](message-security-with-a-windows-client.md)  
 <span data-ttu-id="c9650-127">Sertifika istemcisinin bir çeşitlemesi.</span><span class="sxs-lookup"><span data-stu-id="c9650-127">A variation of the certificate client.</span></span> <span data-ttu-id="c9650-128">Sunucularda sertifikalar vardır ve her bir istemcinin sertifikası vardır.</span><span class="sxs-lookup"><span data-stu-id="c9650-128">Servers have certificates, and each client has a certificate.</span></span> <span data-ttu-id="c9650-129">TLS anlaşması ile bir güvenlik bağlamı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="c9650-129">A security context is established through TLS negotiation.</span></span>  
  
 [<span data-ttu-id="c9650-130">Windows İstemcisi ile Kimlik Bilgileri Görüşmesi Olmadan İleti Güvenliği</span><span class="sxs-lookup"><span data-stu-id="c9650-130">Message Security with a Windows Client without Credential Negotiation</span></span>](message-security-with-a-windows-client-without-credential-negotiation.md)  
 <span data-ttu-id="c9650-131">Kerberos etki alanı tarafından güvenliği sağlanmış bir istemciyi ve hizmeti gösterir.</span><span class="sxs-lookup"><span data-stu-id="c9650-131">Shows a client and service secured by a Kerberos domain.</span></span>  
  
 [<span data-ttu-id="c9650-132">Karşılıklı Sertifikalar ile İleti Güvenliği</span><span class="sxs-lookup"><span data-stu-id="c9650-132">Message Security with Mutual Certificates</span></span>](message-security-with-mutual-certificates.md)  
 <span data-ttu-id="c9650-133">Sunucularda sertifikalar vardır ve her bir istemcinin sertifikası vardır.</span><span class="sxs-lookup"><span data-stu-id="c9650-133">Servers have certificates, and each client has a certificate.</span></span> <span data-ttu-id="c9650-134">Sunucu sertifikası uygulamayla birlikte dağıtılır ve bant dışı kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c9650-134">The server certificate is distributed with the application and is available out of band.</span></span>  
  
 [<span data-ttu-id="c9650-135">Verilen Belirteçlerle İleti Güvenliği</span><span class="sxs-lookup"><span data-stu-id="c9650-135">Message Security with Issued Tokens</span></span>](message-security-with-issued-tokens.md)  
 <span data-ttu-id="c9650-136">Bağımsız etki alanları arasında güven kurulmasını sağlayan Federe güvenlik.</span><span class="sxs-lookup"><span data-stu-id="c9650-136">Federated security that enables the establishment of trust between independent domains.</span></span>  
  
 [<span data-ttu-id="c9650-137">Güvenilir Alt Sistem</span><span class="sxs-lookup"><span data-stu-id="c9650-137">Trusted Subsystem</span></span>](trusted-subsystem.md)  
 <span data-ttu-id="c9650-138">İstemci bir ağ üzerinde dağıtılan bir veya daha fazla Web hizmetine erişir.</span><span class="sxs-lookup"><span data-stu-id="c9650-138">A client accesses one or more Web services that are distributed across a network.</span></span> <span data-ttu-id="c9650-139">Web Hizmetleri, güvenli olması gereken ek kaynaklara (veritabanları veya diğer Web Hizmetleri gibi) erişir.</span><span class="sxs-lookup"><span data-stu-id="c9650-139">The Web services access additional resources (such as databases or other Web services) that must be secured.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="c9650-140">Başvuru</span><span class="sxs-lookup"><span data-stu-id="c9650-140">Reference</span></span>  

 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a><span data-ttu-id="c9650-141">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="c9650-141">Related Sections</span></span>  

 [<span data-ttu-id="c9650-142">Yetkilendirme</span><span class="sxs-lookup"><span data-stu-id="c9650-142">Authorization</span></span>](authorization-in-wcf.md)  
  
 [<span data-ttu-id="c9650-143">Güvenliğe genel bakış</span><span class="sxs-lookup"><span data-stu-id="c9650-143">Security Overview</span></span>](security-overview.md)  
  
 [<span data-ttu-id="c9650-144">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="c9650-144">Security</span></span>](security.md)  
  
 [<span data-ttu-id="c9650-145">Bağlamalar ve Güvenlik</span><span class="sxs-lookup"><span data-stu-id="c9650-145">Bindings and Security</span></span>](bindings-and-security.md)  
  
 [<span data-ttu-id="c9650-146">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="c9650-146">Securing Services and Clients</span></span>](securing-services-and-clients.md)  
  
 [<span data-ttu-id="c9650-147">Kimlik Doğrulaması</span><span class="sxs-lookup"><span data-stu-id="c9650-147">Authentication</span></span>](authentication-in-wcf.md)  
  
 [<span data-ttu-id="c9650-148">Yetkilendirme</span><span class="sxs-lookup"><span data-stu-id="c9650-148">Authorization</span></span>](authorization-in-wcf.md)  
  
 [<span data-ttu-id="c9650-149">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="c9650-149">Federation and Issued Tokens</span></span>](federation-and-issued-tokens.md)  
  
 [<span data-ttu-id="c9650-150">Denetim</span><span class="sxs-lookup"><span data-stu-id="c9650-150">Auditing</span></span>](auditing-security-events.md)  
  
## <a name="see-also"></a><span data-ttu-id="c9650-151">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c9650-151">See also</span></span>

- [<span data-ttu-id="c9650-152">Güvenlik Kılavuzu ve En İyi Uygulamalar</span><span class="sxs-lookup"><span data-stu-id="c9650-152">Security Guidance and Best Practices</span></span>](security-guidance-and-best-practices.md)
- <span data-ttu-id="c9650-153">[Windows Server App Fabric için güvenlik modeli](/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="c9650-153">[Security Model for Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
