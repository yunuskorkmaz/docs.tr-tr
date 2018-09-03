---
title: StrongNameGetPublicKeyEx Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRStrongName2.StrongNameGetPublicKeyEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- StrongNameGetPublicKeyEx
helpviewer_keywords:
- StrongNameGetPublicKeyEx method, ICLRStrongName2 interface [.NET Framework hosting]
- ICLRStrongName2::StrongNameGetPublicKeyEx method [.NET Framework hosting]
ms.assetid: 63d8260c-fb32-4f8f-a357-768afd570f68
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 82dbacdcf89a44455bb4963e73dc5e91bda1cbc7
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43482456"
---
# <a name="strongnamegetpublickeyex-method"></a><span data-ttu-id="105a2-102">StrongNameGetPublicKeyEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="105a2-102">StrongNameGetPublicKeyEx Method</span></span>
<span data-ttu-id="105a2-103">Bir ortak/özel anahtar çiftinden ortak anahtarı alır ve bir karma algoritması ve imza algoritmasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="105a2-103">Gets the public key from a public/private key pair, and specifies a hash algorithm and a signature algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="105a2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="105a2-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="105a2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="105a2-105">Parameters</span></span>  
 `pwzKeyContainer`  
 <span data-ttu-id="105a2-106">[in] Ortak/özel anahtar çiftini içeren anahtar kapsayıcısının adı.</span><span class="sxs-lookup"><span data-stu-id="105a2-106">[in] The name of the key container that contains the public/private key pair.</span></span> <span data-ttu-id="105a2-107">Varsa `pbKeyBlob` boş `szKeyContainer` şifreleme hizmeti sağlayıcısı (CSP) geçerli bir kapsayıcıda belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="105a2-107">If `pbKeyBlob` is null, `szKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="105a2-108">Bu durumda, `StrongNameGetPublicKeyEx` yöntemi, bir kapsayıcıda depolanan bir anahtar çifti öğesinden ortak anahtarı ayıklar.</span><span class="sxs-lookup"><span data-stu-id="105a2-108">In this case, the `StrongNameGetPublicKeyEx` method extracts the public key from the key pair stored in the container.</span></span>  
  
 <span data-ttu-id="105a2-109">Varsa `pbKeyBlob` anahtar çiftini varsayılır anahtar ikili büyük nesne içinde (BLOB) dahil edilmek üzere null değil.</span><span class="sxs-lookup"><span data-stu-id="105a2-109">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="105a2-110">Anahtarları 1024 bit Rivest-Shamir-Adleman (RSA) imzalama anahtarı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="105a2-110">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="105a2-111">Anahtarlar başka tür bu zaman desteklenir.</span><span class="sxs-lookup"><span data-stu-id="105a2-111">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="105a2-112">[in] Ortak/özel anahtar çifti için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="105a2-112">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="105a2-113">Win32 oluşturulan biçimde bu çiftidir `CryptExportKey` işlevi.</span><span class="sxs-lookup"><span data-stu-id="105a2-113">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="105a2-114">Varsa `pbKeyBlob` null, belirtilen anahtar kapsayıcısı olan `szKeyContainer` anahtar çiftini içerdiği varsayılır.</span><span class="sxs-lookup"><span data-stu-id="105a2-114">If `pbKeyBlob` is null, the key container specified by `szKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="105a2-115">[in] Bayt cinsinden boyutu, `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="105a2-115">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="105a2-116">[out] Döndürülen ortak anahtarı BLOB.</span><span class="sxs-lookup"><span data-stu-id="105a2-116">[out] The returned public key BLOB.</span></span> <span data-ttu-id="105a2-117">`ppbPublicKeyBlob` Parametre ortak dil çalışma zamanı tarafından ayrılmış ve arayana döndürülür.</span><span class="sxs-lookup"><span data-stu-id="105a2-117">The `ppbPublicKeyBlob` parameter is allocated by the common language runtime and returned to the caller.</span></span> <span data-ttu-id="105a2-118">Arayanın bellek kullanarak ücretsiz gerekir [Iclrstrongname::strongnamefreebuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="105a2-118">The caller must free the memory by using the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="105a2-119">[out] Döndürülen ortak anahtarı BLOB boyutu.</span><span class="sxs-lookup"><span data-stu-id="105a2-119">[out] The size of the returned public key BLOB.</span></span>  
  
 `uHashAlgId`  
 <span data-ttu-id="105a2-120">[in] Derleme karma algoritması.</span><span class="sxs-lookup"><span data-stu-id="105a2-120">[in] The assembly hash algorithm.</span></span> <span data-ttu-id="105a2-121">Kabul edilen değerlerin listesi için Açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="105a2-121">See the Remarks section for a list of accepted values.</span></span>  
  
 `uReserved`  
 <span data-ttu-id="105a2-122">[in] Gelecekte kullanılmak üzere ayrılmış; Varsayılan olarak null.</span><span class="sxs-lookup"><span data-stu-id="105a2-122">[in] Reserved for future use; defaults to null.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="105a2-123">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="105a2-123">Return Value</span></span>  
 <span data-ttu-id="105a2-124">`S_OK` yöntemi başarıyla tamamlandı Aksi takdirde hata olduğunu gösteren HRESULT değerini (bkz [ortak HRESULT değerlerini](https://go.microsoft.com/fwlink/?LinkId=213878) bir listesi için).</span><span class="sxs-lookup"><span data-stu-id="105a2-124">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="105a2-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="105a2-125">Remarks</span></span>  
 <span data-ttu-id="105a2-126">Ortak anahtarı içeren bir [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) yapısı.</span><span class="sxs-lookup"><span data-stu-id="105a2-126">The public key is contained in a [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="105a2-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="105a2-127">Remarks</span></span>  
 <span data-ttu-id="105a2-128">Aşağıdaki tablo için kabul edilen değerler kümesini gösterir `uHashAlgId` parametresi.</span><span class="sxs-lookup"><span data-stu-id="105a2-128">The following table shows the set of accepted values for the `uHashAlgId` parameter.</span></span>  
  
|<span data-ttu-id="105a2-129">Ad</span><span class="sxs-lookup"><span data-stu-id="105a2-129">Name</span></span>|<span data-ttu-id="105a2-130">Değer</span><span class="sxs-lookup"><span data-stu-id="105a2-130">Value</span></span>|  
|----------|-----------|  
|<span data-ttu-id="105a2-131">Yok.</span><span class="sxs-lookup"><span data-stu-id="105a2-131">None</span></span>|<span data-ttu-id="105a2-132">0</span><span class="sxs-lookup"><span data-stu-id="105a2-132">0</span></span>|  
|<span data-ttu-id="105a2-133">SHA-1</span><span class="sxs-lookup"><span data-stu-id="105a2-133">SHA-1</span></span>|<span data-ttu-id="105a2-134">0x8004</span><span class="sxs-lookup"><span data-stu-id="105a2-134">0x8004</span></span>|  
|<span data-ttu-id="105a2-135">SHA-256</span><span class="sxs-lookup"><span data-stu-id="105a2-135">SHA-256</span></span>|<span data-ttu-id="105a2-136">0x800c</span><span class="sxs-lookup"><span data-stu-id="105a2-136">0x800c</span></span>|  
|<span data-ttu-id="105a2-137">SHA-384</span><span class="sxs-lookup"><span data-stu-id="105a2-137">SHA-384</span></span>|<span data-ttu-id="105a2-138">0x800d</span><span class="sxs-lookup"><span data-stu-id="105a2-138">0x800d</span></span>|  
|<span data-ttu-id="105a2-139">SHA-512</span><span class="sxs-lookup"><span data-stu-id="105a2-139">SHA-512</span></span>|<span data-ttu-id="105a2-140">0x800e</span><span class="sxs-lookup"><span data-stu-id="105a2-140">0x800e</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="105a2-141">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="105a2-141">Requirements</span></span>  
 <span data-ttu-id="105a2-142">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="105a2-142">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="105a2-143">**Başlık:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="105a2-143">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="105a2-144">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="105a2-144">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="105a2-145">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="105a2-145">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="105a2-146">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="105a2-146">See Also</span></span>  
 [<span data-ttu-id="105a2-147">StrongNameTokenFromPublicKey Yöntemi</span><span class="sxs-lookup"><span data-stu-id="105a2-147">StrongNameTokenFromPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)  
 [<span data-ttu-id="105a2-148">PublicKeyBlob Yapısı</span><span class="sxs-lookup"><span data-stu-id="105a2-148">PublicKeyBlob Structure</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)  
 [<span data-ttu-id="105a2-149">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="105a2-149">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)  
 [<span data-ttu-id="105a2-150">StrongNameGetPublicKey Yöntemi</span><span class="sxs-lookup"><span data-stu-id="105a2-150">StrongNameGetPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)
