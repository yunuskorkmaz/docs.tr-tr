---
description: ': ICLRTaskManager:: GetCurrentTaskType yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 984cc490123d6146737d3f018fdf712c7c528635
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799492"
---
# <a name="iclrtaskmanagergetcurrenttasktype-method"></a><span data-ttu-id="81fff-103">ICLRTaskManager::GetCurrentTaskType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="81fff-103">ICLRTaskManager::GetCurrentTaskType Method</span></span>

<span data-ttu-id="81fff-104">Şu anda yürütülmekte olan görevin türünü alır.</span><span class="sxs-lookup"><span data-stu-id="81fff-104">Gets the type of the task that is currently executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81fff-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="81fff-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentTaskType(  
    [out] ETaskType *pTaskType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="81fff-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="81fff-106">Parameters</span></span>  

 `pTaskType`  
 <span data-ttu-id="81fff-107">dışı Şu anda yürütülmekte olan görevin türünü gösteren [ETaskType](etasktype-enumeration.md) numaralandırması değerine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="81fff-107">[out] A pointer to a value of the [ETaskType](etasktype-enumeration.md) enumeration that indicates the type of task that is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81fff-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="81fff-108">Requirements</span></span>  

 <span data-ttu-id="81fff-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="81fff-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81fff-110">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="81fff-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="81fff-111">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="81fff-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="81fff-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81fff-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81fff-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="81fff-113">See also</span></span>

- [<span data-ttu-id="81fff-114">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="81fff-114">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
