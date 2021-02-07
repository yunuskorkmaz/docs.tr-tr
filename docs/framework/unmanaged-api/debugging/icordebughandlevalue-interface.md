---
description: 'Bu konuda daha fazla bilgi edinin: ıcorıınfo Ghandtavalue arabirimi'
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
ms.openlocfilehash: 3bdb1f5668be283d8722c15f4779adfe4d7b3a2d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99692050"
---
# <a name="icordebughandlevalue-interface"></a><span data-ttu-id="21ded-103">ICorDebugHandleValue Arabirimi</span><span class="sxs-lookup"><span data-stu-id="21ded-103">ICorDebugHandleValue Interface</span></span>

<span data-ttu-id="21ded-104">Hata ayıklayıcının çöp toplama için bir tanıtıcı oluşturduğu bir başvuru değerini temsil eden ICorDebugReferenceValue öğesinin bir alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="21ded-104">A subclass of ICorDebugReferenceValue that represents a reference value to which the debugger has created a handle for garbage collection.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="21ded-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="21ded-105">Methods</span></span>  
  
|<span data-ttu-id="21ded-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="21ded-106">Method</span></span>|<span data-ttu-id="21ded-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="21ded-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="21ded-108">Dispose Yöntemi</span><span class="sxs-lookup"><span data-stu-id="21ded-108">Dispose Method</span></span>](icordebughandlevalue-dispose-method.md)|<span data-ttu-id="21ded-109">`ICorDebugHandleValue`Arabirim işaretçisini açıkça serbest bırakmadan bu nesne tarafından başvurulan tanıtıcıyı serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="21ded-109">Releases the handle referenced by this `ICorDebugHandleValue` object without explicitly releasing the interface pointer.</span></span>|  
|[<span data-ttu-id="21ded-110">GetHandleType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="21ded-110">GetHandleType Method</span></span>](icordebughandlevalue-gethandletype-method.md)|<span data-ttu-id="21ded-111">Bunun başvurduğu tanıtıcı türünü açıklayan bir Corıı Ghandlitype değeri alır `ICorDebugHandleValue` .</span><span class="sxs-lookup"><span data-stu-id="21ded-111">Gets a CorDebugHandleType value that describes the kind of handle referenced by this `ICorDebugHandleValue`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="21ded-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="21ded-112">Remarks</span></span>  

 <span data-ttu-id="21ded-113">Bir `ICorDebugReferenceValue` nesne, hata ayıklama kodunun yürütülmesindeki bir kesme tarafından geçersiz kılınır.</span><span class="sxs-lookup"><span data-stu-id="21ded-113">An `ICorDebugReferenceValue` object is invalidated by a break in the execution of debugged code.</span></span> <span data-ttu-id="21ded-114">`ICorDebugHandleValue`, Açıkça yayınlanana kadar kesmeler ve devamlılıklar aracılığıyla başvurusunu korur.</span><span class="sxs-lookup"><span data-stu-id="21ded-114">An `ICorDebugHandleValue` maintains its reference through breaks and continuations, until it is explicitly released.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="21ded-115">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="21ded-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21ded-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="21ded-116">Requirements</span></span>  

 <span data-ttu-id="21ded-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21ded-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21ded-118">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="21ded-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="21ded-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="21ded-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="21ded-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21ded-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21ded-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="21ded-121">See also</span></span>

- [<span data-ttu-id="21ded-122">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="21ded-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
