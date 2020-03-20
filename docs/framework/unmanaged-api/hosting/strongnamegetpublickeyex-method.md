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
ms.openlocfilehash: 93afe1afd9ea9637d039a8b4a4e81267d49c08b6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176233"
---
# <a name="strongnamegetpublickeyex-method"></a><span data-ttu-id="04e0b-102">StrongNameGetPublicKeyEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="04e0b-102">StrongNameGetPublicKeyEx Method</span></span>
<span data-ttu-id="04e0b-103">Ortak anahtarı ortak/özel anahtar çiftinden alır ve karma algoritma ve imza algoritması belirtir.</span><span class="sxs-lookup"><span data-stu-id="04e0b-103">Gets the public key from a public/private key pair, and specifies a hash algorithm and a signature algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04e0b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="04e0b-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="04e0b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="04e0b-105">Parameters</span></span>  
 `pwzKeyContainer`  
 <span data-ttu-id="04e0b-106">[içinde] Ortak/özel anahtar çiftini içeren anahtar kapsayıcısının adı.</span><span class="sxs-lookup"><span data-stu-id="04e0b-106">[in] The name of the key container that contains the public/private key pair.</span></span> <span data-ttu-id="04e0b-107">Null `pbKeyBlob` ise, `szKeyContainer` şifreleme hizmet sağlayıcısı (CSP) içinde geçerli bir kapsayıcı belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="04e0b-107">If `pbKeyBlob` is null, `szKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="04e0b-108">Bu durumda, `StrongNameGetPublicKeyEx` yöntem kapsayıcıda depolanan anahtar çiftinden ortak anahtarı ayıklar.</span><span class="sxs-lookup"><span data-stu-id="04e0b-108">In this case, the `StrongNameGetPublicKeyEx` method extracts the public key from the key pair stored in the container.</span></span>  
  
 <span data-ttu-id="04e0b-109">Null `pbKeyBlob` değilse, anahtar çiftinin anahtar ikili büyük nesnesinde (BLOB) bulunduğu varsayılır.</span><span class="sxs-lookup"><span data-stu-id="04e0b-109">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="04e0b-110">Anahtarlar 1024 bit Rivest-Shamir-Adleman (RSA) imzalama anahtarları olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="04e0b-110">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="04e0b-111">Şu anda başka anahtar türü desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="04e0b-111">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="04e0b-112">[içinde] Ortak/özel anahtar çiftine işaretçi.</span><span class="sxs-lookup"><span data-stu-id="04e0b-112">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="04e0b-113">Bu çift Win32 `CryptExportKey` işlevi tarafından oluşturulan biçimdedir.</span><span class="sxs-lookup"><span data-stu-id="04e0b-113">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="04e0b-114">Null `pbKeyBlob` ise, tarafından `szKeyContainer` belirtilen anahtar kapsayıcı anahtar çiftini içerdiği varsayılır.</span><span class="sxs-lookup"><span data-stu-id="04e0b-114">If `pbKeyBlob` is null, the key container specified by `szKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="04e0b-115">[içinde] Boyutu, bayt, ve. `pbKeyBlob`</span><span class="sxs-lookup"><span data-stu-id="04e0b-115">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="04e0b-116">[çıkış] Döndürülen ortak anahtar BLOB.</span><span class="sxs-lookup"><span data-stu-id="04e0b-116">[out] The returned public key BLOB.</span></span> <span data-ttu-id="04e0b-117">`ppbPublicKeyBlob` Parametre ortak dil çalışma zamanı tarafından ayrılır ve arayana döndürülür.</span><span class="sxs-lookup"><span data-stu-id="04e0b-117">The `ppbPublicKeyBlob` parameter is allocated by the common language runtime and returned to the caller.</span></span> <span data-ttu-id="04e0b-118">Arayan ICLRStrongName kullanarak bellek serbest [gerekir::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="04e0b-118">The caller must free the memory by using the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="04e0b-119">[çıkış] Döndürülen ortak anahtar BLOB boyutu.</span><span class="sxs-lookup"><span data-stu-id="04e0b-119">[out] The size of the returned public key BLOB.</span></span>  
  
 `uHashAlgId`  
 <span data-ttu-id="04e0b-120">[içinde] Derleme karma algoritması.</span><span class="sxs-lookup"><span data-stu-id="04e0b-120">[in] The assembly hash algorithm.</span></span> <span data-ttu-id="04e0b-121">Kabul edilen değerler listesi için Açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="04e0b-121">See the Remarks section for a list of accepted values.</span></span>  
  
 `uReserved`  
 <span data-ttu-id="04e0b-122">[içinde] İleride kullanım için ayrılmış; varsayılan olarak null.</span><span class="sxs-lookup"><span data-stu-id="04e0b-122">[in] Reserved for future use; defaults to null.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="04e0b-123">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="04e0b-123">Return Value</span></span>  
 <span data-ttu-id="04e0b-124">`S_OK`yöntem başarıyla tamamlanırsa; aksi takdirde, başarısızlığı gösteren bir HRESULT değeri (liste için [Ortak HRESULT Değerleri'ne](/windows/win32/seccrypto/common-hresult-values) bakın).</span><span class="sxs-lookup"><span data-stu-id="04e0b-124">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="04e0b-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="04e0b-125">Remarks</span></span>  
 <span data-ttu-id="04e0b-126">Ortak anahtar [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) yapısında yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="04e0b-126">The public key is contained in a [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="04e0b-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="04e0b-127">Remarks</span></span>  
 <span data-ttu-id="04e0b-128">Aşağıdaki `uHashAlgId` tabloda parametre için kabul edilen değerler kümesi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="04e0b-128">The following table shows the set of accepted values for the `uHashAlgId` parameter.</span></span>  
  
|<span data-ttu-id="04e0b-129">Adı</span><span class="sxs-lookup"><span data-stu-id="04e0b-129">Name</span></span>|<span data-ttu-id="04e0b-130">Değer</span><span class="sxs-lookup"><span data-stu-id="04e0b-130">Value</span></span>|  
|----------|-----------|  
|<span data-ttu-id="04e0b-131">None</span><span class="sxs-lookup"><span data-stu-id="04e0b-131">None</span></span>|<span data-ttu-id="04e0b-132">0</span><span class="sxs-lookup"><span data-stu-id="04e0b-132">0</span></span>|  
|<span data-ttu-id="04e0b-133">SHA-1</span><span class="sxs-lookup"><span data-stu-id="04e0b-133">SHA-1</span></span>|<span data-ttu-id="04e0b-134">0x8004</span><span class="sxs-lookup"><span data-stu-id="04e0b-134">0x8004</span></span>|  
|<span data-ttu-id="04e0b-135">SHA-256</span><span class="sxs-lookup"><span data-stu-id="04e0b-135">SHA-256</span></span>|<span data-ttu-id="04e0b-136">0x800c</span><span class="sxs-lookup"><span data-stu-id="04e0b-136">0x800c</span></span>|  
|<span data-ttu-id="04e0b-137">ŞA-384</span><span class="sxs-lookup"><span data-stu-id="04e0b-137">SHA-384</span></span>|<span data-ttu-id="04e0b-138">0x800d</span><span class="sxs-lookup"><span data-stu-id="04e0b-138">0x800d</span></span>|  
|<span data-ttu-id="04e0b-139">ŞAH- 512</span><span class="sxs-lookup"><span data-stu-id="04e0b-139">SHA-512</span></span>|<span data-ttu-id="04e0b-140">0x800e</span><span class="sxs-lookup"><span data-stu-id="04e0b-140">0x800e</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="04e0b-141">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="04e0b-141">Requirements</span></span>  
 <span data-ttu-id="04e0b-142">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="04e0b-142">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04e0b-143">**Üstbilgi:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="04e0b-143">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="04e0b-144">**Kütüphane:** MSCorEE.dll bir kaynak olarak dahil</span><span class="sxs-lookup"><span data-stu-id="04e0b-144">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="04e0b-145">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04e0b-145">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04e0b-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="04e0b-146">See also</span></span>

- [<span data-ttu-id="04e0b-147">StrongNameTokenFromPublicKey Yöntemi</span><span class="sxs-lookup"><span data-stu-id="04e0b-147">StrongNameTokenFromPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [<span data-ttu-id="04e0b-148">PublicKeyBlob Yapısı</span><span class="sxs-lookup"><span data-stu-id="04e0b-148">PublicKeyBlob Structure</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)
- [<span data-ttu-id="04e0b-149">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="04e0b-149">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
- [<span data-ttu-id="04e0b-150">StrongNameGetPublicKey Yöntemi</span><span class="sxs-lookup"><span data-stu-id="04e0b-150">StrongNameGetPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)
