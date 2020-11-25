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
ms.openlocfilehash: 718e6f3f19a5c368091c8a8aad3bd1f6598228df
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727287"
---
# <a name="ihosttaskmanagergetstackguarantee-method"></a><span data-ttu-id="0d2f5-102">IHostTaskManager::GetStackGuarantee Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0d2f5-102">IHostTaskManager::GetStackGuarantee Method</span></span>

<span data-ttu-id="0d2f5-103">Bir yığın işlemi tamamlandıktan sonra, ancak bir işlemin kapatılmadan önce kullanılabilir olması garanti edilen yığın alanı miktarını alır.</span><span class="sxs-lookup"><span data-stu-id="0d2f5-103">Gets the amount of stack space that is guaranteed to be available after a stack operation completes, but before the closing of a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d2f5-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="0d2f5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStackGuarantee(  
    [out] ULONG *pGuarantee  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0d2f5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0d2f5-105">Parameters</span></span>  

 `pGuarantee`  
 <span data-ttu-id="0d2f5-106">dışı Kullanılabilir bayt sayısı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0d2f5-106">[out] A pointer to the number of bytes that are available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d2f5-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0d2f5-107">Requirements</span></span>  

 <span data-ttu-id="0d2f5-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0d2f5-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d2f5-109">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0d2f5-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0d2f5-110">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="0d2f5-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0d2f5-111">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d2f5-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d2f5-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0d2f5-112">See also</span></span>

- [<span data-ttu-id="0d2f5-113">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0d2f5-113">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
