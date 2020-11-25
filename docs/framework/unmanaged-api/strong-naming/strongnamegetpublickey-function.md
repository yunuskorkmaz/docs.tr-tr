---
title: StrongNameGetPublicKey İşlevi
ms.date: 03/30/2017
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
ms.openlocfilehash: c97cc0c1d4c022583d0823abeff998e2ed5f719e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95710980"
---
# <a name="strongnamegetpublickey-function"></a><span data-ttu-id="f7bbb-102">StrongNameGetPublicKey İşlevi</span><span class="sxs-lookup"><span data-stu-id="f7bbb-102">StrongNameGetPublicKey Function</span></span>

<span data-ttu-id="f7bbb-103">Özel/ortak anahtar çiftinden ortak anahtarı alır.</span><span class="sxs-lookup"><span data-stu-id="f7bbb-103">Gets the public key from a private/public key pair.</span></span> <span data-ttu-id="f7bbb-104">Anahtar çifti, bir şifreleme hizmeti sağlayıcısı (CSP) içinde anahtar kapsayıcı adı olarak veya ham bir bayt koleksiyonu olarak sağlanabilir.</span><span class="sxs-lookup"><span data-stu-id="f7bbb-104">The key pair can be supplied either as a key container name within a cryptographic service provider (CSP) or as a raw collection of bytes.</span></span>  
  
 <span data-ttu-id="f7bbb-105">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="f7bbb-105">This function has been deprecated.</span></span> <span data-ttu-id="f7bbb-106">Bunun yerine [ICLRStrongName:: StrongNameGetPublicKey](../hosting/iclrstrongname-strongnamegetpublickey-method.md) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="f7bbb-106">Use the [ICLRStrongName::StrongNameGetPublicKey](../hosting/iclrstrongname-strongnamegetpublickey-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7bbb-107">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="f7bbb-107">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameGetPublicKey (
    [in]  LPCWSTR   szKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f7bbb-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f7bbb-108">Parameters</span></span>  

 `szKeyContainer`  
 <span data-ttu-id="f7bbb-109">'ndaki Ortak/özel anahtar çiftini içeren anahtar kapsayıcısının adı.</span><span class="sxs-lookup"><span data-stu-id="f7bbb-109">[in] The name of the key container that contains the public/private key pair.</span></span> <span data-ttu-id="f7bbb-110">`pbKeyBlob`Null ise, `szKeyContainer` CSP içinde geçerli bir kapsayıcı belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f7bbb-110">If `pbKeyBlob` is null, `szKeyContainer` must specify a valid container within the CSP.</span></span> <span data-ttu-id="f7bbb-111">Bu durumda, `StrongNameGetPublicKey` kapsayıcıda depolanan anahtar çiftinden ortak anahtarı ayıklar.</span><span class="sxs-lookup"><span data-stu-id="f7bbb-111">In this case, `StrongNameGetPublicKey` extracts the public key from the key pair stored in the container.</span></span>  
  
 <span data-ttu-id="f7bbb-112">`pbKeyBlob`Null değilse, anahtar çiftinin anahtar ikili büyük nesne (blob) içinde yer aldığı varsayılır.</span><span class="sxs-lookup"><span data-stu-id="f7bbb-112">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="f7bbb-113">Anahtarlar 1024-bit Rivest-Shamir-Adtaman (RSA) imzalama anahtarları olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f7bbb-113">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="f7bbb-114">Şu anda başka türde anahtarlar desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="f7bbb-114">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="f7bbb-115">'ndaki Ortak/özel anahtar çifti işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="f7bbb-115">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="f7bbb-116">Bu çift Win32 işlevi tarafından oluşturulan biçimdedir `CryptExportKey` .</span><span class="sxs-lookup"><span data-stu-id="f7bbb-116">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="f7bbb-117">`pbKeyBlob`Null ise, tarafından belirtilen anahtar kapsayıcının `szKeyContainer` anahtar çiftini içermesi varsayılır.</span><span class="sxs-lookup"><span data-stu-id="f7bbb-117">If `pbKeyBlob` is null, the key container specified by `szKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="f7bbb-118">'ndaki Bayt cinsinden boyutu `pbKeyBlob` .</span><span class="sxs-lookup"><span data-stu-id="f7bbb-118">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="f7bbb-119">dışı Döndürülen ortak anahtar blobu.</span><span class="sxs-lookup"><span data-stu-id="f7bbb-119">[out] The returned public key BLOB.</span></span> <span data-ttu-id="f7bbb-120">`ppbPublicKeyBlob`Parametresi ortak dil çalışma zamanı tarafından ayrılır ve çağırana döndürülür.</span><span class="sxs-lookup"><span data-stu-id="f7bbb-120">The `ppbPublicKeyBlob` parameter is allocated by the common language runtime and returned to the caller.</span></span> <span data-ttu-id="f7bbb-121">Çağıranın, [StrongNameFreeBuffer](strongnamefreebuffer-function.md) işlevini kullanarak belleği boşaltmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f7bbb-121">The caller must free the memory by using the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="f7bbb-122">dışı Döndürülen ortak anahtar BLOBUNUN boyutu.</span><span class="sxs-lookup"><span data-stu-id="f7bbb-122">[out] The size of the returned public key BLOB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f7bbb-123">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="f7bbb-123">Return Value</span></span>  

 <span data-ttu-id="f7bbb-124">`true` başarıyla tamamlandığında; Aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="f7bbb-124">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f7bbb-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f7bbb-125">Remarks</span></span>  

 <span data-ttu-id="f7bbb-126">Ortak anahtar, [PublicKeyBlob](publickeyblob-structure.md) yapısında bulunur.</span><span class="sxs-lookup"><span data-stu-id="f7bbb-126">The public key is contained in a [PublicKeyBlob](publickeyblob-structure.md) structure.</span></span>  
  
 <span data-ttu-id="f7bbb-127">`StrongNameGetPublicKey`İşlev başarıyla tamamlanmazsa, en son oluşturulan hatayı almak Için [StrongNameErrorInfo](strongnameerrorinfo-function.md) işlevini çağırın.</span><span class="sxs-lookup"><span data-stu-id="f7bbb-127">If the `StrongNameGetPublicKey` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7bbb-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f7bbb-128">Requirements</span></span>  

 <span data-ttu-id="f7bbb-129">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f7bbb-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7bbb-130">**Üst bilgi:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="f7bbb-130">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="f7bbb-131">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="f7bbb-131">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f7bbb-132">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7bbb-132">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7bbb-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f7bbb-133">See also</span></span>

- [<span data-ttu-id="f7bbb-134">StrongNameGetPublicKey Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f7bbb-134">StrongNameGetPublicKey Method</span></span>](../hosting/iclrstrongname-strongnamegetpublickey-method.md)
- [<span data-ttu-id="f7bbb-135">StrongNameTokenFromPublicKey Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f7bbb-135">StrongNameTokenFromPublicKey Method</span></span>](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [<span data-ttu-id="f7bbb-136">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f7bbb-136">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
- [<span data-ttu-id="f7bbb-137">PublicKeyBlob Yapısı</span><span class="sxs-lookup"><span data-stu-id="f7bbb-137">PublicKeyBlob Structure</span></span>](publickeyblob-structure.md)
