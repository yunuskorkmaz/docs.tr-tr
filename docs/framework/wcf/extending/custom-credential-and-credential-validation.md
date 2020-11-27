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
ms.openlocfilehash: 5f2909bb088a5f3d3203fe3c9e24b2df3450aa3f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96257834"
---
# <a name="custom-credential-and-credential-validation"></a><span data-ttu-id="c6aa4-102">Özel Kimlik Bilgileri ve Kimlik Bilgileri Doğrulaması</span><span class="sxs-lookup"><span data-stu-id="c6aa4-102">Custom Credential and Credential Validation</span></span>

<span data-ttu-id="c6aa4-103">Windows Communication Foundation (WCF) güvenliği, hizmetler ve istemciler arasındaki kimlik bilgilerinin değişimini temel alır.</span><span class="sxs-lookup"><span data-stu-id="c6aa4-103">Security in Windows Communication Foundation (WCF) is based on the exchange of credentials between services and clients.</span></span> <span data-ttu-id="c6aa4-104">Çoğu güvenlik senaryosu Windows (Kerberos), Kullanıcı adı ve parolalar ve sertifikalar gibi ortak kimlik bilgisi türleri kullanılarak karşılanabilir.</span><span class="sxs-lookup"><span data-stu-id="c6aa4-104">Most security scenarios can be satisfied using common credential types, such as Windows (Kerberos), username and passwords, and certificates.</span></span> <span data-ttu-id="c6aa4-105">Ancak, yeni bir kimlik bilgisi türü gerekliyse, bu bölümdeki konular yeni türlerin nasıl işleneceğini ve doğrulanacağını açıklamaktadır.</span><span class="sxs-lookup"><span data-stu-id="c6aa4-105">However, if a new type of credential is required, the topics in this section explain how to handle and validate new types.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c6aa4-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="c6aa4-106">In This Section</span></span>  

 [<span data-ttu-id="c6aa4-107">Nasıl yapılır: Özel Bir Sertifika Doğrulayıcı Kullanan Bir Hizmet Oluşturma</span><span class="sxs-lookup"><span data-stu-id="c6aa4-107">How to: Create a Service that Employs a Custom Certificate Validator</span></span>](how-to-create-a-service-that-employs-a-custom-certificate-validator.md)  
 <span data-ttu-id="c6aa4-108">Sınıfından devralarak WCF doğrulamasının nasıl özelleştirileceğini açıklar <xref:System.IdentityModel.Selectors.X509CertificateValidator> .</span><span class="sxs-lookup"><span data-stu-id="c6aa4-108">Explains how to customize WCF validation by inheriting from the <xref:System.IdentityModel.Selectors.X509CertificateValidator> class.</span></span>  
  
 [<span data-ttu-id="c6aa4-109">İzlenecek yol: Özel İstemci ve Hizmet Kimlik Bilgileri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="c6aa4-109">Walkthrough: Creating Custom Client and Service Credentials</span></span>](walkthrough-creating-custom-client-and-service-credentials.md)  
 <span data-ttu-id="c6aa4-110"><xref:System.ServiceModel.Description.ClientCredentials>Ve <xref:System.ServiceModel.Description.ServiceCredentials> sınıflarının yeni kimlik bilgisi türlerini kapsayacak şekilde nasıl genişletileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="c6aa4-110">Demonstrates how to extend the <xref:System.ServiceModel.Description.ClientCredentials> and <xref:System.ServiceModel.Description.ServiceCredentials> classes to accommodate new credential types.</span></span> <span data-ttu-id="c6aa4-111">Bu, ilk olarak özel kimlik bilgisi türlerinin oluşturulmasını sağlayan bir dizi konuda yer alan bir konu sayısıdır.</span><span class="sxs-lookup"><span data-stu-id="c6aa4-111">This is first in a series of topics that enable creation of custom credential types.</span></span>  
  
 [<span data-ttu-id="c6aa4-112">Nasıl yapılır: Özel Güvenlik Belirteci Sağlayıcı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="c6aa4-112">How to: Create a Custom Security Token Provider</span></span>](how-to-create-a-custom-security-token-provider.md)  
 <span data-ttu-id="c6aa4-113">Yeni kimlik bilgisi türlerini işlemek ve kimlik bilgileri için yeni belirteçleri döndürmek üzere bir güvenlik belirteci sağlayıcısının nasıl oluşturulacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="c6aa4-113">Explains how to create a security token provider to handle new credential types and return new tokens for the credential.</span></span> <span data-ttu-id="c6aa4-114">Bu, serideki ikinci konudur.</span><span class="sxs-lookup"><span data-stu-id="c6aa4-114">This is the second topic in the series.</span></span>  
  
 [<span data-ttu-id="c6aa4-115">Nasıl yapılır: Özel Güvenlik Belirteci Kimlik Doğrulayıcı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="c6aa4-115">How to: Create a Custom Security Token Authenticator</span></span>](how-to-create-a-custom-security-token-authenticator.md)  
 <span data-ttu-id="c6aa4-116">Yeni bir kimlik bilgisi türünün kimliğini doğrulamak için özel bir Authenticator oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="c6aa4-116">Explains how to create a custom authenticator to authenticate a new credential type.</span></span> <span data-ttu-id="c6aa4-117">Bu, serideki üçüncü konudur.</span><span class="sxs-lookup"><span data-stu-id="c6aa4-117">This is the third topic in the series.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="c6aa4-118">Başvuru</span><span class="sxs-lookup"><span data-stu-id="c6aa4-118">Reference</span></span>  

 <xref:System.ServiceModel.Security>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.IdentityModel.Policy>  
  
 <xref:System.IdentityModel.Tokens>  
  
 <xref:System.IdentityModel.Selectors>  
  
 <xref:System.IdentityModel.Selectors.X509CertificateValidator>  
  
 <xref:System.ServiceModel.Description.ClientCredentials>  
  
 <xref:System.ServiceModel.Description.ServiceCredentials>  
  
## <a name="related-sections"></a><span data-ttu-id="c6aa4-119">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="c6aa4-119">Related Sections</span></span>  

 [<span data-ttu-id="c6aa4-120">Kimlik Doğrulaması</span><span class="sxs-lookup"><span data-stu-id="c6aa4-120">Authentication</span></span>](../feature-details/authentication-in-wcf.md)  
  
 [<span data-ttu-id="c6aa4-121">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="c6aa4-121">Federation and Issued Tokens</span></span>](../feature-details/federation-and-issued-tokens.md)  
  
 [<span data-ttu-id="c6aa4-122">Yetkilendirme</span><span class="sxs-lookup"><span data-stu-id="c6aa4-122">Authorization</span></span>](../feature-details/authorization-in-wcf.md)  
  
## <a name="see-also"></a><span data-ttu-id="c6aa4-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c6aa4-123">See also</span></span>

- [<span data-ttu-id="c6aa4-124">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="c6aa4-124">Security</span></span>](../feature-details/security.md)
