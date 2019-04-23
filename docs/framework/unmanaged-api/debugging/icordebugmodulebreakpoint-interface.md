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
ms.openlocfilehash: d6a43a264fcaa94ce4e629d8db504e9d416f6b89
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59179718"
---
# <a name="icordebugmodulebreakpoint-interface"></a><span data-ttu-id="53e84-102">ICorDebugModuleBreakpoint Arabirimi</span><span class="sxs-lookup"><span data-stu-id="53e84-102">ICorDebugModuleBreakpoint Interface</span></span>

<span data-ttu-id="53e84-103">Belirli modüllere erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="53e84-103">Provides access to specific modules.</span></span> <span data-ttu-id="53e84-104">Icordebugbreakpoint arabirimi öğesinin arabirimidir.</span><span class="sxs-lookup"><span data-stu-id="53e84-104">This interface is a subclass of the ICorDebugBreakpoint interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="53e84-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="53e84-105">Methods</span></span>  
  
|<span data-ttu-id="53e84-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="53e84-106">Method</span></span>|<span data-ttu-id="53e84-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="53e84-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="53e84-108">GetModule Yöntemi</span><span class="sxs-lookup"><span data-stu-id="53e84-108">GetModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodulebreakpoint-getmodule-method.md)|<span data-ttu-id="53e84-109">Bu Kesme noktasının ayarlandığı modülü başvuran bir Icordebugmodule bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="53e84-109">Gets an interface pointer to an ICorDebugModule that references the module where this breakpoint is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="53e84-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="53e84-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="53e84-111">Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="53e84-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="53e84-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="53e84-112">Requirements</span></span>  
 <span data-ttu-id="53e84-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="53e84-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53e84-114">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="53e84-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="53e84-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="53e84-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="53e84-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53e84-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53e84-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="53e84-117">See also</span></span>

- [<span data-ttu-id="53e84-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="53e84-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
