---
title: Icordebughandlevalue arabirimi1
ms.date: 03/30/2017
api_name:
- ICorDebugHandleValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHandleValue
helpviewer_keywords:
- ICorDebugHandleValue interface [.NET Framework debugging]
ms.assetid: 66fcd2b8-ac66-414b-83a8-75a925e17772
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 102fcff6120822c5de0ede45d43a9cd064270085
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54715484"
---
# <a name="icordebughandlevalue-interface1"></a><span data-ttu-id="a7d0e-102">Icordebughandlevalue arabirimi1</span><span class="sxs-lookup"><span data-stu-id="a7d0e-102">ICorDebugHandleValue Interface1</span></span>
<span data-ttu-id="a7d0e-103">Icordebugreferencevalue için hata ayıklayıcı çöp toplama işlemi için bir tanıtıcı oluşturduğu bir başvuru değeri temsil eden bir alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="a7d0e-103">A subclass of ICorDebugReferenceValue that represents a reference value to which the debugger has created a handle for garbage collection.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a7d0e-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="a7d0e-104">Methods</span></span>  
  
|<span data-ttu-id="a7d0e-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="a7d0e-105">Method</span></span>|<span data-ttu-id="a7d0e-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a7d0e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a7d0e-107">Dispose Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a7d0e-107">Dispose Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-dispose-method.md)|<span data-ttu-id="a7d0e-108">Bu tarafından başvurulan tanıtıcıyı serbest `ICorDebugHandleValue` açıkça arabirim işaretçisi serbest olmadan nesne.</span><span class="sxs-lookup"><span data-stu-id="a7d0e-108">Releases the handle referenced by this `ICorDebugHandleValue` object without explicitly releasing the interface pointer.</span></span>|  
|[<span data-ttu-id="a7d0e-109">GetHandleType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a7d0e-109">GetHandleType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-gethandletype-method.md)|<span data-ttu-id="a7d0e-110">Bu tarafından başvurulan tanıtıcı türü tanımlayan CorDebugHandleType değeri alır `ICorDebugHandleValue`.</span><span class="sxs-lookup"><span data-stu-id="a7d0e-110">Gets a CorDebugHandleType value that describes the kind of handle referenced by this `ICorDebugHandleValue`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a7d0e-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a7d0e-111">Remarks</span></span>  
 <span data-ttu-id="a7d0e-112">Bir `ICorDebugReferenceValue` Nesne geçersiz hata ayıklanan kod yürütülmesi içindeki bir ara.</span><span class="sxs-lookup"><span data-stu-id="a7d0e-112">An `ICorDebugReferenceValue` object is invalidated by a break in the execution of debugged code.</span></span> <span data-ttu-id="a7d0e-113">Bir `ICorDebugHandleValue` açıkça serbest bırakılıncaya kadar sonu ve devamlılıklar, aracılığıyla, bir başvuru tutar.</span><span class="sxs-lookup"><span data-stu-id="a7d0e-113">An `ICorDebugHandleValue` maintains its reference through breaks and continuations, until it is explicitly released.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a7d0e-114">Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="a7d0e-114">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7d0e-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a7d0e-115">Requirements</span></span>  
 <span data-ttu-id="a7d0e-116">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a7d0e-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7d0e-117">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a7d0e-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a7d0e-118">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a7d0e-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a7d0e-119">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7d0e-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7d0e-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a7d0e-120">See also</span></span>
- [<span data-ttu-id="a7d0e-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a7d0e-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
