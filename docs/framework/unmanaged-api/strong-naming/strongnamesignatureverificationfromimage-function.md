---
title: "StrongNameSignatureVerificationFromImage İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StrongNameSignatureVerificationFromImage
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: StrongNameSignatureVerificationFromImage
helpviewer_keywords: StrongnameSignatureVerificationFromImage function [.NET Framework strong naming]
ms.assetid: 9fb144d2-07e0-4a0e-8e05-907bbb6c9e03
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 178dcbae4f8ec40ac9ef14fc00109c83ab87c21a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="strongnamesignatureverificationfromimage-function"></a><span data-ttu-id="c90b0-102">StrongNameSignatureVerificationFromImage İşlevi</span><span class="sxs-lookup"><span data-stu-id="c90b0-102">StrongNameSignatureVerificationFromImage Function</span></span>
<span data-ttu-id="c90b0-103">Bellek zaten eşlendi bütünleştirilmiş ilişkili ortak anahtarı için geçerli olduğunu doğrular.</span><span class="sxs-lookup"><span data-stu-id="c90b0-103">Verifies that an assembly that has already been mapped to memory is valid for the associated public key.</span></span>  
  
 <span data-ttu-id="c90b0-104">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="c90b0-104">This function has been deprecated.</span></span> <span data-ttu-id="c90b0-105">Kullanım [ICLRStrongName::StrongNameVerificationFromImage](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationfromimage-method.md) yöntemi yerine.</span><span class="sxs-lookup"><span data-stu-id="c90b0-105">Use the [ICLRStrongName::StrongNameVerificationFromImage](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationfromimage-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c90b0-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c90b0-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameSignatureVerificationFromImage (  
    [in]  BYTE    *pbBase,  
    [in]  DWORD   dwLength,  
    [in]  DWORD   dwInFlags,  
    [out] DWORD   *pdwOutFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c90b0-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c90b0-107">Parameters</span></span>  
 `pbBase`  
 <span data-ttu-id="c90b0-108">[in] Eşlenen derleme bildirimi göreli sanal adresi.</span><span class="sxs-lookup"><span data-stu-id="c90b0-108">[in] The relative virtual address of the mapped assembly manifest.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="c90b0-109">[in] Eşlenen görüntünün bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="c90b0-109">[in] The size, in bytes, of the mapped image.</span></span>  
  
 `dwInFlags`  
 <span data-ttu-id="c90b0-110">[in] Doğrulama davranışını etkilemek bayraklar.</span><span class="sxs-lookup"><span data-stu-id="c90b0-110">[in] Flags that influence verification behavior.</span></span> <span data-ttu-id="c90b0-111">Aşağıdaki değerleri desteklenir:</span><span class="sxs-lookup"><span data-stu-id="c90b0-111">The following values are supported:</span></span>  
  
-   <span data-ttu-id="c90b0-112">`SN_INFLAG_FORCE_VER`(0x00000001) - kayıt defteri ayarlarını geçersiz kılmak gerekli olduğu halde doğrulama zorlar.</span><span class="sxs-lookup"><span data-stu-id="c90b0-112">`SN_INFLAG_FORCE_VER` (0x00000001) - Forces verification even if it is necessary to override registry settings.</span></span>  
  
-   <span data-ttu-id="c90b0-113">`SN_INFLAG_INSTALL`(0x00000002) - bu görüntü üzerinde gerçekleştirilen ilk doğrulama olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="c90b0-113">`SN_INFLAG_INSTALL` (0x00000002) - Specifies that this is the first verification performed on this image.</span></span>  
  
-   <span data-ttu-id="c90b0-114">`SN_INFLAG_ADMIN_ACCESS`(0x00000004) - önbelleğe erişimi yalnızca yönetici ayrıcalıklarına sahip olan kullanıcılara izin verip belirtir.</span><span class="sxs-lookup"><span data-stu-id="c90b0-114">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) - Specifies that the cache will allow access only to users who have administrative privileges.</span></span>  
  
-   <span data-ttu-id="c90b0-115">`SN_INFLAG_USER_ACCESS`(0x00000008) - derleme yalnızca geçerli kullanıcıya erişilebilir olacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c90b0-115">`SN_INFLAG_USER_ACCESS` (0x00000008) - Specifies that the assembly will be accessible only to the current user.</span></span>  
  
-   <span data-ttu-id="c90b0-116">`SN_INFLAG_ALL_ACCESS`(0x00000010) - önbellek garanti erişim kısıtlama sağlayacak belirtir.</span><span class="sxs-lookup"><span data-stu-id="c90b0-116">`SN_INFLAG_ALL_ACCESS` (0x00000010) - Specifies that the cache will provide no guarantees of access restriction.</span></span>  
  
-   <span data-ttu-id="c90b0-117">`SN_INFLAG_RUNTIME`(0x80000000) - iç hata ayıklama için ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="c90b0-117">`SN_INFLAG_RUNTIME` (0x80000000) - Reserved for internal debugging.</span></span>  
  
 `pdwOutFlags`  
 <span data-ttu-id="c90b0-118">[out] Ek çıkış bilgileri için bir bayrak.</span><span class="sxs-lookup"><span data-stu-id="c90b0-118">[out] A flag for additional output information.</span></span> <span data-ttu-id="c90b0-119">Aşağıdaki değeri desteklenir:</span><span class="sxs-lookup"><span data-stu-id="c90b0-119">The following value is supported:</span></span>  
  
-   <span data-ttu-id="c90b0-120">`SN_OUTFLAG_WAS_VERIFIED`(0x00000001) - bu değeri ayarı `false` doğrulama kayıt defteri ayarları nedeniyle başarılı olduğunu belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="c90b0-120">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001) - This value is set to `false` to specify that the verification succeeded due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c90b0-121">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c90b0-121">Return Value</span></span>  
 <span data-ttu-id="c90b0-122">`true`başarılı tamamlanma; Aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="c90b0-122">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c90b0-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c90b0-123">Remarks</span></span>  
 <span data-ttu-id="c90b0-124">Varsa `StrongNameSignatureVerificationFromImage` işlevi yok başarıyla tamamlanması, çağrı [Strongnameerrorınfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) son oluşturulan hata alınacak işlev.</span><span class="sxs-lookup"><span data-stu-id="c90b0-124">If the `StrongNameSignatureVerificationFromImage` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c90b0-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c90b0-125">Requirements</span></span>  
 <span data-ttu-id="c90b0-126">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c90b0-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c90b0-127">**Başlık:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="c90b0-127">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="c90b0-128">**Kitaplığı:** bir kaynak olarak mscoree.dll dahil</span><span class="sxs-lookup"><span data-stu-id="c90b0-128">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="c90b0-129">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c90b0-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c90b0-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c90b0-130">See Also</span></span>  
 [<span data-ttu-id="c90b0-131">StrongNameSignatureVerificationFromImage Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c90b0-131">StrongNameSignatureVerificationFromImage Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationfromimage-method.md)  
 [<span data-ttu-id="c90b0-132">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c90b0-132">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
