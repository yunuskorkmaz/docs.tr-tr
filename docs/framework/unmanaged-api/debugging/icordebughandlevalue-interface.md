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
ms.openlocfilehash: 94472e84b73cdffe09505088b1e7fbc20a209bc3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138475"
---
# <a name="icordebughandlevalue-interface"></a><span data-ttu-id="a7f7e-102">ICorDebugHandleValue Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a7f7e-102">ICorDebugHandleValue Interface</span></span>

<span data-ttu-id="a7f7e-103">Hata ayıklayıcının çöp toplama için bir tanıtıcı oluşturduğu bir başvuru değerini temsil eden ICorDebugReferenceValue öğesinin bir alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="a7f7e-103">A subclass of ICorDebugReferenceValue that represents a reference value to which the debugger has created a handle for garbage collection.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a7f7e-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="a7f7e-104">Methods</span></span>  
  
|<span data-ttu-id="a7f7e-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="a7f7e-105">Method</span></span>|<span data-ttu-id="a7f7e-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a7f7e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a7f7e-107">Dispose Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a7f7e-107">Dispose Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-dispose-method.md)|<span data-ttu-id="a7f7e-108">Arabirim işaretçisini açıkça serbest bırakmadan bu `ICorDebugHandleValue` nesnesi tarafından başvurulan tanıtıcıyı serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="a7f7e-108">Releases the handle referenced by this `ICorDebugHandleValue` object without explicitly releasing the interface pointer.</span></span>|  
|[<span data-ttu-id="a7f7e-109">GetHandleType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a7f7e-109">GetHandleType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-gethandletype-method.md)|<span data-ttu-id="a7f7e-110">Bu `ICorDebugHandleValue`başvurduğu tanıtıcı türünü açıklayan bir Corıı Ghandlitype değeri alır.</span><span class="sxs-lookup"><span data-stu-id="a7f7e-110">Gets a CorDebugHandleType value that describes the kind of handle referenced by this `ICorDebugHandleValue`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a7f7e-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a7f7e-111">Remarks</span></span>  
 <span data-ttu-id="a7f7e-112">`ICorDebugReferenceValue` nesnesi, hata ayıklama kodunun yürütülmesindeki bir kesme tarafından geçersiz kılınır.</span><span class="sxs-lookup"><span data-stu-id="a7f7e-112">An `ICorDebugReferenceValue` object is invalidated by a break in the execution of debugged code.</span></span> <span data-ttu-id="a7f7e-113">`ICorDebugHandleValue`, açıkça yayınlanana kadar kesmeler ve devamlılıklar aracılığıyla başvurusunu tutar.</span><span class="sxs-lookup"><span data-stu-id="a7f7e-113">An `ICorDebugHandleValue` maintains its reference through breaks and continuations, until it is explicitly released.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a7f7e-114">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="a7f7e-114">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7f7e-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a7f7e-115">Requirements</span></span>  
 <span data-ttu-id="a7f7e-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a7f7e-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7f7e-117">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a7f7e-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a7f7e-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a7f7e-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a7f7e-119">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7f7e-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7f7e-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a7f7e-120">See also</span></span>

- [<span data-ttu-id="a7f7e-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a7f7e-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
