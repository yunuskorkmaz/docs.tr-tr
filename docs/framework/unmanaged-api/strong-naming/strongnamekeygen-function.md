---
title: "StrongNameKeyGen İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StrongNameKeyGen
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: StrongNameKeyGen
helpviewer_keywords: StrongNameKeyGen function [.NET Framework strong naming]
ms.assetid: 883e413a-ad2f-4f7f-b1b9-aeb8fe5b65f8
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4410719674b72bf25be63756edc89802740cb3cf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="strongnamekeygen-function"></a><span data-ttu-id="0d666-102">StrongNameKeyGen İşlevi</span><span class="sxs-lookup"><span data-stu-id="0d666-102">StrongNameKeyGen Function</span></span>
<span data-ttu-id="0d666-103">Güçlü ad kullanmak için yeni bir ortak/özel anahtar çifti oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0d666-103">Creates a new public/private key pair for strong name use.</span></span>  
  
 <span data-ttu-id="0d666-104">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="0d666-104">This function has been deprecated.</span></span> <span data-ttu-id="0d666-105">Kullanım [Iclrstrongname::strongnamekeygen](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md) yöntemi yerine.</span><span class="sxs-lookup"><span data-stu-id="0d666-105">Use the [ICLRStrongName::StrongNameKeyGen](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d666-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0d666-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameKeyGen (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0d666-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0d666-107">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="0d666-108">[in] İstenen anahtar kapsayıcısı adı.</span><span class="sxs-lookup"><span data-stu-id="0d666-108">[in] The requested key container name.</span></span> <span data-ttu-id="0d666-109">`wszKeyContainer`gereken boş olmayan bir dize olabilir veya geçici bir ad oluşturmak için null.</span><span class="sxs-lookup"><span data-stu-id="0d666-109">`wszKeyContainer` must be a non-empty string, or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="0d666-110">[in] Kayıtlı anahtarı bırakın belirtir.</span><span class="sxs-lookup"><span data-stu-id="0d666-110">[in] Specifies whether to leave the key registered.</span></span> <span data-ttu-id="0d666-111">Aşağıdaki değerleri desteklenir:</span><span class="sxs-lookup"><span data-stu-id="0d666-111">The following values are supported:</span></span>  
  
-   <span data-ttu-id="0d666-112">kullanılan 0x00000000 - `wszKeyContainer` bir geçici anahtar kapsayıcı adı oluşturmak için null.</span><span class="sxs-lookup"><span data-stu-id="0d666-112">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
-   <span data-ttu-id="0d666-113">0x00000001 (`SN_LEAVE_KEY`)-anahtar sol kaydedilmesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="0d666-113">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="0d666-114">[out] Döndürülen ortak/özel anahtar çifti.</span><span class="sxs-lookup"><span data-stu-id="0d666-114">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="0d666-115">[out] Bayt olarak boyutu, `ppbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="0d666-115">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0d666-116">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="0d666-116">Return Value</span></span>  
 <span data-ttu-id="0d666-117">`true`başarılı tamamlanma; Aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="0d666-117">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0d666-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0d666-118">Remarks</span></span>  
 <span data-ttu-id="0d666-119">`StrongNameKeyGen` İşlevi 1024 bit anahtar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0d666-119">The `StrongNameKeyGen` function creates a 1024-bit key.</span></span> <span data-ttu-id="0d666-120">Anahtarı aldıktan sonra çağırmalıdır [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) ayrılmış bellek yayımlamayı işlevi.</span><span class="sxs-lookup"><span data-stu-id="0d666-120">After the key is retrieved, you should call the [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) function to release the allocated memory.</span></span>  
  
 <span data-ttu-id="0d666-121">Varsa `StrongNameKeyGen` işlevi yok başarıyla tamamlanması, çağrı [Strongnameerrorınfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) son oluşturulan hata alınacak işlev.</span><span class="sxs-lookup"><span data-stu-id="0d666-121">If the `StrongNameKeyGen` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d666-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0d666-122">Requirements</span></span>  
 <span data-ttu-id="0d666-123">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0d666-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d666-124">**Başlık:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="0d666-124">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="0d666-125">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="0d666-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0d666-126">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d666-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d666-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0d666-127">See Also</span></span>  
 [<span data-ttu-id="0d666-128">StrongNameKeyGen yöntemi</span><span class="sxs-lookup"><span data-stu-id="0d666-128">StrongNameKeyGen Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md)  
 [<span data-ttu-id="0d666-129">StrongNameKeyGenEx yöntemi</span><span class="sxs-lookup"><span data-stu-id="0d666-129">StrongNameKeyGenEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygenex-method.md)  
 [<span data-ttu-id="0d666-130">Iclrstrongname arabirimi</span><span class="sxs-lookup"><span data-stu-id="0d666-130">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
