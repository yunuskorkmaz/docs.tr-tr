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
ms.openlocfilehash: 406468fc6e2b68e8c8e1dfbd0f0f18cce3f013ab
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794451"
---
# <a name="icordebughandlevalue-interface"></a><span data-ttu-id="ea15a-102">ICorDebugHandleValue Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ea15a-102">ICorDebugHandleValue Interface</span></span>

<span data-ttu-id="ea15a-103">Hata ayıklayıcının çöp toplama için bir tanıtıcı oluşturduğu bir başvuru değerini temsil eden ICorDebugReferenceValue öğesinin bir alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="ea15a-103">A subclass of ICorDebugReferenceValue that represents a reference value to which the debugger has created a handle for garbage collection.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ea15a-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="ea15a-104">Methods</span></span>  
  
|<span data-ttu-id="ea15a-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="ea15a-105">Method</span></span>|<span data-ttu-id="ea15a-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ea15a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ea15a-107">Dispose Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ea15a-107">Dispose Method</span></span>](icordebughandlevalue-dispose-method.md)|<span data-ttu-id="ea15a-108">Arabirim işaretçisini açıkça serbest bırakmadan bu `ICorDebugHandleValue` nesnesi tarafından başvurulan tanıtıcıyı serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="ea15a-108">Releases the handle referenced by this `ICorDebugHandleValue` object without explicitly releasing the interface pointer.</span></span>|  
|[<span data-ttu-id="ea15a-109">GetHandleType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ea15a-109">GetHandleType Method</span></span>](icordebughandlevalue-gethandletype-method.md)|<span data-ttu-id="ea15a-110">Bu `ICorDebugHandleValue`başvurduğu tanıtıcı türünü açıklayan bir Corıı Ghandlitype değeri alır.</span><span class="sxs-lookup"><span data-stu-id="ea15a-110">Gets a CorDebugHandleType value that describes the kind of handle referenced by this `ICorDebugHandleValue`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ea15a-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ea15a-111">Remarks</span></span>  
 <span data-ttu-id="ea15a-112">`ICorDebugReferenceValue` nesnesi, hata ayıklama kodunun yürütülmesindeki bir kesme tarafından geçersiz kılınır.</span><span class="sxs-lookup"><span data-stu-id="ea15a-112">An `ICorDebugReferenceValue` object is invalidated by a break in the execution of debugged code.</span></span> <span data-ttu-id="ea15a-113">`ICorDebugHandleValue`, açıkça yayınlanana kadar kesmeler ve devamlılıklar aracılığıyla başvurusunu tutar.</span><span class="sxs-lookup"><span data-stu-id="ea15a-113">An `ICorDebugHandleValue` maintains its reference through breaks and continuations, until it is explicitly released.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ea15a-114">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="ea15a-114">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea15a-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ea15a-115">Requirements</span></span>  
 <span data-ttu-id="ea15a-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ea15a-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea15a-117">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ea15a-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ea15a-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ea15a-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ea15a-119">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea15a-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea15a-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ea15a-120">See also</span></span>

- [<span data-ttu-id="ea15a-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ea15a-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
