---
description: 'Daha fazla bilgi edinin: güvenliği genişletme'
title: Güvenliği Genişletme
ms.date: 03/30/2017
helpviewer_keywords:
- security [WCF], extending
ms.assetid: a015a040-9fdf-4147-9ea9-f83b570be1d4
ms.openlocfilehash: 8dd514e16106ac5cdae072d92c7de66cefd39fe4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99685731"
---
# <a name="extending-security"></a><span data-ttu-id="314ad-103">Güvenliği Genişletme</span><span class="sxs-lookup"><span data-stu-id="314ad-103">Extending Security</span></span>

<span data-ttu-id="314ad-104">Yeni talep türlerini ve özel belirteçleri barındırmak için Windows Communication Foundation (WCF) güvenlik altyapısını genişletebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="314ad-104">To accommodate new claim types and custom tokens, you can extend the security infrastructure of Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="314ad-105">Bu bölümdeki konular, bunun nasıl yapıldığını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="314ad-105">The topics in this section show you how this is done.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="314ad-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="314ad-106">In This Section</span></span>  
  
 [<span data-ttu-id="314ad-107">Özel Kimlik Bilgileri ve Kimlik Bilgileri Doğrulaması</span><span class="sxs-lookup"><span data-stu-id="314ad-107">Custom Credential and Credential Validation</span></span>](custom-credential-and-credential-validation.md)  
 <span data-ttu-id="314ad-108">Özel kimlik bilgileri doğrulanırken kimlik modelinin nasıl kullanıldığını açıklar.</span><span class="sxs-lookup"><span data-stu-id="314ad-108">Explains how the Identity Model is used when validating custom credentials.</span></span>  
  
 [<span data-ttu-id="314ad-109">Özel Belirteçler</span><span class="sxs-lookup"><span data-stu-id="314ad-109">Custom Tokens</span></span>](custom-tokens.md)  
 <span data-ttu-id="314ad-110">Bir güvenlik belirteci hizmetinden (STS) verilen belirteçler genellikle SAML belirteçleridir.</span><span class="sxs-lookup"><span data-stu-id="314ad-110">Issued tokens from a Security Token Service (STS) are typically SAML tokens.</span></span> <span data-ttu-id="314ad-111">Bu konu başlığı altında, özel bir belirteç türünün nasıl oluşturulacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="314ad-111">This topic explains how to create a custom token type.</span></span>  
  
 [<span data-ttu-id="314ad-112">Özel Yetkilendirme</span><span class="sxs-lookup"><span data-stu-id="314ad-112">Custom Authorization</span></span>](custom-authorization.md)  
 <span data-ttu-id="314ad-113">Özel yetkilendirmenin nasıl uygulanacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="314ad-113">Explains how to implement custom authorization.</span></span>  
  
 [<span data-ttu-id="314ad-114">Bir Hizmetin Kimliğini Kimlik Doğrulama için Geçersiz Kılma</span><span class="sxs-lookup"><span data-stu-id="314ad-114">Overriding the Identity of a Service for Authentication</span></span>](overriding-the-identity-of-a-service-for-authentication.md)  
 <span data-ttu-id="314ad-115">Kimlik doğrulaması için bir hizmetin kimliğini geçersiz kılmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="314ad-115">Describes how to override the identity of a service for authentication.</span></span>  
  
 [<span data-ttu-id="314ad-116">Nasıl yapılır: Özel İstemci Kimliği Doğrulayıcı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="314ad-116">How to: Create a Custom Client Identity Verifier</span></span>](how-to-create-a-custom-client-identity-verifier.md)  
 <span data-ttu-id="314ad-117">Özel bir uç nokta kimliğinin nasıl doğrulandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="314ad-117">Demonstrates how to validate a custom endpoint identity.</span></span>  
  
 [<span data-ttu-id="314ad-118">Nasıl yapılır: İmzalama ve Şifreleme için Ayrı X.509 Sertifikaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="314ad-118">How to: Use Separate X.509 Certificates for Signing and Encryption</span></span>](how-to-use-separate-x-509-certificates-for-signing-and-encryption.md)  
 <span data-ttu-id="314ad-119">İletiler genellikle tek bir sertifikayla imzalanıp şifrelenir.</span><span class="sxs-lookup"><span data-stu-id="314ad-119">Messages are typically signed and encrypted with a single certificate.</span></span> <span data-ttu-id="314ad-120">Bu konuda, gerektiğinde iki sertifikanın nasıl kullanılabileceği açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="314ad-120">This topic explains how two certificates can be used, when required.</span></span>  
  
 [<span data-ttu-id="314ad-121">Nasıl yapılır: Bir X.509 Sertifikasının Şifreleme Sağlayıcısını Değiştirme</span><span class="sxs-lookup"><span data-stu-id="314ad-121">How to: Change the Cryptographic Provider for an X.509 Certificate's Private Key</span></span>](change-cryptographic-provider-x509-certificate-private-key.md)  
 <span data-ttu-id="314ad-122">X. 509.440 sertifikasının özel anahtarını sağlamak için kullanılan şifreleme sağlayıcısının ve sağlayıcının Windows Communication Foundation (WCF) çerçevesiyle nasıl tümleştirileceği açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="314ad-122">Explains how to change the cryptographic provider used to provide an X.509 certificate's private key and how to integrate the provider into the Windows Communication Foundation (WCF) framework.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="314ad-123">Başvuru</span><span class="sxs-lookup"><span data-stu-id="314ad-123">Reference</span></span>  

 <xref:System.ServiceModel.ServiceAuthorizationManager>  
  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.IdentityModel.Policy>  
  
 <xref:System.IdentityModel.Tokens>  
  
 <xref:System.IdentityModel.Selectors>  
  
## <a name="related-sections"></a><span data-ttu-id="314ad-124">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="314ad-124">Related Sections</span></span>  

 [<span data-ttu-id="314ad-125">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="314ad-125">Security</span></span>](../feature-details/security.md)  
  
 [<span data-ttu-id="314ad-126">Temel WCF Programlama</span><span class="sxs-lookup"><span data-stu-id="314ad-126">Basic WCF Programming</span></span>](../basic-wcf-programming.md)  
  
## <a name="see-also"></a><span data-ttu-id="314ad-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="314ad-127">See also</span></span>

- [<span data-ttu-id="314ad-128">Güvenliğe genel bakış</span><span class="sxs-lookup"><span data-stu-id="314ad-128">Security Overview</span></span>](../feature-details/security-overview.md)
