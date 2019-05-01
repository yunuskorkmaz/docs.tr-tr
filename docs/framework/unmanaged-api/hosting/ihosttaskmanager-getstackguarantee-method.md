---
title: IHostTaskManager::GetStackGuarantee Yöntemi
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
ms.openlocfilehash: ea1c1f998febccbc80fb10cef5a8dfd229e1987e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61789408"
---
# <a name="ihosttaskmanagergetstackguarantee-method"></a><span data-ttu-id="83312-102">IHostTaskManager::GetStackGuarantee Yöntemi</span><span class="sxs-lookup"><span data-stu-id="83312-102">IHostTaskManager::GetStackGuarantee Method</span></span>
<span data-ttu-id="83312-103">Yığın işlemi tamamlandıktan sonra kullanılabilir olmasını garanti yığın alanı, ancak bir işlemin kapatmadan önce miktarı alır.</span><span class="sxs-lookup"><span data-stu-id="83312-103">Gets the amount of stack space that is guaranteed to be available after a stack operation completes, but before the closing of a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83312-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="83312-104">Syntax</span></span>  
  
```  
HRESULT GetStackGuarantee(  
    [out] ULONG *pGuarantee  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="83312-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="83312-105">Parameters</span></span>  
 `pGuarantee`  
 <span data-ttu-id="83312-106">[out] Kullanılabilir bayt sayısı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="83312-106">[out] A pointer to the number of bytes that are available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83312-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="83312-107">Requirements</span></span>  
 <span data-ttu-id="83312-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83312-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83312-109">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="83312-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="83312-110">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="83312-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="83312-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83312-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83312-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="83312-112">See also</span></span>

- [<span data-ttu-id="83312-113">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="83312-113">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
