---
title: ICLRStrongName::StrongNameFreeBuffer Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameFreeBuffer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameFreeBuffer
helpviewer_keywords:
- StrongNameFreeBuffer method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameFreeBuffer method [.NET Framework hosting]
ms.assetid: 6148c508-bd1d-4a37-85c3-06ecb09cc857
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6ec34bde2b94fc6e03cb01647be9e92daa8955a7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54743198"
---
# <a name="iclrstrongnamestrongnamefreebuffer-method"></a><span data-ttu-id="62696-102">ICLRStrongName::StrongNameFreeBuffer Yöntemi</span><span class="sxs-lookup"><span data-stu-id="62696-102">ICLRStrongName::StrongNameFreeBuffer Method</span></span>
<span data-ttu-id="62696-103">Önceki bir tanımlayıcı ad yöntemi çağrısı ile ayrıldı bellek serbest bırakma [Iclrstrongname::strongnamegetpublickey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md), [Iclrstrongname::strongnametokenfrompublickey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md), veya [ Iclrstrongname::strongnamesignaturegeneration](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md).</span><span class="sxs-lookup"><span data-stu-id="62696-103">Frees memory that was allocated with a previous call to a strong name method such as [ICLRStrongName::StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md), [ICLRStrongName::StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md), or [ICLRStrongName::StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62696-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="62696-104">Syntax</span></span>  
  
```  
HRESULT StrongNameFreeBuffer (   
   [in] BYTE   *pbMemory  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="62696-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="62696-105">Parameters</span></span>  
 `pbMemory`  
 <span data-ttu-id="62696-106">[in] Belleği boşaltmak için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="62696-106">[in] A pointer to the memory to free.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="62696-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="62696-107">Return Value</span></span>  
 <span data-ttu-id="62696-108">`S_OK` yöntemi başarıyla tamamlandı Aksi takdirde hata olduğunu gösteren HRESULT değerini (bkz [ortak HRESULT değerlerini](https://go.microsoft.com/fwlink/?LinkId=213878) bir listesi için).</span><span class="sxs-lookup"><span data-stu-id="62696-108">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62696-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="62696-109">Requirements</span></span>  
 <span data-ttu-id="62696-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="62696-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62696-111">**Üst bilgi:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="62696-111">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="62696-112">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="62696-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="62696-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62696-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62696-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="62696-114">See also</span></span>
- [<span data-ttu-id="62696-115">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="62696-115">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
