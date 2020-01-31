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
ms.openlocfilehash: e1044386bd6251132703c4e98a0cf2ed267d34e0
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791144"
---
# <a name="icordebugvalue-interface"></a><span data-ttu-id="761cc-102">ICorDebugValue Arabirimi</span><span class="sxs-lookup"><span data-stu-id="761cc-102">ICorDebugValue Interface</span></span>
<span data-ttu-id="761cc-103">Hata ayıklanan işlemdeki bir değeri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="761cc-103">Represents a value in the process being debugged.</span></span> <span data-ttu-id="761cc-104">Değer bir okuma veya yazma değeri olabilir.</span><span class="sxs-lookup"><span data-stu-id="761cc-104">The value can be a read or a write value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="761cc-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="761cc-105">Methods</span></span>  
  
|<span data-ttu-id="761cc-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="761cc-106">Method</span></span>|<span data-ttu-id="761cc-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="761cc-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="761cc-108">CreateBreakpoint Yöntemi</span><span class="sxs-lookup"><span data-stu-id="761cc-108">CreateBreakpoint Method</span></span>](icordebugvalue-createbreakpoint-method.md)|<span data-ttu-id="761cc-109">Bu yöntem şu anda uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="761cc-109">This method is not currently implemented.</span></span>|  
|[<span data-ttu-id="761cc-110">GetAddress Yöntemi</span><span class="sxs-lookup"><span data-stu-id="761cc-110">GetAddress Method</span></span>](icordebugvalue-getaddress-method.md)|<span data-ttu-id="761cc-111">Bu `ICorDebugValue` nesnesinin, hata ayıklama sürecinde olan adresini alır.</span><span class="sxs-lookup"><span data-stu-id="761cc-111">Gets the address of this `ICorDebugValue` object, which is in the process of being debugged.</span></span>|  
|[<span data-ttu-id="761cc-112">GetSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="761cc-112">GetSize Method</span></span>](icordebugvalue-getsize-method.md)|<span data-ttu-id="761cc-113">Bu `ICorDebugValue` nesnesinin bayt cinsinden boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="761cc-113">Gets the size, in bytes, of this `ICorDebugValue` object.</span></span>|  
|[<span data-ttu-id="761cc-114">GetType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="761cc-114">GetType Method</span></span>](icordebugvalue-gettype-method.md)|<span data-ttu-id="761cc-115">Bu `ICorDebugValue` nesnesinin temel türünü alır.</span><span class="sxs-lookup"><span data-stu-id="761cc-115">Gets the primitive type of this `ICorDebugValue` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="761cc-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="761cc-116">Remarks</span></span>  
 <span data-ttu-id="761cc-117">Genel olarak, bir değer nesnesinin sahipliği döndürüldüğünde geçirilir.</span><span class="sxs-lookup"><span data-stu-id="761cc-117">In general, ownership of a value object is passed when it is returned.</span></span> <span data-ttu-id="761cc-118">Alıcı, nesne ile işiniz bittiğinde nesneden bir başvuruyu kaldırmaktan sorumludur.</span><span class="sxs-lookup"><span data-stu-id="761cc-118">The recipient is responsible for removing a reference from the object when it is finished with the object.</span></span>  
  
 <span data-ttu-id="761cc-119">Değerin nereden alındığına bağlı olarak, işlem sürdürülmeden sonra değer geçerli kalmayabilir.</span><span class="sxs-lookup"><span data-stu-id="761cc-119">Depending on where the value was retrieved from, the value may not remain valid after the process is resumed.</span></span> <span data-ttu-id="761cc-120">Bu nedenle, genellikle değer [ICorDebugController:: Continue](icordebugcontroller-continue-method.md) yönteminin bir çağrısında tutulmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="761cc-120">So, in general, the value shouldn't be held across a call of the [ICorDebugController::Continue](icordebugcontroller-continue-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="761cc-121">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="761cc-121">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="761cc-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="761cc-122">Requirements</span></span>  
 <span data-ttu-id="761cc-123">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="761cc-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="761cc-124">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="761cc-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="761cc-125">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="761cc-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="761cc-126">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="761cc-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="761cc-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="761cc-127">See also</span></span>

- [<span data-ttu-id="761cc-128">ICorDebugValue3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="761cc-128">ICorDebugValue3 Interface</span></span>](icordebugvalue3-interface.md)
- [<span data-ttu-id="761cc-129">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="761cc-129">Debugging Interfaces</span></span>](debugging-interfaces.md)
