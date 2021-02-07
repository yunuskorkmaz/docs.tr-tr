---
description: ': ICorDebugBreakpointEnum arabirimi hakkında daha fazla bilgi edinin'
title: ICorDebugBreakpointEnum Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugBreakpointEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBreakpointEnum
helpviewer_keywords:
- ICorDebugBreakpointEnum interface [.NET Framework debugging]
ms.assetid: 4c6f4f6e-52cc-402e-881b-7b8526544c90
topic_type:
- apiref
ms.openlocfilehash: 71bd69c4fabba4a7d06f3b4cee5c0cf859d3c92b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99711732"
---
# <a name="icordebugbreakpointenum-interface"></a><span data-ttu-id="5e75c-103">ICorDebugBreakpointEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5e75c-103">ICorDebugBreakpointEnum Interface</span></span>

<span data-ttu-id="5e75c-104">Icordebugger Genum yöntemlerini uygular ve ICorDebugBreakpoint dizilerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="5e75c-104">Implements ICorDebugEnum methods, and enumerates ICorDebugBreakpoint arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5e75c-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="5e75c-105">Methods</span></span>  
  
|<span data-ttu-id="5e75c-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="5e75c-106">Method</span></span>|<span data-ttu-id="5e75c-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5e75c-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5e75c-108">Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5e75c-108">Next Method</span></span>](icordebugbreakpointenum-next-method.md)|<span data-ttu-id="5e75c-109">`ICorDebugBreakpoint`Geçerli konumdan başlayarak Numaralandırmadaki belirtilen örnek sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="5e75c-109">Gets the specified number of `ICorDebugBreakpoint` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5e75c-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5e75c-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5e75c-111">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="5e75c-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5e75c-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5e75c-112">Requirements</span></span>  

 <span data-ttu-id="5e75c-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5e75c-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e75c-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="5e75c-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5e75c-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="5e75c-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5e75c-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5e75c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e75c-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5e75c-117">See also</span></span>

- [<span data-ttu-id="5e75c-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="5e75c-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
