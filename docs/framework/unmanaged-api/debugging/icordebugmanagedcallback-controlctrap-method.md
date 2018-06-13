---
title: ICorDebugManagedCallback::ControlCTrap Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.ControlCTrap
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::ControlCTrap
helpviewer_keywords:
- ICorDebugManagedCallback::ControlCTrap method [.NET Framework debugging]
- ControlCTrap method [.NET Framework debugging]
ms.assetid: 0500854e-2121-43d9-a028-64312da35258
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a9758de5c2801f2c55b7eca149569016ec5b9243
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33412759"
---
# <a name="icordebugmanagedcallbackcontrolctrap-method"></a><span data-ttu-id="03f23-102">ICorDebugManagedCallback::ControlCTrap Yöntemi</span><span class="sxs-lookup"><span data-stu-id="03f23-102">ICorDebugManagedCallback::ControlCTrap Method</span></span>
<span data-ttu-id="03f23-103">Hata ayıklayıcı CTRL + C ayıklanacak işleminde yakalanır bildirir.</span><span class="sxs-lookup"><span data-stu-id="03f23-103">Notifies the debugger that a CTRL+C is trapped in the process that is being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03f23-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="03f23-104">Syntax</span></span>  
  
```  
HRESULT ControlCTrap (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="03f23-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="03f23-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="03f23-106">[in] Bir işaretçi Icordebugprocess nesneye CTRL + C yakalanan işlem temsil eder.</span><span class="sxs-lookup"><span data-stu-id="03f23-106">[in] A pointer to an ICorDebugProcess object that represents the process in which the CTRL+C is trapped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="03f23-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="03f23-107">Return Value</span></span>  
  
|<span data-ttu-id="03f23-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="03f23-108">HRESULT</span></span>|<span data-ttu-id="03f23-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="03f23-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="03f23-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="03f23-110">S_OK</span></span>|<span data-ttu-id="03f23-111">Hata ayıklayıcı CTRL + C tuzak işleyecek.</span><span class="sxs-lookup"><span data-stu-id="03f23-111">The debugger will handle the CTRL+C trap.</span></span>|  
|<span data-ttu-id="03f23-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="03f23-112">S_FALSE</span></span>|<span data-ttu-id="03f23-113">Hata ayıklayıcı CTRL + C tuzak işler değil.</span><span class="sxs-lookup"><span data-stu-id="03f23-113">The debugger will not handle the CTRL+C trap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="03f23-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="03f23-114">Remarks</span></span>  
 <span data-ttu-id="03f23-115">İşlemdeki tüm uygulama etki alanları için bu geri çağırma durdurulur.</span><span class="sxs-lookup"><span data-stu-id="03f23-115">All application domains within the process are stopped for this callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03f23-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="03f23-116">Requirements</span></span>  
 <span data-ttu-id="03f23-117">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="03f23-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03f23-118">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="03f23-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="03f23-119">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="03f23-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="03f23-120">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03f23-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03f23-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="03f23-121">See Also</span></span>  
 [<span data-ttu-id="03f23-122">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="03f23-122">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
