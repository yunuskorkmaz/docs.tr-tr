---
title: Icordebuggenericvalue Interface1
ms.date: 03/30/2017
api_name:
- ICorDebugGenericValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGenericValue
helpviewer_keywords:
- ICorDebugGenericValue interface [.NET Framework debugging]
ms.assetid: bc14f408-b359-4c8c-ade2-888ccdf7261b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0081f020da673023e2c35f9599e9682215e2c9d4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33415070"
---
# <a name="icordebuggenericvalue-interface1"></a><span data-ttu-id="d9bca-102">Icordebuggenericvalue Interface1</span><span class="sxs-lookup"><span data-stu-id="d9bca-102">ICorDebugGenericValue Interface1</span></span>
<span data-ttu-id="d9bca-103">"Tüm değerleri uygular Icordebugvalue" sınıfıdır.</span><span class="sxs-lookup"><span data-stu-id="d9bca-103">A subclass of "ICorDebugValue" that applies to all values.</span></span> <span data-ttu-id="d9bca-104">Bu arabirim, değer için Alma ve Ayarlama yöntemlerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="d9bca-104">This interface provides Get and Set methods for the value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d9bca-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="d9bca-105">Methods</span></span>  
  
|<span data-ttu-id="d9bca-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="d9bca-106">Method</span></span>|<span data-ttu-id="d9bca-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d9bca-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d9bca-108">GetValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d9bca-108">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-getvalue-method.md)|<span data-ttu-id="d9bca-109">Değeri belirtilen arabelleğe kopyalar.</span><span class="sxs-lookup"><span data-stu-id="d9bca-109">Copies the value into the specified buffer.</span></span>|  
|[<span data-ttu-id="d9bca-110">SetValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d9bca-110">SetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-setvalue-method.md)|<span data-ttu-id="d9bca-111">Yeni bir değer belirtilen arabelleğinden kopyalar.</span><span class="sxs-lookup"><span data-stu-id="d9bca-111">Copies a new value from the specified buffer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d9bca-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d9bca-112">Remarks</span></span>  
 <span data-ttu-id="d9bca-113">`ICorDebugGenericValue` Uzaktan erişilebilir olmayan olduğu için alt arabirimidir.</span><span class="sxs-lookup"><span data-stu-id="d9bca-113">`ICorDebugGenericValue` is a sub-interface because it is non-remotable.</span></span>  
  
 <span data-ttu-id="d9bca-114">Referans türleri için başvuru içeriğini yerine başvuru değerdir.</span><span class="sxs-lookup"><span data-stu-id="d9bca-114">For reference types, the value is the reference rather than the contents of the reference.</span></span>  
  
 <span data-ttu-id="d9bca-115">Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="d9bca-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d9bca-116">Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="d9bca-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9bca-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d9bca-117">Requirements</span></span>  
 <span data-ttu-id="d9bca-118">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d9bca-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9bca-119">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d9bca-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d9bca-120">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d9bca-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d9bca-121">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9bca-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9bca-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d9bca-122">See Also</span></span>  
    
 [<span data-ttu-id="d9bca-123">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d9bca-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
