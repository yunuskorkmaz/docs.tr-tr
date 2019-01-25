---
title: Icordebugınternalframe arabirimi1
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
ms.openlocfilehash: 1fab8221bd160a74bb44c3ed0721ad4620e93419
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54692801"
---
# <a name="icordebuginternalframe-interface1"></a><span data-ttu-id="8ba95-102">Icordebugınternalframe arabirimi1</span><span class="sxs-lookup"><span data-stu-id="8ba95-102">ICorDebugInternalFrame Interface1</span></span>
<span data-ttu-id="8ba95-103">Bir çalışma zamanı iç yığın çerçevesinde temsil eder.</span><span class="sxs-lookup"><span data-stu-id="8ba95-103">Represents a runtime-internal frame on the stack.</span></span> <span data-ttu-id="8ba95-104">Icordebugframe arabirimi öğesinin arabirimidir.</span><span class="sxs-lookup"><span data-stu-id="8ba95-104">This interface is a subclass of the ICorDebugFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8ba95-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="8ba95-105">Methods</span></span>  
  
|<span data-ttu-id="8ba95-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="8ba95-106">Method</span></span>|<span data-ttu-id="8ba95-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8ba95-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8ba95-108">GetFrameType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8ba95-108">GetFrameType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe-getframetype-method.md)|<span data-ttu-id="8ba95-109">Bu iç çerçeve türünü alır.</span><span class="sxs-lookup"><span data-stu-id="8ba95-109">Gets the type of this internal frame.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8ba95-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8ba95-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8ba95-111">Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="8ba95-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ba95-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8ba95-112">Requirements</span></span>  
 <span data-ttu-id="8ba95-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8ba95-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ba95-114">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8ba95-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8ba95-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8ba95-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8ba95-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ba95-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ba95-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8ba95-117">See also</span></span>
- [<span data-ttu-id="8ba95-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="8ba95-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
