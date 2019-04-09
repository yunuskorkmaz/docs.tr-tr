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
ms.openlocfilehash: 60a1546068ae6a8c8be1c0af1ef3c7d770c23d70
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59128686"
---
# <a name="icordebugunmanagedcallback-interface"></a><span data-ttu-id="68f1e-102">ICorDebugUnmanagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="68f1e-102">ICorDebugUnmanagedCallback Interface</span></span>
<span data-ttu-id="68f1e-103">Ortak dil çalışma zamanı (CLR) doğrudan ilgili olmayan yerel olayların bildirimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="68f1e-103">Provides notification of native events that are not directly related to the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="68f1e-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="68f1e-104">Methods</span></span>  
  
|<span data-ttu-id="68f1e-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="68f1e-105">Method</span></span>|<span data-ttu-id="68f1e-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="68f1e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="68f1e-107">DebugEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="68f1e-107">DebugEvent Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-debugevent-method.md)|<span data-ttu-id="68f1e-108">Hata ayıklayıcı, yerel bir olay harekete bildirir.</span><span class="sxs-lookup"><span data-stu-id="68f1e-108">Notifies the debugger that a native event has been fired.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="68f1e-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="68f1e-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="68f1e-110">Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="68f1e-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68f1e-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="68f1e-111">Requirements</span></span>  
 <span data-ttu-id="68f1e-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="68f1e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68f1e-113">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="68f1e-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="68f1e-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="68f1e-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="68f1e-115">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="68f1e-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="68f1e-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="68f1e-116">See also</span></span>

- [<span data-ttu-id="68f1e-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="68f1e-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
