---
title: Güvenliği Genişletme
ms.date: 03/30/2017
helpviewer_keywords:
- security [WCF], extending
ms.assetid: a015a040-9fdf-4147-9ea9-f83b570be1d4
ms.openlocfilehash: 45216493a3afa23f24a085964a2c43e19b197d4b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797125"
---
# <a name="extending-security"></a><span data-ttu-id="31771-102">Güvenliği Genişletme</span><span class="sxs-lookup"><span data-stu-id="31771-102">Extending Security</span></span>
<span data-ttu-id="31771-103">Yeni talep türlerini ve özel belirteçleri barındırmak için Windows Communication Foundation (WCF) güvenlik altyapısını genişletebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="31771-103">To accommodate new claim types and custom tokens, you can extend the security infrastructure of Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="31771-104">Bu bölümdeki konular, bunun nasıl yapıldığını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="31771-104">The topics in this section show you how this is done.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="31771-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="31771-105">In This Section</span></span>  
  
 [<span data-ttu-id="31771-106">Özel Kimlik Bilgileri ve Kimlik Bilgileri Doğrulaması</span><span class="sxs-lookup"><span data-stu-id="31771-106">Custom Credential and Credential Validation</span></span>](custom-credential-and-credential-validation.md)  
 <span data-ttu-id="31771-107">Özel kimlik bilgileri doğrulanırken kimlik modelinin nasıl kullanıldığını açıklar.</span><span class="sxs-lookup"><span data-stu-id="31771-107">Explains how the Identity Model is used when validating custom credentials.</span></span>  
  
 [<span data-ttu-id="31771-108">Özel Belirteçler</span><span class="sxs-lookup"><span data-stu-id="31771-108">Custom Tokens</span></span>](custom-tokens.md)  
 <span data-ttu-id="31771-109">Bir güvenlik belirteci hizmetinden (STS) verilen belirteçler genellikle SAML belirteçleridir.</span><span class="sxs-lookup"><span data-stu-id="31771-109">Issued tokens from a Security Token Service (STS) are typically SAML tokens.</span></span> <span data-ttu-id="31771-110">Bu konu başlığı altında, özel bir belirteç türünün nasıl oluşturulacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="31771-110">This topic explains how to create a custom token type.</span></span>  
  
 [<span data-ttu-id="31771-111">Özel Yetkilendirme</span><span class="sxs-lookup"><span data-stu-id="31771-111">Custom Authorization</span></span>](custom-authorization.md)  
 <span data-ttu-id="31771-112">Özel yetkilendirmenin nasıl uygulanacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="31771-112">Explains how to implement custom authorization.</span></span>  
  
 [<span data-ttu-id="31771-113">Bir Hizmetin Kimliğini Kimlik Doğrulama için Geçersiz Kılma</span><span class="sxs-lookup"><span data-stu-id="31771-113">Overriding the Identity of a Service for Authentication</span></span>](overriding-the-identity-of-a-service-for-authentication.md)  
 <span data-ttu-id="31771-114">Kimlik doğrulaması için bir hizmetin kimliğini geçersiz kılmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="31771-114">Describes how to override the identity of a service for authentication.</span></span>  
  
 [<span data-ttu-id="31771-115">Nasıl yapılır: Özel bir Istemci Kimliği Doğrulayıcısı oluşturma</span><span class="sxs-lookup"><span data-stu-id="31771-115">How to: Create a Custom Client Identity Verifier</span></span>](how-to-create-a-custom-client-identity-verifier.md)  
 <span data-ttu-id="31771-116">Özel bir uç nokta kimliğinin nasıl doğrulandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="31771-116">Demonstrates how to validate a custom endpoint identity.</span></span>  
  
 [<span data-ttu-id="31771-117">Nasıl yapılır: Imzalama ve şifreleme için ayrı X. 509.440 sertifikaları kullanma</span><span class="sxs-lookup"><span data-stu-id="31771-117">How to: Use Separate X.509 Certificates for Signing and Encryption</span></span>](how-to-use-separate-x-509-certificates-for-signing-and-encryption.md)  
 <span data-ttu-id="31771-118">İletiler genellikle tek bir sertifikayla imzalanıp şifrelenir.</span><span class="sxs-lookup"><span data-stu-id="31771-118">Messages are typically signed and encrypted with a single certificate.</span></span> <span data-ttu-id="31771-119">Bu konuda, gerektiğinde iki sertifikanın nasıl kullanılabileceği açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="31771-119">This topic explains how two certificates can be used, when required.</span></span>  
  
 [<span data-ttu-id="31771-120">Nasıl yapılır: X. 509.440 sertifikasının özel anahtarı için şifreleme sağlayıcısını değiştirme</span><span class="sxs-lookup"><span data-stu-id="31771-120">How to: Change the Cryptographic Provider for an X.509 Certificate's Private Key</span></span>](change-cryptographic-provider-x509-certificate-private-key.md)  
 <span data-ttu-id="31771-121">X. 509.440 sertifikasının özel anahtarını sağlamak için kullanılan şifreleme sağlayıcısının ve sağlayıcının Windows Communication Foundation (WCF) çerçevesiyle nasıl tümleştirileceği açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="31771-121">Explains how to change the cryptographic provider used to provide an X.509 certificate's private key and how to integrate the provider into the Windows Communication Foundation (WCF) framework.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="31771-122">Başvuru</span><span class="sxs-lookup"><span data-stu-id="31771-122">Reference</span></span>  
 <xref:System.ServiceModel.ServiceAuthorizationManager>  
  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.IdentityModel.Policy>  
  
 <xref:System.IdentityModel.Tokens>  
  
 <xref:System.IdentityModel.Selectors>  
  
## <a name="related-sections"></a><span data-ttu-id="31771-123">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="31771-123">Related Sections</span></span>  
 [<span data-ttu-id="31771-124">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="31771-124">Security</span></span>](../feature-details/security.md)  
  
 [<span data-ttu-id="31771-125">Temel WCF Programlama</span><span class="sxs-lookup"><span data-stu-id="31771-125">Basic WCF Programming</span></span>](../basic-wcf-programming.md)  
  
## <a name="see-also"></a><span data-ttu-id="31771-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="31771-126">See also</span></span>

- [<span data-ttu-id="31771-127">Güvenliğe Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="31771-127">Security Overview</span></span>](../feature-details/security-overview.md)
