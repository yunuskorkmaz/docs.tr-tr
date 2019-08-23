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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b9ea398c32762be31f93002533b15bcf3851b870
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69910240"
---
# <a name="icordebugframeenum-interface"></a><span data-ttu-id="4c9ff-102">ICorDebugFrameEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4c9ff-102">ICorDebugFrameEnum Interface</span></span>

<span data-ttu-id="4c9ff-103">Icordebugger Genum yöntemlerini uygular ve ICorDebugFrame dizilerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="4c9ff-103">Implements ICorDebugEnum methods, and enumerates ICorDebugFrame arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4c9ff-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="4c9ff-104">Methods</span></span>  
  
|<span data-ttu-id="4c9ff-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="4c9ff-105">Method</span></span>|<span data-ttu-id="4c9ff-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4c9ff-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4c9ff-107">Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4c9ff-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframeenum-next-method.md)|<span data-ttu-id="4c9ff-108">Geçerli konumdan başlayarak Numaralandırmadaki `ICorDebugFrame` belirtilen örnek sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="4c9ff-108">Gets the specified number of `ICorDebugFrame` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4c9ff-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4c9ff-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4c9ff-110">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="4c9ff-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4c9ff-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4c9ff-111">Requirements</span></span>  
 <span data-ttu-id="4c9ff-112">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4c9ff-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c9ff-113">**Üst bilgi** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="4c9ff-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4c9ff-114">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="4c9ff-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4c9ff-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4c9ff-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c9ff-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4c9ff-116">See also</span></span>

- [<span data-ttu-id="4c9ff-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="4c9ff-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
