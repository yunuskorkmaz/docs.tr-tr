---
title: "StrongNameSignatureVerification İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StrongNameSignatureVerification
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: StrongNameSignatureVerification
helpviewer_keywords: StrongNameSignatureVerification function [.NET Framework strong naming]
ms.assetid: 933758dd-231e-4382-8819-242c0a13a4b7
topic_type: apiref
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a2c04aba5b774b299e26be8dc532b894b6c6fad5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="strongnamesignatureverification-function"></a><span data-ttu-id="0ea1f-102">StrongNameSignatureVerification İşlevi</span><span class="sxs-lookup"><span data-stu-id="0ea1f-102">StrongNameSignatureVerification Function</span></span>
<span data-ttu-id="0ea1f-103">Derleme bildirimi sağlanan yolunda belirtilen bayrakları göre doğrulanır bir tanımlayıcı ad imzası içerip içermediğini gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="0ea1f-103">Gets a value indicating whether the assembly manifest at the supplied path contains a strong name signature, which is verified according to the specified flags.</span></span>  
  
 <span data-ttu-id="0ea1f-104">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="0ea1f-104">This function has been deprecated.</span></span> <span data-ttu-id="0ea1f-105">Kullanım [Iclrstrongname::strongnamesignatureverification](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md) yöntemi yerine.</span><span class="sxs-lookup"><span data-stu-id="0ea1f-105">Use the [ICLRStrongName::StrongNameSignatureVerification](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ea1f-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0ea1f-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameSignatureVerification (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  DWORD     dwInFlags,  
    [out] DWORD     *pdwOutFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0ea1f-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0ea1f-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="0ea1f-108">[in] Taşınabilir yürütülebilir (.dll veya .exe) dosyayı doğrulamak derleme yolu.</span><span class="sxs-lookup"><span data-stu-id="0ea1f-108">[in] The path to the portable executable (.dll or .exe) file for the assembly to verify.</span></span>  
  
 `dwInFlags`  
 <span data-ttu-id="0ea1f-109">[in] Doğrulama davranışını değiştirmek için işaretler.</span><span class="sxs-lookup"><span data-stu-id="0ea1f-109">[in] Flags to modify the verification behavior.</span></span> <span data-ttu-id="0ea1f-110">Aşağıdaki değerleri desteklenir:</span><span class="sxs-lookup"><span data-stu-id="0ea1f-110">The following values are supported:</span></span>  
  
-   <span data-ttu-id="0ea1f-111">`SN_INFLAG_FORCE_VER`(0x00000001) - kayıt defteri ayarlarını geçersiz kılmak gerekli olduğu halde doğrulama zorlar.</span><span class="sxs-lookup"><span data-stu-id="0ea1f-111">`SN_INFLAG_FORCE_VER` (0x00000001) - Forces verification even if it is necessary to override registry settings.</span></span>  
  
-   <span data-ttu-id="0ea1f-112">`SN_INFLAG_INSTALL`(0x00000002) - Bu bildirimi doğrulanır ilk kez olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="0ea1f-112">`SN_INFLAG_INSTALL` (0x00000002) - Specifies that this is the first time the manifest is verified.</span></span>  
  
-   <span data-ttu-id="0ea1f-113">`SN_INFLAG_ADMIN_ACCESS`(0x00000004) - önbelleğe erişimi yalnızca yönetici ayrıcalıklarına sahip olan kullanıcılara izin verip belirtir.</span><span class="sxs-lookup"><span data-stu-id="0ea1f-113">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) - Specifies that the cache will allow access only to users who have administrative privileges.</span></span>  
  
-   <span data-ttu-id="0ea1f-114">`SN_INFLAG_USER_ACCESS`(0x00000008) - derleme yalnızca geçerli kullanıcıya erişilebilir olacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="0ea1f-114">`SN_INFLAG_USER_ACCESS` (0x00000008) - Specifies that the assembly will be accessible only to the current user.</span></span>  
  
-   <span data-ttu-id="0ea1f-115">`SN_INFLAG_ALL_ACCESS`(0x00000010) - önbellek garanti erişim kısıtlama sağlayacak belirtir.</span><span class="sxs-lookup"><span data-stu-id="0ea1f-115">`SN_INFLAG_ALL_ACCESS` (0x00000010) - Specifies that the cache will provide no guarantees of access restriction.</span></span>  
  
-   <span data-ttu-id="0ea1f-116">`SN_INFLAG_RUNTIME`(0x80000000) - iç hata ayıklama için ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="0ea1f-116">`SN_INFLAG_RUNTIME` (0x80000000) - Reserved for internal debugging.</span></span>  
  
 `pdwOutFlags`  
 <span data-ttu-id="0ea1f-117">[out] Tanımlayıcı ad imzası doğrulandı olup olmadığını belirten işaretler.</span><span class="sxs-lookup"><span data-stu-id="0ea1f-117">[out] Flags indicating whether the strong name signature was verified.</span></span> <span data-ttu-id="0ea1f-118">Aşağıdaki değeri desteklenir:</span><span class="sxs-lookup"><span data-stu-id="0ea1f-118">The following value is supported:</span></span>  
  
-   <span data-ttu-id="0ea1f-119">`SN_OUTFLAG_WAS_VERIFIED`(0x00000001) - bu değeri ayarı `false` doğrulama kayıt defteri ayarları nedeniyle başarılı olduğunu belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="0ea1f-119">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001) - This value is set to `false` to specify that the verification succeeded due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0ea1f-120">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="0ea1f-120">Return Value</span></span>  
 <span data-ttu-id="0ea1f-121">`true`doğrulama başarılı olursa; Aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="0ea1f-121">`true` if the verification was successful; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0ea1f-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0ea1f-122">Requirements</span></span>  
 <span data-ttu-id="0ea1f-123">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0ea1f-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ea1f-124">**Başlık:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="0ea1f-124">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="0ea1f-125">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="0ea1f-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0ea1f-126">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ea1f-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ea1f-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0ea1f-127">See Also</span></span>  
 [<span data-ttu-id="0ea1f-128">StrongNameSignatureVerification yöntemi</span><span class="sxs-lookup"><span data-stu-id="0ea1f-128">StrongNameSignatureVerification Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md)  
 [<span data-ttu-id="0ea1f-129">StrongNameSignatureVerificationEx yöntemi</span><span class="sxs-lookup"><span data-stu-id="0ea1f-129">StrongNameSignatureVerificationEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md)  
 [<span data-ttu-id="0ea1f-130">Iclrstrongname arabirimi</span><span class="sxs-lookup"><span data-stu-id="0ea1f-130">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
