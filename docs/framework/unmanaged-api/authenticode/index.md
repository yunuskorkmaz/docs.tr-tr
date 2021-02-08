---
description: 'Daha fazla bilgi edinin: Authenticode (yönetilmeyen API Başvurusu)'
title: Authenticode (Yönetilmeyen API Başvurusu)
ms.date: 03/30/2017
ms.assetid: 7e8cc303-6e77-4116-aa8b-7ea297a3a467
ms.openlocfilehash: d7a1684fde900bfc01161193d0747b156c6856a8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99772841"
---
# <a name="authenticode-unmanaged-api-reference"></a><span data-ttu-id="2d4b7-103">Authenticode (Yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="2d4b7-103">Authenticode (Unmanaged API Reference)</span></span>

<span data-ttu-id="2d4b7-104">Authenticode XrML lisans oluşturma ve doğrulama modülünü destekler.</span><span class="sxs-lookup"><span data-stu-id="2d4b7-104">Supports the Authenticode XrML license creation and verification module.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2d4b7-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="2d4b7-105">In This Section</span></span>  

 [<span data-ttu-id="2d4b7-106">_AxlGetIssuerPublicKeyHash İşlevi</span><span class="sxs-lookup"><span data-stu-id="2d4b7-106">_AxlGetIssuerPublicKeyHash Function</span></span>](axlgetissuerpublickeyhash-function.md)  
 <span data-ttu-id="2d4b7-107">Belirtilen sertifikayı imzalamak için kullanılan özel anahtarla ilişkili ortak anahtarın SHA-1 karmasını alır.</span><span class="sxs-lookup"><span data-stu-id="2d4b7-107">Retrieves the SHA-1 hash of the public key associated with the private key that is used to sign the specified certificate.</span></span>  
  
 [<span data-ttu-id="2d4b7-108">_AxlPublicKeyBlobToPublicKeyToken İşlevi</span><span class="sxs-lookup"><span data-stu-id="2d4b7-108">_AxlPublicKeyBlobToPublicKeyToken Function</span></span>](axlpublickeyblobtopublickeytoken-function.md)  
 <span data-ttu-id="2d4b7-109">Bir CSP PUBLICKEYBLOB biçiminden tanımlayıcı ad ortak anahtar belirtecini hesaplar.</span><span class="sxs-lookup"><span data-stu-id="2d4b7-109">Computes the strong name public key token from a CSP PUBLICKEYBLOB format.</span></span>  
  
 [<span data-ttu-id="2d4b7-110">_AxlRSAKeyValueToPublicKeyToken İşlevi</span><span class="sxs-lookup"><span data-stu-id="2d4b7-110">_AxlRSAKeyValueToPublicKeyToken Function</span></span>](axlrsakeyvaluetopublickeytoken-function.md)  
 <span data-ttu-id="2d4b7-111">Bir mod ve üs değeri bir tanımlayıcı ad ortak anahtar belirtecine dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="2d4b7-111">Converts a Modulus and Exponent to a strong name public key token.</span></span>  
  
 [<span data-ttu-id="2d4b7-112">CertFreeAuthenticodeSignerInfo İşlevi</span><span class="sxs-lookup"><span data-stu-id="2d4b7-112">CertFreeAuthenticodeSignerInfo Function</span></span>](certfreeauthenticodesignerinfo-function.md)  
 <span data-ttu-id="2d4b7-113">AXL_AUTHENTICODE_SIGNER_INFO yapısı için ayrılan kaynakları boşaltır.</span><span class="sxs-lookup"><span data-stu-id="2d4b7-113">Frees resources allocated for the AXL_AUTHENTICODE_SIGNER_INFO structure.</span></span>  
  
 [<span data-ttu-id="2d4b7-114">CertFreeAuthenticodeTimestamperInfo İşlevi</span><span class="sxs-lookup"><span data-stu-id="2d4b7-114">CertFreeAuthenticodeTimestamperInfo Function</span></span>](certfreeauthenticodetimestamperinfo-function.md)  
 <span data-ttu-id="2d4b7-115">AXL_AUTHENTICODE_TIMESTAMPER_INFO yapısı için ayrılan kaynakları boşaltır.</span><span class="sxs-lookup"><span data-stu-id="2d4b7-115">Frees resources allocated for the AXL_AUTHENTICODE_TIMESTAMPER_INFO structure.</span></span>  
  
 [<span data-ttu-id="2d4b7-116">CertTimestampAuthenticodeLicense İşlevi</span><span class="sxs-lookup"><span data-stu-id="2d4b7-116">CertTimestampAuthenticodeLicense Function</span></span>](certtimestampauthenticodelicense-function.md)  
 <span data-ttu-id="2d4b7-117">Zaman damgaları CertCreateAuthenticodeLicense tarafından oluşturulan bir Authenticode XrML lisansı.</span><span class="sxs-lookup"><span data-stu-id="2d4b7-117">Time stamps an Authenticode XrML license created by CertCreateAuthenticodeLicense.</span></span>  
  
 [<span data-ttu-id="2d4b7-118">CertVerifyAuthenticodeLicense İşlevi</span><span class="sxs-lookup"><span data-stu-id="2d4b7-118">CertVerifyAuthenticodeLicense Function</span></span>](certverifyauthenticodelicense-function.md)  
 <span data-ttu-id="2d4b7-119">Authenticode XrML lisansının geçerliliğini doğrular.</span><span class="sxs-lookup"><span data-stu-id="2d4b7-119">Verifies the validity of an Authenticode XrML license.</span></span>  
  
 [<span data-ttu-id="2d4b7-120">AXL_AUTHENTICODE_SIGNER_INFO Yapısı</span><span class="sxs-lookup"><span data-stu-id="2d4b7-120">AXL_AUTHENTICODE_SIGNER_INFO Structure</span></span>](axl-authenticode-signer-info-structure.md)  
 <span data-ttu-id="2d4b7-121">Authenticode imzalayan bilgilerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2d4b7-121">Defines the Authenticode signer information.</span></span>  
  
 [<span data-ttu-id="2d4b7-122">AXL_AUTHENTICODE_TIMESTAMPER_INFO Yapısı</span><span class="sxs-lookup"><span data-stu-id="2d4b7-122">AXL_AUTHENTICODE_TIMESTAMPER_INFO Structure</span></span>](axl-authenticode-timestamper-info-structure.md)  
 <span data-ttu-id="2d4b7-123">Authenticode zaman Stamper bilgilerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2d4b7-123">Defines the Authenticode time stamper information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d4b7-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2d4b7-124">See also</span></span>

- [<span data-ttu-id="2d4b7-125">Yönetilmeyen API başvurusu</span><span class="sxs-lookup"><span data-stu-id="2d4b7-125">Unmanaged API Reference</span></span>](../index.md)
