---
title: Icordebugmodulebreakpoint Interface1
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
ms.openlocfilehash: c04d5f779306a67e389f768cefdf633f3d72f0ee
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33416143"
---
# <a name="icordebugmodulebreakpoint-interface1"></a><span data-ttu-id="370dd-102">Icordebugmodulebreakpoint Interface1</span><span class="sxs-lookup"><span data-stu-id="370dd-102">ICorDebugModuleBreakpoint Interface1</span></span>
<span data-ttu-id="370dd-103">Belirli modüller erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="370dd-103">Provides access to specific modules.</span></span> <span data-ttu-id="370dd-104">Bu arabirim Icordebugbreakpoint arabirimi sınıfıdır.</span><span class="sxs-lookup"><span data-stu-id="370dd-104">This interface is a subclass of the ICorDebugBreakpoint interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="370dd-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="370dd-105">Methods</span></span>  
  
|<span data-ttu-id="370dd-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="370dd-106">Method</span></span>|<span data-ttu-id="370dd-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="370dd-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="370dd-108">GetModule Yöntemi</span><span class="sxs-lookup"><span data-stu-id="370dd-108">GetModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodulebreakpoint-getmodule-method.md)|<span data-ttu-id="370dd-109">Arabirim işaretçisi bu kesme ayarlandığı modülü başvuruda bulunan bir Icordebugmodule alır.</span><span class="sxs-lookup"><span data-stu-id="370dd-109">Gets an interface pointer to an ICorDebugModule that references the module where this breakpoint is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="370dd-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="370dd-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="370dd-111">Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="370dd-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="370dd-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="370dd-112">Requirements</span></span>  
 <span data-ttu-id="370dd-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="370dd-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="370dd-114">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="370dd-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="370dd-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="370dd-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="370dd-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="370dd-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="370dd-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="370dd-117">See Also</span></span>  
 [<span data-ttu-id="370dd-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="370dd-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
