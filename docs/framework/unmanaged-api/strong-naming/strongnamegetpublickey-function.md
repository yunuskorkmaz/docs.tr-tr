---
title: "StrongNameGetPublicKey İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- StrongNameGetPublicKey
api_location:
- mscoree.dll
- mscorsn.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameGetPublicKey
helpviewer_keywords:
- StrongNameGetPublicKey function [.NET Framework strong naming]
ms.assetid: 5b58c87f-3f72-40df-9b9a-291076931cc3
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: cec7c1edac24d43924abb2bf8784d45ed6372129
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="strongnamegetpublickey-function"></a><span data-ttu-id="d23c3-102">StrongNameGetPublicKey İşlevi</span><span class="sxs-lookup"><span data-stu-id="d23c3-102">StrongNameGetPublicKey Function</span></span>
<span data-ttu-id="d23c3-103">Ortak anahtarı bir özel/ortak anahtar çifti alır.</span><span class="sxs-lookup"><span data-stu-id="d23c3-103">Gets the public key from a private/public key pair.</span></span> <span data-ttu-id="d23c3-104">Anahtar çifti, şifreleme hizmeti sağlayıcısı (CSP) içinde bir anahtar kapsayıcı adı veya ham bayt koleksiyonu olarak sağlanabilir.</span><span class="sxs-lookup"><span data-stu-id="d23c3-104">The key pair can be supplied either as a key container name within a cryptographic service provider (CSP) or as a raw collection of bytes.</span></span>  
  
 <span data-ttu-id="d23c3-105">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="d23c3-105">This function has been deprecated.</span></span> <span data-ttu-id="d23c3-106">Kullanım [Iclrstrongname::strongnamegetpublickey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md) yöntemi yerine.</span><span class="sxs-lookup"><span data-stu-id="d23c3-106">Use the [ICLRStrongName::StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d23c3-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d23c3-107">Syntax</span></span>  
  
```  
BOOLEAN StrongNameGetPublicKey (   
    [in]  LPCWSTR   szKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d23c3-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d23c3-108">Parameters</span></span>  
 `szKeyContainer`  
 <span data-ttu-id="d23c3-109">[in] Ortak/özel anahtar çiftini içeren anahtar kapsayıcı adı.</span><span class="sxs-lookup"><span data-stu-id="d23c3-109">[in] The name of the key container that contains the public/private key pair.</span></span> <span data-ttu-id="d23c3-110">Varsa `pbKeyBlob` null, `szKeyContainer` CSP Geçerli kapsayıcıda belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="d23c3-110">If `pbKeyBlob` is null, `szKeyContainer` must specify a valid container within the CSP.</span></span> <span data-ttu-id="d23c3-111">Bu durumda, `StrongNameGetPublicKey` kapsayıcısında depolanan anahtar çifti gelen ortak anahtarı ayıklar.</span><span class="sxs-lookup"><span data-stu-id="d23c3-111">In this case, `StrongNameGetPublicKey` extracts the public key from the key pair stored in the container.</span></span>  
  
 <span data-ttu-id="d23c3-112">Varsa `pbKeyBlob` anahtar çifti varsayılır anahtar ikili büyük nesne (BLOB) dahil edilmek üzere null değil.</span><span class="sxs-lookup"><span data-stu-id="d23c3-112">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="d23c3-113">1024 bit Rivest-Shamir-Adleman (RSA) anahtarları İmzalama anahtarları olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d23c3-113">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="d23c3-114">Başka tür anahtarları şu anda desteklenir.</span><span class="sxs-lookup"><span data-stu-id="d23c3-114">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="d23c3-115">[in] Ortak/özel anahtar çifti için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d23c3-115">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="d23c3-116">Bu çiftidir Win32 tarafından oluşturulan biçiminde `CryptExportKey` işlevi.</span><span class="sxs-lookup"><span data-stu-id="d23c3-116">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="d23c3-117">Varsa `pbKeyBlob` null, belirtilen anahtar kapsayıcısı olan `szKeyContainer` anahtar çiftini içeren varsayılır.</span><span class="sxs-lookup"><span data-stu-id="d23c3-117">If `pbKeyBlob` is null, the key container specified by `szKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="d23c3-118">[in] Bayt olarak boyutu, `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="d23c3-118">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="d23c3-119">[out] Döndürülen ortak anahtarı BLOB.</span><span class="sxs-lookup"><span data-stu-id="d23c3-119">[out] The returned public key BLOB.</span></span> <span data-ttu-id="d23c3-120">`ppbPublicKeyBlob` Parametresi ortak dil çalışma zamanı tarafından ayrılmış ve yapana.</span><span class="sxs-lookup"><span data-stu-id="d23c3-120">The `ppbPublicKeyBlob` parameter is allocated by the common language runtime and returned to the caller.</span></span> <span data-ttu-id="d23c3-121">Kullanarak, çağıran belleği serbest gerekir [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="d23c3-121">The caller must free the memory by using the [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) function.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="d23c3-122">[out] Döndürülen ortak anahtarı BLOB boyutu.</span><span class="sxs-lookup"><span data-stu-id="d23c3-122">[out] The size of the returned public key BLOB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d23c3-123">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d23c3-123">Return Value</span></span>  
 <span data-ttu-id="d23c3-124">`true`başarılı tamamlanma; Aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="d23c3-124">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d23c3-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d23c3-125">Remarks</span></span>  
 <span data-ttu-id="d23c3-126">Ortak anahtar içeren bir [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) yapısı.</span><span class="sxs-lookup"><span data-stu-id="d23c3-126">The public key is contained in a [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) structure.</span></span>  
  
 <span data-ttu-id="d23c3-127">Varsa `StrongNameGetPublicKey` işlevi yok başarıyla tamamlanması, çağrı [Strongnameerrorınfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) son oluşturulan hata alınacak işlev.</span><span class="sxs-lookup"><span data-stu-id="d23c3-127">If the `StrongNameGetPublicKey` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d23c3-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d23c3-128">Requirements</span></span>  
 <span data-ttu-id="d23c3-129">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d23c3-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d23c3-130">**Başlık:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="d23c3-130">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="d23c3-131">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="d23c3-131">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d23c3-132">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d23c3-132">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d23c3-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d23c3-133">See Also</span></span>  
 [<span data-ttu-id="d23c3-134">StrongNameGetPublicKey Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d23c3-134">StrongNameGetPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)  
 [<span data-ttu-id="d23c3-135">StrongNameTokenFromPublicKey Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d23c3-135">StrongNameTokenFromPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)  
 [<span data-ttu-id="d23c3-136">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d23c3-136">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)  
 [<span data-ttu-id="d23c3-137">PublicKeyBlob Yapısı</span><span class="sxs-lookup"><span data-stu-id="d23c3-137">PublicKeyBlob Structure</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)
