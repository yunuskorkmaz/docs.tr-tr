---
title: StrongNameSignatureVerificationFromImage İşlevi
ms.date: 03/30/2017
api_name:
- StrongNameSignatureVerificationFromImage
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureVerificationFromImage
helpviewer_keywords:
- StrongnameSignatureVerificationFromImage function [.NET Framework strong naming]
ms.assetid: 9fb144d2-07e0-4a0e-8e05-907bbb6c9e03
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 844449bbce847883e5ba125d656adc4480f1fd23
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57497073"
---
# <a name="strongnamesignatureverificationfromimage-function"></a><span data-ttu-id="ea2f6-102">StrongNameSignatureVerificationFromImage İşlevi</span><span class="sxs-lookup"><span data-stu-id="ea2f6-102">StrongNameSignatureVerificationFromImage Function</span></span>
<span data-ttu-id="ea2f6-103">Bellek zaten eşleştirilmiş bir derleme için ilişkili ortak anahtar geçerli olduğunu doğrular.</span><span class="sxs-lookup"><span data-stu-id="ea2f6-103">Verifies that an assembly that has already been mapped to memory is valid for the associated public key.</span></span>  
  
 <span data-ttu-id="ea2f6-104">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="ea2f6-104">This function has been deprecated.</span></span> <span data-ttu-id="ea2f6-105">Kullanım [ICLRStrongName::StrongNameVerificationFromImage](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationfromimage-method.md) yöntemi yerine.</span><span class="sxs-lookup"><span data-stu-id="ea2f6-105">Use the [ICLRStrongName::StrongNameVerificationFromImage](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationfromimage-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea2f6-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ea2f6-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameSignatureVerificationFromImage (  
    [in]  BYTE    *pbBase,  
    [in]  DWORD   dwLength,  
    [in]  DWORD   dwInFlags,  
    [out] DWORD   *pdwOutFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ea2f6-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ea2f6-107">Parameters</span></span>  
 `pbBase`  
 <span data-ttu-id="ea2f6-108">[in] Eşlenen derleme bildirimi göreli sanal adres.</span><span class="sxs-lookup"><span data-stu-id="ea2f6-108">[in] The relative virtual address of the mapped assembly manifest.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="ea2f6-109">[in] Baytlarında eşlenen görüntünün boyutu.</span><span class="sxs-lookup"><span data-stu-id="ea2f6-109">[in] The size, in bytes, of the mapped image.</span></span>  
  
 `dwInFlags`  
 <span data-ttu-id="ea2f6-110">[in] Doğrulama davranışını etkileyen bayraklar.</span><span class="sxs-lookup"><span data-stu-id="ea2f6-110">[in] Flags that influence verification behavior.</span></span> <span data-ttu-id="ea2f6-111">Aşağıdaki değerleri desteklenir:</span><span class="sxs-lookup"><span data-stu-id="ea2f6-111">The following values are supported:</span></span>  
  
-   <span data-ttu-id="ea2f6-112">`SN_INFLAG_FORCE_VER` (0x00000001) - kayıt defteri ayarlarını geçersiz kılmak gerekli olsa bile doğrulama zorlar.</span><span class="sxs-lookup"><span data-stu-id="ea2f6-112">`SN_INFLAG_FORCE_VER` (0x00000001) - Forces verification even if it is necessary to override registry settings.</span></span>  
  
-   <span data-ttu-id="ea2f6-113">`SN_INFLAG_INSTALL` (0x00000002) - bu görüntüye gerçekleştirilen ilk doğrulama olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="ea2f6-113">`SN_INFLAG_INSTALL` (0x00000002) - Specifies that this is the first verification performed on this image.</span></span>  
  
-   <span data-ttu-id="ea2f6-114">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) - önbellek yönetici ayrıcalıklarına sahip kullanıcılara erişimi sağlayacak belirtir.</span><span class="sxs-lookup"><span data-stu-id="ea2f6-114">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) - Specifies that the cache will allow access only to users who have administrative privileges.</span></span>  
  
-   <span data-ttu-id="ea2f6-115">`SN_INFLAG_USER_ACCESS` (0x00000008) - derleme yalnızca geçerli kullanıcı için erişilebilir olacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ea2f6-115">`SN_INFLAG_USER_ACCESS` (0x00000008) - Specifies that the assembly will be accessible only to the current user.</span></span>  
  
-   <span data-ttu-id="ea2f6-116">`SN_INFLAG_ALL_ACCESS` (0x00000010) - önbellek garanti erişim kısıtlama sağlayacak belirtir.</span><span class="sxs-lookup"><span data-stu-id="ea2f6-116">`SN_INFLAG_ALL_ACCESS` (0x00000010) - Specifies that the cache will provide no guarantees of access restriction.</span></span>  
  
-   <span data-ttu-id="ea2f6-117">`SN_INFLAG_RUNTIME` (0x80000000) - iç hata ayıklama için ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="ea2f6-117">`SN_INFLAG_RUNTIME` (0x80000000) - Reserved for internal debugging.</span></span>  
  
 `pdwOutFlags`  
 <span data-ttu-id="ea2f6-118">[out] Çıktı ek bilgi için bir bayrak.</span><span class="sxs-lookup"><span data-stu-id="ea2f6-118">[out] A flag for additional output information.</span></span> <span data-ttu-id="ea2f6-119">Aşağıdaki değeri desteklenir:</span><span class="sxs-lookup"><span data-stu-id="ea2f6-119">The following value is supported:</span></span>  
  
-   <span data-ttu-id="ea2f6-120">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001) - bu değeri ayarı `false` doğrulama kayıt defteri ayarları nedeniyle başarılı olduğunu belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="ea2f6-120">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001) - This value is set to `false` to specify that the verification succeeded due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ea2f6-121">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ea2f6-121">Return Value</span></span>  
 <span data-ttu-id="ea2f6-122">`true` başarıyla tamamlandığında; Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="ea2f6-122">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ea2f6-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ea2f6-123">Remarks</span></span>  
 <span data-ttu-id="ea2f6-124">Varsa `StrongNameSignatureVerificationFromImage` işlevi değil başarıyla tamamlanması, çağrı [Strongnameerrorınfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) oluşturulan son hatayı alması için işlevi.</span><span class="sxs-lookup"><span data-stu-id="ea2f6-124">If the `StrongNameSignatureVerificationFromImage` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea2f6-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ea2f6-125">Requirements</span></span>  
 <span data-ttu-id="ea2f6-126">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ea2f6-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea2f6-127">**Üst bilgi:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="ea2f6-127">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="ea2f6-128">**Kitaplığı:** Bir kaynak olarak mscoree.dll dahil</span><span class="sxs-lookup"><span data-stu-id="ea2f6-128">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="ea2f6-129">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea2f6-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea2f6-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ea2f6-130">See also</span></span>
- [<span data-ttu-id="ea2f6-131">StrongNameSignatureVerificationFromImage Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ea2f6-131">StrongNameSignatureVerificationFromImage Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationfromimage-method.md)
- [<span data-ttu-id="ea2f6-132">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ea2f6-132">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
