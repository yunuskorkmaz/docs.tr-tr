---
title: Icordebuggenericvalue arabirimi1
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
ms.openlocfilehash: ce4c1b73ab806958627bb68bfdcfcae890bc5e67
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54709838"
---
# <a name="icordebuggenericvalue-interface1"></a><span data-ttu-id="66a65-102">Icordebuggenericvalue arabirimi1</span><span class="sxs-lookup"><span data-stu-id="66a65-102">ICorDebugGenericValue Interface1</span></span>
<span data-ttu-id="66a65-103">"Tüm değerlere uygulanır Icordebugvalue" öğesinin.</span><span class="sxs-lookup"><span data-stu-id="66a65-103">A subclass of "ICorDebugValue" that applies to all values.</span></span> <span data-ttu-id="66a65-104">Bu arabirim, değer için Alma ve Ayarlama yöntemlerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="66a65-104">This interface provides Get and Set methods for the value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="66a65-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="66a65-105">Methods</span></span>  
  
|<span data-ttu-id="66a65-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="66a65-106">Method</span></span>|<span data-ttu-id="66a65-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="66a65-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="66a65-108">GetValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="66a65-108">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-getvalue-method.md)|<span data-ttu-id="66a65-109">Değeri belirtilen arabelleğe kopyalar.</span><span class="sxs-lookup"><span data-stu-id="66a65-109">Copies the value into the specified buffer.</span></span>|  
|[<span data-ttu-id="66a65-110">SetValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="66a65-110">SetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-setvalue-method.md)|<span data-ttu-id="66a65-111">Yeni bir değer belirtilen arabellek kopyalar.</span><span class="sxs-lookup"><span data-stu-id="66a65-111">Copies a new value from the specified buffer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="66a65-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="66a65-112">Remarks</span></span>  
 <span data-ttu-id="66a65-113">`ICorDebugGenericValue` erişilemeyen olduğu için alt arabirimidir.</span><span class="sxs-lookup"><span data-stu-id="66a65-113">`ICorDebugGenericValue` is a sub-interface because it is non-remotable.</span></span>  
  
 <span data-ttu-id="66a65-114">Başvuru türleri için başvuru içeriği yerine başvuru değerdir.</span><span class="sxs-lookup"><span data-stu-id="66a65-114">For reference types, the value is the reference rather than the contents of the reference.</span></span>  
  
 <span data-ttu-id="66a65-115">Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="66a65-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="66a65-116">Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="66a65-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66a65-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="66a65-117">Requirements</span></span>  
 <span data-ttu-id="66a65-118">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="66a65-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66a65-119">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="66a65-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="66a65-120">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="66a65-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="66a65-121">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66a65-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66a65-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="66a65-122">See also</span></span>

- [<span data-ttu-id="66a65-123">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="66a65-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
