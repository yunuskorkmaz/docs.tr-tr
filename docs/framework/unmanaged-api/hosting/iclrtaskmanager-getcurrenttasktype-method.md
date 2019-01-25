---
title: ICLRTaskManager::GetCurrentTaskType Metodu
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7d2a8818ef180b3522a53e29fa84453ea9033a2a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54522407"
---
# <a name="iclrtaskmanagergetcurrenttasktype-method"></a><span data-ttu-id="8c1c0-102">ICLRTaskManager::GetCurrentTaskType Metodu</span><span class="sxs-lookup"><span data-stu-id="8c1c0-102">ICLRTaskManager::GetCurrentTaskType Method</span></span>
<span data-ttu-id="8c1c0-103">Şu anda yürütülmekte olan görevi türünü alır.</span><span class="sxs-lookup"><span data-stu-id="8c1c0-103">Gets the type of the task that is currently executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c1c0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8c1c0-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentTaskType(  
    [out] ETaskType *pTaskType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8c1c0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8c1c0-105">Parameters</span></span>  
 `pTaskType`  
 <span data-ttu-id="8c1c0-106">[out] Bir işaretçi değerini [ETaskType](../../../../docs/framework/unmanaged-api/hosting/etasktype-enumeration.md) şu anda yürütülmekte olan görevi türünü belirten sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="8c1c0-106">[out] A pointer to a value of the [ETaskType](../../../../docs/framework/unmanaged-api/hosting/etasktype-enumeration.md) enumeration that indicates the type of task that is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c1c0-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8c1c0-107">Requirements</span></span>  
 <span data-ttu-id="8c1c0-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8c1c0-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c1c0-109">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8c1c0-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8c1c0-110">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="8c1c0-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8c1c0-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c1c0-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c1c0-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8c1c0-112">See also</span></span>
- [<span data-ttu-id="8c1c0-113">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8c1c0-113">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
