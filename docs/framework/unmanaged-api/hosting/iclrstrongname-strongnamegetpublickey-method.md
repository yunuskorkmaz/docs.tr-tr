---
title: ICLRStrongName::StrongNameGetPublicKey Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameGetPublicKey
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameGetPublicKey
helpviewer_keywords:
- StrongNameGetPublicKey method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameGetPublicKey method [.NET Framework hosting]
ms.assetid: a31dcaa9-a404-4c1d-8cc7-081827c52935
topic_type:
- apiref
ms.openlocfilehash: cb96c7e17627205db0573e56fc8c2a29e7717434
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181931"
---
# <a name="iclrstrongnamestrongnamegetpublickey-method"></a><span data-ttu-id="ac344-102">ICLRStrongName::StrongNameGetPublicKey Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ac344-102">ICLRStrongName::StrongNameGetPublicKey Method</span></span>
<span data-ttu-id="ac344-103">Ortak anahtarı genel/özel anahtar çiftinden alır.</span><span class="sxs-lookup"><span data-stu-id="ac344-103">Gets the public key from a public/private key pair.</span></span> <span data-ttu-id="ac344-104">Anahtar çifti, bir şifreleme hizmet sağlayıcısı (CSP) içinde önemli bir kapsayıcı adı olarak veya ham bir bayt koleksiyonu olarak sağlanabilir.</span><span class="sxs-lookup"><span data-stu-id="ac344-104">The key pair can be supplied either as a key container name within a cryptographic service provider (CSP) or as a raw collection of bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac344-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ac344-105">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameGetPublicKey (
    [in]  LPCWSTR   szKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ac344-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ac344-106">Parameters</span></span>  
 `szKeyContainer`  
 <span data-ttu-id="ac344-107">[içinde] Ortak/özel anahtar çiftini içeren anahtar kapsayıcısının adı.</span><span class="sxs-lookup"><span data-stu-id="ac344-107">[in] The name of the key container that contains the public/private key pair.</span></span> <span data-ttu-id="ac344-108">Null `pbKeyBlob` ise, `szKeyContainer` CSP içinde geçerli bir kapsayıcı belirtmelidir.</span><span class="sxs-lookup"><span data-stu-id="ac344-108">If `pbKeyBlob` is null, `szKeyContainer` must specify a valid container within the CSP.</span></span> <span data-ttu-id="ac344-109">Bu durumda, [ICLRStrongName::StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md) yöntemi, kapsayıcıda depolanan anahtar çiftinden ortak anahtarı ayıklar.</span><span class="sxs-lookup"><span data-stu-id="ac344-109">In this case, the [ICLRStrongName::StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md) method extracts the public key from the key pair stored in the container.</span></span>  
  
 <span data-ttu-id="ac344-110">Null `pbKeyBlob` değilse, anahtar çiftinin anahtar ikili büyük nesnesinde (BLOB) bulunduğu varsayılır.</span><span class="sxs-lookup"><span data-stu-id="ac344-110">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="ac344-111">Anahtarlar 1024 bit Rivest-Shamir-Adleman (RSA) imzalama anahtarları olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ac344-111">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="ac344-112">Şu anda başka anahtar türü desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="ac344-112">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="ac344-113">[içinde] Ortak/özel anahtar çiftine işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ac344-113">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="ac344-114">Bu çift Win32 `CryptExportKey` işlevi tarafından oluşturulan biçimdedir.</span><span class="sxs-lookup"><span data-stu-id="ac344-114">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="ac344-115">Null `pbKeyBlob` ise, tarafından `szKeyContainer` belirtilen anahtar kapsayıcı anahtar çiftini içerdiği varsayılır.</span><span class="sxs-lookup"><span data-stu-id="ac344-115">If `pbKeyBlob` is null, the key container specified by `szKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="ac344-116">[içinde] Boyutu, bayt, ve. `pbKeyBlob`</span><span class="sxs-lookup"><span data-stu-id="ac344-116">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="ac344-117">[çıkış] Döndürülen ortak anahtar BLOB.</span><span class="sxs-lookup"><span data-stu-id="ac344-117">[out] The returned public key BLOB.</span></span> <span data-ttu-id="ac344-118">`ppbPublicKeyBlob` Parametre ortak dil çalışma zamanı tarafından ayrılır ve arayana döndürülür.</span><span class="sxs-lookup"><span data-stu-id="ac344-118">The `ppbPublicKeyBlob` parameter is allocated by the common language runtime and returned to the caller.</span></span> <span data-ttu-id="ac344-119">Arayan ICLRStrongName kullanarak bellek serbest [gerekir::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="ac344-119">The caller must free the memory by using the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="ac344-120">[çıkış] Döndürülen ortak anahtar BLOB boyutu.</span><span class="sxs-lookup"><span data-stu-id="ac344-120">[out] The size of the returned public key BLOB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ac344-121">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ac344-121">Return Value</span></span>  
 <span data-ttu-id="ac344-122">`S_OK`yöntem başarıyla tamamlanırsa; aksi takdirde, başarısızlığı gösteren bir HRESULT değeri (liste için [Ortak HRESULT Değerleri'ne](/windows/win32/seccrypto/common-hresult-values) bakın).</span><span class="sxs-lookup"><span data-stu-id="ac344-122">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ac344-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ac344-123">Remarks</span></span>  
 <span data-ttu-id="ac344-124">Ortak anahtar [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) yapısında yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="ac344-124">The public key is contained in a [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac344-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ac344-125">Requirements</span></span>  
 <span data-ttu-id="ac344-126">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac344-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac344-127">**Üstbilgi:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="ac344-127">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="ac344-128">**Kütüphane:** MSCorEE.dll bir kaynak olarak dahil</span><span class="sxs-lookup"><span data-stu-id="ac344-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ac344-129">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac344-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac344-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ac344-130">See also</span></span>

- [<span data-ttu-id="ac344-131">StrongNameTokenFromPublicKey Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ac344-131">StrongNameTokenFromPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [<span data-ttu-id="ac344-132">PublicKeyBlob Yapısı</span><span class="sxs-lookup"><span data-stu-id="ac344-132">PublicKeyBlob Structure</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)
- [<span data-ttu-id="ac344-133">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ac344-133">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
