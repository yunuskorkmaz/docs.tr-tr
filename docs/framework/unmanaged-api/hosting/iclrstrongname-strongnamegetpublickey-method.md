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
ms.openlocfilehash: 943251357a91ea9ae3d492fa7bf20eebf948b8b2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73135070"
---
# <a name="iclrstrongnamestrongnamegetpublickey-method"></a><span data-ttu-id="8c482-102">ICLRStrongName::StrongNameGetPublicKey Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8c482-102">ICLRStrongName::StrongNameGetPublicKey Method</span></span>
<span data-ttu-id="8c482-103">Ortak/özel anahtar çiftinden ortak anahtarı alır.</span><span class="sxs-lookup"><span data-stu-id="8c482-103">Gets the public key from a public/private key pair.</span></span> <span data-ttu-id="8c482-104">Anahtar çifti, bir şifreleme hizmeti sağlayıcısı (CSP) içinde anahtar kapsayıcı adı olarak veya ham bir bayt koleksiyonu olarak sağlanabilir.</span><span class="sxs-lookup"><span data-stu-id="8c482-104">The key pair can be supplied either as a key container name within a cryptographic service provider (CSP) or as a raw collection of bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c482-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8c482-105">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameGetPublicKey (   
    [in]  LPCWSTR   szKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8c482-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8c482-106">Parameters</span></span>  
 `szKeyContainer`  
 <span data-ttu-id="8c482-107">'ndaki Ortak/özel anahtar çiftini içeren anahtar kapsayıcısının adı.</span><span class="sxs-lookup"><span data-stu-id="8c482-107">[in] The name of the key container that contains the public/private key pair.</span></span> <span data-ttu-id="8c482-108">`pbKeyBlob` null ise, `szKeyContainer` CSP içinde geçerli bir kapsayıcı belirtmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="8c482-108">If `pbKeyBlob` is null, `szKeyContainer` must specify a valid container within the CSP.</span></span> <span data-ttu-id="8c482-109">Bu durumda, [ICLRStrongName:: StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md) yöntemi kapsayıcıda depolanan anahtar çiftinden ortak anahtarı ayıklar.</span><span class="sxs-lookup"><span data-stu-id="8c482-109">In this case, the [ICLRStrongName::StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md) method extracts the public key from the key pair stored in the container.</span></span>  
  
 <span data-ttu-id="8c482-110">`pbKeyBlob` null değilse, anahtar çiftinin anahtar ikili büyük nesne (BLOB) içinde yer aldığı varsayılır.</span><span class="sxs-lookup"><span data-stu-id="8c482-110">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="8c482-111">Anahtarlar 1024-bit Rivest-Shamir-Adtaman (RSA) imzalama anahtarları olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8c482-111">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="8c482-112">Şu anda başka türde anahtarlar desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="8c482-112">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="8c482-113">'ndaki Ortak/özel anahtar çifti işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="8c482-113">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="8c482-114">Bu çift, Win32 `CryptExportKey` işlevi tarafından oluşturulan biçimdedir.</span><span class="sxs-lookup"><span data-stu-id="8c482-114">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="8c482-115">`pbKeyBlob` null ise, `szKeyContainer` tarafından belirtilen anahtar kapsayıcısının anahtar çiftini içermesi varsayılır.</span><span class="sxs-lookup"><span data-stu-id="8c482-115">If `pbKeyBlob` is null, the key container specified by `szKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="8c482-116">'ndaki `pbKeyBlob`bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="8c482-116">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="8c482-117">dışı Döndürülen ortak anahtar blobu.</span><span class="sxs-lookup"><span data-stu-id="8c482-117">[out] The returned public key BLOB.</span></span> <span data-ttu-id="8c482-118">`ppbPublicKeyBlob` parametresi ortak dil çalışma zamanı tarafından ayrılır ve çağırana döndürülür.</span><span class="sxs-lookup"><span data-stu-id="8c482-118">The `ppbPublicKeyBlob` parameter is allocated by the common language runtime and returned to the caller.</span></span> <span data-ttu-id="8c482-119">Çağıranın, [ICLRStrongName:: StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) metodunu kullanarak belleği boşaltmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8c482-119">The caller must free the memory by using the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="8c482-120">dışı Döndürülen ortak anahtar BLOBUNUN boyutu.</span><span class="sxs-lookup"><span data-stu-id="8c482-120">[out] The size of the returned public key BLOB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8c482-121">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8c482-121">Return Value</span></span>  
 <span data-ttu-id="8c482-122">Yöntem başarıyla tamamlanırsa `S_OK`; Aksi takdirde, hata belirten bir HRESULT değeri (bkz. bir liste için [genel HRESULT değerleri](https://go.microsoft.com/fwlink/?LinkId=213878) ).</span><span class="sxs-lookup"><span data-stu-id="8c482-122">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8c482-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8c482-123">Remarks</span></span>  
 <span data-ttu-id="8c482-124">Ortak anahtar, [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) yapısında bulunur.</span><span class="sxs-lookup"><span data-stu-id="8c482-124">The public key is contained in a [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c482-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8c482-125">Requirements</span></span>  
 <span data-ttu-id="8c482-126">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8c482-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c482-127">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="8c482-127">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="8c482-128">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="8c482-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8c482-129">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c482-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c482-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8c482-130">See also</span></span>

- [<span data-ttu-id="8c482-131">StrongNameTokenFromPublicKey Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8c482-131">StrongNameTokenFromPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [<span data-ttu-id="8c482-132">PublicKeyBlob Yapısı</span><span class="sxs-lookup"><span data-stu-id="8c482-132">PublicKeyBlob Structure</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)
- [<span data-ttu-id="8c482-133">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8c482-133">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
