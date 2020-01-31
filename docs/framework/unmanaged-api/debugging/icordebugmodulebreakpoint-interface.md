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
ms.openlocfilehash: df3ad3fa4ef4eeee7e23ca1629da7a8b8ce09711
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792920"
---
# <a name="icordebugmodulebreakpoint-interface"></a><span data-ttu-id="c04d8-102">ICorDebugModuleBreakpoint Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c04d8-102">ICorDebugModuleBreakpoint Interface</span></span>

<span data-ttu-id="c04d8-103">Belirli modüllere erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="c04d8-103">Provides access to specific modules.</span></span> <span data-ttu-id="c04d8-104">Bu arabirim, ICorDebugBreakpoint arabiriminin bir alt sınıfıdır.</span><span class="sxs-lookup"><span data-stu-id="c04d8-104">This interface is a subclass of the ICorDebugBreakpoint interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c04d8-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="c04d8-105">Methods</span></span>  
  
|<span data-ttu-id="c04d8-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="c04d8-106">Method</span></span>|<span data-ttu-id="c04d8-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c04d8-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c04d8-108">GetModule Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c04d8-108">GetModule Method</span></span>](icordebugmodulebreakpoint-getmodule-method.md)|<span data-ttu-id="c04d8-109">Bu kesme noktasının ayarlandığı modüle başvuran bir ICorDebugModule için bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="c04d8-109">Gets an interface pointer to an ICorDebugModule that references the module where this breakpoint is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c04d8-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c04d8-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c04d8-111">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="c04d8-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c04d8-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c04d8-112">Requirements</span></span>  
 <span data-ttu-id="c04d8-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c04d8-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c04d8-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c04d8-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c04d8-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c04d8-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c04d8-116">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c04d8-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c04d8-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c04d8-117">See also</span></span>

- [<span data-ttu-id="c04d8-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c04d8-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
