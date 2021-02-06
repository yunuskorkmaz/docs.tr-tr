---
description: ': ICorConfiguration:: SetGCThreadControl Yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 8b9388bdefb9da2ce51b62ab68eeee54645e43ad
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99636650"
---
# <a name="icorconfigurationsetgcthreadcontrol-method"></a><span data-ttu-id="a0ab7-103">ICorConfiguration::SetGCThreadControl Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a0ab7-103">ICorConfiguration::SetGCThreadControl Method</span></span>

<span data-ttu-id="a0ab7-104">Bir çöp toplama işlemi için engellenmeyen çalışma zamanı olmayan görevler için iş parçacıkları zamanlama için geri çağırma arabirimini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="a0ab7-104">Sets the callback interface for scheduling threads for non-runtime tasks that would otherwise be blocked for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0ab7-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a0ab7-105">Syntax</span></span>  
  
```cpp  
HRESULT SetGCThreadControl (  
    [in] IGCThreadControl* pGCThreadControl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a0ab7-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a0ab7-106">Parameters</span></span>  

 `pGCThreadControl`  
 <span data-ttu-id="a0ab7-107">'ndaki Çalışma zamanı olmayan görevler için iş parçacıklarının askıya alınma hakkında bilgi veren bir [IGCThreadControl](igcthreadcontrol-interface.md) nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a0ab7-107">[in] A pointer to an [IGCThreadControl](igcthreadcontrol-interface.md) object that notifies the host about the suspension of threads for non-runtime tasks.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a0ab7-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a0ab7-108">Remarks</span></span>  

 <span data-ttu-id="a0ab7-109">Konak, bir iş parçacığını yeniden zamanlamalı [IGCThreadControl:: Threadıblockingforaskıya](igcthreadcontrol-threadisblockingforsuspension-method.md) alma geri araması içinde seçim gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="a0ab7-109">The host may choose within the [IGCThreadControl::ThreadIsBlockingForSuspension](igcthreadcontrol-threadisblockingforsuspension-method.md) callback whether to reschedule a thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a0ab7-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a0ab7-110">Requirements</span></span>  

 <span data-ttu-id="a0ab7-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a0ab7-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0ab7-112">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a0ab7-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a0ab7-113">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="a0ab7-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a0ab7-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a0ab7-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0ab7-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a0ab7-115">See also</span></span>

- [<span data-ttu-id="a0ab7-116">ICorConfiguration Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a0ab7-116">ICorConfiguration Interface</span></span>](icorconfiguration-interface.md)
