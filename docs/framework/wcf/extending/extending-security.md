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
ms.workload: dotnet
ms.openlocfilehash: ecbbaac0023ca528967abe2cb60c3d790772fb2e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="extending-security"></a><span data-ttu-id="161f3-102">Güvenliği Genişletme</span><span class="sxs-lookup"><span data-stu-id="161f3-102">Extending Security</span></span>
<span data-ttu-id="161f3-103">Yeni talep türlerini ve özel belirteçler uyum sağlamak için güvenlik altyapısı genişletebilirsiniz [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="161f3-103">To accommodate new claim types and custom tokens, you can extend the security infrastructure of [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span></span> <span data-ttu-id="161f3-104">Bu bölümdeki konular, bunun nasıl yapılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="161f3-104">The topics in this section show you how this is done.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="161f3-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="161f3-105">In This Section</span></span>  
 [<span data-ttu-id="161f3-106">Güvenlik mimarisi</span><span class="sxs-lookup"><span data-stu-id="161f3-106">Security Architecture</span></span>](http://msdn.microsoft.com/en-us/16593476-d36a-408d-808c-ae6fd483e28f)  
 <span data-ttu-id="161f3-107">Mimarisi anlatılmaktadır [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] güvenlik sistemi.</span><span class="sxs-lookup"><span data-stu-id="161f3-107">Walks through the architecture of the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] security system.</span></span>  
  
 [<span data-ttu-id="161f3-108">Özel Kimlik Bilgileri ve Kimlik Bilgileri Doğrulaması</span><span class="sxs-lookup"><span data-stu-id="161f3-108">Custom Credential and Credential Validation</span></span>](../../../../docs/framework/wcf/extending/custom-credential-and-credential-validation.md)  
 <span data-ttu-id="161f3-109">Özel kimlik doğrulama sırasında kimlik modeli nasıl kullanıldığını açıklar.</span><span class="sxs-lookup"><span data-stu-id="161f3-109">Explains how the Identity Model is used when validating custom credentials.</span></span>  
  
 [<span data-ttu-id="161f3-110">Özel Belirteçler</span><span class="sxs-lookup"><span data-stu-id="161f3-110">Custom Tokens</span></span>](../../../../docs/framework/wcf/extending/custom-tokens.md)  
 <span data-ttu-id="161f3-111">Verilen belirteçler bir güvenlik belirteci hizmeti (STS) normal SAML belirteçleri uygulanır.</span><span class="sxs-lookup"><span data-stu-id="161f3-111">Issued tokens from a Security Token Service (STS) are typically SAML tokens.</span></span> <span data-ttu-id="161f3-112">Bu konuda bir özel belirteç türünün nasıl oluşturulacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="161f3-112">This topic explains how to create a custom token type.</span></span>  
  
 [<span data-ttu-id="161f3-113">Özel Yetkilendirme</span><span class="sxs-lookup"><span data-stu-id="161f3-113">Custom Authorization</span></span>](../../../../docs/framework/wcf/extending/custom-authorization.md)  
 <span data-ttu-id="161f3-114">Özel yetkilendirme uygulamak açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="161f3-114">Explains how to implement custom authorization.</span></span>  
  
 [<span data-ttu-id="161f3-115">Bir Hizmetin Kimliğini Kimlik Doğrulama için Geçersiz Kılma</span><span class="sxs-lookup"><span data-stu-id="161f3-115">Overriding the Identity of a Service for Authentication</span></span>](../../../../docs/framework/wcf/extending/overriding-the-identity-of-a-service-for-authentication.md)  
 <span data-ttu-id="161f3-116">Kimlik doğrulaması için bir hizmetin kimliğini geçersiz kılmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="161f3-116">Describes how to override the identity of a service for authentication.</span></span>  
  
 [<span data-ttu-id="161f3-117">Nasıl yapılır: Özel İstemci Kimliği Doğrulayıcı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="161f3-117">How to: Create a Custom Client Identity Verifier</span></span>](../../../../docs/framework/wcf/extending/how-to-create-a-custom-client-identity-verifier.md)  
 <span data-ttu-id="161f3-118">Özel uç noktası kimlik doğrulamak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="161f3-118">Demonstrates how to validate a custom endpoint identity.</span></span>  
  
 [<span data-ttu-id="161f3-119">Nasıl Yapılır: İmzalama ve Şifreleme için Ayrı X.509 Sertifikaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="161f3-119">How to: Use Separate X.509 Certificates for Signing and Encryption</span></span>](../../../../docs/framework/wcf/extending/how-to-use-separate-x-509-certificates-for-signing-and-encryption.md)  
 <span data-ttu-id="161f3-120">İletiler genellikle imzalı ve tek bir sertifika ile şifrelenir.</span><span class="sxs-lookup"><span data-stu-id="161f3-120">Messages are typically signed and encrypted with a single certificate.</span></span> <span data-ttu-id="161f3-121">Bu konu nasıl iki sertifika açıklar, gerekli olduğunda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="161f3-121">This topic explains how two certificates can be used, when required.</span></span>  
  
 [<span data-ttu-id="161f3-122">Nasıl yapılır: Bir X.509 Sertifikasının Şifreleme Sağlayıcısını Değiştirme</span><span class="sxs-lookup"><span data-stu-id="161f3-122">How to: Change the Cryptographic Provider for an X.509 Certificate's Private Key</span></span>](../../../../docs/framework/wcf/extending/change-cryptographic-provider-x509-certificate-private-key.md)  
 <span data-ttu-id="161f3-123">Bir X.509 sertifikasının özel anahtarı sağlamak için kullanılan şifreleme sağlayıcısını değiştirme ve sağlayıcısını tümleştirme açıklanmaktadır [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] framework.</span><span class="sxs-lookup"><span data-stu-id="161f3-123">Explains how to change the cryptographic provider used to provide an X.509 certificate's private key and how to integrate the provider into the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] framework.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="161f3-124">Başvuru</span><span class="sxs-lookup"><span data-stu-id="161f3-124">Reference</span></span>  
 <xref:System.ServiceModel.ServiceAuthorizationManager>  
  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.IdentityModel.Policy>  
  
 <xref:System.IdentityModel.Tokens>  
  
 <xref:System.IdentityModel.Selectors>  
  
## <a name="related-sections"></a><span data-ttu-id="161f3-125">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="161f3-125">Related Sections</span></span>  
 [<span data-ttu-id="161f3-126">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="161f3-126">Security</span></span>](../../../../docs/framework/wcf/feature-details/security.md)  
  
 [<span data-ttu-id="161f3-127">Temel WCF Programlama</span><span class="sxs-lookup"><span data-stu-id="161f3-127">Basic WCF Programming</span></span>](../../../../docs/framework/wcf/basic-wcf-programming.md)  
  
## <a name="see-also"></a><span data-ttu-id="161f3-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="161f3-128">See Also</span></span>  
 [<span data-ttu-id="161f3-129">Güvenliğe Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="161f3-129">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
