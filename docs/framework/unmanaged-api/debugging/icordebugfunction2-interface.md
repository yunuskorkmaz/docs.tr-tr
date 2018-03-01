---
title: Icordebugfunction2 Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugFunction2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction2
helpviewer_keywords:
- ICorDebugFunction2 interface [.NET Framework debugging]
ms.assetid: 2b936bef-9b75-48bf-859f-42e419c65f1c
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7ac3a4cd5ec2aff1b60cd51ca33d411e5cc81eb1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugfunction2-interface1"></a><span data-ttu-id="b9dc4-102">Icordebugfunction2 Interface1</span><span class="sxs-lookup"><span data-stu-id="b9dc4-102">ICorDebugFunction2 Interface1</span></span>
<span data-ttu-id="b9dc4-103">Mantıksal olarak hangi kullanıcı olmayan kod atlar sadece kendi kodumu adımla için hata ayıklama, destek sağlamak için ICorDebugFunction arabirimi genişletir.</span><span class="sxs-lookup"><span data-stu-id="b9dc4-103">Logically extends the ICorDebugFunction interface to provide support for Just My Code step-through debugging, which skips non-user code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b9dc4-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="b9dc4-104">Methods</span></span>  
  
|<span data-ttu-id="b9dc4-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="b9dc4-105">Method</span></span>|<span data-ttu-id="b9dc4-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b9dc4-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b9dc4-107">EnumerateNativeCode Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b9dc4-107">EnumerateNativeCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-enumeratenativecode-method.md)|<span data-ttu-id="b9dc4-108">(Henüz uygulanmadı.) Bu Icordebugfunction2 nesnesi tarafından başvurulan işlev yerel kod deyimlerinde içeren bir Icordebugcodeenum için bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="b9dc4-108">(Not yet implemented.) Gets an interface pointer to an ICorDebugCodeEnum that contains the native code statements in the function referenced by this ICorDebugFunction2 object.</span></span>|  
|[<span data-ttu-id="b9dc4-109">GetJMCStatus Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b9dc4-109">GetJMCStatus Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-getjmcstatus-method.md)|<span data-ttu-id="b9dc4-110">Bu işlev kullanıcı kodu olarak işaretlenmiş olup olmadığını belirten bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="b9dc4-110">Gets a value that indicates whether this function is marked as user code.</span></span>|  
|[<span data-ttu-id="b9dc4-111">GetVersionNumber Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b9dc4-111">GetVersionNumber Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-getversionnumber-method.md)|<span data-ttu-id="b9dc4-112">Bu işlev Düzenle ve devam et sürümünü alır.</span><span class="sxs-lookup"><span data-stu-id="b9dc4-112">Gets the Edit and Continue version of this function.</span></span>|  
|[<span data-ttu-id="b9dc4-113">SetJMCStatus Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b9dc4-113">SetJMCStatus Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-setjmcstatus-method.md)|<span data-ttu-id="b9dc4-114">Bu işlev sadece kendi kodumu işaretler atlama.</span><span class="sxs-lookup"><span data-stu-id="b9dc4-114">Marks this function for Just My Code stepping.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b9dc4-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b9dc4-115">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b9dc4-116">Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="b9dc4-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9dc4-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b9dc4-117">Requirements</span></span>  
 <span data-ttu-id="b9dc4-118">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b9dc4-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9dc4-119">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b9dc4-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b9dc4-120">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b9dc4-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b9dc4-121">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b9dc4-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9dc4-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b9dc4-122">See Also</span></span>  
 [<span data-ttu-id="b9dc4-123">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="b9dc4-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
