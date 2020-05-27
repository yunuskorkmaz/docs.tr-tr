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
ms.openlocfilehash: d76242eb8539f2e8dffbf39b7eaf595664bdce8e
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842029"
---
# <a name="ihosttaskmanagergetstackguarantee-method"></a><span data-ttu-id="e41d9-102">IHostTaskManager::GetStackGuarantee Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e41d9-102">IHostTaskManager::GetStackGuarantee Method</span></span>
<span data-ttu-id="e41d9-103">Bir yığın işlemi tamamlandıktan sonra, ancak bir işlemin kapatılmadan önce kullanılabilir olması garanti edilen yığın alanı miktarını alır.</span><span class="sxs-lookup"><span data-stu-id="e41d9-103">Gets the amount of stack space that is guaranteed to be available after a stack operation completes, but before the closing of a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e41d9-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="e41d9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStackGuarantee(  
    [out] ULONG *pGuarantee  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e41d9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e41d9-105">Parameters</span></span>  
 `pGuarantee`  
 <span data-ttu-id="e41d9-106">dışı Kullanılabilir bayt sayısı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e41d9-106">[out] A pointer to the number of bytes that are available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e41d9-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e41d9-107">Requirements</span></span>  
 <span data-ttu-id="e41d9-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e41d9-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e41d9-109">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e41d9-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e41d9-110">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="e41d9-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e41d9-111">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e41d9-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e41d9-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e41d9-112">See also</span></span>

- [<span data-ttu-id="e41d9-113">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e41d9-113">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
