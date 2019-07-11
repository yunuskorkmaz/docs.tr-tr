---
title: StrongNameKeyGenEx İşlevi
ms.date: 03/30/2017
api_name:
- StrongNameKeyGenEx
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameKeyGenEx
helpviewer_keywords:
- StrongNameKeyGenEx function [.NET Framework strong naming]
ms.assetid: 36bd10b9-9857-45f3-8d3b-0da091d6169e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d2ed9ba4b580b8f64fc05dbb429742442a36acf5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67757469"
---
# <a name="strongnamekeygenex-function"></a><span data-ttu-id="3f3d0-102">StrongNameKeyGenEx İşlevi</span><span class="sxs-lookup"><span data-stu-id="3f3d0-102">StrongNameKeyGenEx Function</span></span>
<span data-ttu-id="3f3d0-103">Tanımlayıcı ad kullanmak için belirtilen anahtar boyutu ile yeni bir ortak/özel anahtar çifti oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3f3d0-103">Generates a new public/private key pair with the specified key size, for strong name use.</span></span>  
  
 <span data-ttu-id="3f3d0-104">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="3f3d0-104">This function has been deprecated.</span></span> <span data-ttu-id="3f3d0-105">Kullanım [Iclrstrongname::strongnamekeygenex](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygenex-method.md) yöntemi yerine.</span><span class="sxs-lookup"><span data-stu-id="3f3d0-105">Use the [ICLRStrongName::StrongNameKeyGenEx](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygenex-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f3d0-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3f3d0-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameKeyGenEx (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [in]  DWORD     dwKeySize,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3f3d0-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3f3d0-107">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="3f3d0-108">[in] İstenen anahtar kapsayıcısı adı.</span><span class="sxs-lookup"><span data-stu-id="3f3d0-108">[in] The requested key container name.</span></span> <span data-ttu-id="3f3d0-109">`wszKeyContainer` gereken boş olmayan bir dize olması veya geçici bir ad oluşturmak için null.</span><span class="sxs-lookup"><span data-stu-id="3f3d0-109">`wszKeyContainer` must be a non-empty string, or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="3f3d0-110">[in] Kaydedilen anahtar bırakın belirtir.</span><span class="sxs-lookup"><span data-stu-id="3f3d0-110">[in] Specifies whether to leave the key registered.</span></span> <span data-ttu-id="3f3d0-111">Aşağıdaki değerleri desteklenir:</span><span class="sxs-lookup"><span data-stu-id="3f3d0-111">The following values are supported:</span></span>  
  
- <span data-ttu-id="3f3d0-112">kullanılan 0x00000000 - `wszKeyContainer` geçici bir anahtar kapsayıcısı adını oluşturmak için null.</span><span class="sxs-lookup"><span data-stu-id="3f3d0-112">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
- <span data-ttu-id="3f3d0-113">0x00000001 (`SN_LEAVE_KEY`)-anahtar sol kaydedilmesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="3f3d0-113">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `dwKeySize`  
 <span data-ttu-id="3f3d0-114">[in] İstenen bit cinsinden anahtar boyutunu.</span><span class="sxs-lookup"><span data-stu-id="3f3d0-114">[in] The requested size of the key, in bits.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="3f3d0-115">[out] Döndürülen ortak/özel anahtar çifti.</span><span class="sxs-lookup"><span data-stu-id="3f3d0-115">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="3f3d0-116">[out] Bayt cinsinden boyutu, `ppbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="3f3d0-116">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3f3d0-117">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3f3d0-117">Return Value</span></span>  
 <span data-ttu-id="3f3d0-118">`true` başarıyla tamamlandığında; Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="3f3d0-118">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3f3d0-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3f3d0-119">Remarks</span></span>  
 <span data-ttu-id="3f3d0-120">.NET Framework sürümleri 1.0 ve 1.1 gerektiren bir `dwKeySize` derlemeyi bir katı adla imzalamak için 1024 bit 2048 bit anahtar için desteklenen sürüm 2.0 ekler.</span><span class="sxs-lookup"><span data-stu-id="3f3d0-120">The .NET Framework versions 1.0 and 1.1 require a `dwKeySize` of 1024 bits to sign an assembly with a strong name; version 2.0 adds supports for 2048-bit keys.</span></span>  
  
 <span data-ttu-id="3f3d0-121">Anahtarı aldıktan sonra çağırmalıdır [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) ayrılan belleği serbest bırakmak için işlevi.</span><span class="sxs-lookup"><span data-stu-id="3f3d0-121">After the key is retrieved, you should call the [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) function to release the allocated memory.</span></span>  
  
 <span data-ttu-id="3f3d0-122">Varsa `StrongNameKeyGenEx` işlevi değil başarıyla tamamlanması, çağrı [Strongnameerrorınfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) oluşturulan son hatayı alması için işlevi.</span><span class="sxs-lookup"><span data-stu-id="3f3d0-122">If the `StrongNameKeyGenEx` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f3d0-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3f3d0-123">Requirements</span></span>  
 <span data-ttu-id="3f3d0-124">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3f3d0-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f3d0-125">**Üst bilgi:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="3f3d0-125">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="3f3d0-126">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="3f3d0-126">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3f3d0-127">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f3d0-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f3d0-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3f3d0-128">See also</span></span>

- [<span data-ttu-id="3f3d0-129">StrongNameKeyGenEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3f3d0-129">StrongNameKeyGenEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygenex-method.md)
- [<span data-ttu-id="3f3d0-130">StrongNameKeyGen Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3f3d0-130">StrongNameKeyGen Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md)
- [<span data-ttu-id="3f3d0-131">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3f3d0-131">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
