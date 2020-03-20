---
title: Authenticode (Yönetilmeyen API Başvurusu)
ms.date: 03/30/2017
ms.assetid: 7e8cc303-6e77-4116-aa8b-7ea297a3a467
ms.openlocfilehash: 1b8b2222950c75f7f9d2ec2704f722087645cd7e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73132466"
---
# <a name="authenticode-unmanaged-api-reference"></a><span data-ttu-id="7eb2e-102">Authenticode (Yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="7eb2e-102">Authenticode (Unmanaged API Reference)</span></span>
<span data-ttu-id="7eb2e-103">Authenticode XrML lisans oluşturma ve doğrulama modüllerini destekler.</span><span class="sxs-lookup"><span data-stu-id="7eb2e-103">Supports the Authenticode XrML license creation and verification module.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7eb2e-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="7eb2e-104">In This Section</span></span>  
 [<span data-ttu-id="7eb2e-105">_AxlGetIssuerPublicKeyHash İşlevi</span><span class="sxs-lookup"><span data-stu-id="7eb2e-105">_AxlGetIssuerPublicKeyHash Function</span></span>](axlgetissuerpublickeyhash-function.md)  
 <span data-ttu-id="7eb2e-106">Belirtilen sertifikayı imzalamak için kullanılan özel anahtarla ilişkili ortak anahtarın SHA-1 karmasını alır.</span><span class="sxs-lookup"><span data-stu-id="7eb2e-106">Retrieves the SHA-1 hash of the public key associated with the private key that is used to sign the specified certificate.</span></span>  
  
 [<span data-ttu-id="7eb2e-107">_AxlPublicKeyBlobToPublicKeyToken İşlevi</span><span class="sxs-lookup"><span data-stu-id="7eb2e-107">_AxlPublicKeyBlobToPublicKeyToken Function</span></span>](axlpublickeyblobtopublickeytoken-function.md)  
 <span data-ttu-id="7eb2e-108">CSP PUBLICKEYBLOB biçiminden güçlü ad ortak anahtar belirteci'ni hesaplar.</span><span class="sxs-lookup"><span data-stu-id="7eb2e-108">Computes the strong name public key token from a CSP PUBLICKEYBLOB format.</span></span>  
  
 [<span data-ttu-id="7eb2e-109">_AxlRSAKeyValueToPublicKeyToken İşlevi</span><span class="sxs-lookup"><span data-stu-id="7eb2e-109">_AxlRSAKeyValueToPublicKeyToken Function</span></span>](axlrsakeyvaluetopublickeytoken-function.md)  
 <span data-ttu-id="7eb2e-110">Bir Modülü ve Üstel'i güçlü bir ad public key jetonuna dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="7eb2e-110">Converts a Modulus and Exponent to a strong name public key token.</span></span>  
  
 [<span data-ttu-id="7eb2e-111">CertFreeAuthenticodeSignerInfo İşlevi</span><span class="sxs-lookup"><span data-stu-id="7eb2e-111">CertFreeAuthenticodeSignerInfo Function</span></span>](certfreeauthenticodesignerinfo-function.md)  
 <span data-ttu-id="7eb2e-112">AXL_AUTHENTICODE_SIGNER_INFO yapı için ayrılan kaynakları serbest sağlar.</span><span class="sxs-lookup"><span data-stu-id="7eb2e-112">Frees resources allocated for the AXL_AUTHENTICODE_SIGNER_INFO structure.</span></span>  
  
 [<span data-ttu-id="7eb2e-113">CertFreeAuthenticodeTimestamperInfo İşlevi</span><span class="sxs-lookup"><span data-stu-id="7eb2e-113">CertFreeAuthenticodeTimestamperInfo Function</span></span>](certfreeauthenticodetimestamperinfo-function.md)  
 <span data-ttu-id="7eb2e-114">AXL_AUTHENTICODE_TIMESTAMPER_INFO yapı için ayrılan kaynakları serbest sağlar.</span><span class="sxs-lookup"><span data-stu-id="7eb2e-114">Frees resources allocated for the AXL_AUTHENTICODE_TIMESTAMPER_INFO structure.</span></span>  
  
 [<span data-ttu-id="7eb2e-115">CertTimestampAuthenticodeLicense İşlevi</span><span class="sxs-lookup"><span data-stu-id="7eb2e-115">CertTimestampAuthenticodeLicense Function</span></span>](certtimestampauthenticodelicense-function.md)  
 <span data-ttu-id="7eb2e-116">Zaman, CertCreateAuthenticodeLicense tarafından oluşturulan Authenticode XrML lisansını damgalar.</span><span class="sxs-lookup"><span data-stu-id="7eb2e-116">Time stamps an Authenticode XrML license created by CertCreateAuthenticodeLicense.</span></span>  
  
 [<span data-ttu-id="7eb2e-117">CertVerifyAuthenticodeLicense İşlevi</span><span class="sxs-lookup"><span data-stu-id="7eb2e-117">CertVerifyAuthenticodeLicense Function</span></span>](certverifyauthenticodelicense-function.md)  
 <span data-ttu-id="7eb2e-118">Authenticode XrML lisansının geçerliliğini doğrular.</span><span class="sxs-lookup"><span data-stu-id="7eb2e-118">Verifies the validity of an Authenticode XrML license.</span></span>  
  
 [<span data-ttu-id="7eb2e-119">AXL_AUTHENTICODE_SIGNER_INFO Yapısı</span><span class="sxs-lookup"><span data-stu-id="7eb2e-119">AXL_AUTHENTICODE_SIGNER_INFO Structure</span></span>](axl-authenticode-signer-info-structure.md)  
 <span data-ttu-id="7eb2e-120">Authenticode imzalayan bilgileri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7eb2e-120">Defines the Authenticode signer information.</span></span>  
  
 [<span data-ttu-id="7eb2e-121">AXL_AUTHENTICODE_TIMESTAMPER_INFO Yapısı</span><span class="sxs-lookup"><span data-stu-id="7eb2e-121">AXL_AUTHENTICODE_TIMESTAMPER_INFO Structure</span></span>](axl-authenticode-timestamper-info-structure.md)  
 <span data-ttu-id="7eb2e-122">Authenticode zaman damgalayıcı bilgilerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7eb2e-122">Defines the Authenticode time stamper information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7eb2e-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7eb2e-123">See also</span></span>

- [<span data-ttu-id="7eb2e-124">Yönetilmeyen API Başvurusu</span><span class="sxs-lookup"><span data-stu-id="7eb2e-124">Unmanaged API Reference</span></span>](../index.md)
