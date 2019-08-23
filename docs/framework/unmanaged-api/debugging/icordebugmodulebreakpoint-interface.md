---
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 03616f2756830e180155102492b15e18fee1085c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965122"
---
# <a name="icordebugmodulebreakpoint-interface"></a><span data-ttu-id="51af3-102">ICorDebugModuleBreakpoint Arabirimi</span><span class="sxs-lookup"><span data-stu-id="51af3-102">ICorDebugModuleBreakpoint Interface</span></span>

<span data-ttu-id="51af3-103">Belirli modüllere erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="51af3-103">Provides access to specific modules.</span></span> <span data-ttu-id="51af3-104">Bu arabirim, ICorDebugBreakpoint arabiriminin bir alt sınıfıdır.</span><span class="sxs-lookup"><span data-stu-id="51af3-104">This interface is a subclass of the ICorDebugBreakpoint interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="51af3-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="51af3-105">Methods</span></span>  
  
|<span data-ttu-id="51af3-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="51af3-106">Method</span></span>|<span data-ttu-id="51af3-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="51af3-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="51af3-108">GetModule Yöntemi</span><span class="sxs-lookup"><span data-stu-id="51af3-108">GetModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodulebreakpoint-getmodule-method.md)|<span data-ttu-id="51af3-109">Bu kesme noktasının ayarlandığı modüle başvuran bir ICorDebugModule için bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="51af3-109">Gets an interface pointer to an ICorDebugModule that references the module where this breakpoint is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="51af3-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="51af3-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="51af3-111">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="51af3-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51af3-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="51af3-112">Requirements</span></span>  
 <span data-ttu-id="51af3-113">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="51af3-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51af3-114">**Üst bilgi** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="51af3-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="51af3-115">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="51af3-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="51af3-116">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="51af3-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51af3-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="51af3-117">See also</span></span>

- [<span data-ttu-id="51af3-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="51af3-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
