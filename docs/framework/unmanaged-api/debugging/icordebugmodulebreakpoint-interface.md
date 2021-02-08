---
description: ': ICorDebugModuleBreakpoint arabirimi hakkında daha fazla bilgi edinin'
title: ICorDebugModuleBreakpoint Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugModuleBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModuleBreakpoint
helpviewer_keywords:
- ICorDebugModuleBreakpoint interface [.NET Framework debugging]
ms.assetid: 34667162-f314-475f-ae1b-ce9cb0fcbb83
topic_type:
- apiref
ms.openlocfilehash: c864850400471c9a3580de9bb94262c62656edf0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790756"
---
# <a name="icordebugmodulebreakpoint-interface"></a><span data-ttu-id="16d1b-103">ICorDebugModuleBreakpoint Arabirimi</span><span class="sxs-lookup"><span data-stu-id="16d1b-103">ICorDebugModuleBreakpoint Interface</span></span>

<span data-ttu-id="16d1b-104">Belirli modüllere erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="16d1b-104">Provides access to specific modules.</span></span> <span data-ttu-id="16d1b-105">Bu arabirim, ICorDebugBreakpoint arabiriminin bir alt sınıfıdır.</span><span class="sxs-lookup"><span data-stu-id="16d1b-105">This interface is a subclass of the ICorDebugBreakpoint interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="16d1b-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="16d1b-106">Methods</span></span>  
  
|<span data-ttu-id="16d1b-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="16d1b-107">Method</span></span>|<span data-ttu-id="16d1b-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="16d1b-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="16d1b-109">GetModule Yöntemi</span><span class="sxs-lookup"><span data-stu-id="16d1b-109">GetModule Method</span></span>](icordebugmodulebreakpoint-getmodule-method.md)|<span data-ttu-id="16d1b-110">Bu kesme noktasının ayarlandığı modüle başvuran bir ICorDebugModule için bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="16d1b-110">Gets an interface pointer to an ICorDebugModule that references the module where this breakpoint is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="16d1b-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="16d1b-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="16d1b-112">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="16d1b-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16d1b-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="16d1b-113">Requirements</span></span>  

 <span data-ttu-id="16d1b-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="16d1b-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16d1b-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="16d1b-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="16d1b-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="16d1b-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="16d1b-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16d1b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16d1b-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="16d1b-118">See also</span></span>

- [<span data-ttu-id="16d1b-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="16d1b-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
