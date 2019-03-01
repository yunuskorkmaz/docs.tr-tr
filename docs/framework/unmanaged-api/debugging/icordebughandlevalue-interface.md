---
title: ICorDebugHandleValue Arabirimi
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
ms.openlocfilehash: 6dddc1665dff5c1a0629d25aa99066ce6eeca94a
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56981445"
---
# <a name="icordebughandlevalue-interface"></a><span data-ttu-id="0438a-102">ICorDebugHandleValue Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0438a-102">ICorDebugHandleValue Interface</span></span>

<span data-ttu-id="0438a-103">Icordebugreferencevalue için hata ayıklayıcı çöp toplama işlemi için bir tanıtıcı oluşturduğu bir başvuru değeri temsil eden bir alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="0438a-103">A subclass of ICorDebugReferenceValue that represents a reference value to which the debugger has created a handle for garbage collection.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0438a-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="0438a-104">Methods</span></span>  
  
|<span data-ttu-id="0438a-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="0438a-105">Method</span></span>|<span data-ttu-id="0438a-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0438a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0438a-107">Dispose Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0438a-107">Dispose Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-dispose-method.md)|<span data-ttu-id="0438a-108">Bu tarafından başvurulan tanıtıcıyı serbest `ICorDebugHandleValue` açıkça arabirim işaretçisi serbest olmadan nesne.</span><span class="sxs-lookup"><span data-stu-id="0438a-108">Releases the handle referenced by this `ICorDebugHandleValue` object without explicitly releasing the interface pointer.</span></span>|  
|[<span data-ttu-id="0438a-109">GetHandleType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0438a-109">GetHandleType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-gethandletype-method.md)|<span data-ttu-id="0438a-110">Bu tarafından başvurulan tanıtıcı türü tanımlayan CorDebugHandleType değeri alır `ICorDebugHandleValue`.</span><span class="sxs-lookup"><span data-stu-id="0438a-110">Gets a CorDebugHandleType value that describes the kind of handle referenced by this `ICorDebugHandleValue`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0438a-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0438a-111">Remarks</span></span>  
 <span data-ttu-id="0438a-112">Bir `ICorDebugReferenceValue` Nesne geçersiz hata ayıklanan kod yürütülmesi içindeki bir ara.</span><span class="sxs-lookup"><span data-stu-id="0438a-112">An `ICorDebugReferenceValue` object is invalidated by a break in the execution of debugged code.</span></span> <span data-ttu-id="0438a-113">Bir `ICorDebugHandleValue` açıkça serbest bırakılıncaya kadar sonu ve devamlılıklar, aracılığıyla, bir başvuru tutar.</span><span class="sxs-lookup"><span data-stu-id="0438a-113">An `ICorDebugHandleValue` maintains its reference through breaks and continuations, until it is explicitly released.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0438a-114">Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="0438a-114">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0438a-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0438a-115">Requirements</span></span>  
 <span data-ttu-id="0438a-116">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0438a-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0438a-117">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0438a-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0438a-118">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0438a-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0438a-119">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0438a-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0438a-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0438a-120">See also</span></span>
- [<span data-ttu-id="0438a-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="0438a-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
