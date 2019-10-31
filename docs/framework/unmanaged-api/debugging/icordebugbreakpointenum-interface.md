---
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
ms.openlocfilehash: 5fb4a8a508cde4455bbee8c08432d3549e3fac43
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122750"
---
# <a name="icordebugbreakpointenum-interface"></a><span data-ttu-id="609f7-102">ICorDebugBreakpointEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="609f7-102">ICorDebugBreakpointEnum Interface</span></span>

<span data-ttu-id="609f7-103">Icordebugger Genum yöntemlerini uygular ve ICorDebugBreakpoint dizilerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="609f7-103">Implements ICorDebugEnum methods, and enumerates ICorDebugBreakpoint arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="609f7-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="609f7-104">Methods</span></span>  
  
|<span data-ttu-id="609f7-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="609f7-105">Method</span></span>|<span data-ttu-id="609f7-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="609f7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="609f7-107">Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="609f7-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpointenum-next-method.md)|<span data-ttu-id="609f7-108">Geçerli konumdan başlayarak Numaralandırmadaki belirtilen `ICorDebugBreakpoint` örneği sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="609f7-108">Gets the specified number of `ICorDebugBreakpoint` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="609f7-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="609f7-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="609f7-110">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="609f7-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="609f7-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="609f7-111">Requirements</span></span>  
 <span data-ttu-id="609f7-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="609f7-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="609f7-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="609f7-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="609f7-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="609f7-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="609f7-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="609f7-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="609f7-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="609f7-116">See also</span></span>

- [<span data-ttu-id="609f7-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="609f7-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
