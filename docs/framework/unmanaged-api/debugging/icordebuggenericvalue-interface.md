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
ms.openlocfilehash: 61c159e30efb33dca4043e5b5306c9544acd614a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebuggenericvalue-interface1"></a><span data-ttu-id="92efe-102">Icordebuggenericvalue Interface1</span><span class="sxs-lookup"><span data-stu-id="92efe-102">ICorDebugGenericValue Interface1</span></span>
<span data-ttu-id="92efe-103">"Tüm değerleri uygular Icordebugvalue" sınıfıdır.</span><span class="sxs-lookup"><span data-stu-id="92efe-103">A subclass of "ICorDebugValue" that applies to all values.</span></span> <span data-ttu-id="92efe-104">Bu arabirim, değer için Alma ve Ayarlama yöntemlerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="92efe-104">This interface provides Get and Set methods for the value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="92efe-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="92efe-105">Methods</span></span>  
  
|<span data-ttu-id="92efe-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="92efe-106">Method</span></span>|<span data-ttu-id="92efe-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="92efe-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="92efe-108">GetValue yöntemi</span><span class="sxs-lookup"><span data-stu-id="92efe-108">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-getvalue-method.md)|<span data-ttu-id="92efe-109">Değeri belirtilen arabelleğe kopyalar.</span><span class="sxs-lookup"><span data-stu-id="92efe-109">Copies the value into the specified buffer.</span></span>|  
|[<span data-ttu-id="92efe-110">SetValue yöntemi</span><span class="sxs-lookup"><span data-stu-id="92efe-110">SetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-setvalue-method.md)|<span data-ttu-id="92efe-111">Yeni bir değer belirtilen arabelleğinden kopyalar.</span><span class="sxs-lookup"><span data-stu-id="92efe-111">Copies a new value from the specified buffer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="92efe-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="92efe-112">Remarks</span></span>  
 <span data-ttu-id="92efe-113">`ICorDebugGenericValue`Uzaktan erişilebilir olmayan olduğu için alt arabirimidir.</span><span class="sxs-lookup"><span data-stu-id="92efe-113">`ICorDebugGenericValue` is a sub-interface because it is non-remotable.</span></span>  
  
 <span data-ttu-id="92efe-114">Referans türleri için başvuru içeriğini yerine başvuru değerdir.</span><span class="sxs-lookup"><span data-stu-id="92efe-114">For reference types, the value is the reference rather than the contents of the reference.</span></span>  
  
 <span data-ttu-id="92efe-115">Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="92efe-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="92efe-116">Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="92efe-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92efe-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="92efe-117">Requirements</span></span>  
 <span data-ttu-id="92efe-118">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92efe-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92efe-119">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="92efe-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="92efe-120">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="92efe-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="92efe-121">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92efe-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92efe-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="92efe-122">See Also</span></span>  
    
 [<span data-ttu-id="92efe-123">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="92efe-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
