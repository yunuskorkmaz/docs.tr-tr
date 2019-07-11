---
title: ICLRStrongName::StrongNameKeyDelete Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameKeyDelete
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameKeyDelete
helpviewer_keywords:
- StrongNameKeyDelete method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameKeyDelete method [.NET Framework hosting]
ms.assetid: 0163412f-f617-4428-89e0-03992fec31e8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 540fda24a8085a3066dc0485228d3ea3bc56fb98
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67747782"
---
# <a name="iclrstrongnamestrongnamekeydelete-method"></a><span data-ttu-id="54196-102">ICLRStrongName::StrongNameKeyDelete Yöntemi</span><span class="sxs-lookup"><span data-stu-id="54196-102">ICLRStrongName::StrongNameKeyDelete Method</span></span>
<span data-ttu-id="54196-103">Belirtilen anahtar kapsayıcısında siler.</span><span class="sxs-lookup"><span data-stu-id="54196-103">Deletes the specified key container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54196-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="54196-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameKeyDelete (  
    [in]  LPCWSTR   wszKeyContainer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="54196-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="54196-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="54196-106">[in] Silinecek anahtar kapsayıcısının adı.</span><span class="sxs-lookup"><span data-stu-id="54196-106">[in] The name of the key container to delete.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="54196-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="54196-107">Return Value</span></span>  
 <span data-ttu-id="54196-108">`S_OK` yöntemi başarıyla tamamlandı Aksi takdirde hata olduğunu gösteren HRESULT değerini (bkz [ortak HRESULT değerlerini](https://go.microsoft.com/fwlink/?LinkId=213878) bir listesi için).</span><span class="sxs-lookup"><span data-stu-id="54196-108">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="54196-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="54196-109">Remarks</span></span>  
 <span data-ttu-id="54196-110">Kullanım [Iclrstrongname::strongnamekeyınstall](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md) bir kapsayıcıya bir ortak/özel anahtar çifti almak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="54196-110">Use the [ICLRStrongName::StrongNameKeyInstall](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md) method to import a public/private key pair into a container.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="54196-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="54196-111">Requirements</span></span>  
 <span data-ttu-id="54196-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="54196-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="54196-113">**Üst bilgi:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="54196-113">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="54196-114">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="54196-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="54196-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="54196-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54196-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="54196-116">See also</span></span>

- [<span data-ttu-id="54196-117">StrongNameKeyInstall Yöntemi</span><span class="sxs-lookup"><span data-stu-id="54196-117">StrongNameKeyInstall Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md)
- [<span data-ttu-id="54196-118">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="54196-118">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
