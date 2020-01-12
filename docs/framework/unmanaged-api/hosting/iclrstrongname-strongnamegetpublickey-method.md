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
ms.openlocfilehash: fd7f95ea01de397509c2a7b5fc08c0ac401a8da9
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75899602"
---
# <a name="iclrstrongnamestrongnamegetpublickey-method"></a><span data-ttu-id="63388-102">ICLRStrongName::StrongNameGetPublicKey Yöntemi</span><span class="sxs-lookup"><span data-stu-id="63388-102">ICLRStrongName::StrongNameGetPublicKey Method</span></span>
<span data-ttu-id="63388-103">Ortak/özel anahtar çiftinden ortak anahtarı alır.</span><span class="sxs-lookup"><span data-stu-id="63388-103">Gets the public key from a public/private key pair.</span></span> <span data-ttu-id="63388-104">Anahtar çifti, bir şifreleme hizmeti sağlayıcısı (CSP) içinde anahtar kapsayıcı adı olarak veya ham bir bayt koleksiyonu olarak sağlanabilir.</span><span class="sxs-lookup"><span data-stu-id="63388-104">The key pair can be supplied either as a key container name within a cryptographic service provider (CSP) or as a raw collection of bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63388-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="63388-105">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameGetPublicKey (   
    [in]  LPCWSTR   szKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="63388-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="63388-106">Parameters</span></span>  
 `szKeyContainer`  
 <span data-ttu-id="63388-107">'ndaki Ortak/özel anahtar çiftini içeren anahtar kapsayıcısının adı.</span><span class="sxs-lookup"><span data-stu-id="63388-107">[in] The name of the key container that contains the public/private key pair.</span></span> <span data-ttu-id="63388-108">`pbKeyBlob` null ise, `szKeyContainer` CSP içinde geçerli bir kapsayıcı belirtmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="63388-108">If `pbKeyBlob` is null, `szKeyContainer` must specify a valid container within the CSP.</span></span> <span data-ttu-id="63388-109">Bu durumda, [ICLRStrongName:: StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md) yöntemi kapsayıcıda depolanan anahtar çiftinden ortak anahtarı ayıklar.</span><span class="sxs-lookup"><span data-stu-id="63388-109">In this case, the [ICLRStrongName::StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md) method extracts the public key from the key pair stored in the container.</span></span>  
  
 <span data-ttu-id="63388-110">`pbKeyBlob` null değilse, anahtar çiftinin anahtar ikili büyük nesne (BLOB) içinde yer aldığı varsayılır.</span><span class="sxs-lookup"><span data-stu-id="63388-110">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="63388-111">Anahtarlar 1024-bit Rivest-Shamir-Adtaman (RSA) imzalama anahtarları olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="63388-111">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="63388-112">Şu anda başka türde anahtarlar desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="63388-112">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="63388-113">'ndaki Ortak/özel anahtar çifti işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="63388-113">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="63388-114">Bu çift, Win32 `CryptExportKey` işlevi tarafından oluşturulan biçimdedir.</span><span class="sxs-lookup"><span data-stu-id="63388-114">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="63388-115">`pbKeyBlob` null ise, `szKeyContainer` tarafından belirtilen anahtar kapsayıcısının anahtar çiftini içermesi varsayılır.</span><span class="sxs-lookup"><span data-stu-id="63388-115">If `pbKeyBlob` is null, the key container specified by `szKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="63388-116">'ndaki `pbKeyBlob`bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="63388-116">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="63388-117">dışı Döndürülen ortak anahtar blobu.</span><span class="sxs-lookup"><span data-stu-id="63388-117">[out] The returned public key BLOB.</span></span> <span data-ttu-id="63388-118">`ppbPublicKeyBlob` parametresi ortak dil çalışma zamanı tarafından ayrılır ve çağırana döndürülür.</span><span class="sxs-lookup"><span data-stu-id="63388-118">The `ppbPublicKeyBlob` parameter is allocated by the common language runtime and returned to the caller.</span></span> <span data-ttu-id="63388-119">Çağıranın, [ICLRStrongName:: StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) metodunu kullanarak belleği boşaltmalıdır.</span><span class="sxs-lookup"><span data-stu-id="63388-119">The caller must free the memory by using the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="63388-120">dışı Döndürülen ortak anahtar BLOBUNUN boyutu.</span><span class="sxs-lookup"><span data-stu-id="63388-120">[out] The size of the returned public key BLOB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="63388-121">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="63388-121">Return Value</span></span>  
 <span data-ttu-id="63388-122">Yöntem başarıyla tamamlanırsa `S_OK`; Aksi takdirde, hata belirten bir HRESULT değeri (bkz. bir liste için [genel HRESULT değerleri](/windows/win32/seccrypto/common-hresult-values) ).</span><span class="sxs-lookup"><span data-stu-id="63388-122">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="63388-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="63388-123">Remarks</span></span>  
 <span data-ttu-id="63388-124">Ortak anahtar, [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) yapısında bulunur.</span><span class="sxs-lookup"><span data-stu-id="63388-124">The public key is contained in a [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63388-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="63388-125">Requirements</span></span>  
 <span data-ttu-id="63388-126">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="63388-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63388-127">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="63388-127">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="63388-128">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="63388-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="63388-129">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63388-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63388-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="63388-130">See also</span></span>

- [<span data-ttu-id="63388-131">StrongNameTokenFromPublicKey Yöntemi</span><span class="sxs-lookup"><span data-stu-id="63388-131">StrongNameTokenFromPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [<span data-ttu-id="63388-132">PublicKeyBlob Yapısı</span><span class="sxs-lookup"><span data-stu-id="63388-132">PublicKeyBlob Structure</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)
- [<span data-ttu-id="63388-133">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="63388-133">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
