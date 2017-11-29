---
title: "Güvenliği Genişletme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: security [WCF], extending
ms.assetid: a015a040-9fdf-4147-9ea9-f83b570be1d4
caps.latest.revision: "23"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: a3950b156ede806382bbe4e013db5d94a8b20a23
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="extending-security"></a><span data-ttu-id="2abd8-102">Güvenliği Genişletme</span><span class="sxs-lookup"><span data-stu-id="2abd8-102">Extending Security</span></span>
<span data-ttu-id="2abd8-103">Yeni talep türlerini ve özel belirteçler uyum sağlamak için güvenlik altyapısı genişletebilirsiniz [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2abd8-103">To accommodate new claim types and custom tokens, you can extend the security infrastructure of [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span></span> <span data-ttu-id="2abd8-104">Bu bölümdeki konular, bunun nasıl yapılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2abd8-104">The topics in this section show you how this is done.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2abd8-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="2abd8-105">In This Section</span></span>  
 [<span data-ttu-id="2abd8-106">Güvenlik mimarisi</span><span class="sxs-lookup"><span data-stu-id="2abd8-106">Security Architecture</span></span>](http://msdn.microsoft.com/en-us/16593476-d36a-408d-808c-ae6fd483e28f)  
 <span data-ttu-id="2abd8-107">Mimarisi anlatılmaktadır [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] güvenlik sistemi.</span><span class="sxs-lookup"><span data-stu-id="2abd8-107">Walks through the architecture of the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] security system.</span></span>  
  
 [<span data-ttu-id="2abd8-108">Özel kimlik bilgileri ve kimlik bilgileri doğrulaması</span><span class="sxs-lookup"><span data-stu-id="2abd8-108">Custom Credential and Credential Validation</span></span>](../../../../docs/framework/wcf/extending/custom-credential-and-credential-validation.md)  
 <span data-ttu-id="2abd8-109">Özel kimlik doğrulama sırasında kimlik modeli nasıl kullanıldığını açıklar.</span><span class="sxs-lookup"><span data-stu-id="2abd8-109">Explains how the Identity Model is used when validating custom credentials.</span></span>  
  
 [<span data-ttu-id="2abd8-110">Özel belirteçler</span><span class="sxs-lookup"><span data-stu-id="2abd8-110">Custom Tokens</span></span>](../../../../docs/framework/wcf/extending/custom-tokens.md)  
 <span data-ttu-id="2abd8-111">Verilen belirteçler bir güvenlik belirteci hizmeti (STS) normal SAML belirteçleri uygulanır.</span><span class="sxs-lookup"><span data-stu-id="2abd8-111">Issued tokens from a Security Token Service (STS) are typically SAML tokens.</span></span> <span data-ttu-id="2abd8-112">Bu konuda bir özel belirteç türünün nasıl oluşturulacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2abd8-112">This topic explains how to create a custom token type.</span></span>  
  
 [<span data-ttu-id="2abd8-113">Özel yetkilendirme</span><span class="sxs-lookup"><span data-stu-id="2abd8-113">Custom Authorization</span></span>](../../../../docs/framework/wcf/extending/custom-authorization.md)  
 <span data-ttu-id="2abd8-114">Özel yetkilendirme uygulamak açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2abd8-114">Explains how to implement custom authorization.</span></span>  
  
 [<span data-ttu-id="2abd8-115">Kimlik doğrulaması için bir hizmetin kimliğini geçersiz kılma</span><span class="sxs-lookup"><span data-stu-id="2abd8-115">Overriding the Identity of a Service for Authentication</span></span>](../../../../docs/framework/wcf/extending/overriding-the-identity-of-a-service-for-authentication.md)  
 <span data-ttu-id="2abd8-116">Kimlik doğrulaması için bir hizmetin kimliğini geçersiz kılmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="2abd8-116">Describes how to override the identity of a service for authentication.</span></span>  
  
 [<span data-ttu-id="2abd8-117">Nasıl yapılır: Özel İstemci Kimliği Doğrulayıcı oluşturma</span><span class="sxs-lookup"><span data-stu-id="2abd8-117">How to: Create a Custom Client Identity Verifier</span></span>](../../../../docs/framework/wcf/extending/how-to-create-a-custom-client-identity-verifier.md)  
 <span data-ttu-id="2abd8-118">Özel uç noktası kimlik doğrulamak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="2abd8-118">Demonstrates how to validate a custom endpoint identity.</span></span>  
  
 [<span data-ttu-id="2abd8-119">Nasıl yapılır: ayrı X.509 sertifikaları imzalamak için kullanın ve şifreleme</span><span class="sxs-lookup"><span data-stu-id="2abd8-119">How to: Use Separate X.509 Certificates for Signing and Encryption</span></span>](../../../../docs/framework/wcf/extending/how-to-use-separate-x-509-certificates-for-signing-and-encryption.md)  
 <span data-ttu-id="2abd8-120">İletiler genellikle imzalı ve tek bir sertifika ile şifrelenir.</span><span class="sxs-lookup"><span data-stu-id="2abd8-120">Messages are typically signed and encrypted with a single certificate.</span></span> <span data-ttu-id="2abd8-121">Bu konu nasıl iki sertifika açıklar, gerekli olduğunda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2abd8-121">This topic explains how two certificates can be used, when required.</span></span>  
  
 [<span data-ttu-id="2abd8-122">Nasıl yapılır: bir X.509 sertifikasının özel anahtar şifreleme sağlayıcısını değiştirme</span><span class="sxs-lookup"><span data-stu-id="2abd8-122">How to: Change the Cryptographic Provider for an X.509 Certificate's Private Key</span></span>](../../../../docs/framework/wcf/extending/change-cryptographic-provider-x509-certificate-private-key.md)  
 <span data-ttu-id="2abd8-123">Bir X.509 sertifikasının özel anahtarı sağlamak için kullanılan şifreleme sağlayıcısını değiştirme ve sağlayıcısını tümleştirme açıklanmaktadır [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] framework.</span><span class="sxs-lookup"><span data-stu-id="2abd8-123">Explains how to change the cryptographic provider used to provide an X.509 certificate's private key and how to integrate the provider into the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] framework.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="2abd8-124">Başvuru</span><span class="sxs-lookup"><span data-stu-id="2abd8-124">Reference</span></span>  
 <xref:System.ServiceModel.ServiceAuthorizationManager>  
  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.IdentityModel.Policy>  
  
 <xref:System.IdentityModel.Tokens>  
  
 <xref:System.IdentityModel.Selectors>  
  
## <a name="related-sections"></a><span data-ttu-id="2abd8-125">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="2abd8-125">Related Sections</span></span>  
 [<span data-ttu-id="2abd8-126">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="2abd8-126">Security</span></span>](../../../../docs/framework/wcf/feature-details/security.md)  
  
 [<span data-ttu-id="2abd8-127">Temel WCF programlama</span><span class="sxs-lookup"><span data-stu-id="2abd8-127">Basic WCF Programming</span></span>](../../../../docs/framework/wcf/basic-wcf-programming.md)  
  
## <a name="see-also"></a><span data-ttu-id="2abd8-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2abd8-128">See Also</span></span>  
 [<span data-ttu-id="2abd8-129">Güvenlik genel bakış</span><span class="sxs-lookup"><span data-stu-id="2abd8-129">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
