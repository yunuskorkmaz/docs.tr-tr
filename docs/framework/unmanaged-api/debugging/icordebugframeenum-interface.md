---
description: ': ICorDebugFrameEnum arabirimi hakkında daha fazla bilgi edinin'
title: ICorDebugFrameEnum Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugFrameEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrameEnum
helpviewer_keywords:
- ICorDebugFrameEnum interface [.NET Framework debugging]
ms.assetid: ee3f85d3-044e-46b8-945c-93ebfa5d9e91
topic_type:
- apiref
ms.openlocfilehash: 61a83bd960182c28888d3c5459cf43c9bc7f2be3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99692816"
---
# <a name="icordebugframeenum-interface"></a><span data-ttu-id="5d5d0-103">ICorDebugFrameEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5d5d0-103">ICorDebugFrameEnum Interface</span></span>

<span data-ttu-id="5d5d0-104">Icordebugger Genum yöntemlerini uygular ve ICorDebugFrame dizilerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="5d5d0-104">Implements ICorDebugEnum methods, and enumerates ICorDebugFrame arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5d5d0-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="5d5d0-105">Methods</span></span>  
  
|<span data-ttu-id="5d5d0-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="5d5d0-106">Method</span></span>|<span data-ttu-id="5d5d0-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5d5d0-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5d5d0-108">Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5d5d0-108">Next Method</span></span>](icordebugframeenum-next-method.md)|<span data-ttu-id="5d5d0-109">`ICorDebugFrame`Geçerli konumdan başlayarak Numaralandırmadaki belirtilen örnek sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="5d5d0-109">Gets the specified number of `ICorDebugFrame` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5d5d0-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5d5d0-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5d5d0-111">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="5d5d0-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d5d0-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5d5d0-112">Requirements</span></span>  

 <span data-ttu-id="5d5d0-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5d5d0-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d5d0-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="5d5d0-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5d5d0-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="5d5d0-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5d5d0-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d5d0-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d5d0-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5d5d0-117">See also</span></span>

- [<span data-ttu-id="5d5d0-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="5d5d0-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
