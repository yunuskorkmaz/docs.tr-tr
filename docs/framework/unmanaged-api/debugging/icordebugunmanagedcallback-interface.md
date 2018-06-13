---
title: ICorDebugUnmanagedCallback Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugUnmanagedCallback
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugUnmanagedCallback
helpviewer_keywords:
- ICorDebugUnmanagedCallback interface [.NET Framework debugging]
ms.assetid: bc71cbca-7d73-40e5-84dd-2109fade3c2a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5b55b27d45ef3efea10215c8a4163b5981f9d145
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422871"
---
# <a name="icordebugunmanagedcallback-interface"></a><span data-ttu-id="6bc27-102">ICorDebugUnmanagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6bc27-102">ICorDebugUnmanagedCallback Interface</span></span>
<span data-ttu-id="6bc27-103">Ortak dil çalışma zamanı (CLR) doğrudan ilgili olmayan yerel olay bildirim sağlar.</span><span class="sxs-lookup"><span data-stu-id="6bc27-103">Provides notification of native events that are not directly related to the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6bc27-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="6bc27-104">Methods</span></span>  
  
|<span data-ttu-id="6bc27-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="6bc27-105">Method</span></span>|<span data-ttu-id="6bc27-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6bc27-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6bc27-107">DebugEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6bc27-107">DebugEvent Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-debugevent-method.md)|<span data-ttu-id="6bc27-108">Hata ayıklayıcı yerel olay harekete olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="6bc27-108">Notifies the debugger that a native event has been fired.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6bc27-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6bc27-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6bc27-110">Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="6bc27-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6bc27-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6bc27-111">Requirements</span></span>  
 <span data-ttu-id="6bc27-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6bc27-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6bc27-113">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6bc27-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6bc27-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6bc27-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6bc27-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6bc27-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bc27-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6bc27-116">See Also</span></span>  
 [<span data-ttu-id="6bc27-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="6bc27-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
