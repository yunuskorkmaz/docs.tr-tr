---
description: ': ICorDebugValue arabirimi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: cae8fdef5c1c49cbabc25d3d547cb5748a9eeee1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99690322"
---
# <a name="icordebugvalue-interface"></a><span data-ttu-id="a389f-103">ICorDebugValue Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a389f-103">ICorDebugValue Interface</span></span>

<span data-ttu-id="a389f-104">Hata ayıklanan işlemdeki bir değeri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a389f-104">Represents a value in the process being debugged.</span></span> <span data-ttu-id="a389f-105">Değer bir okuma veya yazma değeri olabilir.</span><span class="sxs-lookup"><span data-stu-id="a389f-105">The value can be a read or a write value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a389f-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="a389f-106">Methods</span></span>  
  
|<span data-ttu-id="a389f-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="a389f-107">Method</span></span>|<span data-ttu-id="a389f-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a389f-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a389f-109">CreateBreakpoint Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a389f-109">CreateBreakpoint Method</span></span>](icordebugvalue-createbreakpoint-method.md)|<span data-ttu-id="a389f-110">Bu yöntem şu anda uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="a389f-110">This method is not currently implemented.</span></span>|  
|[<span data-ttu-id="a389f-111">GetAddress Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a389f-111">GetAddress Method</span></span>](icordebugvalue-getaddress-method.md)|<span data-ttu-id="a389f-112">Bu `ICorDebugValue` nesnenin, hata ayıklama sürecinde olan adresini alır.</span><span class="sxs-lookup"><span data-stu-id="a389f-112">Gets the address of this `ICorDebugValue` object, which is in the process of being debugged.</span></span>|  
|[<span data-ttu-id="a389f-113">GetSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a389f-113">GetSize Method</span></span>](icordebugvalue-getsize-method.md)|<span data-ttu-id="a389f-114">Bu nesnenin boyutunu bayt cinsinden alır `ICorDebugValue` .</span><span class="sxs-lookup"><span data-stu-id="a389f-114">Gets the size, in bytes, of this `ICorDebugValue` object.</span></span>|  
|[<span data-ttu-id="a389f-115">GetType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a389f-115">GetType Method</span></span>](icordebugvalue-gettype-method.md)|<span data-ttu-id="a389f-116">Bu nesnenin temel türünü alır `ICorDebugValue` .</span><span class="sxs-lookup"><span data-stu-id="a389f-116">Gets the primitive type of this `ICorDebugValue` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a389f-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a389f-117">Remarks</span></span>  

 <span data-ttu-id="a389f-118">Genel olarak, bir değer nesnesinin sahipliği döndürüldüğünde geçirilir.</span><span class="sxs-lookup"><span data-stu-id="a389f-118">In general, ownership of a value object is passed when it is returned.</span></span> <span data-ttu-id="a389f-119">Alıcı, nesne ile işiniz bittiğinde nesneden bir başvuruyu kaldırmaktan sorumludur.</span><span class="sxs-lookup"><span data-stu-id="a389f-119">The recipient is responsible for removing a reference from the object when it is finished with the object.</span></span>  
  
 <span data-ttu-id="a389f-120">Değerin nereden alındığına bağlı olarak, işlem sürdürülmeden sonra değer geçerli kalmayabilir.</span><span class="sxs-lookup"><span data-stu-id="a389f-120">Depending on where the value was retrieved from, the value may not remain valid after the process is resumed.</span></span> <span data-ttu-id="a389f-121">Bu nedenle, genellikle değer [ICorDebugController:: Continue](icordebugcontroller-continue-method.md) yönteminin bir çağrısında tutulmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="a389f-121">So, in general, the value shouldn't be held across a call of the [ICorDebugController::Continue](icordebugcontroller-continue-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a389f-122">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="a389f-122">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a389f-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a389f-123">Requirements</span></span>  

 <span data-ttu-id="a389f-124">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a389f-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a389f-125">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a389f-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a389f-126">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a389f-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a389f-127">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a389f-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a389f-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a389f-128">See also</span></span>

- [<span data-ttu-id="a389f-129">ICorDebugValue3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a389f-129">ICorDebugValue3 Interface</span></span>](icordebugvalue3-interface.md)
- [<span data-ttu-id="a389f-130">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a389f-130">Debugging Interfaces</span></span>](debugging-interfaces.md)
