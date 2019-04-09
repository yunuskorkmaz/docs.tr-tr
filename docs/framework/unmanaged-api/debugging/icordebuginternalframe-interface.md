---
title: ICorDebugInternalFrame Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugInternalFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugInternalFrame
helpviewer_keywords:
- ICorDebugInternalFrame interface [.NET Framework debugging]
ms.assetid: bb4772ca-0d54-4185-b738-7a6ffe9ea85a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2f16b4628215bee2410708edeb337b41fbdc0311
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59109830"
---
# <a name="icordebuginternalframe-interface"></a><span data-ttu-id="5b620-102">ICorDebugInternalFrame Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5b620-102">ICorDebugInternalFrame Interface</span></span>

<span data-ttu-id="5b620-103">Bir çalışma zamanı iç yığın çerçevesinde temsil eder.</span><span class="sxs-lookup"><span data-stu-id="5b620-103">Represents a runtime-internal frame on the stack.</span></span> <span data-ttu-id="5b620-104">Icordebugframe arabirimi öğesinin arabirimidir.</span><span class="sxs-lookup"><span data-stu-id="5b620-104">This interface is a subclass of the ICorDebugFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5b620-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="5b620-105">Methods</span></span>  
  
|<span data-ttu-id="5b620-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="5b620-106">Method</span></span>|<span data-ttu-id="5b620-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5b620-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5b620-108">GetFrameType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5b620-108">GetFrameType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe-getframetype-method.md)|<span data-ttu-id="5b620-109">Bu iç çerçeve türünü alır.</span><span class="sxs-lookup"><span data-stu-id="5b620-109">Gets the type of this internal frame.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5b620-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5b620-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5b620-111">Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="5b620-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b620-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5b620-112">Requirements</span></span>  
 <span data-ttu-id="5b620-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5b620-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b620-114">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5b620-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5b620-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5b620-115">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="5b620-116">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="5b620-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5b620-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5b620-117">See also</span></span>

- [<span data-ttu-id="5b620-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="5b620-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
