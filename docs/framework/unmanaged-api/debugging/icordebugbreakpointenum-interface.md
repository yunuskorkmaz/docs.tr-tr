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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e8192bd7ccaebab78158f11adb79509031132ecd
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937013"
---
# <a name="icordebugbreakpointenum-interface"></a><span data-ttu-id="4d03e-102">ICorDebugBreakpointEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4d03e-102">ICorDebugBreakpointEnum Interface</span></span>

<span data-ttu-id="4d03e-103">Icordebugger Genum yöntemlerini uygular ve ICorDebugBreakpoint dizilerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="4d03e-103">Implements ICorDebugEnum methods, and enumerates ICorDebugBreakpoint arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4d03e-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="4d03e-104">Methods</span></span>  
  
|<span data-ttu-id="4d03e-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="4d03e-105">Method</span></span>|<span data-ttu-id="4d03e-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4d03e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4d03e-107">Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4d03e-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpointenum-next-method.md)|<span data-ttu-id="4d03e-108">Geçerli konumdan başlayarak Numaralandırmadaki `ICorDebugBreakpoint` belirtilen örnek sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="4d03e-108">Gets the specified number of `ICorDebugBreakpoint` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4d03e-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4d03e-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4d03e-110">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="4d03e-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d03e-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4d03e-111">Requirements</span></span>  
 <span data-ttu-id="4d03e-112">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4d03e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d03e-113">**Üst bilgi** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="4d03e-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4d03e-114">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="4d03e-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4d03e-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4d03e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d03e-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4d03e-116">See also</span></span>

- [<span data-ttu-id="4d03e-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="4d03e-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
