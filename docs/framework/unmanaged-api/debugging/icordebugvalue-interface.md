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
ms.openlocfilehash: 7d3c35ed6cda637e3b885afe089ddfa590d51076
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95683621"
---
# <a name="icordebugvalue-interface"></a><span data-ttu-id="61b45-102">ICorDebugValue Arabirimi</span><span class="sxs-lookup"><span data-stu-id="61b45-102">ICorDebugValue Interface</span></span>

<span data-ttu-id="61b45-103">Hata ayıklanan işlemdeki bir değeri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="61b45-103">Represents a value in the process being debugged.</span></span> <span data-ttu-id="61b45-104">Değer bir okuma veya yazma değeri olabilir.</span><span class="sxs-lookup"><span data-stu-id="61b45-104">The value can be a read or a write value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="61b45-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="61b45-105">Methods</span></span>  
  
|<span data-ttu-id="61b45-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="61b45-106">Method</span></span>|<span data-ttu-id="61b45-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="61b45-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="61b45-108">CreateBreakpoint Yöntemi</span><span class="sxs-lookup"><span data-stu-id="61b45-108">CreateBreakpoint Method</span></span>](icordebugvalue-createbreakpoint-method.md)|<span data-ttu-id="61b45-109">Bu yöntem şu anda uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="61b45-109">This method is not currently implemented.</span></span>|  
|[<span data-ttu-id="61b45-110">GetAddress Yöntemi</span><span class="sxs-lookup"><span data-stu-id="61b45-110">GetAddress Method</span></span>](icordebugvalue-getaddress-method.md)|<span data-ttu-id="61b45-111">Bu `ICorDebugValue` nesnenin, hata ayıklama sürecinde olan adresini alır.</span><span class="sxs-lookup"><span data-stu-id="61b45-111">Gets the address of this `ICorDebugValue` object, which is in the process of being debugged.</span></span>|  
|[<span data-ttu-id="61b45-112">GetSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="61b45-112">GetSize Method</span></span>](icordebugvalue-getsize-method.md)|<span data-ttu-id="61b45-113">Bu nesnenin boyutunu bayt cinsinden alır `ICorDebugValue` .</span><span class="sxs-lookup"><span data-stu-id="61b45-113">Gets the size, in bytes, of this `ICorDebugValue` object.</span></span>|  
|[<span data-ttu-id="61b45-114">GetType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="61b45-114">GetType Method</span></span>](icordebugvalue-gettype-method.md)|<span data-ttu-id="61b45-115">Bu nesnenin temel türünü alır `ICorDebugValue` .</span><span class="sxs-lookup"><span data-stu-id="61b45-115">Gets the primitive type of this `ICorDebugValue` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="61b45-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="61b45-116">Remarks</span></span>  

 <span data-ttu-id="61b45-117">Genel olarak, bir değer nesnesinin sahipliği döndürüldüğünde geçirilir.</span><span class="sxs-lookup"><span data-stu-id="61b45-117">In general, ownership of a value object is passed when it is returned.</span></span> <span data-ttu-id="61b45-118">Alıcı, nesne ile işiniz bittiğinde nesneden bir başvuruyu kaldırmaktan sorumludur.</span><span class="sxs-lookup"><span data-stu-id="61b45-118">The recipient is responsible for removing a reference from the object when it is finished with the object.</span></span>  
  
 <span data-ttu-id="61b45-119">Değerin nereden alındığına bağlı olarak, işlem sürdürülmeden sonra değer geçerli kalmayabilir.</span><span class="sxs-lookup"><span data-stu-id="61b45-119">Depending on where the value was retrieved from, the value may not remain valid after the process is resumed.</span></span> <span data-ttu-id="61b45-120">Bu nedenle, genellikle değer [ICorDebugController:: Continue](icordebugcontroller-continue-method.md) yönteminin bir çağrısında tutulmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="61b45-120">So, in general, the value shouldn't be held across a call of the [ICorDebugController::Continue](icordebugcontroller-continue-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="61b45-121">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="61b45-121">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="61b45-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="61b45-122">Requirements</span></span>  

 <span data-ttu-id="61b45-123">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="61b45-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61b45-124">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="61b45-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="61b45-125">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="61b45-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="61b45-126">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="61b45-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61b45-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="61b45-127">See also</span></span>

- [<span data-ttu-id="61b45-128">ICorDebugValue3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="61b45-128">ICorDebugValue3 Interface</span></span>](icordebugvalue3-interface.md)
- [<span data-ttu-id="61b45-129">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="61b45-129">Debugging Interfaces</span></span>](debugging-interfaces.md)
