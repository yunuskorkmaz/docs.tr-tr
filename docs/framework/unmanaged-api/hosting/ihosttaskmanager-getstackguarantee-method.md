---
title: IHostTaskManager::GetStackGuarantee Metodu
ms.date: 03/30/2017
api_name:
- IHostTaskManager.GetStackGuarantee
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::GetStackGuarantee
helpviewer_keywords:
- GetStackGuarantee method [.NET Framework hosting]
- IHostTaskManager::GetStackGuarantee method [.NET Framework hosting]
ms.assetid: 8176d732-c25c-4520-811d-e3310f339947
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ad95f8ee5188c38bb19882d3c7fa6bf98fcc9d2a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54625256"
---
# <a name="ihosttaskmanagergetstackguarantee-method"></a><span data-ttu-id="bd85a-102">IHostTaskManager::GetStackGuarantee Metodu</span><span class="sxs-lookup"><span data-stu-id="bd85a-102">IHostTaskManager::GetStackGuarantee Method</span></span>
<span data-ttu-id="bd85a-103">Yığın işlemi tamamlandıktan sonra kullanılabilir olmasını garanti yığın alanı, ancak bir işlemin kapatmadan önce miktarı alır.</span><span class="sxs-lookup"><span data-stu-id="bd85a-103">Gets the amount of stack space that is guaranteed to be available after a stack operation completes, but before the closing of a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd85a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bd85a-104">Syntax</span></span>  
  
```  
HRESULT GetStackGuarantee(  
    [out] ULONG *pGuarantee  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bd85a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bd85a-105">Parameters</span></span>  
 `pGuarantee`  
 <span data-ttu-id="bd85a-106">[out] Kullanılabilir bayt sayısı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="bd85a-106">[out] A pointer to the number of bytes that are available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd85a-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bd85a-107">Requirements</span></span>  
 <span data-ttu-id="bd85a-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bd85a-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd85a-109">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="bd85a-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bd85a-110">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="bd85a-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bd85a-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd85a-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd85a-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bd85a-112">See also</span></span>
- [<span data-ttu-id="bd85a-113">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bd85a-113">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
