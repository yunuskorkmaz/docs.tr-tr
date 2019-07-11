---
title: StrongNameKeyGen İşlevi
ms.date: 03/30/2017
api_name:
- StrongNameKeyGen
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameKeyGen
helpviewer_keywords:
- StrongNameKeyGen function [.NET Framework strong naming]
ms.assetid: 883e413a-ad2f-4f7f-b1b9-aeb8fe5b65f8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 74445b03e78ff68426f60c3e306d9151d0ba288a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780989"
---
# <a name="strongnamekeygen-function"></a><span data-ttu-id="f27df-102">StrongNameKeyGen İşlevi</span><span class="sxs-lookup"><span data-stu-id="f27df-102">StrongNameKeyGen Function</span></span>
<span data-ttu-id="f27df-103">Tanımlayıcı ad kullanmak için yeni bir ortak/özel anahtar çifti oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f27df-103">Creates a new public/private key pair for strong name use.</span></span>  
  
 <span data-ttu-id="f27df-104">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="f27df-104">This function has been deprecated.</span></span> <span data-ttu-id="f27df-105">Kullanım [Iclrstrongname::strongnamekeygen](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md) yöntemi yerine.</span><span class="sxs-lookup"><span data-stu-id="f27df-105">Use the [ICLRStrongName::StrongNameKeyGen](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f27df-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f27df-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameKeyGen (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f27df-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f27df-107">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="f27df-108">[in] İstenen anahtar kapsayıcısı adı.</span><span class="sxs-lookup"><span data-stu-id="f27df-108">[in] The requested key container name.</span></span> <span data-ttu-id="f27df-109">`wszKeyContainer` gereken boş olmayan bir dize olması veya geçici bir ad oluşturmak için null.</span><span class="sxs-lookup"><span data-stu-id="f27df-109">`wszKeyContainer` must be a non-empty string, or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="f27df-110">[in] Kaydedilen anahtar bırakın belirtir.</span><span class="sxs-lookup"><span data-stu-id="f27df-110">[in] Specifies whether to leave the key registered.</span></span> <span data-ttu-id="f27df-111">Aşağıdaki değerleri desteklenir:</span><span class="sxs-lookup"><span data-stu-id="f27df-111">The following values are supported:</span></span>  
  
- <span data-ttu-id="f27df-112">kullanılan 0x00000000 - `wszKeyContainer` geçici bir anahtar kapsayıcısı adını oluşturmak için null.</span><span class="sxs-lookup"><span data-stu-id="f27df-112">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
- <span data-ttu-id="f27df-113">0x00000001 (`SN_LEAVE_KEY`)-anahtar sol kaydedilmesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f27df-113">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="f27df-114">[out] Döndürülen ortak/özel anahtar çifti.</span><span class="sxs-lookup"><span data-stu-id="f27df-114">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="f27df-115">[out] Bayt cinsinden boyutu, `ppbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="f27df-115">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f27df-116">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="f27df-116">Return Value</span></span>  
 <span data-ttu-id="f27df-117">`true` başarıyla tamamlandığında; Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="f27df-117">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f27df-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f27df-118">Remarks</span></span>  
 <span data-ttu-id="f27df-119">`StrongNameKeyGen` İşlevi 1024 bit anahtar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f27df-119">The `StrongNameKeyGen` function creates a 1024-bit key.</span></span> <span data-ttu-id="f27df-120">Anahtarı aldıktan sonra çağırmalıdır [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) ayrılan belleği serbest bırakmak için işlevi.</span><span class="sxs-lookup"><span data-stu-id="f27df-120">After the key is retrieved, you should call the [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) function to release the allocated memory.</span></span>  
  
 <span data-ttu-id="f27df-121">Varsa `StrongNameKeyGen` işlevi değil başarıyla tamamlanması, çağrı [Strongnameerrorınfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) oluşturulan son hatayı alması için işlevi.</span><span class="sxs-lookup"><span data-stu-id="f27df-121">If the `StrongNameKeyGen` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f27df-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f27df-122">Requirements</span></span>  
 <span data-ttu-id="f27df-123">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f27df-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f27df-124">**Üst bilgi:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="f27df-124">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="f27df-125">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="f27df-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f27df-126">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f27df-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f27df-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f27df-127">See also</span></span>

- [<span data-ttu-id="f27df-128">StrongNameKeyGen Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f27df-128">StrongNameKeyGen Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md)
- [<span data-ttu-id="f27df-129">StrongNameKeyGenEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f27df-129">StrongNameKeyGenEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygenex-method.md)
- [<span data-ttu-id="f27df-130">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f27df-130">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
