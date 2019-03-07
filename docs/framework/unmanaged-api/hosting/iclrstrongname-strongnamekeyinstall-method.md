---
title: ICLRStrongName::StrongNameKeyInstall Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameKeyInstall
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameKeyInstall
helpviewer_keywords:
- ICLRStrongName::StrongNameKeyInstall method [.NET Framework hosting]
- StrongNameKeyInstall method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 5c15cf3b-164c-49d1-8e57-e42949d55acf
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9803ca3b5047b6819ef76958a169b62dfe9d675d
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57499517"
---
# <a name="iclrstrongnamestrongnamekeyinstall-method"></a><span data-ttu-id="7d17a-102">ICLRStrongName::StrongNameKeyInstall Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7d17a-102">ICLRStrongName::StrongNameKeyInstall Method</span></span>
<span data-ttu-id="7d17a-103">Bir ortak/özel anahtar çifti bir kapsayıcının içine aktarır.</span><span class="sxs-lookup"><span data-stu-id="7d17a-103">Imports a public/private key pair into a container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d17a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7d17a-104">Syntax</span></span>  
  
```  
HRESULT StrongNameKeyInstall (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7d17a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7d17a-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="7d17a-106">[in] Anahtar kapsayıcısının adı.</span><span class="sxs-lookup"><span data-stu-id="7d17a-106">[in] The name of the key container.</span></span> <span data-ttu-id="7d17a-107">`wszKeyContainer` boş olmayan bir dize olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7d17a-107">`wszKeyContainer` must be a non-empty string.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="7d17a-108">[in] İkili bir anahtar çifti.</span><span class="sxs-lookup"><span data-stu-id="7d17a-108">[in] The binary key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="7d17a-109">[in] Bayt cinsinden boyutu, `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="7d17a-109">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7d17a-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="7d17a-110">Return Value</span></span>  
 <span data-ttu-id="7d17a-111">`S_OK` yöntemi başarıyla tamamlandı Aksi takdirde hata olduğunu gösteren HRESULT değerini (bkz [ortak HRESULT değerlerini](https://go.microsoft.com/fwlink/?LinkId=213878) bir listesi için).</span><span class="sxs-lookup"><span data-stu-id="7d17a-111">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7d17a-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7d17a-112">Remarks</span></span>  
 <span data-ttu-id="7d17a-113">Kullanım [Iclrstrongname::strongnamekeydelete](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md) anahtar kapsayıcısını silme için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="7d17a-113">Use the [ICLRStrongName::StrongNameKeyDelete](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md) method to delete the key container.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d17a-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7d17a-114">Requirements</span></span>  
 <span data-ttu-id="7d17a-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7d17a-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d17a-116">**Üst bilgi:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="7d17a-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="7d17a-117">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="7d17a-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7d17a-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d17a-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d17a-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7d17a-119">See also</span></span>
- [<span data-ttu-id="7d17a-120">StrongNameKeyDelete Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7d17a-120">StrongNameKeyDelete Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md)
- [<span data-ttu-id="7d17a-121">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7d17a-121">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
