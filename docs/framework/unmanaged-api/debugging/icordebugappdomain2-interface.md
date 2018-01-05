---
title: Icordebugappdomain2 Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAppDomain2
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugAppDomain2
helpviewer_keywords: ICorDebugAppDomain2 interface [.NET Framework debugging]
ms.assetid: 314d29f3-feb0-4a92-9530-b569c280cc31
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c811107fcf32696aee17810af06ac0b2ddc9102d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugappdomain2-interface1"></a><span data-ttu-id="7a441-102">Icordebugappdomain2 Interface1</span><span class="sxs-lookup"><span data-stu-id="7a441-102">ICorDebugAppDomain2 Interface1</span></span>
<span data-ttu-id="7a441-103">Diziler, işaretçileri, işlev işaretçileri ve başvuru türleri ile çalışmak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="7a441-103">Provides methods to work with arrays, pointers, function pointers, and reference types.</span></span> <span data-ttu-id="7a441-104">Bu arabirim, Icordebugappdomain arabirimi uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="7a441-104">This interface is an extension of the ICorDebugAppDomain interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7a441-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="7a441-105">Methods</span></span>  
  
|<span data-ttu-id="7a441-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="7a441-106">Method</span></span>|<span data-ttu-id="7a441-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7a441-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7a441-108">GetArrayOrPointerType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7a441-108">GetArrayOrPointerType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain2-getarrayorpointertype-method.md)|<span data-ttu-id="7a441-109">Belirtilen türe veya bir işaretçi veya belirtilen tür referansı dizisini alır.</span><span class="sxs-lookup"><span data-stu-id="7a441-109">Gets an array of the specified type, or a pointer or reference to the specified type.</span></span>|  
|[<span data-ttu-id="7a441-110">GetFunctionPointerType</span><span class="sxs-lookup"><span data-stu-id="7a441-110">GetFunctionPointerType</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain2-getfunctionpointertype-method.md)|<span data-ttu-id="7a441-111">Bir işaretçi belirli bir imzaya sahip bir işlevi alır.</span><span class="sxs-lookup"><span data-stu-id="7a441-111">Gets a pointer to a function that has a given signature.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7a441-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7a441-112">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7a441-113">Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="7a441-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a441-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7a441-114">Requirements</span></span>  
 <span data-ttu-id="7a441-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7a441-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a441-116">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7a441-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7a441-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7a441-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7a441-118">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7a441-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a441-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7a441-119">See Also</span></span>  
 [<span data-ttu-id="7a441-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="7a441-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
