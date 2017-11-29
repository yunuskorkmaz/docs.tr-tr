---
title: "StrongNameGetPublicKeyEx Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRStrongName2.StrongNameGetPublicKeyEx
api_location: mscoree.dll
api_type: COM
f1_keywords: StrongNameGetPublicKeyEx
helpviewer_keywords:
- StrongNameGetPublicKeyEx method, ICLRStrongName2 interface [.NET Framework hosting]
- ICLRStrongName2::StrongNameGetPublicKeyEx method [.NET Framework hosting]
ms.assetid: 63d8260c-fb32-4f8f-a357-768afd570f68
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f39c5c948d43fd0e9387c1cc0319a46d25ec86ec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="strongnamegetpublickeyex-method"></a><span data-ttu-id="5ab4b-102">StrongNameGetPublicKeyEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5ab4b-102">StrongNameGetPublicKeyEx Method</span></span>
<span data-ttu-id="5ab4b-103">Ortak anahtarı bir genel/özel anahtar çifti alır ve bir karma algoritması ve imza algoritmasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5ab4b-103">Gets the public key from a public/private key pair, and specifies a hash algorithm and a signature algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ab4b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5ab4b-104">Syntax</span></span>  
  
```  
HRESULT StrongNameGetPublicKey (   
    [in]  LPCWSTR   pwzKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
    [in]  ULONG     uHashAlgId,  
    [in]  ULONG     uReserved,  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5ab4b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5ab4b-105">Parameters</span></span>  
 `pwzKeyContainer`  
 <span data-ttu-id="5ab4b-106">[in] Ortak/özel anahtar çiftini içeren anahtar kapsayıcı adı.</span><span class="sxs-lookup"><span data-stu-id="5ab4b-106">[in] The name of the key container that contains the public/private key pair.</span></span> <span data-ttu-id="5ab4b-107">Varsa `pbKeyBlob` null, `szKeyContainer` şifreleme hizmeti sağlayıcısı (CSP) geçerli bir kapsayıcıda belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="5ab4b-107">If `pbKeyBlob` is null, `szKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="5ab4b-108">Bu durumda, `StrongNameGetPublicKeyEx` yöntemi kapsayıcısında depolanan anahtar çifti gelen ortak anahtarı ayıklar.</span><span class="sxs-lookup"><span data-stu-id="5ab4b-108">In this case, the `StrongNameGetPublicKeyEx` method extracts the public key from the key pair stored in the container.</span></span>  
  
 <span data-ttu-id="5ab4b-109">Varsa `pbKeyBlob` anahtar çifti varsayılır anahtar ikili büyük nesne (BLOB) dahil edilmek üzere null değil.</span><span class="sxs-lookup"><span data-stu-id="5ab4b-109">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="5ab4b-110">1024 bit Rivest-Shamir-Adleman (RSA) anahtarları İmzalama anahtarları olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5ab4b-110">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="5ab4b-111">Başka tür anahtarları şu anda desteklenir.</span><span class="sxs-lookup"><span data-stu-id="5ab4b-111">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="5ab4b-112">[in] Ortak/özel anahtar çifti için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5ab4b-112">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="5ab4b-113">Bu çiftidir Win32 tarafından oluşturulan biçiminde `CryptExportKey` işlevi.</span><span class="sxs-lookup"><span data-stu-id="5ab4b-113">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="5ab4b-114">Varsa `pbKeyBlob` null, belirtilen anahtar kapsayıcısı olan `szKeyContainer` anahtar çiftini içeren varsayılır.</span><span class="sxs-lookup"><span data-stu-id="5ab4b-114">If `pbKeyBlob` is null, the key container specified by `szKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="5ab4b-115">[in] Bayt olarak boyutu, `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="5ab4b-115">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="5ab4b-116">[out] Döndürülen ortak anahtarı BLOB.</span><span class="sxs-lookup"><span data-stu-id="5ab4b-116">[out] The returned public key BLOB.</span></span> <span data-ttu-id="5ab4b-117">`ppbPublicKeyBlob` Parametresi ortak dil çalışma zamanı tarafından ayrılmış ve yapana.</span><span class="sxs-lookup"><span data-stu-id="5ab4b-117">The `ppbPublicKeyBlob` parameter is allocated by the common language runtime and returned to the caller.</span></span> <span data-ttu-id="5ab4b-118">Kullanarak, çağıran belleği serbest gerekir [Iclrstrongname::strongnamefreebuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5ab4b-118">The caller must free the memory by using the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="5ab4b-119">[out] Döndürülen ortak anahtarı BLOB boyutu.</span><span class="sxs-lookup"><span data-stu-id="5ab4b-119">[out] The size of the returned public key BLOB.</span></span>  
  
 `uHashAlgId`  
 <span data-ttu-id="5ab4b-120">[in] Derleme karma algoritması.</span><span class="sxs-lookup"><span data-stu-id="5ab4b-120">[in] The assembly hash algorithm.</span></span> <span data-ttu-id="5ab4b-121">Kabul edilen değerlerin listesi için Açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="5ab4b-121">See the Remarks section for a list of accepted values.</span></span>  
  
 `uReserved`  
 <span data-ttu-id="5ab4b-122">[in] Gelecekte kullanılmak üzere ayrılmış; Varsayılan değeri: null.</span><span class="sxs-lookup"><span data-stu-id="5ab4b-122">[in] Reserved for future use; defaults to null.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5ab4b-123">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5ab4b-123">Return Value</span></span>  
 <span data-ttu-id="5ab4b-124">`S_OK`Yöntem başarıyla tamamlandı Aksi takdirde hata belirten bir HRESULT değeri (bkz [ortak HRESULT değerleri](http://go.microsoft.com/fwlink/?LinkId=213878) bir listesi için).</span><span class="sxs-lookup"><span data-stu-id="5ab4b-124">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5ab4b-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5ab4b-125">Remarks</span></span>  
 <span data-ttu-id="5ab4b-126">Ortak anahtar içeren bir [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) yapısı.</span><span class="sxs-lookup"><span data-stu-id="5ab4b-126">The public key is contained in a [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5ab4b-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5ab4b-127">Remarks</span></span>  
 <span data-ttu-id="5ab4b-128">Aşağıdaki tabloda için kabul edilen değerler kümesi gösterilmektedir `uHashAlgId` parametresi.</span><span class="sxs-lookup"><span data-stu-id="5ab4b-128">The following table shows the set of accepted values for the `uHashAlgId` parameter.</span></span>  
  
|<span data-ttu-id="5ab4b-129">Ad</span><span class="sxs-lookup"><span data-stu-id="5ab4b-129">Name</span></span>|<span data-ttu-id="5ab4b-130">Değer</span><span class="sxs-lookup"><span data-stu-id="5ab4b-130">Value</span></span>|  
|----------|-----------|  
|<span data-ttu-id="5ab4b-131">Yok.</span><span class="sxs-lookup"><span data-stu-id="5ab4b-131">None</span></span>|<span data-ttu-id="5ab4b-132">0</span><span class="sxs-lookup"><span data-stu-id="5ab4b-132">0</span></span>|  
|<span data-ttu-id="5ab4b-133">SHA-1</span><span class="sxs-lookup"><span data-stu-id="5ab4b-133">SHA-1</span></span>|<span data-ttu-id="5ab4b-134">0x8004</span><span class="sxs-lookup"><span data-stu-id="5ab4b-134">0x8004</span></span>|  
|<span data-ttu-id="5ab4b-135">SHA-256</span><span class="sxs-lookup"><span data-stu-id="5ab4b-135">SHA-256</span></span>|<span data-ttu-id="5ab4b-136">0x800c</span><span class="sxs-lookup"><span data-stu-id="5ab4b-136">0x800c</span></span>|  
|<span data-ttu-id="5ab4b-137">SHA-384</span><span class="sxs-lookup"><span data-stu-id="5ab4b-137">SHA-384</span></span>|<span data-ttu-id="5ab4b-138">0x800d</span><span class="sxs-lookup"><span data-stu-id="5ab4b-138">0x800d</span></span>|  
|<span data-ttu-id="5ab4b-139">SHA-512</span><span class="sxs-lookup"><span data-stu-id="5ab4b-139">SHA-512</span></span>|<span data-ttu-id="5ab4b-140">0x800e</span><span class="sxs-lookup"><span data-stu-id="5ab4b-140">0x800e</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5ab4b-141">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5ab4b-141">Requirements</span></span>  
 <span data-ttu-id="5ab4b-142">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5ab4b-142">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ab4b-143">**Başlık:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="5ab4b-143">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="5ab4b-144">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="5ab4b-144">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5ab4b-145">**.NET framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ab4b-145">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ab4b-146">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5ab4b-146">See Also</span></span>  
 [<span data-ttu-id="5ab4b-147">StrongNameTokenFromPublicKey yöntemi</span><span class="sxs-lookup"><span data-stu-id="5ab4b-147">StrongNameTokenFromPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)  
 [<span data-ttu-id="5ab4b-148">PublicKeyBlob yapısı</span><span class="sxs-lookup"><span data-stu-id="5ab4b-148">PublicKeyBlob Structure</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)  
 [<span data-ttu-id="5ab4b-149">Iclrstrongname arabirimi</span><span class="sxs-lookup"><span data-stu-id="5ab4b-149">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)  
 [<span data-ttu-id="5ab4b-150">StrongNameGetPublicKey yöntemi</span><span class="sxs-lookup"><span data-stu-id="5ab4b-150">StrongNameGetPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)
