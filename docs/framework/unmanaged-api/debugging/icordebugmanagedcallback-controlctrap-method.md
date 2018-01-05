---
title: "ICorDebugManagedCallback::ControlCTrap Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback.ControlCTrap
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback::ControlCTrap
helpviewer_keywords:
- ICorDebugManagedCallback::ControlCTrap method [.NET Framework debugging]
- ControlCTrap method [.NET Framework debugging]
ms.assetid: 0500854e-2121-43d9-a028-64312da35258
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6c5de52b810efeaf7b5c103dcd39a37a37ab3272
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallbackcontrolctrap-method"></a><span data-ttu-id="7f4f9-102">ICorDebugManagedCallback::ControlCTrap Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7f4f9-102">ICorDebugManagedCallback::ControlCTrap Method</span></span>
<span data-ttu-id="7f4f9-103">Hata ayıklayıcı CTRL + C ayıklanacak işleminde yakalanır bildirir.</span><span class="sxs-lookup"><span data-stu-id="7f4f9-103">Notifies the debugger that a CTRL+C is trapped in the process that is being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f4f9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7f4f9-104">Syntax</span></span>  
  
```  
HRESULT ControlCTrap (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7f4f9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7f4f9-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="7f4f9-106">[in] Bir işaretçi Icordebugprocess nesneye CTRL + C yakalanan işlem temsil eder.</span><span class="sxs-lookup"><span data-stu-id="7f4f9-106">[in] A pointer to an ICorDebugProcess object that represents the process in which the CTRL+C is trapped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7f4f9-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="7f4f9-107">Return Value</span></span>  
  
|<span data-ttu-id="7f4f9-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7f4f9-108">HRESULT</span></span>|<span data-ttu-id="7f4f9-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7f4f9-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7f4f9-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="7f4f9-110">S_OK</span></span>|<span data-ttu-id="7f4f9-111">Hata ayıklayıcı CTRL + C tuzak işleyecek.</span><span class="sxs-lookup"><span data-stu-id="7f4f9-111">The debugger will handle the CTRL+C trap.</span></span>|  
|<span data-ttu-id="7f4f9-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="7f4f9-112">S_FALSE</span></span>|<span data-ttu-id="7f4f9-113">Hata ayıklayıcı CTRL + C tuzak işler değil.</span><span class="sxs-lookup"><span data-stu-id="7f4f9-113">The debugger will not handle the CTRL+C trap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7f4f9-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7f4f9-114">Remarks</span></span>  
 <span data-ttu-id="7f4f9-115">İşlemdeki tüm uygulama etki alanları için bu geri çağırma durdurulur.</span><span class="sxs-lookup"><span data-stu-id="7f4f9-115">All application domains within the process are stopped for this callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f4f9-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7f4f9-116">Requirements</span></span>  
 <span data-ttu-id="7f4f9-117">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7f4f9-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f4f9-118">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7f4f9-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7f4f9-119">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7f4f9-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7f4f9-120">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f4f9-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f4f9-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7f4f9-121">See Also</span></span>  
 [<span data-ttu-id="7f4f9-122">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7f4f9-122">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
