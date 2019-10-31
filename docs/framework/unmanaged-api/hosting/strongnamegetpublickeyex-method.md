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
ms.openlocfilehash: 700bcc5b818c452d3642d325fb6fe19cbb162474
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141451"
---
# <a name="strongnamegetpublickeyex-method"></a><span data-ttu-id="34e0d-102">StrongNameGetPublicKeyEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="34e0d-102">StrongNameGetPublicKeyEx Method</span></span>
<span data-ttu-id="34e0d-103">Ortak/özel anahtar çiftinden ortak anahtarı alır ve bir karma algoritmasını ve bir imza algoritmasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="34e0d-103">Gets the public key from a public/private key pair, and specifies a hash algorithm and a signature algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34e0d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="34e0d-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="34e0d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="34e0d-105">Parameters</span></span>  
 `pwzKeyContainer`  
 <span data-ttu-id="34e0d-106">'ndaki Ortak/özel anahtar çiftini içeren anahtar kapsayıcısının adı.</span><span class="sxs-lookup"><span data-stu-id="34e0d-106">[in] The name of the key container that contains the public/private key pair.</span></span> <span data-ttu-id="34e0d-107">`pbKeyBlob` null ise, `szKeyContainer` şifreleme hizmeti sağlayıcısı 'nda (CSP) geçerli bir kapsayıcı belirtmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="34e0d-107">If `pbKeyBlob` is null, `szKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="34e0d-108">Bu durumda `StrongNameGetPublicKeyEx` yöntemi, kapsayıcıda depolanan anahtar çiftinden ortak anahtarı ayıklar.</span><span class="sxs-lookup"><span data-stu-id="34e0d-108">In this case, the `StrongNameGetPublicKeyEx` method extracts the public key from the key pair stored in the container.</span></span>  
  
 <span data-ttu-id="34e0d-109">`pbKeyBlob` null değilse, anahtar çiftinin anahtar ikili büyük nesne (BLOB) içinde yer aldığı varsayılır.</span><span class="sxs-lookup"><span data-stu-id="34e0d-109">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="34e0d-110">Anahtarlar 1024-bit Rivest-Shamir-Adtaman (RSA) imzalama anahtarları olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="34e0d-110">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="34e0d-111">Şu anda başka türde anahtarlar desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="34e0d-111">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="34e0d-112">'ndaki Ortak/özel anahtar çifti işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="34e0d-112">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="34e0d-113">Bu çift, Win32 `CryptExportKey` işlevi tarafından oluşturulan biçimdedir.</span><span class="sxs-lookup"><span data-stu-id="34e0d-113">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="34e0d-114">`pbKeyBlob` null ise, `szKeyContainer` tarafından belirtilen anahtar kapsayıcısının anahtar çiftini içermesi varsayılır.</span><span class="sxs-lookup"><span data-stu-id="34e0d-114">If `pbKeyBlob` is null, the key container specified by `szKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="34e0d-115">'ndaki `pbKeyBlob`bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="34e0d-115">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="34e0d-116">dışı Döndürülen ortak anahtar blobu.</span><span class="sxs-lookup"><span data-stu-id="34e0d-116">[out] The returned public key BLOB.</span></span> <span data-ttu-id="34e0d-117">`ppbPublicKeyBlob` parametresi ortak dil çalışma zamanı tarafından ayrılır ve çağırana döndürülür.</span><span class="sxs-lookup"><span data-stu-id="34e0d-117">The `ppbPublicKeyBlob` parameter is allocated by the common language runtime and returned to the caller.</span></span> <span data-ttu-id="34e0d-118">Çağıranın, [ICLRStrongName:: StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) metodunu kullanarak belleği boşaltmalıdır.</span><span class="sxs-lookup"><span data-stu-id="34e0d-118">The caller must free the memory by using the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="34e0d-119">dışı Döndürülen ortak anahtar BLOBUNUN boyutu.</span><span class="sxs-lookup"><span data-stu-id="34e0d-119">[out] The size of the returned public key BLOB.</span></span>  
  
 `uHashAlgId`  
 <span data-ttu-id="34e0d-120">'ndaki Bütünleştirilmiş kod karma algoritması.</span><span class="sxs-lookup"><span data-stu-id="34e0d-120">[in] The assembly hash algorithm.</span></span> <span data-ttu-id="34e0d-121">Kabul edilen değerlerin bir listesi için bkz. açıklamalar bölümü.</span><span class="sxs-lookup"><span data-stu-id="34e0d-121">See the Remarks section for a list of accepted values.</span></span>  
  
 `uReserved`  
 <span data-ttu-id="34e0d-122">'ndaki Gelecekte kullanılmak üzere ayrılmıştır; Varsayılan olarak null değerini alır.</span><span class="sxs-lookup"><span data-stu-id="34e0d-122">[in] Reserved for future use; defaults to null.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="34e0d-123">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="34e0d-123">Return Value</span></span>  
 <span data-ttu-id="34e0d-124">Yöntem başarıyla tamamlanırsa `S_OK`; Aksi takdirde, hata belirten bir HRESULT değeri (bkz. bir liste için [genel HRESULT değerleri](https://go.microsoft.com/fwlink/?LinkId=213878) ).</span><span class="sxs-lookup"><span data-stu-id="34e0d-124">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="34e0d-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="34e0d-125">Remarks</span></span>  
 <span data-ttu-id="34e0d-126">Ortak anahtar, [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) yapısında bulunur.</span><span class="sxs-lookup"><span data-stu-id="34e0d-126">The public key is contained in a [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="34e0d-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="34e0d-127">Remarks</span></span>  
 <span data-ttu-id="34e0d-128">Aşağıdaki tabloda `uHashAlgId` parametresi için kabul edilen değerler kümesi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="34e0d-128">The following table shows the set of accepted values for the `uHashAlgId` parameter.</span></span>  
  
|<span data-ttu-id="34e0d-129">Name</span><span class="sxs-lookup"><span data-stu-id="34e0d-129">Name</span></span>|<span data-ttu-id="34e0d-130">Değer</span><span class="sxs-lookup"><span data-stu-id="34e0d-130">Value</span></span>|  
|----------|-----------|  
|<span data-ttu-id="34e0d-131">Yok.</span><span class="sxs-lookup"><span data-stu-id="34e0d-131">None</span></span>|<span data-ttu-id="34e0d-132">0</span><span class="sxs-lookup"><span data-stu-id="34e0d-132">0</span></span>|  
|<span data-ttu-id="34e0d-133">SHA-1</span><span class="sxs-lookup"><span data-stu-id="34e0d-133">SHA-1</span></span>|<span data-ttu-id="34e0d-134">0x8004</span><span class="sxs-lookup"><span data-stu-id="34e0d-134">0x8004</span></span>|  
|<span data-ttu-id="34e0d-135">SHA-256</span><span class="sxs-lookup"><span data-stu-id="34e0d-135">SHA-256</span></span>|<span data-ttu-id="34e0d-136">0x800c</span><span class="sxs-lookup"><span data-stu-id="34e0d-136">0x800c</span></span>|  
|<span data-ttu-id="34e0d-137">SHA-384</span><span class="sxs-lookup"><span data-stu-id="34e0d-137">SHA-384</span></span>|<span data-ttu-id="34e0d-138">0x800d</span><span class="sxs-lookup"><span data-stu-id="34e0d-138">0x800d</span></span>|  
|<span data-ttu-id="34e0d-139">SHA-512</span><span class="sxs-lookup"><span data-stu-id="34e0d-139">SHA-512</span></span>|<span data-ttu-id="34e0d-140">0x800e</span><span class="sxs-lookup"><span data-stu-id="34e0d-140">0x800e</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="34e0d-141">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="34e0d-141">Requirements</span></span>  
 <span data-ttu-id="34e0d-142">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="34e0d-142">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="34e0d-143">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="34e0d-143">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="34e0d-144">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="34e0d-144">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="34e0d-145">**.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="34e0d-145">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34e0d-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="34e0d-146">See also</span></span>

- [<span data-ttu-id="34e0d-147">StrongNameTokenFromPublicKey Yöntemi</span><span class="sxs-lookup"><span data-stu-id="34e0d-147">StrongNameTokenFromPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [<span data-ttu-id="34e0d-148">PublicKeyBlob Yapısı</span><span class="sxs-lookup"><span data-stu-id="34e0d-148">PublicKeyBlob Structure</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)
- [<span data-ttu-id="34e0d-149">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="34e0d-149">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
- [<span data-ttu-id="34e0d-150">StrongNameGetPublicKey Yöntemi</span><span class="sxs-lookup"><span data-stu-id="34e0d-150">StrongNameGetPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)
