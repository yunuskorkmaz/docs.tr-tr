---
title: ICLRStrongName::StrongNameSignatureVerificationFromImage Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameSignatureVerificationFromImage
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureVerificationFromImage
helpviewer_keywords:
- ICLRStrongName::StrongNameSignatureVerificationFromImage method [.NET Framework hosting]
- StrongNameSignatureVerificationFromImage method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: da91c138-ee30-4fd4-a040-464d97d7e41a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a7e09ac96a8803f41d78b532c9da67315e5dd6b4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59113743"
---
# <a name="iclrstrongnamestrongnamesignatureverificationfromimage-method"></a><span data-ttu-id="e9d5d-102">ICLRStrongName::StrongNameSignatureVerificationFromImage Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e9d5d-102">ICLRStrongName::StrongNameSignatureVerificationFromImage Method</span></span>
<span data-ttu-id="e9d5d-103">Bellek zaten eşleştirilmiş bir derleme için ilişkili ortak anahtar geçerli olduğunu doğrular.</span><span class="sxs-lookup"><span data-stu-id="e9d5d-103">Verifies that an assembly that has already been mapped to memory is valid for the associated public key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9d5d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e9d5d-104">Syntax</span></span>  
  
```  
HRESULT StrongNameSignatureVerificationFromImage (  
    [in]  BYTE    *pbBase,  
    [in]  DWORD   dwLength,  
    [in]  DWORD   dwInFlags,  
    [out] DWORD   *pdwOutFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e9d5d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e9d5d-105">Parameters</span></span>  
 `pbBase`  
 <span data-ttu-id="e9d5d-106">[in] Eşlenen derleme bildirimi göreli sanal adres.</span><span class="sxs-lookup"><span data-stu-id="e9d5d-106">[in] The relative virtual address of the mapped assembly manifest.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="e9d5d-107">[in] Baytlarında eşlenen görüntünün boyutu.</span><span class="sxs-lookup"><span data-stu-id="e9d5d-107">[in] The size, in bytes, of the mapped image.</span></span>  
  
 `dwInFlags`  
 <span data-ttu-id="e9d5d-108">[in] Doğrulama davranışını etkileyen bayraklar.</span><span class="sxs-lookup"><span data-stu-id="e9d5d-108">[in] Flags that influence verification behavior.</span></span> <span data-ttu-id="e9d5d-109">Aşağıdaki değerleri desteklenir:</span><span class="sxs-lookup"><span data-stu-id="e9d5d-109">The following values are supported:</span></span>  
  
-   <span data-ttu-id="e9d5d-110">`SN_INFLAG_FORCE_VER` (0x00000001) - kayıt defteri ayarlarını geçersiz kılmak gerekli olsa bile doğrulama zorlar.</span><span class="sxs-lookup"><span data-stu-id="e9d5d-110">`SN_INFLAG_FORCE_VER` (0x00000001) - Forces verification even if it is necessary to override registry settings.</span></span>  
  
-   <span data-ttu-id="e9d5d-111">`SN_INFLAG_INSTALL` (0x00000002) - bu görüntüye gerçekleştirilen ilk doğrulama olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="e9d5d-111">`SN_INFLAG_INSTALL` (0x00000002) - Specifies that this is the first verification performed on this image.</span></span>  
  
-   <span data-ttu-id="e9d5d-112">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) - önbellek yönetici ayrıcalıklarına sahip kullanıcılara erişimi sağlayacak belirtir.</span><span class="sxs-lookup"><span data-stu-id="e9d5d-112">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) - Specifies that the cache will allow access only to users who have administrative privileges.</span></span>  
  
-   <span data-ttu-id="e9d5d-113">`SN_INFLAG_USER_ACCESS` (0x00000008) - derleme yalnızca geçerli kullanıcı için erişilebilir olacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e9d5d-113">`SN_INFLAG_USER_ACCESS` (0x00000008) - Specifies that the assembly will be accessible only to the current user.</span></span>  
  
-   <span data-ttu-id="e9d5d-114">`SN_INFLAG_ALL_ACCESS` (0x00000010) - önbellek garanti erişim kısıtlama sağlayacak belirtir.</span><span class="sxs-lookup"><span data-stu-id="e9d5d-114">`SN_INFLAG_ALL_ACCESS` (0x00000010) - Specifies that the cache will provide no guarantees of access restriction.</span></span>  
  
-   <span data-ttu-id="e9d5d-115">`SN_INFLAG_RUNTIME` (0x80000000) - iç hata ayıklama için ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="e9d5d-115">`SN_INFLAG_RUNTIME` (0x80000000) - Reserved for internal debugging.</span></span>  
  
 `pdwOutFlags`  
 <span data-ttu-id="e9d5d-116">[out] Çıktı ek bilgi için bir bayrak.</span><span class="sxs-lookup"><span data-stu-id="e9d5d-116">[out] A flag for additional output information.</span></span> <span data-ttu-id="e9d5d-117">Aşağıdaki değeri desteklenir:</span><span class="sxs-lookup"><span data-stu-id="e9d5d-117">The following value is supported:</span></span>  
  
-   <span data-ttu-id="e9d5d-118">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001) - bu değeri ayarı `false` doğrulama kayıt defteri ayarları nedeniyle başarılı olduğunu belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="e9d5d-118">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001) - This value is set to `false` to specify that the verification succeeded due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e9d5d-119">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e9d5d-119">Return Value</span></span>  
 <span data-ttu-id="e9d5d-120">`S_OK` yöntemi başarıyla tamamlandı Aksi takdirde hata olduğunu gösteren HRESULT değerini (bkz [ortak HRESULT değerlerini](https://go.microsoft.com/fwlink/?LinkId=213878) bir listesi için).</span><span class="sxs-lookup"><span data-stu-id="e9d5d-120">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9d5d-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e9d5d-121">Requirements</span></span>  
 <span data-ttu-id="e9d5d-122">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e9d5d-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9d5d-123">**Üst bilgi:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="e9d5d-123">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="e9d5d-124">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="e9d5d-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e9d5d-125">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9d5d-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9d5d-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e9d5d-126">See also</span></span>

- [<span data-ttu-id="e9d5d-127">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e9d5d-127">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
