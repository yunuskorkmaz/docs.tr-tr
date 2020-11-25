---
title: ICLRTaskManager::GetCurrentTaskType Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRTaskManager.GetCurrentTaskType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager::GetCurrentTaskType
helpviewer_keywords:
- GetCurrentTaskType method [.NET Framework hosting]
- ICLRTaskManager::GetCurrentTaskType method [.NET Framework hosting]
ms.assetid: 6b0d9259-dbe2-45bb-b34d-990f60c73424
topic_type:
- apiref
ms.openlocfilehash: 684b94471c53701c5ebe1dc7e7593eae16ad50fd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728790"
---
# <a name="iclrtaskmanagergetcurrenttasktype-method"></a><span data-ttu-id="f0072-102">ICLRTaskManager::GetCurrentTaskType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f0072-102">ICLRTaskManager::GetCurrentTaskType Method</span></span>

<span data-ttu-id="f0072-103">Şu anda yürütülmekte olan görevin türünü alır.</span><span class="sxs-lookup"><span data-stu-id="f0072-103">Gets the type of the task that is currently executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0072-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="f0072-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentTaskType(  
    [out] ETaskType *pTaskType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f0072-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f0072-105">Parameters</span></span>  

 `pTaskType`  
 <span data-ttu-id="f0072-106">dışı Şu anda yürütülmekte olan görevin türünü gösteren [ETaskType](etasktype-enumeration.md) numaralandırması değerine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f0072-106">[out] A pointer to a value of the [ETaskType](etasktype-enumeration.md) enumeration that indicates the type of task that is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0072-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f0072-107">Requirements</span></span>  

 <span data-ttu-id="f0072-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f0072-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0072-109">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f0072-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f0072-110">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="f0072-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f0072-111">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0072-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0072-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f0072-112">See also</span></span>

- [<span data-ttu-id="f0072-113">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f0072-113">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
