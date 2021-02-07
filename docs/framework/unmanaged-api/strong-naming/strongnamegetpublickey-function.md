---
description: 'Daha fazla bilgi edinin: StrongNameGetPublicKey Işlevi'
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
ms.openlocfilehash: c94ffdd20e83b03da27b2f44ebbc279cfd8b8afc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99670579"
---
# <a name="strongnamegetpublickey-function"></a><span data-ttu-id="9c6cd-103">StrongNameGetPublicKey İşlevi</span><span class="sxs-lookup"><span data-stu-id="9c6cd-103">StrongNameGetPublicKey Function</span></span>

<span data-ttu-id="9c6cd-104">Özel/ortak anahtar çiftinden ortak anahtarı alır.</span><span class="sxs-lookup"><span data-stu-id="9c6cd-104">Gets the public key from a private/public key pair.</span></span> <span data-ttu-id="9c6cd-105">Anahtar çifti, bir şifreleme hizmeti sağlayıcısı (CSP) içinde anahtar kapsayıcı adı olarak veya ham bir bayt koleksiyonu olarak sağlanabilir.</span><span class="sxs-lookup"><span data-stu-id="9c6cd-105">The key pair can be supplied either as a key container name within a cryptographic service provider (CSP) or as a raw collection of bytes.</span></span>  
  
 <span data-ttu-id="9c6cd-106">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="9c6cd-106">This function has been deprecated.</span></span> <span data-ttu-id="9c6cd-107">Bunun yerine [ICLRStrongName:: StrongNameGetPublicKey](../hosting/iclrstrongname-strongnamegetpublickey-method.md) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="9c6cd-107">Use the [ICLRStrongName::StrongNameGetPublicKey](../hosting/iclrstrongname-strongnamegetpublickey-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c6cd-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9c6cd-108">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameGetPublicKey (
    [in]  LPCWSTR   szKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9c6cd-109">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9c6cd-109">Parameters</span></span>  

 `szKeyContainer`  
 <span data-ttu-id="9c6cd-110">'ndaki Ortak/özel anahtar çiftini içeren anahtar kapsayıcısının adı.</span><span class="sxs-lookup"><span data-stu-id="9c6cd-110">[in] The name of the key container that contains the public/private key pair.</span></span> <span data-ttu-id="9c6cd-111">`pbKeyBlob`Null ise, `szKeyContainer` CSP içinde geçerli bir kapsayıcı belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="9c6cd-111">If `pbKeyBlob` is null, `szKeyContainer` must specify a valid container within the CSP.</span></span> <span data-ttu-id="9c6cd-112">Bu durumda, `StrongNameGetPublicKey` kapsayıcıda depolanan anahtar çiftinden ortak anahtarı ayıklar.</span><span class="sxs-lookup"><span data-stu-id="9c6cd-112">In this case, `StrongNameGetPublicKey` extracts the public key from the key pair stored in the container.</span></span>  
  
 <span data-ttu-id="9c6cd-113">`pbKeyBlob`Null değilse, anahtar çiftinin anahtar ikili büyük nesne (blob) içinde yer aldığı varsayılır.</span><span class="sxs-lookup"><span data-stu-id="9c6cd-113">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="9c6cd-114">Anahtarlar 1024-bit Rivest-Shamir-Adtaman (RSA) imzalama anahtarları olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9c6cd-114">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="9c6cd-115">Şu anda başka türde anahtarlar desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="9c6cd-115">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="9c6cd-116">'ndaki Ortak/özel anahtar çifti işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="9c6cd-116">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="9c6cd-117">Bu çift Win32 işlevi tarafından oluşturulan biçimdedir `CryptExportKey` .</span><span class="sxs-lookup"><span data-stu-id="9c6cd-117">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="9c6cd-118">`pbKeyBlob`Null ise, tarafından belirtilen anahtar kapsayıcının `szKeyContainer` anahtar çiftini içermesi varsayılır.</span><span class="sxs-lookup"><span data-stu-id="9c6cd-118">If `pbKeyBlob` is null, the key container specified by `szKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="9c6cd-119">'ndaki Bayt cinsinden boyutu `pbKeyBlob` .</span><span class="sxs-lookup"><span data-stu-id="9c6cd-119">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="9c6cd-120">dışı Döndürülen ortak anahtar blobu.</span><span class="sxs-lookup"><span data-stu-id="9c6cd-120">[out] The returned public key BLOB.</span></span> <span data-ttu-id="9c6cd-121">`ppbPublicKeyBlob`Parametresi ortak dil çalışma zamanı tarafından ayrılır ve çağırana döndürülür.</span><span class="sxs-lookup"><span data-stu-id="9c6cd-121">The `ppbPublicKeyBlob` parameter is allocated by the common language runtime and returned to the caller.</span></span> <span data-ttu-id="9c6cd-122">Çağıranın, [StrongNameFreeBuffer](strongnamefreebuffer-function.md) işlevini kullanarak belleği boşaltmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9c6cd-122">The caller must free the memory by using the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="9c6cd-123">dışı Döndürülen ortak anahtar BLOBUNUN boyutu.</span><span class="sxs-lookup"><span data-stu-id="9c6cd-123">[out] The size of the returned public key BLOB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9c6cd-124">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="9c6cd-124">Return Value</span></span>  

 <span data-ttu-id="9c6cd-125">`true` başarıyla tamamlandığında; Aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="9c6cd-125">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9c6cd-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9c6cd-126">Remarks</span></span>  

 <span data-ttu-id="9c6cd-127">Ortak anahtar, [PublicKeyBlob](publickeyblob-structure.md) yapısında bulunur.</span><span class="sxs-lookup"><span data-stu-id="9c6cd-127">The public key is contained in a [PublicKeyBlob](publickeyblob-structure.md) structure.</span></span>  
  
 <span data-ttu-id="9c6cd-128">`StrongNameGetPublicKey`İşlev başarıyla tamamlanmazsa, en son oluşturulan hatayı almak Için [StrongNameErrorInfo](strongnameerrorinfo-function.md) işlevini çağırın.</span><span class="sxs-lookup"><span data-stu-id="9c6cd-128">If the `StrongNameGetPublicKey` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9c6cd-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9c6cd-129">Requirements</span></span>  

 <span data-ttu-id="9c6cd-130">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9c6cd-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9c6cd-131">**Üst bilgi:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="9c6cd-131">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="9c6cd-132">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="9c6cd-132">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9c6cd-133">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9c6cd-133">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c6cd-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9c6cd-134">See also</span></span>

- [<span data-ttu-id="9c6cd-135">StrongNameGetPublicKey Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9c6cd-135">StrongNameGetPublicKey Method</span></span>](../hosting/iclrstrongname-strongnamegetpublickey-method.md)
- [<span data-ttu-id="9c6cd-136">StrongNameTokenFromPublicKey Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9c6cd-136">StrongNameTokenFromPublicKey Method</span></span>](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [<span data-ttu-id="9c6cd-137">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9c6cd-137">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
- [<span data-ttu-id="9c6cd-138">PublicKeyBlob Yapısı</span><span class="sxs-lookup"><span data-stu-id="9c6cd-138">PublicKeyBlob Structure</span></span>](publickeyblob-structure.md)
