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
ms.openlocfilehash: c901e21521e941c51939958175a5316808890e9f
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83208648"
---
# <a name="icordebughandlevalue-interface"></a><span data-ttu-id="6f5ef-102">ICorDebugHandleValue Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6f5ef-102">ICorDebugHandleValue Interface</span></span>

<span data-ttu-id="6f5ef-103">Hata ayıklayıcının çöp toplama için bir tanıtıcı oluşturduğu bir başvuru değerini temsil eden ICorDebugReferenceValue öğesinin bir alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="6f5ef-103">A subclass of ICorDebugReferenceValue that represents a reference value to which the debugger has created a handle for garbage collection.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6f5ef-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="6f5ef-104">Methods</span></span>  
  
|<span data-ttu-id="6f5ef-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="6f5ef-105">Method</span></span>|<span data-ttu-id="6f5ef-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6f5ef-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6f5ef-107">Dispose Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6f5ef-107">Dispose Method</span></span>](icordebughandlevalue-dispose-method.md)|<span data-ttu-id="6f5ef-108">`ICorDebugHandleValue`Arabirim işaretçisini açıkça serbest bırakmadan bu nesne tarafından başvurulan tanıtıcıyı serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="6f5ef-108">Releases the handle referenced by this `ICorDebugHandleValue` object without explicitly releasing the interface pointer.</span></span>|  
|[<span data-ttu-id="6f5ef-109">GetHandleType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6f5ef-109">GetHandleType Method</span></span>](icordebughandlevalue-gethandletype-method.md)|<span data-ttu-id="6f5ef-110">Bunun başvurduğu tanıtıcı türünü açıklayan bir Corıı Ghandlitype değeri alır `ICorDebugHandleValue` .</span><span class="sxs-lookup"><span data-stu-id="6f5ef-110">Gets a CorDebugHandleType value that describes the kind of handle referenced by this `ICorDebugHandleValue`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6f5ef-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6f5ef-111">Remarks</span></span>  
 <span data-ttu-id="6f5ef-112">Bir `ICorDebugReferenceValue` nesne, hata ayıklama kodunun yürütülmesindeki bir kesme tarafından geçersiz kılınır.</span><span class="sxs-lookup"><span data-stu-id="6f5ef-112">An `ICorDebugReferenceValue` object is invalidated by a break in the execution of debugged code.</span></span> <span data-ttu-id="6f5ef-113">`ICorDebugHandleValue`, Açıkça yayınlanana kadar kesmeler ve devamlılıklar aracılığıyla başvurusunu korur.</span><span class="sxs-lookup"><span data-stu-id="6f5ef-113">An `ICorDebugHandleValue` maintains its reference through breaks and continuations, until it is explicitly released.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6f5ef-114">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="6f5ef-114">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f5ef-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6f5ef-115">Requirements</span></span>  
 <span data-ttu-id="6f5ef-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6f5ef-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f5ef-117">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6f5ef-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6f5ef-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="6f5ef-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6f5ef-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f5ef-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f5ef-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6f5ef-120">See also</span></span>

- [<span data-ttu-id="6f5ef-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="6f5ef-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
