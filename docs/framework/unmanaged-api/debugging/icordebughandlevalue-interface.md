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
ms.openlocfilehash: 9a9eb63e681b47f058901b0ff002015baffe6048
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59117450"
---
# <a name="icordebughandlevalue-interface"></a><span data-ttu-id="43afc-102">ICorDebugHandleValue Arabirimi</span><span class="sxs-lookup"><span data-stu-id="43afc-102">ICorDebugHandleValue Interface</span></span>

<span data-ttu-id="43afc-103">Icordebugreferencevalue için hata ayıklayıcı çöp toplama işlemi için bir tanıtıcı oluşturduğu bir başvuru değeri temsil eden bir alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="43afc-103">A subclass of ICorDebugReferenceValue that represents a reference value to which the debugger has created a handle for garbage collection.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="43afc-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="43afc-104">Methods</span></span>  
  
|<span data-ttu-id="43afc-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="43afc-105">Method</span></span>|<span data-ttu-id="43afc-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="43afc-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="43afc-107">Dispose Yöntemi</span><span class="sxs-lookup"><span data-stu-id="43afc-107">Dispose Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-dispose-method.md)|<span data-ttu-id="43afc-108">Bu tarafından başvurulan tanıtıcıyı serbest `ICorDebugHandleValue` açıkça arabirim işaretçisi serbest olmadan nesne.</span><span class="sxs-lookup"><span data-stu-id="43afc-108">Releases the handle referenced by this `ICorDebugHandleValue` object without explicitly releasing the interface pointer.</span></span>|  
|[<span data-ttu-id="43afc-109">GetHandleType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="43afc-109">GetHandleType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-gethandletype-method.md)|<span data-ttu-id="43afc-110">Bu tarafından başvurulan tanıtıcı türü tanımlayan CorDebugHandleType değeri alır `ICorDebugHandleValue`.</span><span class="sxs-lookup"><span data-stu-id="43afc-110">Gets a CorDebugHandleType value that describes the kind of handle referenced by this `ICorDebugHandleValue`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="43afc-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="43afc-111">Remarks</span></span>  
 <span data-ttu-id="43afc-112">Bir `ICorDebugReferenceValue` Nesne geçersiz hata ayıklanan kod yürütülmesi içindeki bir ara.</span><span class="sxs-lookup"><span data-stu-id="43afc-112">An `ICorDebugReferenceValue` object is invalidated by a break in the execution of debugged code.</span></span> <span data-ttu-id="43afc-113">Bir `ICorDebugHandleValue` açıkça serbest bırakılıncaya kadar sonu ve devamlılıklar, aracılığıyla, bir başvuru tutar.</span><span class="sxs-lookup"><span data-stu-id="43afc-113">An `ICorDebugHandleValue` maintains its reference through breaks and continuations, until it is explicitly released.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="43afc-114">Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="43afc-114">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="43afc-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="43afc-115">Requirements</span></span>  
 <span data-ttu-id="43afc-116">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="43afc-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="43afc-117">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="43afc-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="43afc-118">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="43afc-118">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="43afc-119">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="43afc-119">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="43afc-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="43afc-120">See also</span></span>

- [<span data-ttu-id="43afc-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="43afc-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
