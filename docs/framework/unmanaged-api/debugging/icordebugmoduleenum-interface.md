---
description: 'Şu konuda daha fazla bilgi edinin: ICorDebugModuleEnum arabirimi'
title: ICorDebugModuleEnum Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugModuleEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModuleEnum
helpviewer_keywords:
- ICorDebugModuleEnum interface [.NET Framework debugging]
ms.assetid: 2fb93cd6-6d47-4fdc-a9a0-047726fd03a1
topic_type:
- apiref
ms.openlocfilehash: c9c847f926984ed2b8aea87463e351cd97a62c80
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801052"
---
# <a name="icordebugmoduleenum-interface"></a><span data-ttu-id="91fdd-103">ICorDebugModuleEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="91fdd-103">ICorDebugModuleEnum Interface</span></span>

<span data-ttu-id="91fdd-104">Icordebugger Genum yöntemlerini uygular ve ICorDebugModule dizilerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="91fdd-104">Implements ICorDebugEnum methods, and enumerates ICorDebugModule arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="91fdd-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="91fdd-105">Methods</span></span>  
  
|<span data-ttu-id="91fdd-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="91fdd-106">Method</span></span>|<span data-ttu-id="91fdd-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="91fdd-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="91fdd-108">Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="91fdd-108">Next Method</span></span>](icordebugmoduleenum-next-method.md)|<span data-ttu-id="91fdd-109">`ICorDebugModule`Geçerli konumdan başlayarak Numaralandırmadaki belirtilen örnek sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="91fdd-109">Gets the specified number of `ICorDebugModule` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="91fdd-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="91fdd-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="91fdd-111">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="91fdd-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91fdd-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="91fdd-112">Requirements</span></span>  

 <span data-ttu-id="91fdd-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="91fdd-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91fdd-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="91fdd-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="91fdd-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="91fdd-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="91fdd-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="91fdd-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91fdd-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="91fdd-117">See also</span></span>

- [<span data-ttu-id="91fdd-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="91fdd-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
