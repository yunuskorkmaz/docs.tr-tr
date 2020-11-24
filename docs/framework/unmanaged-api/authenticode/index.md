---
title: Authenticode (Yönetilmeyen API Başvurusu)
ms.date: 03/30/2017
ms.assetid: 7e8cc303-6e77-4116-aa8b-7ea297a3a467
ms.openlocfilehash: 9b3e1585278bda82dedf7542e866a551867b9c9f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674053"
---
# <a name="authenticode-unmanaged-api-reference"></a><span data-ttu-id="4ed8c-102">Authenticode (Yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="4ed8c-102">Authenticode (Unmanaged API Reference)</span></span>

<span data-ttu-id="4ed8c-103">Authenticode XrML lisans oluşturma ve doğrulama modülünü destekler.</span><span class="sxs-lookup"><span data-stu-id="4ed8c-103">Supports the Authenticode XrML license creation and verification module.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4ed8c-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="4ed8c-104">In This Section</span></span>  

 [<span data-ttu-id="4ed8c-105">_AxlGetIssuerPublicKeyHash İşlevi</span><span class="sxs-lookup"><span data-stu-id="4ed8c-105">_AxlGetIssuerPublicKeyHash Function</span></span>](axlgetissuerpublickeyhash-function.md)  
 <span data-ttu-id="4ed8c-106">Belirtilen sertifikayı imzalamak için kullanılan özel anahtarla ilişkili ortak anahtarın SHA-1 karmasını alır.</span><span class="sxs-lookup"><span data-stu-id="4ed8c-106">Retrieves the SHA-1 hash of the public key associated with the private key that is used to sign the specified certificate.</span></span>  
  
 [<span data-ttu-id="4ed8c-107">_AxlPublicKeyBlobToPublicKeyToken İşlevi</span><span class="sxs-lookup"><span data-stu-id="4ed8c-107">_AxlPublicKeyBlobToPublicKeyToken Function</span></span>](axlpublickeyblobtopublickeytoken-function.md)  
 <span data-ttu-id="4ed8c-108">Bir CSP PUBLICKEYBLOB biçiminden tanımlayıcı ad ortak anahtar belirtecini hesaplar.</span><span class="sxs-lookup"><span data-stu-id="4ed8c-108">Computes the strong name public key token from a CSP PUBLICKEYBLOB format.</span></span>  
  
 [<span data-ttu-id="4ed8c-109">_AxlRSAKeyValueToPublicKeyToken İşlevi</span><span class="sxs-lookup"><span data-stu-id="4ed8c-109">_AxlRSAKeyValueToPublicKeyToken Function</span></span>](axlrsakeyvaluetopublickeytoken-function.md)  
 <span data-ttu-id="4ed8c-110">Bir mod ve üs değeri bir tanımlayıcı ad ortak anahtar belirtecine dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="4ed8c-110">Converts a Modulus and Exponent to a strong name public key token.</span></span>  
  
 [<span data-ttu-id="4ed8c-111">CertFreeAuthenticodeSignerInfo İşlevi</span><span class="sxs-lookup"><span data-stu-id="4ed8c-111">CertFreeAuthenticodeSignerInfo Function</span></span>](certfreeauthenticodesignerinfo-function.md)  
 <span data-ttu-id="4ed8c-112">AXL_AUTHENTICODE_SIGNER_INFO yapısı için ayrılan kaynakları boşaltır.</span><span class="sxs-lookup"><span data-stu-id="4ed8c-112">Frees resources allocated for the AXL_AUTHENTICODE_SIGNER_INFO structure.</span></span>  
  
 [<span data-ttu-id="4ed8c-113">CertFreeAuthenticodeTimestamperInfo İşlevi</span><span class="sxs-lookup"><span data-stu-id="4ed8c-113">CertFreeAuthenticodeTimestamperInfo Function</span></span>](certfreeauthenticodetimestamperinfo-function.md)  
 <span data-ttu-id="4ed8c-114">AXL_AUTHENTICODE_TIMESTAMPER_INFO yapısı için ayrılan kaynakları boşaltır.</span><span class="sxs-lookup"><span data-stu-id="4ed8c-114">Frees resources allocated for the AXL_AUTHENTICODE_TIMESTAMPER_INFO structure.</span></span>  
  
 [<span data-ttu-id="4ed8c-115">CertTimestampAuthenticodeLicense İşlevi</span><span class="sxs-lookup"><span data-stu-id="4ed8c-115">CertTimestampAuthenticodeLicense Function</span></span>](certtimestampauthenticodelicense-function.md)  
 <span data-ttu-id="4ed8c-116">Zaman damgaları CertCreateAuthenticodeLicense tarafından oluşturulan bir Authenticode XrML lisansı.</span><span class="sxs-lookup"><span data-stu-id="4ed8c-116">Time stamps an Authenticode XrML license created by CertCreateAuthenticodeLicense.</span></span>  
  
 [<span data-ttu-id="4ed8c-117">CertVerifyAuthenticodeLicense İşlevi</span><span class="sxs-lookup"><span data-stu-id="4ed8c-117">CertVerifyAuthenticodeLicense Function</span></span>](certverifyauthenticodelicense-function.md)  
 <span data-ttu-id="4ed8c-118">Authenticode XrML lisansının geçerliliğini doğrular.</span><span class="sxs-lookup"><span data-stu-id="4ed8c-118">Verifies the validity of an Authenticode XrML license.</span></span>  
  
 [<span data-ttu-id="4ed8c-119">AXL_AUTHENTICODE_SIGNER_INFO Yapısı</span><span class="sxs-lookup"><span data-stu-id="4ed8c-119">AXL_AUTHENTICODE_SIGNER_INFO Structure</span></span>](axl-authenticode-signer-info-structure.md)  
 <span data-ttu-id="4ed8c-120">Authenticode imzalayan bilgilerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4ed8c-120">Defines the Authenticode signer information.</span></span>  
  
 [<span data-ttu-id="4ed8c-121">AXL_AUTHENTICODE_TIMESTAMPER_INFO Yapısı</span><span class="sxs-lookup"><span data-stu-id="4ed8c-121">AXL_AUTHENTICODE_TIMESTAMPER_INFO Structure</span></span>](axl-authenticode-timestamper-info-structure.md)  
 <span data-ttu-id="4ed8c-122">Authenticode zaman Stamper bilgilerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4ed8c-122">Defines the Authenticode time stamper information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ed8c-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4ed8c-123">See also</span></span>

- [<span data-ttu-id="4ed8c-124">Yönetilmeyen API başvurusu</span><span class="sxs-lookup"><span data-stu-id="4ed8c-124">Unmanaged API Reference</span></span>](../index.md)
