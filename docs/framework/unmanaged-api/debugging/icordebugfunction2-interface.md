---
title: Icordebugfunction2 Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFunction2
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugFunction2
helpviewer_keywords: ICorDebugFunction2 interface [.NET Framework debugging]
ms.assetid: 2b936bef-9b75-48bf-859f-42e419c65f1c
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4c2806003e06d00a492568d1e2d86add66b5f0ee
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugfunction2-interface1"></a><span data-ttu-id="ffb88-102">Icordebugfunction2 Interface1</span><span class="sxs-lookup"><span data-stu-id="ffb88-102">ICorDebugFunction2 Interface1</span></span>
<span data-ttu-id="ffb88-103">Mantıksal olarak hangi kullanıcı olmayan kod atlar sadece kendi kodumu adımla için hata ayıklama, destek sağlamak için ICorDebugFunction arabirimi genişletir.</span><span class="sxs-lookup"><span data-stu-id="ffb88-103">Logically extends the ICorDebugFunction interface to provide support for Just My Code step-through debugging, which skips non-user code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ffb88-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="ffb88-104">Methods</span></span>  
  
|<span data-ttu-id="ffb88-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="ffb88-105">Method</span></span>|<span data-ttu-id="ffb88-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ffb88-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ffb88-107">EnumerateNativeCode yöntemi</span><span class="sxs-lookup"><span data-stu-id="ffb88-107">EnumerateNativeCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-enumeratenativecode-method.md)|<span data-ttu-id="ffb88-108">(Henüz uygulanmadı.) Bu Icordebugfunction2 nesnesi tarafından başvurulan işlev yerel kod deyimlerinde içeren bir Icordebugcodeenum için bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="ffb88-108">(Not yet implemented.) Gets an interface pointer to an ICorDebugCodeEnum that contains the native code statements in the function referenced by this ICorDebugFunction2 object.</span></span>|  
|[<span data-ttu-id="ffb88-109">GetJMCStatus yöntemi</span><span class="sxs-lookup"><span data-stu-id="ffb88-109">GetJMCStatus Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-getjmcstatus-method.md)|<span data-ttu-id="ffb88-110">Bu işlev kullanıcı kodu olarak işaretlenmiş olup olmadığını belirten bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="ffb88-110">Gets a value that indicates whether this function is marked as user code.</span></span>|  
|[<span data-ttu-id="ffb88-111">GetVersionNumber yöntemi</span><span class="sxs-lookup"><span data-stu-id="ffb88-111">GetVersionNumber Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-getversionnumber-method.md)|<span data-ttu-id="ffb88-112">Bu işlev Düzenle ve devam et sürümünü alır.</span><span class="sxs-lookup"><span data-stu-id="ffb88-112">Gets the Edit and Continue version of this function.</span></span>|  
|[<span data-ttu-id="ffb88-113">SetJMCStatus yöntemi</span><span class="sxs-lookup"><span data-stu-id="ffb88-113">SetJMCStatus Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-setjmcstatus-method.md)|<span data-ttu-id="ffb88-114">Bu işlev sadece kendi kodumu işaretler atlama.</span><span class="sxs-lookup"><span data-stu-id="ffb88-114">Marks this function for Just My Code stepping.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ffb88-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ffb88-115">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ffb88-116">Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="ffb88-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ffb88-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ffb88-117">Requirements</span></span>  
 <span data-ttu-id="ffb88-118">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ffb88-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ffb88-119">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ffb88-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ffb88-120">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ffb88-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ffb88-121">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ffb88-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffb88-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ffb88-122">See Also</span></span>  
 [<span data-ttu-id="ffb88-123">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ffb88-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
