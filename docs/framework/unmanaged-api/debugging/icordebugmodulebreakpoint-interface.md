---
title: Icordebugmodulebreakpoint Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModuleBreakpoint
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModuleBreakpoint
helpviewer_keywords: ICorDebugModuleBreakpoint interface [.NET Framework debugging]
ms.assetid: 34667162-f314-475f-ae1b-ce9cb0fcbb83
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3e3937c6c0baef4cc927b5c5d789826c70beebf2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmodulebreakpoint-interface1"></a><span data-ttu-id="aed27-102">Icordebugmodulebreakpoint Interface1</span><span class="sxs-lookup"><span data-stu-id="aed27-102">ICorDebugModuleBreakpoint Interface1</span></span>
<span data-ttu-id="aed27-103">Belirli modüller erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="aed27-103">Provides access to specific modules.</span></span> <span data-ttu-id="aed27-104">Bu arabirim Icordebugbreakpoint arabirimi sınıfıdır.</span><span class="sxs-lookup"><span data-stu-id="aed27-104">This interface is a subclass of the ICorDebugBreakpoint interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="aed27-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="aed27-105">Methods</span></span>  
  
|<span data-ttu-id="aed27-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="aed27-106">Method</span></span>|<span data-ttu-id="aed27-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aed27-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="aed27-108">GetModule yöntemi</span><span class="sxs-lookup"><span data-stu-id="aed27-108">GetModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodulebreakpoint-getmodule-method.md)|<span data-ttu-id="aed27-109">Arabirim işaretçisi bu kesme ayarlandığı modülü başvuruda bulunan bir Icordebugmodule alır.</span><span class="sxs-lookup"><span data-stu-id="aed27-109">Gets an interface pointer to an ICorDebugModule that references the module where this breakpoint is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aed27-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="aed27-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="aed27-111">Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="aed27-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aed27-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="aed27-112">Requirements</span></span>  
 <span data-ttu-id="aed27-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aed27-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aed27-114">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="aed27-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="aed27-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aed27-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aed27-116">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aed27-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aed27-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="aed27-117">See Also</span></span>  
 [<span data-ttu-id="aed27-118">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="aed27-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
