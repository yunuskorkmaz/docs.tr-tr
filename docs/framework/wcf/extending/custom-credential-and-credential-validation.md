---
title: "Özel Kimlik Bilgileri ve Kimlik Bilgileri Doğrulaması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- credentials [WCF], custom
- credentials [WCF]
- custom credentials [WCF]
- credential validation [WCF]
- credentials [WCF], validation
ms.assetid: da831bec-e281-4d44-b343-437b5eef688e
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 021a4e206a5abfb3508e8e548114de7e61dd2d04
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="custom-credential-and-credential-validation"></a><span data-ttu-id="5b1ef-102">Özel Kimlik Bilgileri ve Kimlik Bilgileri Doğrulaması</span><span class="sxs-lookup"><span data-stu-id="5b1ef-102">Custom Credential and Credential Validation</span></span>
<span data-ttu-id="5b1ef-103">Güvenlik [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] exchange Hizmetleri ve istemciler arasında kimlik bilgilerinin temel alır.</span><span class="sxs-lookup"><span data-stu-id="5b1ef-103">Security in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] is based on the exchange of credentials between services and clients.</span></span> <span data-ttu-id="5b1ef-104">Çoğu güvenlik senaryoları Windows (Kerberos), kullanıcı adı ve parolaları ve sertifikaları gibi ortak kimlik bilgisi türlerini kullanarak karşılanabilir.</span><span class="sxs-lookup"><span data-stu-id="5b1ef-104">Most security scenarios can be satisfied using common credential types, such as Windows (Kerberos), username and passwords, and certificates.</span></span> <span data-ttu-id="5b1ef-105">Yeni bir kimlik bilgisi türünü gerekliyse, ancak, bu bölümdeki konular, işlemek ve yeni türleri doğrulamak açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5b1ef-105">However, if a new type of credential is required, the topics in this section explain how to handle and validate new types.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5b1ef-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="5b1ef-106">In This Section</span></span>  
 [<span data-ttu-id="5b1ef-107">Nasıl yapılır: özel bir sertifika Doğrulayıcı kullanan bir hizmet oluşturma</span><span class="sxs-lookup"><span data-stu-id="5b1ef-107">How to: Create a Service that Employs a Custom Certificate Validator</span></span>](../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)  
 <span data-ttu-id="5b1ef-108">Nasıl özelleştirileceği açıklanır [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] içinden devralma tarafından doğrulama <xref:System.IdentityModel.Selectors.X509CertificateValidator> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="5b1ef-108">Explains how to customize [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] validation by inheriting from the <xref:System.IdentityModel.Selectors.X509CertificateValidator> class.</span></span>  
  
 [<span data-ttu-id="5b1ef-109">İzlenecek yol: Özel istemci ve hizmet kimlik bilgileri oluşturma</span><span class="sxs-lookup"><span data-stu-id="5b1ef-109">Walkthrough: Creating Custom Client and Service Credentials</span></span>](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)  
 <span data-ttu-id="5b1ef-110">Nasıl genişletileceğini gösterir <xref:System.ServiceModel.Description.ClientCredentials> ve <xref:System.ServiceModel.Description.ServiceCredentials> sınıfları yeni uyum sağlamak için kimlik bilgisi türü.</span><span class="sxs-lookup"><span data-stu-id="5b1ef-110">Demonstrates how to extend the <xref:System.ServiceModel.Description.ClientCredentials> and <xref:System.ServiceModel.Description.ServiceCredentials> classes to accommodate new credential types.</span></span> <span data-ttu-id="5b1ef-111">Bu özel kimlik bilgisi türlerinin oluşturulmasını sağlamak konuları serisinde ilktir.</span><span class="sxs-lookup"><span data-stu-id="5b1ef-111">This is first in a series of topics that enable creation of custom credential types.</span></span>  
  
 [<span data-ttu-id="5b1ef-112">Nasıl yapılır: özel güvenlik belirteci sağlayıcı oluşturma</span><span class="sxs-lookup"><span data-stu-id="5b1ef-112">How to: Create a Custom Security Token Provider</span></span>](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md)  
 <span data-ttu-id="5b1ef-113">Yeni kimlik bilgisi türlerinin işlemek ve kimlik bilgisi için yeni belirteçleri dönmek için bir güvenlik belirteci sağlayıcı oluşturma açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5b1ef-113">Explains how to create a security token provider to handle new credential types and return new tokens for the credential.</span></span> <span data-ttu-id="5b1ef-114">Bu serideki ikinci konudur.</span><span class="sxs-lookup"><span data-stu-id="5b1ef-114">This is the second topic in the series.</span></span>  
  
 [<span data-ttu-id="5b1ef-115">Nasıl yapılır: özel güvenlik belirteci kimlik doğrulayıcı oluşturma</span><span class="sxs-lookup"><span data-stu-id="5b1ef-115">How to: Create a Custom Security Token Authenticator</span></span>](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md)  
 <span data-ttu-id="5b1ef-116">Yeni bir kimlik bilgisi türü kimlik doğrulaması yapmak için özel bir kimlik doğrulayıcı oluşturma açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5b1ef-116">Explains how to create a custom authenticator to authenticate a new credential type.</span></span> <span data-ttu-id="5b1ef-117">Bu serideki üçüncü konudur.</span><span class="sxs-lookup"><span data-stu-id="5b1ef-117">This is the third topic in the series.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="5b1ef-118">Başvuru</span><span class="sxs-lookup"><span data-stu-id="5b1ef-118">Reference</span></span>  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.IdentityModel.Policy>  
  
 <xref:System.IdentityModel.Tokens>  
  
 <xref:System.IdentityModel.Selectors>  
  
 <xref:System.IdentityModel.Selectors.X509CertificateValidator>  
  
 <xref:System.ServiceModel.Description.ClientCredentials>  
  
 <xref:System.ServiceModel.Description.ServiceCredentials>  
  
## <a name="related-sections"></a><span data-ttu-id="5b1ef-119">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="5b1ef-119">Related Sections</span></span>  
 [<span data-ttu-id="5b1ef-120">Kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="5b1ef-120">Authentication</span></span>](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)  
  
 [<span data-ttu-id="5b1ef-121">Federasyon ve verilen belirteçler</span><span class="sxs-lookup"><span data-stu-id="5b1ef-121">Federation and Issued Tokens</span></span>](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
  
 [<span data-ttu-id="5b1ef-122">Yetkilendirme</span><span class="sxs-lookup"><span data-stu-id="5b1ef-122">Authorization</span></span>](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
  
## <a name="see-also"></a><span data-ttu-id="5b1ef-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5b1ef-123">See Also</span></span>  
 [<span data-ttu-id="5b1ef-124">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="5b1ef-124">Security</span></span>](../../../../docs/framework/wcf/feature-details/security.md)
