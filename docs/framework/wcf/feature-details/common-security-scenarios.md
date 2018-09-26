---
title: Ortak Güvenlik Senaryoları
ms.date: 03/30/2017
helpviewer_keywords:
- security [WCF], scenarios
ms.assetid: 201923b5-5162-4a8a-8d4c-e7bd242748d5
author: BrucePerlerMS
ms.openlocfilehash: 081518fb1b3eb1f66c772cd401c19c0eb523d32a
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47111262"
---
# <a name="common-security-scenarios"></a><span data-ttu-id="67d18-102">Ortak Güvenlik Senaryoları</span><span class="sxs-lookup"><span data-stu-id="67d18-102">Common Security Scenarios</span></span>
<span data-ttu-id="67d18-103">Bu bölümdeki konular, katalog hizmeti güvenlik yapılandırmalarını ve olası istemci bir numarası.</span><span class="sxs-lookup"><span data-stu-id="67d18-103">The topics in this section catalog a number of possible client and service security configurations.</span></span> <span data-ttu-id="67d18-104">Yapılandırmaları bir dizi etkene göre değişir.</span><span class="sxs-lookup"><span data-stu-id="67d18-104">Configurations vary according to a number of factors.</span></span> <span data-ttu-id="67d18-105">Örneğin, bir hizmet veya istemci intranet üzerinde olup veya olup Windows ya da (Örneğin HTTPS) aktarım güvenliği sağlanır.</span><span class="sxs-lookup"><span data-stu-id="67d18-105">For example, whether a service or client is on an intranet, or whether the security is provided by Windows or transport (such as HTTPS).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="67d18-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="67d18-106">In This Section</span></span>  
 [<span data-ttu-id="67d18-107">İnternet Güvenli Olmayan Hizmet ve İstemci</span><span class="sxs-lookup"><span data-stu-id="67d18-107">Internet Unsecured Client and Service</span></span>](../../../../docs/framework/wcf/feature-details/internet-unsecured-client-and-service.md)  
 <span data-ttu-id="67d18-108">Genel, güvenli olmayan bir istemci ve hizmet örneği.</span><span class="sxs-lookup"><span data-stu-id="67d18-108">An example of a public, unsecured client and service.</span></span>  
  
 [<span data-ttu-id="67d18-109">İntranet Güvenli Olmayan Hizmet ve İstemci</span><span class="sxs-lookup"><span data-stu-id="67d18-109">Intranet Unsecured Client and Service</span></span>](../../../../docs/framework/wcf/feature-details/intranet-unsecured-client-and-service.md)  
 <span data-ttu-id="67d18-110">WCF uygulaması için özel bir güvenli ağ üzerinden bilgi sağlamak için temel bir Windows Communication Foundation (WCF) hizmeti geliştirdi.</span><span class="sxs-lookup"><span data-stu-id="67d18-110">A basic Windows Communication Foundation (WCF) service developed to provide information on a secure private network to a WCF application.</span></span>  
  
 [<span data-ttu-id="67d18-111">Temel Kimlik Doğrulama ile Aktarım Güvenliği</span><span class="sxs-lookup"><span data-stu-id="67d18-111">Transport Security with Basic Authentication</span></span>](../../../../docs/framework/wcf/feature-details/transport-security-with-basic-authentication.md)  
 <span data-ttu-id="67d18-112">Uygulamaya özel kimlik doğrulaması kullanarak oturum etmesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="67d18-112">The application allows clients to log on using custom authentication.</span></span>  
  
 [<span data-ttu-id="67d18-113">Windows Kimlik Doğrulaması ile Aktarım Güvenliği</span><span class="sxs-lookup"><span data-stu-id="67d18-113">Transport Security with Windows Authentication</span></span>](../../../../docs/framework/wcf/feature-details/transport-security-with-windows-authentication.md)  
 <span data-ttu-id="67d18-114">Bir istemci ve hizmet Windows güvenlik güvenli gösterir.</span><span class="sxs-lookup"><span data-stu-id="67d18-114">Shows a client and service secured by Windows security.</span></span>  
  
 [<span data-ttu-id="67d18-115">Anonim İstemci ile Aktarım Güvenliği</span><span class="sxs-lookup"><span data-stu-id="67d18-115">Transport Security with an Anonymous Client</span></span>](../../../../docs/framework/wcf/feature-details/transport-security-with-an-anonymous-client.md)  
 <span data-ttu-id="67d18-116">Bu senaryo, gizliliği ve bütünlüğü sağlamak için Aktarım güvenliği (Örneğin HTTPS) kullanır.</span><span class="sxs-lookup"><span data-stu-id="67d18-116">This scenario uses transport security (such as HTTPS) to ensure confidentiality and integrity.</span></span>  
  
 [<span data-ttu-id="67d18-117">Sertifika Kimlik Doğrulama ile Aktarım Güvenliği</span><span class="sxs-lookup"><span data-stu-id="67d18-117">Transport Security with Certificate Authentication</span></span>](../../../../docs/framework/wcf/feature-details/transport-security-with-certificate-authentication.md)  
 <span data-ttu-id="67d18-118">Bir istemci ve hizmet güvenliği bir sertifika ile sağlanan gösterir.</span><span class="sxs-lookup"><span data-stu-id="67d18-118">Shows a client and service secured by a certificate.</span></span>  
  
 [<span data-ttu-id="67d18-119">Anonim İstemci ile İleti Güvenliği</span><span class="sxs-lookup"><span data-stu-id="67d18-119">Message Security with an Anonymous Client</span></span>](../../../../docs/framework/wcf/feature-details/message-security-with-an-anonymous-client.md)  
 <span data-ttu-id="67d18-120">Bir istemci ve hizmet tarafından WCF ileti güvenliğini güvenli gösterir.</span><span class="sxs-lookup"><span data-stu-id="67d18-120">Shows a client and service secured by WCF message security.</span></span>  
  
 [<span data-ttu-id="67d18-121">Kullanıcı Adı İstemcisi ile İleti Güvenliği</span><span class="sxs-lookup"><span data-stu-id="67d18-121">Message Security with a User Name Client</span></span>](../../../../docs/framework/wcf/feature-details/message-security-with-a-user-name-client.md)  
 <span data-ttu-id="67d18-122">İstemci istemciler, bir etki alanı kullanıcı adı ve parola kullanarak oturum açmasına izin veren bir Windows Forms uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="67d18-122">The client is a Windows Forms application that allows clients to log on using a domain user name and password.</span></span>  
  
 [<span data-ttu-id="67d18-123">Sertifika İstemcisi ile İleti Güvenliği</span><span class="sxs-lookup"><span data-stu-id="67d18-123">Message Security with a Certificate Client</span></span>](../../../../docs/framework/wcf/feature-details/message-security-with-a-certificate-client.md)  
 <span data-ttu-id="67d18-124">Sunucuları sertifikaları ve her bir istemciye bir sertifika gerekir.</span><span class="sxs-lookup"><span data-stu-id="67d18-124">Servers have certificates, and each client has a certificate.</span></span> <span data-ttu-id="67d18-125">Bir güvenlik bağlamı anlaşması ile Aktarım Katmanı Güvenliği (TLS) oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="67d18-125">A security context is established through Transport Layer Security (TLS) negotiation.</span></span>  
  
 [<span data-ttu-id="67d18-126">Windows İstemcisi ile İleti Güvenliği</span><span class="sxs-lookup"><span data-stu-id="67d18-126">Message Security with a Windows Client</span></span>](../../../../docs/framework/wcf/feature-details/message-security-with-a-windows-client.md)  
 <span data-ttu-id="67d18-127">Sertifika istemcisi çeşitlemesi.</span><span class="sxs-lookup"><span data-stu-id="67d18-127">A variation of the certificate client.</span></span> <span data-ttu-id="67d18-128">Sunucuları sertifikaları ve her bir istemciye bir sertifika gerekir.</span><span class="sxs-lookup"><span data-stu-id="67d18-128">Servers have certificates, and each client has a certificate.</span></span> <span data-ttu-id="67d18-129">Bir güvenlik bağlamı TLS anlaşması ile oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="67d18-129">A security context is established through TLS negotiation.</span></span>  
  
 [<span data-ttu-id="67d18-130">Windows İstemcisi ile Kimlik Bilgileri Görüşmesi Olmadan İleti Güvenliği</span><span class="sxs-lookup"><span data-stu-id="67d18-130">Message Security with a Windows Client without Credential Negotiation</span></span>](../../../../docs/framework/wcf/feature-details/message-security-with-a-windows-client-without-credential-negotiation.md)  
 <span data-ttu-id="67d18-131">Bir istemci ve hizmet güvenli bir Kerberos etki alanı tarafından gösterilir.</span><span class="sxs-lookup"><span data-stu-id="67d18-131">Shows a client and service secured by a Kerberos domain.</span></span>  
  
 [<span data-ttu-id="67d18-132">Karşılıklı Sertifikalar ile İleti Güvenliği</span><span class="sxs-lookup"><span data-stu-id="67d18-132">Message Security with Mutual Certificates</span></span>](../../../../docs/framework/wcf/feature-details/message-security-with-mutual-certificates.md)  
 <span data-ttu-id="67d18-133">Sunucuları sertifikaları ve her bir istemciye bir sertifika gerekir.</span><span class="sxs-lookup"><span data-stu-id="67d18-133">Servers have certificates, and each client has a certificate.</span></span> <span data-ttu-id="67d18-134">Sunucu sertifikası ile uygulama dağıtılır ve bant dışı kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="67d18-134">The server certificate is distributed with the application and is available out of band.</span></span>  
  
 [<span data-ttu-id="67d18-135">Verilen Belirteçlerle İleti Güvenliği</span><span class="sxs-lookup"><span data-stu-id="67d18-135">Message Security with Issued Tokens</span></span>](../../../../docs/framework/wcf/feature-details/message-security-with-issued-tokens.md)  
 <span data-ttu-id="67d18-136">Bağımsız bir etki alanı arasında güven kurulması sağlayan birleşik güvenliği.</span><span class="sxs-lookup"><span data-stu-id="67d18-136">Federated security that enables the establishment of trust between independent domains.</span></span>  
  
 [<span data-ttu-id="67d18-137">Güvenilir Alt Sistem</span><span class="sxs-lookup"><span data-stu-id="67d18-137">Trusted Subsystem</span></span>](../../../../docs/framework/wcf/feature-details/trusted-subsystem.md)  
 <span data-ttu-id="67d18-138">Bir istemci, bir ağ üzerinden dağıtılan bir veya daha fazla Web Hizmetleri erişir.</span><span class="sxs-lookup"><span data-stu-id="67d18-138">A client accesses one or more Web services that are distributed across a network.</span></span> <span data-ttu-id="67d18-139">Web Hizmetleri, korunması gereken ek kaynakları (örneğin, veritabanları veya diğer Web hizmetlerini) erişin.</span><span class="sxs-lookup"><span data-stu-id="67d18-139">The Web services access additional resources (such as databases or other Web services) that must be secured.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="67d18-140">Başvuru</span><span class="sxs-lookup"><span data-stu-id="67d18-140">Reference</span></span>  
 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a><span data-ttu-id="67d18-141">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="67d18-141">Related Sections</span></span>  
 [<span data-ttu-id="67d18-142">Yetkilendirme</span><span class="sxs-lookup"><span data-stu-id="67d18-142">Authorization</span></span>](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
  
 [<span data-ttu-id="67d18-143">Güvenliğe Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="67d18-143">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
  
 [<span data-ttu-id="67d18-144">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="67d18-144">Security</span></span>](../../../../docs/framework/wcf/feature-details/security.md)  
  
 [<span data-ttu-id="67d18-145">Bağlamalar ve Güvenlik</span><span class="sxs-lookup"><span data-stu-id="67d18-145">Bindings and Security</span></span>](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)  
  
 [<span data-ttu-id="67d18-146">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="67d18-146">Securing Services and Clients</span></span>](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
  
 [<span data-ttu-id="67d18-147">Kimlik Doğrulaması</span><span class="sxs-lookup"><span data-stu-id="67d18-147">Authentication</span></span>](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)  
  
 [<span data-ttu-id="67d18-148">Yetkilendirme</span><span class="sxs-lookup"><span data-stu-id="67d18-148">Authorization</span></span>](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
  
 [<span data-ttu-id="67d18-149">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="67d18-149">Federation and Issued Tokens</span></span>](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
  
 [<span data-ttu-id="67d18-150">Denetim</span><span class="sxs-lookup"><span data-stu-id="67d18-150">Auditing</span></span>](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)  
  
## <a name="see-also"></a><span data-ttu-id="67d18-151">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="67d18-151">See Also</span></span>  
 [<span data-ttu-id="67d18-152">Güvenlik Kılavuzu ve En İyi Uygulamalar</span><span class="sxs-lookup"><span data-stu-id="67d18-152">Security Guidance and Best Practices</span></span>](../../../../docs/framework/wcf/feature-details/security-guidance-and-best-practices.md)  
 [<span data-ttu-id="67d18-153">Windows Server AppFabric için güvenlik modeli</span><span class="sxs-lookup"><span data-stu-id="67d18-153">Security Model for Windows Server App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
