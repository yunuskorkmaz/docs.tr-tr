---
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
ms.openlocfilehash: 3a33d25ee13e12a2612d0132da1dc84c24f2f95b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73090533"
---
# <a name="icordebugframeenum-interface"></a><span data-ttu-id="fd2db-102">ICorDebugFrameEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fd2db-102">ICorDebugFrameEnum Interface</span></span>

<span data-ttu-id="fd2db-103">Icordebugger Genum yöntemlerini uygular ve ICorDebugFrame dizilerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="fd2db-103">Implements ICorDebugEnum methods, and enumerates ICorDebugFrame arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fd2db-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="fd2db-104">Methods</span></span>  
  
|<span data-ttu-id="fd2db-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="fd2db-105">Method</span></span>|<span data-ttu-id="fd2db-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fd2db-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fd2db-107">Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fd2db-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframeenum-next-method.md)|<span data-ttu-id="fd2db-108">Geçerli konumdan başlayarak Numaralandırmadaki belirtilen `ICorDebugFrame` örneği sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="fd2db-108">Gets the specified number of `ICorDebugFrame` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fd2db-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fd2db-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fd2db-110">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="fd2db-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fd2db-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fd2db-111">Requirements</span></span>  
 <span data-ttu-id="fd2db-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fd2db-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fd2db-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="fd2db-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fd2db-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="fd2db-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fd2db-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fd2db-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd2db-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fd2db-116">See also</span></span>

- [<span data-ttu-id="fd2db-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="fd2db-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
