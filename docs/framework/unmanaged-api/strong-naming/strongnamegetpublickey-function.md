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
ms.openlocfilehash: 966a2a628f30f1999688da7b6ba435c1d6cb830c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73094658"
---
# <a name="strongnamegetpublickey-function"></a><span data-ttu-id="3aa0c-102">StrongNameGetPublicKey İşlevi</span><span class="sxs-lookup"><span data-stu-id="3aa0c-102">StrongNameGetPublicKey Function</span></span>
<span data-ttu-id="3aa0c-103">Özel/ortak anahtar çiftinden ortak anahtarı alır.</span><span class="sxs-lookup"><span data-stu-id="3aa0c-103">Gets the public key from a private/public key pair.</span></span> <span data-ttu-id="3aa0c-104">Anahtar çifti, bir şifreleme hizmeti sağlayıcısı (CSP) içinde anahtar kapsayıcı adı olarak veya ham bir bayt koleksiyonu olarak sağlanabilir.</span><span class="sxs-lookup"><span data-stu-id="3aa0c-104">The key pair can be supplied either as a key container name within a cryptographic service provider (CSP) or as a raw collection of bytes.</span></span>  
  
 <span data-ttu-id="3aa0c-105">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="3aa0c-105">This function has been deprecated.</span></span> <span data-ttu-id="3aa0c-106">Bunun yerine [ICLRStrongName:: StrongNameGetPublicKey](../hosting/iclrstrongname-strongnamegetpublickey-method.md) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="3aa0c-106">Use the [ICLRStrongName::StrongNameGetPublicKey](../hosting/iclrstrongname-strongnamegetpublickey-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3aa0c-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3aa0c-107">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameGetPublicKey (   
    [in]  LPCWSTR   szKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3aa0c-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3aa0c-108">Parameters</span></span>  
 `szKeyContainer`  
 <span data-ttu-id="3aa0c-109">'ndaki Ortak/özel anahtar çiftini içeren anahtar kapsayıcısının adı.</span><span class="sxs-lookup"><span data-stu-id="3aa0c-109">[in] The name of the key container that contains the public/private key pair.</span></span> <span data-ttu-id="3aa0c-110">`pbKeyBlob` null ise, `szKeyContainer` CSP içinde geçerli bir kapsayıcı belirtmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="3aa0c-110">If `pbKeyBlob` is null, `szKeyContainer` must specify a valid container within the CSP.</span></span> <span data-ttu-id="3aa0c-111">Bu durumda, `StrongNameGetPublicKey` kapsayıcıda depolanan anahtar çiftinden ortak anahtarı ayıklar.</span><span class="sxs-lookup"><span data-stu-id="3aa0c-111">In this case, `StrongNameGetPublicKey` extracts the public key from the key pair stored in the container.</span></span>  
  
 <span data-ttu-id="3aa0c-112">`pbKeyBlob` null değilse, anahtar çiftinin anahtar ikili büyük nesne (BLOB) içinde yer aldığı varsayılır.</span><span class="sxs-lookup"><span data-stu-id="3aa0c-112">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="3aa0c-113">Anahtarlar 1024-bit Rivest-Shamir-Adtaman (RSA) imzalama anahtarları olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3aa0c-113">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="3aa0c-114">Şu anda başka türde anahtarlar desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="3aa0c-114">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="3aa0c-115">'ndaki Ortak/özel anahtar çifti işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="3aa0c-115">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="3aa0c-116">Bu çift, Win32 `CryptExportKey` işlevi tarafından oluşturulan biçimdedir.</span><span class="sxs-lookup"><span data-stu-id="3aa0c-116">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="3aa0c-117">`pbKeyBlob` null ise, `szKeyContainer` tarafından belirtilen anahtar kapsayıcısının anahtar çiftini içermesi varsayılır.</span><span class="sxs-lookup"><span data-stu-id="3aa0c-117">If `pbKeyBlob` is null, the key container specified by `szKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="3aa0c-118">'ndaki `pbKeyBlob`bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="3aa0c-118">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="3aa0c-119">dışı Döndürülen ortak anahtar blobu.</span><span class="sxs-lookup"><span data-stu-id="3aa0c-119">[out] The returned public key BLOB.</span></span> <span data-ttu-id="3aa0c-120">`ppbPublicKeyBlob` parametresi ortak dil çalışma zamanı tarafından ayrılır ve çağırana döndürülür.</span><span class="sxs-lookup"><span data-stu-id="3aa0c-120">The `ppbPublicKeyBlob` parameter is allocated by the common language runtime and returned to the caller.</span></span> <span data-ttu-id="3aa0c-121">Çağıranın, [StrongNameFreeBuffer](strongnamefreebuffer-function.md) işlevini kullanarak belleği boşaltmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3aa0c-121">The caller must free the memory by using the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="3aa0c-122">dışı Döndürülen ortak anahtar BLOBUNUN boyutu.</span><span class="sxs-lookup"><span data-stu-id="3aa0c-122">[out] The size of the returned public key BLOB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3aa0c-123">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3aa0c-123">Return Value</span></span>  
 <span data-ttu-id="3aa0c-124">başarılı tamamlamada `true`; Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="3aa0c-124">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3aa0c-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3aa0c-125">Remarks</span></span>  
 <span data-ttu-id="3aa0c-126">Ortak anahtar, [PublicKeyBlob](publickeyblob-structure.md) yapısında bulunur.</span><span class="sxs-lookup"><span data-stu-id="3aa0c-126">The public key is contained in a [PublicKeyBlob](publickeyblob-structure.md) structure.</span></span>  
  
 <span data-ttu-id="3aa0c-127">`StrongNameGetPublicKey` işlevi başarıyla tamamlanmazsa, en son oluşturulan hatayı almak için [StrongNameErrorInfo](strongnameerrorinfo-function.md) işlevini çağırın.</span><span class="sxs-lookup"><span data-stu-id="3aa0c-127">If the `StrongNameGetPublicKey` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3aa0c-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3aa0c-128">Requirements</span></span>  
 <span data-ttu-id="3aa0c-129">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3aa0c-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3aa0c-130">**Üst bilgi:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="3aa0c-130">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="3aa0c-131">**Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="3aa0c-131">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3aa0c-132">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3aa0c-132">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3aa0c-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3aa0c-133">See also</span></span>

- [<span data-ttu-id="3aa0c-134">StrongNameGetPublicKey Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3aa0c-134">StrongNameGetPublicKey Method</span></span>](../hosting/iclrstrongname-strongnamegetpublickey-method.md)
- [<span data-ttu-id="3aa0c-135">StrongNameTokenFromPublicKey Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3aa0c-135">StrongNameTokenFromPublicKey Method</span></span>](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [<span data-ttu-id="3aa0c-136">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3aa0c-136">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
- [<span data-ttu-id="3aa0c-137">PublicKeyBlob Yapısı</span><span class="sxs-lookup"><span data-stu-id="3aa0c-137">PublicKeyBlob Structure</span></span>](publickeyblob-structure.md)
