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
ms.openlocfilehash: 3a2badf8f164abd1bbb8892ec5db28f7cf39f5c5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67775658"
---
# <a name="iclrstrongnamestrongnamekeyinstall-method"></a><span data-ttu-id="69897-102">ICLRStrongName::StrongNameKeyInstall Yöntemi</span><span class="sxs-lookup"><span data-stu-id="69897-102">ICLRStrongName::StrongNameKeyInstall Method</span></span>
<span data-ttu-id="69897-103">Bir ortak/özel anahtar çifti bir kapsayıcının içine aktarır.</span><span class="sxs-lookup"><span data-stu-id="69897-103">Imports a public/private key pair into a container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69897-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="69897-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameKeyInstall (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="69897-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="69897-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="69897-106">[in] Anahtar kapsayıcısının adı.</span><span class="sxs-lookup"><span data-stu-id="69897-106">[in] The name of the key container.</span></span> <span data-ttu-id="69897-107">`wszKeyContainer` boş olmayan bir dize olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="69897-107">`wszKeyContainer` must be a non-empty string.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="69897-108">[in] İkili bir anahtar çifti.</span><span class="sxs-lookup"><span data-stu-id="69897-108">[in] The binary key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="69897-109">[in] Bayt cinsinden boyutu, `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="69897-109">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="69897-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="69897-110">Return Value</span></span>  
 <span data-ttu-id="69897-111">`S_OK` yöntemi başarıyla tamamlandı Aksi takdirde hata olduğunu gösteren HRESULT değerini (bkz [ortak HRESULT değerlerini](https://go.microsoft.com/fwlink/?LinkId=213878) bir listesi için).</span><span class="sxs-lookup"><span data-stu-id="69897-111">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="69897-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="69897-112">Remarks</span></span>  
 <span data-ttu-id="69897-113">Kullanım [Iclrstrongname::strongnamekeydelete](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md) anahtar kapsayıcısını silme için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="69897-113">Use the [ICLRStrongName::StrongNameKeyDelete](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md) method to delete the key container.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69897-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="69897-114">Requirements</span></span>  
 <span data-ttu-id="69897-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="69897-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="69897-116">**Üst bilgi:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="69897-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="69897-117">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="69897-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="69897-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="69897-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69897-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="69897-119">See also</span></span>

- [<span data-ttu-id="69897-120">StrongNameKeyDelete Yöntemi</span><span class="sxs-lookup"><span data-stu-id="69897-120">StrongNameKeyDelete Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md)
- [<span data-ttu-id="69897-121">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="69897-121">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
