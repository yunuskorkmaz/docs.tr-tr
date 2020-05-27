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
ms.openlocfilehash: 1904a98f254a988ce035847a4cdeede182aa07bf
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84006382"
---
# <a name="strongnamegetpublickeyex-method"></a><span data-ttu-id="1393e-102">StrongNameGetPublicKeyEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1393e-102">StrongNameGetPublicKeyEx Method</span></span>
<span data-ttu-id="1393e-103">Ortak/özel anahtar çiftinden ortak anahtarı alır ve bir karma algoritmasını ve bir imza algoritmasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="1393e-103">Gets the public key from a public/private key pair, and specifies a hash algorithm and a signature algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1393e-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="1393e-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="1393e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1393e-105">Parameters</span></span>  
 `pwzKeyContainer`  
 <span data-ttu-id="1393e-106">'ndaki Ortak/özel anahtar çiftini içeren anahtar kapsayıcısının adı.</span><span class="sxs-lookup"><span data-stu-id="1393e-106">[in] The name of the key container that contains the public/private key pair.</span></span> <span data-ttu-id="1393e-107">`pbKeyBlob`Null ise, `szKeyContainer` şifreleme hizmet sağlayıcısı (CSP) içinde geçerli bir kapsayıcı belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="1393e-107">If `pbKeyBlob` is null, `szKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="1393e-108">Bu durumda, `StrongNameGetPublicKeyEx` yöntemi kapsayıcıda depolanan anahtar çiftinden ortak anahtarı ayıklar.</span><span class="sxs-lookup"><span data-stu-id="1393e-108">In this case, the `StrongNameGetPublicKeyEx` method extracts the public key from the key pair stored in the container.</span></span>  
  
 <span data-ttu-id="1393e-109">`pbKeyBlob`Null değilse, anahtar çiftinin anahtar ikili büyük nesne (blob) içinde yer aldığı varsayılır.</span><span class="sxs-lookup"><span data-stu-id="1393e-109">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="1393e-110">Anahtarlar 1024-bit Rivest-Shamir-Adtaman (RSA) imzalama anahtarları olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1393e-110">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="1393e-111">Şu anda başka türde anahtarlar desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="1393e-111">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="1393e-112">'ndaki Ortak/özel anahtar çifti işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="1393e-112">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="1393e-113">Bu çift Win32 işlevi tarafından oluşturulan biçimdedir `CryptExportKey` .</span><span class="sxs-lookup"><span data-stu-id="1393e-113">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="1393e-114">`pbKeyBlob`Null ise, tarafından belirtilen anahtar kapsayıcının `szKeyContainer` anahtar çiftini içermesi varsayılır.</span><span class="sxs-lookup"><span data-stu-id="1393e-114">If `pbKeyBlob` is null, the key container specified by `szKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="1393e-115">'ndaki Bayt cinsinden boyutu `pbKeyBlob` .</span><span class="sxs-lookup"><span data-stu-id="1393e-115">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="1393e-116">dışı Döndürülen ortak anahtar blobu.</span><span class="sxs-lookup"><span data-stu-id="1393e-116">[out] The returned public key BLOB.</span></span> <span data-ttu-id="1393e-117">`ppbPublicKeyBlob`Parametresi ortak dil çalışma zamanı tarafından ayrılır ve çağırana döndürülür.</span><span class="sxs-lookup"><span data-stu-id="1393e-117">The `ppbPublicKeyBlob` parameter is allocated by the common language runtime and returned to the caller.</span></span> <span data-ttu-id="1393e-118">Çağıranın, [ICLRStrongName:: StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) metodunu kullanarak belleği boşaltmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1393e-118">The caller must free the memory by using the [ICLRStrongName::StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="1393e-119">dışı Döndürülen ortak anahtar BLOBUNUN boyutu.</span><span class="sxs-lookup"><span data-stu-id="1393e-119">[out] The size of the returned public key BLOB.</span></span>  
  
 `uHashAlgId`  
 <span data-ttu-id="1393e-120">'ndaki Bütünleştirilmiş kod karma algoritması.</span><span class="sxs-lookup"><span data-stu-id="1393e-120">[in] The assembly hash algorithm.</span></span> <span data-ttu-id="1393e-121">Kabul edilen değerlerin bir listesi için bkz. açıklamalar bölümü.</span><span class="sxs-lookup"><span data-stu-id="1393e-121">See the Remarks section for a list of accepted values.</span></span>  
  
 `uReserved`  
 <span data-ttu-id="1393e-122">'ndaki Gelecekte kullanılmak üzere ayrılmıştır; Varsayılan olarak null değerini alır.</span><span class="sxs-lookup"><span data-stu-id="1393e-122">[in] Reserved for future use; defaults to null.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1393e-123">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="1393e-123">Return Value</span></span>  
 <span data-ttu-id="1393e-124">`S_OK`Yöntem başarıyla tamamlanırsa; Aksi takdirde, hata belirten bir HRESULT değeri (bkz. bir liste için [genel HRESULT değerleri](/windows/win32/seccrypto/common-hresult-values) ).</span><span class="sxs-lookup"><span data-stu-id="1393e-124">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1393e-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1393e-125">Remarks</span></span>  
 <span data-ttu-id="1393e-126">Ortak anahtar, [PublicKeyBlob](../strong-naming/publickeyblob-structure.md) yapısında bulunur.</span><span class="sxs-lookup"><span data-stu-id="1393e-126">The public key is contained in a [PublicKeyBlob](../strong-naming/publickeyblob-structure.md) structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1393e-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1393e-127">Remarks</span></span>  
 <span data-ttu-id="1393e-128">Aşağıdaki tabloda parametresi için kabul edilen değerler kümesi gösterilmektedir `uHashAlgId` .</span><span class="sxs-lookup"><span data-stu-id="1393e-128">The following table shows the set of accepted values for the `uHashAlgId` parameter.</span></span>  
  
|<span data-ttu-id="1393e-129">Name</span><span class="sxs-lookup"><span data-stu-id="1393e-129">Name</span></span>|<span data-ttu-id="1393e-130">Değer</span><span class="sxs-lookup"><span data-stu-id="1393e-130">Value</span></span>|  
|----------|-----------|  
|<span data-ttu-id="1393e-131">Yok</span><span class="sxs-lookup"><span data-stu-id="1393e-131">None</span></span>|<span data-ttu-id="1393e-132">0</span><span class="sxs-lookup"><span data-stu-id="1393e-132">0</span></span>|  
|<span data-ttu-id="1393e-133">SHA-1</span><span class="sxs-lookup"><span data-stu-id="1393e-133">SHA-1</span></span>|<span data-ttu-id="1393e-134">0x8004</span><span class="sxs-lookup"><span data-stu-id="1393e-134">0x8004</span></span>|  
|<span data-ttu-id="1393e-135">SHA-256</span><span class="sxs-lookup"><span data-stu-id="1393e-135">SHA-256</span></span>|<span data-ttu-id="1393e-136">0x800c</span><span class="sxs-lookup"><span data-stu-id="1393e-136">0x800c</span></span>|  
|<span data-ttu-id="1393e-137">SHA-384</span><span class="sxs-lookup"><span data-stu-id="1393e-137">SHA-384</span></span>|<span data-ttu-id="1393e-138">0x800d</span><span class="sxs-lookup"><span data-stu-id="1393e-138">0x800d</span></span>|  
|<span data-ttu-id="1393e-139">SHA-512</span><span class="sxs-lookup"><span data-stu-id="1393e-139">SHA-512</span></span>|<span data-ttu-id="1393e-140">0x800e</span><span class="sxs-lookup"><span data-stu-id="1393e-140">0x800e</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1393e-141">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1393e-141">Requirements</span></span>  
 <span data-ttu-id="1393e-142">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1393e-142">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1393e-143">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="1393e-143">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="1393e-144">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="1393e-144">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1393e-145">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1393e-145">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1393e-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1393e-146">See also</span></span>

- [<span data-ttu-id="1393e-147">StrongNameTokenFromPublicKey Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1393e-147">StrongNameTokenFromPublicKey Method</span></span>](iclrstrongname-strongnametokenfrompublickey-method.md)
- [<span data-ttu-id="1393e-148">PublicKeyBlob Yapısı</span><span class="sxs-lookup"><span data-stu-id="1393e-148">PublicKeyBlob Structure</span></span>](../strong-naming/publickeyblob-structure.md)
- [<span data-ttu-id="1393e-149">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1393e-149">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
- [<span data-ttu-id="1393e-150">StrongNameGetPublicKey Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1393e-150">StrongNameGetPublicKey Method</span></span>](iclrstrongname-strongnamegetpublickey-method.md)
