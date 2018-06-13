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
ms.openlocfilehash: 60dbb8d8461015c791a70d6c2617b1c81e5ba17f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33434274"
---
# <a name="iclrstrongnamestrongnamesignatureverificationfromimage-method"></a><span data-ttu-id="d80b5-102">ICLRStrongName::StrongNameSignatureVerificationFromImage Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d80b5-102">ICLRStrongName::StrongNameSignatureVerificationFromImage Method</span></span>
<span data-ttu-id="d80b5-103">Bellek zaten eşlendi bütünleştirilmiş ilişkili ortak anahtarı için geçerli olduğunu doğrular.</span><span class="sxs-lookup"><span data-stu-id="d80b5-103">Verifies that an assembly that has already been mapped to memory is valid for the associated public key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d80b5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d80b5-104">Syntax</span></span>  
  
```  
HRESULT StrongNameSignatureVerificationFromImage (  
    [in]  BYTE    *pbBase,  
    [in]  DWORD   dwLength,  
    [in]  DWORD   dwInFlags,  
    [out] DWORD   *pdwOutFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d80b5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d80b5-105">Parameters</span></span>  
 `pbBase`  
 <span data-ttu-id="d80b5-106">[in] Eşlenen derleme bildirimi göreli sanal adresi.</span><span class="sxs-lookup"><span data-stu-id="d80b5-106">[in] The relative virtual address of the mapped assembly manifest.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="d80b5-107">[in] Eşlenen görüntünün bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="d80b5-107">[in] The size, in bytes, of the mapped image.</span></span>  
  
 `dwInFlags`  
 <span data-ttu-id="d80b5-108">[in] Doğrulama davranışını etkilemek bayraklar.</span><span class="sxs-lookup"><span data-stu-id="d80b5-108">[in] Flags that influence verification behavior.</span></span> <span data-ttu-id="d80b5-109">Aşağıdaki değerleri desteklenir:</span><span class="sxs-lookup"><span data-stu-id="d80b5-109">The following values are supported:</span></span>  
  
-   <span data-ttu-id="d80b5-110">`SN_INFLAG_FORCE_VER` (0x00000001) - kayıt defteri ayarlarını geçersiz kılmak gerekli olduğu halde doğrulama zorlar.</span><span class="sxs-lookup"><span data-stu-id="d80b5-110">`SN_INFLAG_FORCE_VER` (0x00000001) - Forces verification even if it is necessary to override registry settings.</span></span>  
  
-   <span data-ttu-id="d80b5-111">`SN_INFLAG_INSTALL` (0x00000002) - bu görüntü üzerinde gerçekleştirilen ilk doğrulama olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="d80b5-111">`SN_INFLAG_INSTALL` (0x00000002) - Specifies that this is the first verification performed on this image.</span></span>  
  
-   <span data-ttu-id="d80b5-112">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) - önbelleğe erişimi yalnızca yönetici ayrıcalıklarına sahip olan kullanıcılara izin verip belirtir.</span><span class="sxs-lookup"><span data-stu-id="d80b5-112">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) - Specifies that the cache will allow access only to users who have administrative privileges.</span></span>  
  
-   <span data-ttu-id="d80b5-113">`SN_INFLAG_USER_ACCESS` (0x00000008) - derleme yalnızca geçerli kullanıcıya erişilebilir olacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d80b5-113">`SN_INFLAG_USER_ACCESS` (0x00000008) - Specifies that the assembly will be accessible only to the current user.</span></span>  
  
-   <span data-ttu-id="d80b5-114">`SN_INFLAG_ALL_ACCESS` (0x00000010) - önbellek garanti erişim kısıtlama sağlayacak belirtir.</span><span class="sxs-lookup"><span data-stu-id="d80b5-114">`SN_INFLAG_ALL_ACCESS` (0x00000010) - Specifies that the cache will provide no guarantees of access restriction.</span></span>  
  
-   <span data-ttu-id="d80b5-115">`SN_INFLAG_RUNTIME` (0x80000000) - iç hata ayıklama için ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="d80b5-115">`SN_INFLAG_RUNTIME` (0x80000000) - Reserved for internal debugging.</span></span>  
  
 `pdwOutFlags`  
 <span data-ttu-id="d80b5-116">[out] Ek çıkış bilgileri için bir bayrak.</span><span class="sxs-lookup"><span data-stu-id="d80b5-116">[out] A flag for additional output information.</span></span> <span data-ttu-id="d80b5-117">Aşağıdaki değeri desteklenir:</span><span class="sxs-lookup"><span data-stu-id="d80b5-117">The following value is supported:</span></span>  
  
-   <span data-ttu-id="d80b5-118">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001) - bu değeri ayarı `false` doğrulama kayıt defteri ayarları nedeniyle başarılı olduğunu belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="d80b5-118">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001) - This value is set to `false` to specify that the verification succeeded due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d80b5-119">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d80b5-119">Return Value</span></span>  
 <span data-ttu-id="d80b5-120">`S_OK` Yöntem başarıyla tamamlandı Aksi takdirde hata belirten bir HRESULT değeri (bkz [ortak HRESULT değerleri](http://go.microsoft.com/fwlink/?LinkId=213878) bir listesi için).</span><span class="sxs-lookup"><span data-stu-id="d80b5-120">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d80b5-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d80b5-121">Requirements</span></span>  
 <span data-ttu-id="d80b5-122">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d80b5-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d80b5-123">**Başlık:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="d80b5-123">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="d80b5-124">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="d80b5-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d80b5-125">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d80b5-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d80b5-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d80b5-126">See Also</span></span>  
 [<span data-ttu-id="d80b5-127">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d80b5-127">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
