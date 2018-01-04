---
title: ICorDebugUnmanagedCallback Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugUnmanagedCallback
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugUnmanagedCallback
helpviewer_keywords: ICorDebugUnmanagedCallback interface [.NET Framework debugging]
ms.assetid: bc71cbca-7d73-40e5-84dd-2109fade3c2a
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e2a0dc561010ead94f1b2ffcd306a6067a04d7e4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugunmanagedcallback-interface"></a><span data-ttu-id="d4010-102">ICorDebugUnmanagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d4010-102">ICorDebugUnmanagedCallback Interface</span></span>
<span data-ttu-id="d4010-103">Ortak dil çalışma zamanı (CLR) doğrudan ilgili olmayan yerel olay bildirim sağlar.</span><span class="sxs-lookup"><span data-stu-id="d4010-103">Provides notification of native events that are not directly related to the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d4010-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="d4010-104">Methods</span></span>  
  
|<span data-ttu-id="d4010-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="d4010-105">Method</span></span>|<span data-ttu-id="d4010-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d4010-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d4010-107">DebugEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d4010-107">DebugEvent Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-debugevent-method.md)|<span data-ttu-id="d4010-108">Hata ayıklayıcı yerel olay harekete olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="d4010-108">Notifies the debugger that a native event has been fired.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d4010-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d4010-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d4010-110">Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="d4010-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4010-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d4010-111">Requirements</span></span>  
 <span data-ttu-id="d4010-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d4010-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4010-113">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d4010-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d4010-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d4010-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d4010-115">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4010-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4010-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d4010-116">See Also</span></span>  
 [<span data-ttu-id="d4010-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d4010-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
