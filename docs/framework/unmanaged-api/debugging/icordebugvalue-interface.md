---
title: ICorDebugValue Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue
helpviewer_keywords:
- ICorDebugValue interface [.NET Framework debugging]
ms.assetid: b2f7007f-c446-4b18-aed1-a25cff8aee31
topic_type:
- apiref
ms.openlocfilehash: b8d2e49031e59db0527de3c848d7d390095797bf
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396785"
---
# <a name="icordebugvalue-interface"></a><span data-ttu-id="3af99-102">ICorDebugValue Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3af99-102">ICorDebugValue Interface</span></span>
<span data-ttu-id="3af99-103">Hata ayıklanan işlemdeki bir değeri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3af99-103">Represents a value in the process being debugged.</span></span> <span data-ttu-id="3af99-104">Değer bir okuma veya yazma değeri olabilir.</span><span class="sxs-lookup"><span data-stu-id="3af99-104">The value can be a read or a write value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3af99-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="3af99-105">Methods</span></span>  
  
|<span data-ttu-id="3af99-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="3af99-106">Method</span></span>|<span data-ttu-id="3af99-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3af99-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3af99-108">CreateBreakpoint Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3af99-108">CreateBreakpoint Method</span></span>](icordebugvalue-createbreakpoint-method.md)|<span data-ttu-id="3af99-109">Bu yöntem şu anda uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="3af99-109">This method is not currently implemented.</span></span>|  
|[<span data-ttu-id="3af99-110">GetAddress Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3af99-110">GetAddress Method</span></span>](icordebugvalue-getaddress-method.md)|<span data-ttu-id="3af99-111">Bu `ICorDebugValue` nesnenin, hata ayıklama sürecinde olan adresini alır.</span><span class="sxs-lookup"><span data-stu-id="3af99-111">Gets the address of this `ICorDebugValue` object, which is in the process of being debugged.</span></span>|  
|[<span data-ttu-id="3af99-112">GetSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3af99-112">GetSize Method</span></span>](icordebugvalue-getsize-method.md)|<span data-ttu-id="3af99-113">Bu nesnenin boyutunu bayt cinsinden alır `ICorDebugValue` .</span><span class="sxs-lookup"><span data-stu-id="3af99-113">Gets the size, in bytes, of this `ICorDebugValue` object.</span></span>|  
|[<span data-ttu-id="3af99-114">GetType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3af99-114">GetType Method</span></span>](icordebugvalue-gettype-method.md)|<span data-ttu-id="3af99-115">Bu nesnenin temel türünü alır `ICorDebugValue` .</span><span class="sxs-lookup"><span data-stu-id="3af99-115">Gets the primitive type of this `ICorDebugValue` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3af99-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3af99-116">Remarks</span></span>  
 <span data-ttu-id="3af99-117">Genel olarak, bir değer nesnesinin sahipliği döndürüldüğünde geçirilir.</span><span class="sxs-lookup"><span data-stu-id="3af99-117">In general, ownership of a value object is passed when it is returned.</span></span> <span data-ttu-id="3af99-118">Alıcı, nesne ile işiniz bittiğinde nesneden bir başvuruyu kaldırmaktan sorumludur.</span><span class="sxs-lookup"><span data-stu-id="3af99-118">The recipient is responsible for removing a reference from the object when it is finished with the object.</span></span>  
  
 <span data-ttu-id="3af99-119">Değerin nereden alındığına bağlı olarak, işlem sürdürülmeden sonra değer geçerli kalmayabilir.</span><span class="sxs-lookup"><span data-stu-id="3af99-119">Depending on where the value was retrieved from, the value may not remain valid after the process is resumed.</span></span> <span data-ttu-id="3af99-120">Bu nedenle, genellikle değer [ICorDebugController:: Continue](icordebugcontroller-continue-method.md) yönteminin bir çağrısında tutulmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="3af99-120">So, in general, the value shouldn't be held across a call of the [ICorDebugController::Continue](icordebugcontroller-continue-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3af99-121">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="3af99-121">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3af99-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3af99-122">Requirements</span></span>  
 <span data-ttu-id="3af99-123">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3af99-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3af99-124">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="3af99-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3af99-125">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="3af99-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3af99-126">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3af99-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3af99-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3af99-127">See also</span></span>

- [<span data-ttu-id="3af99-128">ICorDebugValue3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3af99-128">ICorDebugValue3 Interface</span></span>](icordebugvalue3-interface.md)
- [<span data-ttu-id="3af99-129">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="3af99-129">Debugging Interfaces</span></span>](debugging-interfaces.md)
