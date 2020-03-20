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
ms.openlocfilehash: fcdd4a3f07b4499fd2388b5d165c409da9150466
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176935"
---
# <a name="strongnamegetpublickey-function"></a><span data-ttu-id="cb755-102">StrongNameGetPublicKey İşlevi</span><span class="sxs-lookup"><span data-stu-id="cb755-102">StrongNameGetPublicKey Function</span></span>
<span data-ttu-id="cb755-103">Ortak anahtarı özel/ortak anahtar çiftinden alır.</span><span class="sxs-lookup"><span data-stu-id="cb755-103">Gets the public key from a private/public key pair.</span></span> <span data-ttu-id="cb755-104">Anahtar çifti, bir şifreleme hizmet sağlayıcısı (CSP) içinde önemli bir kapsayıcı adı olarak veya ham bir bayt koleksiyonu olarak sağlanabilir.</span><span class="sxs-lookup"><span data-stu-id="cb755-104">The key pair can be supplied either as a key container name within a cryptographic service provider (CSP) or as a raw collection of bytes.</span></span>  
  
 <span data-ttu-id="cb755-105">Bu işlev amortismana kaldırıldı.</span><span class="sxs-lookup"><span data-stu-id="cb755-105">This function has been deprecated.</span></span> <span data-ttu-id="cb755-106">Bunun yerine [ICLRStrongName::StrongNameGetPublicKey](../hosting/iclrstrongname-strongnamegetpublickey-method.md) yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="cb755-106">Use the [ICLRStrongName::StrongNameGetPublicKey](../hosting/iclrstrongname-strongnamegetpublickey-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb755-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cb755-107">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameGetPublicKey (
    [in]  LPCWSTR   szKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cb755-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cb755-108">Parameters</span></span>  
 `szKeyContainer`  
 <span data-ttu-id="cb755-109">[içinde] Ortak/özel anahtar çiftini içeren anahtar kapsayıcısının adı.</span><span class="sxs-lookup"><span data-stu-id="cb755-109">[in] The name of the key container that contains the public/private key pair.</span></span> <span data-ttu-id="cb755-110">Null `pbKeyBlob` ise, `szKeyContainer` CSP içinde geçerli bir kapsayıcı belirtmelidir.</span><span class="sxs-lookup"><span data-stu-id="cb755-110">If `pbKeyBlob` is null, `szKeyContainer` must specify a valid container within the CSP.</span></span> <span data-ttu-id="cb755-111">Bu durumda, `StrongNameGetPublicKey` ortak anahtarı kapsayıcıda depolanan anahtar çiftinden ayıklar.</span><span class="sxs-lookup"><span data-stu-id="cb755-111">In this case, `StrongNameGetPublicKey` extracts the public key from the key pair stored in the container.</span></span>  
  
 <span data-ttu-id="cb755-112">Null `pbKeyBlob` değilse, anahtar çiftinin anahtar ikili büyük nesnesinde (BLOB) bulunduğu varsayılır.</span><span class="sxs-lookup"><span data-stu-id="cb755-112">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="cb755-113">Anahtarlar 1024 bit Rivest-Shamir-Adleman (RSA) imzalama anahtarları olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="cb755-113">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="cb755-114">Şu anda başka anahtar türü desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="cb755-114">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="cb755-115">[içinde] Ortak/özel anahtar çiftine işaretçi.</span><span class="sxs-lookup"><span data-stu-id="cb755-115">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="cb755-116">Bu çift Win32 `CryptExportKey` işlevi tarafından oluşturulan biçimdedir.</span><span class="sxs-lookup"><span data-stu-id="cb755-116">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="cb755-117">Null `pbKeyBlob` ise, tarafından `szKeyContainer` belirtilen anahtar kapsayıcı anahtar çiftini içerdiği varsayılır.</span><span class="sxs-lookup"><span data-stu-id="cb755-117">If `pbKeyBlob` is null, the key container specified by `szKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="cb755-118">[içinde] Boyutu, bayt, ve. `pbKeyBlob`</span><span class="sxs-lookup"><span data-stu-id="cb755-118">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="cb755-119">[çıkış] Döndürülen ortak anahtar BLOB.</span><span class="sxs-lookup"><span data-stu-id="cb755-119">[out] The returned public key BLOB.</span></span> <span data-ttu-id="cb755-120">`ppbPublicKeyBlob` Parametre ortak dil çalışma zamanı tarafından ayrılır ve arayana döndürülür.</span><span class="sxs-lookup"><span data-stu-id="cb755-120">The `ppbPublicKeyBlob` parameter is allocated by the common language runtime and returned to the caller.</span></span> <span data-ttu-id="cb755-121">Arayan [StrongNameFreeBuffer](strongnamefreebuffer-function.md) işlevini kullanarak belleği serbest etmelidir.</span><span class="sxs-lookup"><span data-stu-id="cb755-121">The caller must free the memory by using the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="cb755-122">[çıkış] Döndürülen ortak anahtar BLOB boyutu.</span><span class="sxs-lookup"><span data-stu-id="cb755-122">[out] The size of the returned public key BLOB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cb755-123">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="cb755-123">Return Value</span></span>  
 <span data-ttu-id="cb755-124">`true`başarılı bir şekilde tamamlandığında; aksi `false`takdirde, .</span><span class="sxs-lookup"><span data-stu-id="cb755-124">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cb755-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cb755-125">Remarks</span></span>  
 <span data-ttu-id="cb755-126">Ortak anahtar [PublicKeyBlob](publickeyblob-structure.md) yapısında yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="cb755-126">The public key is contained in a [PublicKeyBlob](publickeyblob-structure.md) structure.</span></span>  
  
 <span data-ttu-id="cb755-127">`StrongNameGetPublicKey` İşlev başarıyla tamamlanmamışsa, oluşturulan son hatayı almak için [StrongNameErrorInfo](strongnameerrorinfo-function.md) işlevini arayın.</span><span class="sxs-lookup"><span data-stu-id="cb755-127">If the `StrongNameGetPublicKey` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb755-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cb755-128">Requirements</span></span>  
 <span data-ttu-id="cb755-129">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb755-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb755-130">**Üstbilgi:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="cb755-130">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="cb755-131">**Kütüphane:** MsCorEE.dll bir kaynak olarak dahil</span><span class="sxs-lookup"><span data-stu-id="cb755-131">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cb755-132">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb755-132">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb755-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cb755-133">See also</span></span>

- [<span data-ttu-id="cb755-134">StrongNameGetPublicKey Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cb755-134">StrongNameGetPublicKey Method</span></span>](../hosting/iclrstrongname-strongnamegetpublickey-method.md)
- [<span data-ttu-id="cb755-135">StrongNameTokenFromPublicKey Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cb755-135">StrongNameTokenFromPublicKey Method</span></span>](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [<span data-ttu-id="cb755-136">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cb755-136">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
- [<span data-ttu-id="cb755-137">PublicKeyBlob Yapısı</span><span class="sxs-lookup"><span data-stu-id="cb755-137">PublicKeyBlob Structure</span></span>](publickeyblob-structure.md)
