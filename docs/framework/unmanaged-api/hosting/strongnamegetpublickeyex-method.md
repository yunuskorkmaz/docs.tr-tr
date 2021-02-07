---
description: 'Daha fazla bilgi edinin: StrongNameGetPublicKeyEx Yöntemi'
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
ms.openlocfilehash: bc9d40afc34509f852a0961823e264255125fa16
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99679309"
---
# <a name="strongnamegetpublickeyex-method"></a><span data-ttu-id="9b1a7-103">StrongNameGetPublicKeyEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9b1a7-103">StrongNameGetPublicKeyEx Method</span></span>

<span data-ttu-id="9b1a7-104">Ortak/özel anahtar çiftinden ortak anahtarı alır ve bir karma algoritmasını ve bir imza algoritmasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="9b1a7-104">Gets the public key from a public/private key pair, and specifies a hash algorithm and a signature algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b1a7-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9b1a7-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="9b1a7-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9b1a7-106">Parameters</span></span>  

 `pwzKeyContainer`  
 <span data-ttu-id="9b1a7-107">'ndaki Ortak/özel anahtar çiftini içeren anahtar kapsayıcısının adı.</span><span class="sxs-lookup"><span data-stu-id="9b1a7-107">[in] The name of the key container that contains the public/private key pair.</span></span> <span data-ttu-id="9b1a7-108">`pbKeyBlob`Null ise, `szKeyContainer` şifreleme hizmet sağlayıcısı (CSP) içinde geçerli bir kapsayıcı belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="9b1a7-108">If `pbKeyBlob` is null, `szKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="9b1a7-109">Bu durumda, `StrongNameGetPublicKeyEx` yöntemi kapsayıcıda depolanan anahtar çiftinden ortak anahtarı ayıklar.</span><span class="sxs-lookup"><span data-stu-id="9b1a7-109">In this case, the `StrongNameGetPublicKeyEx` method extracts the public key from the key pair stored in the container.</span></span>  
  
 <span data-ttu-id="9b1a7-110">`pbKeyBlob`Null değilse, anahtar çiftinin anahtar ikili büyük nesne (blob) içinde yer aldığı varsayılır.</span><span class="sxs-lookup"><span data-stu-id="9b1a7-110">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="9b1a7-111">Anahtarlar 1024-bit Rivest-Shamir-Adtaman (RSA) imzalama anahtarları olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9b1a7-111">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="9b1a7-112">Şu anda başka türde anahtarlar desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="9b1a7-112">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="9b1a7-113">'ndaki Ortak/özel anahtar çifti işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="9b1a7-113">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="9b1a7-114">Bu çift Win32 işlevi tarafından oluşturulan biçimdedir `CryptExportKey` .</span><span class="sxs-lookup"><span data-stu-id="9b1a7-114">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="9b1a7-115">`pbKeyBlob`Null ise, tarafından belirtilen anahtar kapsayıcının `szKeyContainer` anahtar çiftini içermesi varsayılır.</span><span class="sxs-lookup"><span data-stu-id="9b1a7-115">If `pbKeyBlob` is null, the key container specified by `szKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="9b1a7-116">'ndaki Bayt cinsinden boyutu `pbKeyBlob` .</span><span class="sxs-lookup"><span data-stu-id="9b1a7-116">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="9b1a7-117">dışı Döndürülen ortak anahtar blobu.</span><span class="sxs-lookup"><span data-stu-id="9b1a7-117">[out] The returned public key BLOB.</span></span> <span data-ttu-id="9b1a7-118">`ppbPublicKeyBlob`Parametresi ortak dil çalışma zamanı tarafından ayrılır ve çağırana döndürülür.</span><span class="sxs-lookup"><span data-stu-id="9b1a7-118">The `ppbPublicKeyBlob` parameter is allocated by the common language runtime and returned to the caller.</span></span> <span data-ttu-id="9b1a7-119">Çağıranın, [ICLRStrongName:: StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) metodunu kullanarak belleği boşaltmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9b1a7-119">The caller must free the memory by using the [ICLRStrongName::StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="9b1a7-120">dışı Döndürülen ortak anahtar BLOBUNUN boyutu.</span><span class="sxs-lookup"><span data-stu-id="9b1a7-120">[out] The size of the returned public key BLOB.</span></span>  
  
 `uHashAlgId`  
 <span data-ttu-id="9b1a7-121">'ndaki Bütünleştirilmiş kod karma algoritması.</span><span class="sxs-lookup"><span data-stu-id="9b1a7-121">[in] The assembly hash algorithm.</span></span> <span data-ttu-id="9b1a7-122">Kabul edilen değerlerin bir listesi için bkz. açıklamalar bölümü.</span><span class="sxs-lookup"><span data-stu-id="9b1a7-122">See the Remarks section for a list of accepted values.</span></span>  
  
 `uReserved`  
 <span data-ttu-id="9b1a7-123">'ndaki Gelecekte kullanılmak üzere ayrılmıştır; Varsayılan olarak null değerini alır.</span><span class="sxs-lookup"><span data-stu-id="9b1a7-123">[in] Reserved for future use; defaults to null.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9b1a7-124">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="9b1a7-124">Return Value</span></span>  

 <span data-ttu-id="9b1a7-125">`S_OK` Yöntem başarıyla tamamlanırsa; Aksi takdirde, hata belirten bir HRESULT değeri (bkz. bir liste için [genel HRESULT değerleri](/windows/win32/seccrypto/common-hresult-values) ).</span><span class="sxs-lookup"><span data-stu-id="9b1a7-125">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9b1a7-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9b1a7-126">Remarks</span></span>  

 <span data-ttu-id="9b1a7-127">Ortak anahtar, [PublicKeyBlob](../strong-naming/publickeyblob-structure.md) yapısında bulunur.</span><span class="sxs-lookup"><span data-stu-id="9b1a7-127">The public key is contained in a [PublicKeyBlob](../strong-naming/publickeyblob-structure.md) structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9b1a7-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9b1a7-128">Remarks</span></span>  

 <span data-ttu-id="9b1a7-129">Aşağıdaki tabloda parametresi için kabul edilen değerler kümesi gösterilmektedir `uHashAlgId` .</span><span class="sxs-lookup"><span data-stu-id="9b1a7-129">The following table shows the set of accepted values for the `uHashAlgId` parameter.</span></span>  
  
|<span data-ttu-id="9b1a7-130">Name</span><span class="sxs-lookup"><span data-stu-id="9b1a7-130">Name</span></span>|<span data-ttu-id="9b1a7-131">Değer</span><span class="sxs-lookup"><span data-stu-id="9b1a7-131">Value</span></span>|  
|----------|-----------|  
|<span data-ttu-id="9b1a7-132">Yok</span><span class="sxs-lookup"><span data-stu-id="9b1a7-132">None</span></span>|<span data-ttu-id="9b1a7-133">0</span><span class="sxs-lookup"><span data-stu-id="9b1a7-133">0</span></span>|  
|<span data-ttu-id="9b1a7-134">SHA-1</span><span class="sxs-lookup"><span data-stu-id="9b1a7-134">SHA-1</span></span>|<span data-ttu-id="9b1a7-135">0x8004</span><span class="sxs-lookup"><span data-stu-id="9b1a7-135">0x8004</span></span>|  
|<span data-ttu-id="9b1a7-136">SHA-256</span><span class="sxs-lookup"><span data-stu-id="9b1a7-136">SHA-256</span></span>|<span data-ttu-id="9b1a7-137">0x800c</span><span class="sxs-lookup"><span data-stu-id="9b1a7-137">0x800c</span></span>|  
|<span data-ttu-id="9b1a7-138">SHA-384</span><span class="sxs-lookup"><span data-stu-id="9b1a7-138">SHA-384</span></span>|<span data-ttu-id="9b1a7-139">0x800d</span><span class="sxs-lookup"><span data-stu-id="9b1a7-139">0x800d</span></span>|  
|<span data-ttu-id="9b1a7-140">SHA-512</span><span class="sxs-lookup"><span data-stu-id="9b1a7-140">SHA-512</span></span>|<span data-ttu-id="9b1a7-141">0x800e</span><span class="sxs-lookup"><span data-stu-id="9b1a7-141">0x800e</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9b1a7-142">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9b1a7-142">Requirements</span></span>  

 <span data-ttu-id="9b1a7-143">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9b1a7-143">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b1a7-144">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="9b1a7-144">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="9b1a7-145">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="9b1a7-145">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9b1a7-146">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b1a7-146">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b1a7-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9b1a7-147">See also</span></span>

- [<span data-ttu-id="9b1a7-148">StrongNameTokenFromPublicKey Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9b1a7-148">StrongNameTokenFromPublicKey Method</span></span>](iclrstrongname-strongnametokenfrompublickey-method.md)
- [<span data-ttu-id="9b1a7-149">PublicKeyBlob Yapısı</span><span class="sxs-lookup"><span data-stu-id="9b1a7-149">PublicKeyBlob Structure</span></span>](../strong-naming/publickeyblob-structure.md)
- [<span data-ttu-id="9b1a7-150">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9b1a7-150">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
- [<span data-ttu-id="9b1a7-151">StrongNameGetPublicKey Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9b1a7-151">StrongNameGetPublicKey Method</span></span>](iclrstrongname-strongnamegetpublickey-method.md)
