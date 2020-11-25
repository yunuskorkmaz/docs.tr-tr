---
title: ICorConfiguration::SetGCThreadControl Yöntemi
ms.date: 03/30/2017
api_name:
- ICorConfiguration.SetGCThreadControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SetGCThreadControl
helpviewer_keywords:
- ICorConfiguration::SetGCThreadControl method [.NET Framework hosting]
- SetGCThreadControl method [.NET Framework hosting]
ms.assetid: 72e38e61-3d56-4ae3-b8f6-0ab7922aaf11
topic_type:
- apiref
ms.openlocfilehash: 28b012bbe3f8c11ecd0afb8b5905336bd99c349c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724032"
---
# <a name="icorconfigurationsetgcthreadcontrol-method"></a><span data-ttu-id="dedea-102">ICorConfiguration::SetGCThreadControl Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dedea-102">ICorConfiguration::SetGCThreadControl Method</span></span>

<span data-ttu-id="dedea-103">Bir çöp toplama işlemi için engellenmeyen çalışma zamanı olmayan görevler için iş parçacıkları zamanlama için geri çağırma arabirimini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="dedea-103">Sets the callback interface for scheduling threads for non-runtime tasks that would otherwise be blocked for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dedea-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="dedea-104">Syntax</span></span>  
  
```cpp  
HRESULT SetGCThreadControl (  
    [in] IGCThreadControl* pGCThreadControl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dedea-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="dedea-105">Parameters</span></span>  

 `pGCThreadControl`  
 <span data-ttu-id="dedea-106">'ndaki Çalışma zamanı olmayan görevler için iş parçacıklarının askıya alınma hakkında bilgi veren bir [IGCThreadControl](igcthreadcontrol-interface.md) nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="dedea-106">[in] A pointer to an [IGCThreadControl](igcthreadcontrol-interface.md) object that notifies the host about the suspension of threads for non-runtime tasks.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dedea-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dedea-107">Remarks</span></span>  

 <span data-ttu-id="dedea-108">Konak, bir iş parçacığını yeniden zamanlamalı [IGCThreadControl:: Threadıblockingforaskıya](igcthreadcontrol-threadisblockingforsuspension-method.md) alma geri araması içinde seçim gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="dedea-108">The host may choose within the [IGCThreadControl::ThreadIsBlockingForSuspension](igcthreadcontrol-threadisblockingforsuspension-method.md) callback whether to reschedule a thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dedea-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dedea-109">Requirements</span></span>  

 <span data-ttu-id="dedea-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dedea-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dedea-111">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="dedea-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dedea-112">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="dedea-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dedea-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dedea-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dedea-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dedea-114">See also</span></span>

- [<span data-ttu-id="dedea-115">ICorConfiguration Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dedea-115">ICorConfiguration Interface</span></span>](icorconfiguration-interface.md)
