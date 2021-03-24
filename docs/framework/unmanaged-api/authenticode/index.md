---
description: 'Daha fazla bilgi edinin: Authenticode (yönetilmeyen API Başvurusu)'
title: Authenticode (Yönetilmeyen API Başvurusu)
ms.date: 03/30/2017
ms.assetid: 7e8cc303-6e77-4116-aa8b-7ea297a3a467
ms.openlocfilehash: 0a4a9b4ba3cc9a5818896508c80bc31073f514e7
ms.sourcegitcommit: 26721a2260deabb3318cc98af8619306711153cd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/24/2021
ms.locfileid: "105027850"
---
# <a name="authenticode-unmanaged-api-reference"></a><span data-ttu-id="f1e79-103">Authenticode (Yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="f1e79-103">Authenticode (Unmanaged API Reference)</span></span>

<span data-ttu-id="f1e79-104">Authenticode XrML lisans oluşturma ve doğrulama modülünü destekler.</span><span class="sxs-lookup"><span data-stu-id="f1e79-104">Supports the Authenticode XrML license creation and verification module.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f1e79-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="f1e79-105">In This Section</span></span>  

 [<span data-ttu-id="f1e79-106">_AxlGetIssuerPublicKeyHash İşlevi</span><span class="sxs-lookup"><span data-stu-id="f1e79-106">_AxlGetIssuerPublicKeyHash Function</span></span>](axlgetissuerpublickeyhash-function.md)  
 <span data-ttu-id="f1e79-107">Belirtilen sertifikayı imzalamak için kullanılan özel anahtarla ilişkili ortak anahtarın SHA-1 karmasını alır.</span><span class="sxs-lookup"><span data-stu-id="f1e79-107">Retrieves the SHA-1 hash of the public key associated with the private key that is used to sign the specified certificate.</span></span>  
  
 [<span data-ttu-id="f1e79-108">_AxlPublicKeyBlobToPublicKeyToken İşlevi</span><span class="sxs-lookup"><span data-stu-id="f1e79-108">_AxlPublicKeyBlobToPublicKeyToken Function</span></span>](axlpublickeyblobtopublickeytoken-function.md)  
 <span data-ttu-id="f1e79-109">Bir CSP PUBLICKEYBLOB biçiminden tanımlayıcı ad ortak anahtar belirtecini hesaplar.</span><span class="sxs-lookup"><span data-stu-id="f1e79-109">Computes the strong name public key token from a CSP PUBLICKEYBLOB format.</span></span>  
  
 [<span data-ttu-id="f1e79-110">_AxlRSAKeyValueToPublicKeyToken İşlevi</span><span class="sxs-lookup"><span data-stu-id="f1e79-110">_AxlRSAKeyValueToPublicKeyToken Function</span></span>](axlrsakeyvaluetopublickeytoken-function.md)  
 <span data-ttu-id="f1e79-111">Bir mod ve üs değeri bir tanımlayıcı ad ortak anahtar belirtecine dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="f1e79-111">Converts a Modulus and Exponent to a strong name public key token.</span></span>  
  
 [<span data-ttu-id="f1e79-112">CertFreeAuthenticodeSignerInfo İşlevi</span><span class="sxs-lookup"><span data-stu-id="f1e79-112">CertFreeAuthenticodeSignerInfo Function</span></span>](certfreeauthenticodesignerinfo-function.md)  
 <span data-ttu-id="f1e79-113">AXL_AUTHENTICODE_SIGNER_INFO yapısı için ayrılan kaynakları boşaltır.</span><span class="sxs-lookup"><span data-stu-id="f1e79-113">Frees resources allocated for the AXL_AUTHENTICODE_SIGNER_INFO structure.</span></span>  
  
 [<span data-ttu-id="f1e79-114">CertFreeAuthenticodeTimestamperInfo İşlevi</span><span class="sxs-lookup"><span data-stu-id="f1e79-114">CertFreeAuthenticodeTimestamperInfo Function</span></span>](certfreeauthenticodetimestamperinfo-function.md)  
 <span data-ttu-id="f1e79-115">AXL_AUTHENTICODE_TIMESTAMPER_INFO yapısı için ayrılan kaynakları boşaltır.</span><span class="sxs-lookup"><span data-stu-id="f1e79-115">Frees resources allocated for the AXL_AUTHENTICODE_TIMESTAMPER_INFO structure.</span></span>  
  
 [<span data-ttu-id="f1e79-116">CertTimestampAuthenticodeLicense İşlevi</span><span class="sxs-lookup"><span data-stu-id="f1e79-116">CertTimestampAuthenticodeLicense Function</span></span>](certtimestampauthenticodelicense-function.md)  
 <span data-ttu-id="f1e79-117">Zaman damgaları CertCreateAuthenticodeLicense tarafından oluşturulan bir Authenticode XrML lisansı.</span><span class="sxs-lookup"><span data-stu-id="f1e79-117">Time stamps an Authenticode XrML license created by CertCreateAuthenticodeLicense.</span></span>  
  
 [<span data-ttu-id="f1e79-118">CertVerifyAuthenticodeLicense İşlevi</span><span class="sxs-lookup"><span data-stu-id="f1e79-118">CertVerifyAuthenticodeLicense Function</span></span>](certverifyauthenticodelicense-function.md)  
 <span data-ttu-id="f1e79-119">Authenticode XrML lisansının geçerliliğini doğrular.</span><span class="sxs-lookup"><span data-stu-id="f1e79-119">Verifies the validity of an Authenticode XrML license.</span></span>  
  
 [<span data-ttu-id="f1e79-120">AXL_AUTHENTICODE_SIGNER_INFO Yapısı</span><span class="sxs-lookup"><span data-stu-id="f1e79-120">AXL_AUTHENTICODE_SIGNER_INFO Structure</span></span>](axl-authenticode-signer-info-structure.md)  
 <span data-ttu-id="f1e79-121">Authenticode imzalayan bilgilerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f1e79-121">Defines the Authenticode signer information.</span></span>  
  
 [<span data-ttu-id="f1e79-122">AXL_AUTHENTICODE_TIMESTAMPER_INFO Yapısı</span><span class="sxs-lookup"><span data-stu-id="f1e79-122">AXL_AUTHENTICODE_TIMESTAMPER_INFO Structure</span></span>](axl-authenticode-timestamper-info-structure.md)  
 <span data-ttu-id="f1e79-123">Authenticode zaman Stamper bilgilerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f1e79-123">Defines the Authenticode time stamper information.</span></span>  

## <a name="requirements"></a><span data-ttu-id="f1e79-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f1e79-124">Requirements</span></span>

<span data-ttu-id="f1e79-125">**Kitaplık**: clr.dll</span><span class="sxs-lookup"><span data-stu-id="f1e79-125">**Library**: clr.dll</span></span>
  
## <a name="see-also"></a><span data-ttu-id="f1e79-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f1e79-126">See also</span></span>

- [<span data-ttu-id="f1e79-127">Yönetilmeyen API başvurusu</span><span class="sxs-lookup"><span data-stu-id="f1e79-127">Unmanaged API Reference</span></span>](../index.md)
