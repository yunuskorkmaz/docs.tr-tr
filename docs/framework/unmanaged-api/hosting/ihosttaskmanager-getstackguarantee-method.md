---
description: ': IHostTaskManager:: Getstackgarantisi yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 6c8bd9839ea0c1fdb72fbbd296061d1a2b6edfe1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753802"
---
# <a name="ihosttaskmanagergetstackguarantee-method"></a><span data-ttu-id="0cb5f-103">IHostTaskManager::GetStackGuarantee Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0cb5f-103">IHostTaskManager::GetStackGuarantee Method</span></span>

<span data-ttu-id="0cb5f-104">Bir yığın işlemi tamamlandıktan sonra, ancak bir işlemin kapatılmadan önce kullanılabilir olması garanti edilen yığın alanı miktarını alır.</span><span class="sxs-lookup"><span data-stu-id="0cb5f-104">Gets the amount of stack space that is guaranteed to be available after a stack operation completes, but before the closing of a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0cb5f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0cb5f-105">Syntax</span></span>  
  
```cpp  
HRESULT GetStackGuarantee(  
    [out] ULONG *pGuarantee  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0cb5f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0cb5f-106">Parameters</span></span>  

 `pGuarantee`  
 <span data-ttu-id="0cb5f-107">dışı Kullanılabilir bayt sayısı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0cb5f-107">[out] A pointer to the number of bytes that are available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0cb5f-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0cb5f-108">Requirements</span></span>  

 <span data-ttu-id="0cb5f-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0cb5f-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0cb5f-110">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0cb5f-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0cb5f-111">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="0cb5f-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0cb5f-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0cb5f-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cb5f-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0cb5f-113">See also</span></span>

- [<span data-ttu-id="0cb5f-114">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0cb5f-114">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
