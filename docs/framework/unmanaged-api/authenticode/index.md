---
title: Authenticode (Yönetilmeyen API Başvurusu)
ms.date: 03/30/2017
ms.assetid: 7e8cc303-6e77-4116-aa8b-7ea297a3a467
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 408219307015d5c39cb581b3884ed9810f4c0566
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61941649"
---
# <a name="authenticode-unmanaged-api-reference"></a><span data-ttu-id="744d7-102">Authenticode (Yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="744d7-102">Authenticode (Unmanaged API Reference)</span></span>
<span data-ttu-id="744d7-103">Authenticode XrML lisans oluşturma ve doğrulama modülü destekler.</span><span class="sxs-lookup"><span data-stu-id="744d7-103">Supports the Authenticode XrML license creation and verification module.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="744d7-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="744d7-104">In This Section</span></span>  
 [<span data-ttu-id="744d7-105">_AxlGetIssuerPublicKeyHash İşlevi</span><span class="sxs-lookup"><span data-stu-id="744d7-105">_AxlGetIssuerPublicKeyHash Function</span></span>](../../../../docs/framework/unmanaged-api/authenticode/axlgetissuerpublickeyhash-function.md)  
 <span data-ttu-id="744d7-106">Belirtilen sertifika imzalamak için kullanılan özel anahtarıyla ilişkilendirilmiş ortak anahtar SHA-1 karmasını alır.</span><span class="sxs-lookup"><span data-stu-id="744d7-106">Retrieves the SHA-1 hash of the public key associated with the private key that is used to sign the specified certificate.</span></span>  
  
 [<span data-ttu-id="744d7-107">_AxlPublicKeyBlobToPublicKeyToken İşlevi</span><span class="sxs-lookup"><span data-stu-id="744d7-107">_AxlPublicKeyBlobToPublicKeyToken Function</span></span>](../../../../docs/framework/unmanaged-api/authenticode/axlpublickeyblobtopublickeytoken-function.md)  
 <span data-ttu-id="744d7-108">Tanımlayıcı ad ortak anahtar belirteci, bir CSP PUBLICKEYBLOB biçiminden hesaplar.</span><span class="sxs-lookup"><span data-stu-id="744d7-108">Computes the strong name public key token from a CSP PUBLICKEYBLOB format.</span></span>  
  
 [<span data-ttu-id="744d7-109">_AxlRSAKeyValueToPublicKeyToken İşlevi</span><span class="sxs-lookup"><span data-stu-id="744d7-109">_AxlRSAKeyValueToPublicKeyToken Function</span></span>](../../../../docs/framework/unmanaged-api/authenticode/axlrsakeyvaluetopublickeytoken-function.md)  
 <span data-ttu-id="744d7-110">Tanımlayıcı ad bir ortak anahtar belirteci için bir mod ve üs dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="744d7-110">Converts a Modulus and Exponent to a strong name public key token.</span></span>  
  
 [<span data-ttu-id="744d7-111">CertFreeAuthenticodeSignerInfo İşlevi</span><span class="sxs-lookup"><span data-stu-id="744d7-111">CertFreeAuthenticodeSignerInfo Function</span></span>](../../../../docs/framework/unmanaged-api/authenticode/certfreeauthenticodesignerinfo-function.md)  
 <span data-ttu-id="744d7-112">Axl_authentıcode_sıgner_ınfo yapısı için ayrılan kaynakları serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="744d7-112">Frees resources allocated for the AXL_AUTHENTICODE_SIGNER_INFO structure.</span></span>  
  
 [<span data-ttu-id="744d7-113">CertFreeAuthenticodeTimestamperInfo İşlevi</span><span class="sxs-lookup"><span data-stu-id="744d7-113">CertFreeAuthenticodeTimestamperInfo Function</span></span>](../../../../docs/framework/unmanaged-api/authenticode/certfreeauthenticodetimestamperinfo-function.md)  
 <span data-ttu-id="744d7-114">Axl_authentıcode_tımestamper_ınfo yapısı için ayrılan kaynakları serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="744d7-114">Frees resources allocated for the AXL_AUTHENTICODE_TIMESTAMPER_INFO structure.</span></span>  
  
 [<span data-ttu-id="744d7-115">CertTimestampAuthenticodeLicense İşlevi</span><span class="sxs-lookup"><span data-stu-id="744d7-115">CertTimestampAuthenticodeLicense Function</span></span>](../../../../docs/framework/unmanaged-api/authenticode/certtimestampauthenticodelicense-function.md)  
 <span data-ttu-id="744d7-116">CertCreateAuthenticodeLicense tarafından oluşturulan bir Authenticode XrML lisans zaman damgaları.</span><span class="sxs-lookup"><span data-stu-id="744d7-116">Time stamps an Authenticode XrML license created by CertCreateAuthenticodeLicense.</span></span>  
  
 [<span data-ttu-id="744d7-117">CertVerifyAuthenticodeLicense İşlevi</span><span class="sxs-lookup"><span data-stu-id="744d7-117">CertVerifyAuthenticodeLicense Function</span></span>](../../../../docs/framework/unmanaged-api/authenticode/certverifyauthenticodelicense-function.md)  
 <span data-ttu-id="744d7-118">Authenticode XrML lisans geçerliliğini doğrular.</span><span class="sxs-lookup"><span data-stu-id="744d7-118">Verifies the validity of an Authenticode XrML license.</span></span>  
  
 [<span data-ttu-id="744d7-119">AXL_AUTHENTICODE_SIGNER_INFO Yapısı</span><span class="sxs-lookup"><span data-stu-id="744d7-119">AXL_AUTHENTICODE_SIGNER_INFO Structure</span></span>](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md)  
 <span data-ttu-id="744d7-120">Authenticode imzalayan bilgileri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="744d7-120">Defines the Authenticode signer information.</span></span>  
  
 [<span data-ttu-id="744d7-121">AXL_AUTHENTICODE_TIMESTAMPER_INFO Yapısı</span><span class="sxs-lookup"><span data-stu-id="744d7-121">AXL_AUTHENTICODE_TIMESTAMPER_INFO Structure</span></span>](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md)  
 <span data-ttu-id="744d7-122">Zaman stamper Authenticode bilgileri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="744d7-122">Defines the Authenticode time stamper information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="744d7-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="744d7-123">See also</span></span>

- [<span data-ttu-id="744d7-124">Yönetilmeyen API Başvurusu</span><span class="sxs-lookup"><span data-stu-id="744d7-124">Unmanaged API Reference</span></span>](../../../../docs/framework/unmanaged-api/index.md)
