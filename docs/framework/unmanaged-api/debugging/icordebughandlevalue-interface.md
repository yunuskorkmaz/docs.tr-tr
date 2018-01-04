---
title: Icordebughandlevalue Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugHandleValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugHandleValue
helpviewer_keywords: ICorDebugHandleValue interface [.NET Framework debugging]
ms.assetid: 66fcd2b8-ac66-414b-83a8-75a925e17772
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b8df7b46bf22fa1a3a8633cbad7ad1a6582b4860
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebughandlevalue-interface1"></a><span data-ttu-id="1db71-102">Icordebughandlevalue Interface1</span><span class="sxs-lookup"><span data-stu-id="1db71-102">ICorDebugHandleValue Interface1</span></span>
<span data-ttu-id="1db71-103">Hata ayıklayıcı çöp toplama için bir tanıtıcı oluşturduğu başvuru değeri temsil eden Icordebugreferencevalue sınıfıdır.</span><span class="sxs-lookup"><span data-stu-id="1db71-103">A subclass of ICorDebugReferenceValue that represents a reference value to which the debugger has created a handle for garbage collection.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1db71-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="1db71-104">Methods</span></span>  
  
|<span data-ttu-id="1db71-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="1db71-105">Method</span></span>|<span data-ttu-id="1db71-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1db71-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1db71-107">Dispose Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1db71-107">Dispose Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-dispose-method.md)|<span data-ttu-id="1db71-108">Bu tarafından başvurulan tanıtıcı serbest `ICorDebugHandleValue` açıkça arabirimi işaretçisi serbest olmadan nesnesi.</span><span class="sxs-lookup"><span data-stu-id="1db71-108">Releases the handle referenced by this `ICorDebugHandleValue` object without explicitly releasing the interface pointer.</span></span>|  
|[<span data-ttu-id="1db71-109">GetHandleType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1db71-109">GetHandleType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-gethandletype-method.md)|<span data-ttu-id="1db71-110">Bu tarafından başvurulan tanıtıcı türünü tanımlayan bir CorDebugHandleType değeri alır `ICorDebugHandleValue`.</span><span class="sxs-lookup"><span data-stu-id="1db71-110">Gets a CorDebugHandleType value that describes the kind of handle referenced by this `ICorDebugHandleValue`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1db71-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1db71-111">Remarks</span></span>  
 <span data-ttu-id="1db71-112">Bir `ICorDebugReferenceValue` hata ayıklaması kod yürütmeyi aranın tarafından nesnesi geçersiz.</span><span class="sxs-lookup"><span data-stu-id="1db71-112">An `ICorDebugReferenceValue` object is invalidated by a break in the execution of debugged code.</span></span> <span data-ttu-id="1db71-113">Bir `ICorDebugHandleValue` açıkça serbest kadar sonları ve devamlılıklar, aracılığıyla kendi başvuru korur.</span><span class="sxs-lookup"><span data-stu-id="1db71-113">An `ICorDebugHandleValue` maintains its reference through breaks and continuations, until it is explicitly released.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1db71-114">Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="1db71-114">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1db71-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1db71-115">Requirements</span></span>  
 <span data-ttu-id="1db71-116">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1db71-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1db71-117">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1db71-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1db71-118">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1db71-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1db71-119">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1db71-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1db71-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1db71-120">See Also</span></span>  
 [<span data-ttu-id="1db71-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="1db71-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
