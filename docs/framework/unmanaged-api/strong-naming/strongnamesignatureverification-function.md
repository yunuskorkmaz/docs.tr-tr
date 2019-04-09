---
title: StrongNameSignatureVerification İşlevi
ms.date: 03/30/2017
api_name:
- StrongNameSignatureVerification
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureVerification
helpviewer_keywords:
- StrongNameSignatureVerification function [.NET Framework strong naming]
ms.assetid: 933758dd-231e-4382-8819-242c0a13a4b7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c398663b84637d2551b0d94bd59b9e0994721ba5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59124773"
---
# <a name="strongnamesignatureverification-function"></a><span data-ttu-id="26e6d-102">StrongNameSignatureVerification İşlevi</span><span class="sxs-lookup"><span data-stu-id="26e6d-102">StrongNameSignatureVerification Function</span></span>
<span data-ttu-id="26e6d-103">Sağlanan yol, derleme bildirimi belirtilen bayraklar göre doğrulanan bir tanımlayıcı ad imzası içerip içermediğini gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="26e6d-103">Gets a value indicating whether the assembly manifest at the supplied path contains a strong name signature, which is verified according to the specified flags.</span></span>  
  
 <span data-ttu-id="26e6d-104">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="26e6d-104">This function has been deprecated.</span></span> <span data-ttu-id="26e6d-105">Kullanım [Iclrstrongname::strongnamesignatureverification](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md) yöntemi yerine.</span><span class="sxs-lookup"><span data-stu-id="26e6d-105">Use the [ICLRStrongName::StrongNameSignatureVerification](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26e6d-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="26e6d-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameSignatureVerification (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  DWORD     dwInFlags,  
    [out] DWORD     *pdwOutFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="26e6d-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="26e6d-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="26e6d-108">[in] Taşınabilir yürütülebilir (.dll veya .exe) dosyayı doğrulamak derleme yolu.</span><span class="sxs-lookup"><span data-stu-id="26e6d-108">[in] The path to the portable executable (.dll or .exe) file for the assembly to verify.</span></span>  
  
 `dwInFlags`  
 <span data-ttu-id="26e6d-109">[in] Doğrulama davranışını değiştirmek için işaretler.</span><span class="sxs-lookup"><span data-stu-id="26e6d-109">[in] Flags to modify the verification behavior.</span></span> <span data-ttu-id="26e6d-110">Aşağıdaki değerleri desteklenir:</span><span class="sxs-lookup"><span data-stu-id="26e6d-110">The following values are supported:</span></span>  
  
-   `SN_INFLAG_FORCE_VER` <span data-ttu-id="26e6d-111">(0x00000001) - kayıt defteri ayarlarını geçersiz kılmak gerekli olsa bile doğrulama zorlar.</span><span class="sxs-lookup"><span data-stu-id="26e6d-111">(0x00000001) - Forces verification even if it is necessary to override registry settings.</span></span>  
  
-   `SN_INFLAG_INSTALL` <span data-ttu-id="26e6d-112">(0x00000002) - Bu bildirimi doğrulanır ilk kez olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="26e6d-112">(0x00000002) - Specifies that this is the first time the manifest is verified.</span></span>  
  
-   `SN_INFLAG_ADMIN_ACCESS` <span data-ttu-id="26e6d-113">(0x00000004) - önbellek yönetici ayrıcalıklarına sahip kullanıcılara erişimi sağlayacak belirtir.</span><span class="sxs-lookup"><span data-stu-id="26e6d-113">(0x00000004) - Specifies that the cache will allow access only to users who have administrative privileges.</span></span>  
  
-   `SN_INFLAG_USER_ACCESS` <span data-ttu-id="26e6d-114">(0x00000008) - derleme yalnızca geçerli kullanıcı için erişilebilir olacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="26e6d-114">(0x00000008) - Specifies that the assembly will be accessible only to the current user.</span></span>  
  
-   `SN_INFLAG_ALL_ACCESS` <span data-ttu-id="26e6d-115">(0x00000010) - önbellek garanti erişim kısıtlama sağlayacak belirtir.</span><span class="sxs-lookup"><span data-stu-id="26e6d-115">(0x00000010) - Specifies that the cache will provide no guarantees of access restriction.</span></span>  
  
-   `SN_INFLAG_RUNTIME` <span data-ttu-id="26e6d-116">(0x80000000) - iç hata ayıklama için ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="26e6d-116">(0x80000000) - Reserved for internal debugging.</span></span>  
  
 `pdwOutFlags`  
 <span data-ttu-id="26e6d-117">[out] Tanımlayıcı ad imzası doğrulandı olup olmadığını belirten bayrak.</span><span class="sxs-lookup"><span data-stu-id="26e6d-117">[out] Flags indicating whether the strong name signature was verified.</span></span> <span data-ttu-id="26e6d-118">Aşağıdaki değeri desteklenir:</span><span class="sxs-lookup"><span data-stu-id="26e6d-118">The following value is supported:</span></span>  
  
-   `SN_OUTFLAG_WAS_VERIFIED` <span data-ttu-id="26e6d-119">(0x00000001) - bu değeri ayarı `false` doğrulama kayıt defteri ayarları nedeniyle başarılı olduğunu belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="26e6d-119">(0x00000001) - This value is set to `false` to specify that the verification succeeded due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="26e6d-120">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="26e6d-120">Return Value</span></span>  
 `true` <span data-ttu-id="26e6d-121">doğrulama başarılı olduysa; Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="26e6d-121">if the verification was successful; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="26e6d-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="26e6d-122">Requirements</span></span>  
 <span data-ttu-id="26e6d-123">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="26e6d-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26e6d-124">**Üst bilgi:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="26e6d-124">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="26e6d-125">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="26e6d-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="26e6d-126">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="26e6d-126">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="26e6d-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="26e6d-127">See also</span></span>

- [<span data-ttu-id="26e6d-128">StrongNameSignatureVerification Yöntemi</span><span class="sxs-lookup"><span data-stu-id="26e6d-128">StrongNameSignatureVerification Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md)
- [<span data-ttu-id="26e6d-129">StrongNameSignatureVerificationEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="26e6d-129">StrongNameSignatureVerificationEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md)
- [<span data-ttu-id="26e6d-130">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="26e6d-130">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
