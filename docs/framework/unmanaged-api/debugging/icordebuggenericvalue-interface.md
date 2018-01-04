---
title: Icordebuggenericvalue Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugGenericValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugGenericValue
helpviewer_keywords: ICorDebugGenericValue interface [.NET Framework debugging]
ms.assetid: bc14f408-b359-4c8c-ade2-888ccdf7261b
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d6c6fb4893edf0bcda9d6f7ddbeea7054f5b4fd5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebuggenericvalue-interface1"></a><span data-ttu-id="185cf-102">Icordebuggenericvalue Interface1</span><span class="sxs-lookup"><span data-stu-id="185cf-102">ICorDebugGenericValue Interface1</span></span>
<span data-ttu-id="185cf-103">"Tüm değerleri uygular Icordebugvalue" sınıfıdır.</span><span class="sxs-lookup"><span data-stu-id="185cf-103">A subclass of "ICorDebugValue" that applies to all values.</span></span> <span data-ttu-id="185cf-104">Bu arabirim, değer için Alma ve Ayarlama yöntemlerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="185cf-104">This interface provides Get and Set methods for the value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="185cf-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="185cf-105">Methods</span></span>  
  
|<span data-ttu-id="185cf-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="185cf-106">Method</span></span>|<span data-ttu-id="185cf-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="185cf-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="185cf-108">GetValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="185cf-108">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-getvalue-method.md)|<span data-ttu-id="185cf-109">Değeri belirtilen arabelleğe kopyalar.</span><span class="sxs-lookup"><span data-stu-id="185cf-109">Copies the value into the specified buffer.</span></span>|  
|[<span data-ttu-id="185cf-110">SetValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="185cf-110">SetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-setvalue-method.md)|<span data-ttu-id="185cf-111">Yeni bir değer belirtilen arabelleğinden kopyalar.</span><span class="sxs-lookup"><span data-stu-id="185cf-111">Copies a new value from the specified buffer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="185cf-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="185cf-112">Remarks</span></span>  
 <span data-ttu-id="185cf-113">`ICorDebugGenericValue`Uzaktan erişilebilir olmayan olduğu için alt arabirimidir.</span><span class="sxs-lookup"><span data-stu-id="185cf-113">`ICorDebugGenericValue` is a sub-interface because it is non-remotable.</span></span>  
  
 <span data-ttu-id="185cf-114">Referans türleri için başvuru içeriğini yerine başvuru değerdir.</span><span class="sxs-lookup"><span data-stu-id="185cf-114">For reference types, the value is the reference rather than the contents of the reference.</span></span>  
  
 <span data-ttu-id="185cf-115">Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="185cf-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="185cf-116">Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="185cf-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="185cf-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="185cf-117">Requirements</span></span>  
 <span data-ttu-id="185cf-118">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="185cf-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="185cf-119">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="185cf-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="185cf-120">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="185cf-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="185cf-121">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="185cf-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="185cf-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="185cf-122">See Also</span></span>  
    
 [<span data-ttu-id="185cf-123">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="185cf-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
