---
title: Özel Kimlik Bilgileri ve Kimlik Bilgileri Doğrulaması
ms.date: 03/30/2017
helpviewer_keywords:
- credentials [WCF], custom
- credentials [WCF]
- custom credentials [WCF]
- credential validation [WCF]
- credentials [WCF], validation
ms.assetid: da831bec-e281-4d44-b343-437b5eef688e
ms.openlocfilehash: 731131d4bc967aa3ae95eca1f9e9cbb2770f8f7c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54746576"
---
# <a name="custom-credential-and-credential-validation"></a><span data-ttu-id="46013-102">Özel Kimlik Bilgileri ve Kimlik Bilgileri Doğrulaması</span><span class="sxs-lookup"><span data-stu-id="46013-102">Custom Credential and Credential Validation</span></span>
<span data-ttu-id="46013-103">Güvenlik Windows Communication Foundation (WCF) hizmet ve istemcileri arasında kimlik bilgilerinin exchange temel alır.</span><span class="sxs-lookup"><span data-stu-id="46013-103">Security in Windows Communication Foundation (WCF) is based on the exchange of credentials between services and clients.</span></span> <span data-ttu-id="46013-104">Çoğu güvenlik senaryoları Windows (Kerberos), kullanıcı adı ve parolalar ve sertifikalar gibi ortak kimlik bilgisi türlerinin kullanarak karşılanabilir.</span><span class="sxs-lookup"><span data-stu-id="46013-104">Most security scenarios can be satisfied using common credential types, such as Windows (Kerberos), username and passwords, and certificates.</span></span> <span data-ttu-id="46013-105">Ancak, yeni bir kimlik bilgisi türü gerekiyorsa, bu bölümdeki konular, yeni türleri doğrulamak ve işlemek nasıl açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="46013-105">However, if a new type of credential is required, the topics in this section explain how to handle and validate new types.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="46013-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="46013-106">In This Section</span></span>  
 [<span data-ttu-id="46013-107">Nasıl yapılır: Özel bir sertifika Doğrulayıcı kullanan bir hizmet oluşturma</span><span class="sxs-lookup"><span data-stu-id="46013-107">How to: Create a Service that Employs a Custom Certificate Validator</span></span>](../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)  
 <span data-ttu-id="46013-108">WCF doğrulama devralarak özelleştirmek nasıl açıklar <xref:System.IdentityModel.Selectors.X509CertificateValidator> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="46013-108">Explains how to customize WCF validation by inheriting from the <xref:System.IdentityModel.Selectors.X509CertificateValidator> class.</span></span>  
  
 [<span data-ttu-id="46013-109">İzlenecek yol: Özel istemci ve hizmet kimlik bilgilerini oluşturma</span><span class="sxs-lookup"><span data-stu-id="46013-109">Walkthrough: Creating Custom Client and Service Credentials</span></span>](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)  
 <span data-ttu-id="46013-110">Nasıl genişleteceğinizi gösterir <xref:System.ServiceModel.Description.ClientCredentials> ve <xref:System.ServiceModel.Description.ServiceCredentials> sınıfları yeni uyum sağlamak için kimlik bilgisi türü.</span><span class="sxs-lookup"><span data-stu-id="46013-110">Demonstrates how to extend the <xref:System.ServiceModel.Description.ClientCredentials> and <xref:System.ServiceModel.Description.ServiceCredentials> classes to accommodate new credential types.</span></span> <span data-ttu-id="46013-111">Özel kimlik bilgisi türlerinin oluşturulmasını sağlayan konuları bir dizi içinde ilk budur.</span><span class="sxs-lookup"><span data-stu-id="46013-111">This is first in a series of topics that enable creation of custom credential types.</span></span>  
  
 [<span data-ttu-id="46013-112">Nasıl yapılır: Özel güvenlik belirteci sağlayıcı oluşturma</span><span class="sxs-lookup"><span data-stu-id="46013-112">How to: Create a Custom Security Token Provider</span></span>](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md)  
 <span data-ttu-id="46013-113">Yeni kimlik bilgisi türlerinin işlemek ve kimlik bilgisi için yeni belirteçleri döndürmek için bir güvenlik belirteci sağlayıcı oluşturma açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="46013-113">Explains how to create a security token provider to handle new credential types and return new tokens for the credential.</span></span> <span data-ttu-id="46013-114">Serinin ikinci bölümüne budur.</span><span class="sxs-lookup"><span data-stu-id="46013-114">This is the second topic in the series.</span></span>  
  
 [<span data-ttu-id="46013-115">Nasıl yapılır: Özel güvenlik belirteci kimlik doğrulayıcı oluşturma</span><span class="sxs-lookup"><span data-stu-id="46013-115">How to: Create a Custom Security Token Authenticator</span></span>](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md)  
 <span data-ttu-id="46013-116">Yeni bir kimlik bilgisi türü kimlik doğrulaması için özel bir kimlik doğrulayıcı oluşturma açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="46013-116">Explains how to create a custom authenticator to authenticate a new credential type.</span></span> <span data-ttu-id="46013-117">Bu, serideki üçüncü konudur.</span><span class="sxs-lookup"><span data-stu-id="46013-117">This is the third topic in the series.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="46013-118">Başvuru</span><span class="sxs-lookup"><span data-stu-id="46013-118">Reference</span></span>  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.IdentityModel.Policy>  
  
 <xref:System.IdentityModel.Tokens>  
  
 <xref:System.IdentityModel.Selectors>  
  
 <xref:System.IdentityModel.Selectors.X509CertificateValidator>  
  
 <xref:System.ServiceModel.Description.ClientCredentials>  
  
 <xref:System.ServiceModel.Description.ServiceCredentials>  
  
## <a name="related-sections"></a><span data-ttu-id="46013-119">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="46013-119">Related Sections</span></span>  
 [<span data-ttu-id="46013-120">Kimlik Doğrulaması</span><span class="sxs-lookup"><span data-stu-id="46013-120">Authentication</span></span>](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)  
  
 [<span data-ttu-id="46013-121">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="46013-121">Federation and Issued Tokens</span></span>](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
  
 [<span data-ttu-id="46013-122">Yetkilendirme</span><span class="sxs-lookup"><span data-stu-id="46013-122">Authorization</span></span>](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
  
## <a name="see-also"></a><span data-ttu-id="46013-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="46013-123">See also</span></span>
- [<span data-ttu-id="46013-124">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="46013-124">Security</span></span>](../../../../docs/framework/wcf/feature-details/security.md)
