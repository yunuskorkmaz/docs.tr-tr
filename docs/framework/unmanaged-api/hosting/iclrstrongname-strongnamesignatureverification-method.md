---
title: ICLRStrongName::StrongNameSignatureVerification Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameSignatureVerification
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureVerification
helpviewer_keywords:
- ICLRStrongName::StrongNameSignatureVerification method [.NET Framework hosting]
- StrongNameSignatureVerification method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 734dc4d1-0a76-4736-b5ac-cb4253b3dd49
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6b773203ef390122626ea3c51644e43e571740ca
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54569316"
---
# <a name="iclrstrongnamestrongnamesignatureverification-method"></a><span data-ttu-id="103b2-102">ICLRStrongName::StrongNameSignatureVerification Yöntemi</span><span class="sxs-lookup"><span data-stu-id="103b2-102">ICLRStrongName::StrongNameSignatureVerification Method</span></span>
<span data-ttu-id="103b2-103">Sağlanan yol, derleme bildirimi belirtilen bayraklar göre doğrulanan bir tanımlayıcı ad imzası içerip içermediğini gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="103b2-103">Gets a value that indicates whether the assembly manifest at the supplied path contains a strong name signature, which is verified according to the specified flags.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="103b2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="103b2-104">Syntax</span></span>  
  
```  
HRESULT StrongNameSignatureVerification (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  DWORD     dwInFlags,  
    [out] DWORD     *pdwOutFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="103b2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="103b2-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="103b2-106">[in] Taşınabilir yürütülebilir (.dll veya .exe) dosyayı doğrulamak derleme yolu.</span><span class="sxs-lookup"><span data-stu-id="103b2-106">[in] The path to the portable executable (.dll or .exe) file for the assembly to verify.</span></span>  
  
 `dwInFlags`  
 <span data-ttu-id="103b2-107">[in] Doğrulama davranışını değiştirmek için işaretler.</span><span class="sxs-lookup"><span data-stu-id="103b2-107">[in] Flags to modify the verification behavior.</span></span> <span data-ttu-id="103b2-108">Aşağıdaki değerleri desteklenir:</span><span class="sxs-lookup"><span data-stu-id="103b2-108">The following values are supported:</span></span>  
  
-   <span data-ttu-id="103b2-109">`SN_INFLAG_FORCE_VER` (0x00000001) - kayıt defteri ayarlarını geçersiz kılmak gerekli olsa bile doğrulama zorlar.</span><span class="sxs-lookup"><span data-stu-id="103b2-109">`SN_INFLAG_FORCE_VER` (0x00000001) - Forces verification even if it is necessary to override registry settings.</span></span>  
  
-   <span data-ttu-id="103b2-110">`SN_INFLAG_INSTALL` (0x00000002) - Bu bildirimi doğrulanır ilk kez olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="103b2-110">`SN_INFLAG_INSTALL` (0x00000002) - Specifies that this is the first time the manifest is verified.</span></span>  
  
-   <span data-ttu-id="103b2-111">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) - önbellek yönetici ayrıcalıklarına sahip kullanıcılara erişimi sağlayacak belirtir.</span><span class="sxs-lookup"><span data-stu-id="103b2-111">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) - Specifies that the cache will allow access only to users who have administrative privileges.</span></span>  
  
-   <span data-ttu-id="103b2-112">`SN_INFLAG_USER_ACCESS` (0x00000008) - derleme yalnızca geçerli kullanıcı için erişilebilir olacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="103b2-112">`SN_INFLAG_USER_ACCESS` (0x00000008) - Specifies that the assembly will be accessible only to the current user.</span></span>  
  
-   <span data-ttu-id="103b2-113">`SN_INFLAG_ALL_ACCESS` (0x00000010) - önbellek garanti erişim kısıtlama sağlayacak belirtir.</span><span class="sxs-lookup"><span data-stu-id="103b2-113">`SN_INFLAG_ALL_ACCESS` (0x00000010) - Specifies that the cache will provide no guarantees of access restriction.</span></span>  
  
-   <span data-ttu-id="103b2-114">`SN_INFLAG_RUNTIME` (0x80000000) - iç hata ayıklama için ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="103b2-114">`SN_INFLAG_RUNTIME` (0x80000000) - Reserved for internal debugging.</span></span>  
  
 `pdwOutFlags`  
 <span data-ttu-id="103b2-115">[out] Tanımlayıcı ad imzası doğrulandı olup olmadığını belirten bayrak.</span><span class="sxs-lookup"><span data-stu-id="103b2-115">[out] Flags indicating whether the strong name signature was verified.</span></span> <span data-ttu-id="103b2-116">Aşağıdaki değeri desteklenir:</span><span class="sxs-lookup"><span data-stu-id="103b2-116">The following value is supported:</span></span>  
  
-   <span data-ttu-id="103b2-117">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001) - bu değeri ayarı `false` doğrulama kayıt defteri ayarları nedeniyle başarılı olduğunu belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="103b2-117">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001) - This value is set to `false` to specify that the verification succeeded due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="103b2-118">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="103b2-118">Return Value</span></span>  
 <span data-ttu-id="103b2-119">`S_OK` yöntemi başarıyla tamamlandı Aksi takdirde hata olduğunu gösteren HRESULT değerini (bkz [ortak HRESULT değerlerini](https://go.microsoft.com/fwlink/?LinkId=213878) bir listesi için).</span><span class="sxs-lookup"><span data-stu-id="103b2-119">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="103b2-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="103b2-120">Requirements</span></span>  
 <span data-ttu-id="103b2-121">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="103b2-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="103b2-122">**Üst bilgi:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="103b2-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="103b2-123">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="103b2-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="103b2-124">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="103b2-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="103b2-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="103b2-125">See also</span></span>
- [<span data-ttu-id="103b2-126">StrongNameSignatureVerificationEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="103b2-126">StrongNameSignatureVerificationEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md)
- [<span data-ttu-id="103b2-127">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="103b2-127">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
