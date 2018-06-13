---
title: Icordebugfunction2 Interface1
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d765f87e36c98b5f664e84d85b883bc949fccf54
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33415340"
---
# <a name="icordebugfunction2-interface1"></a><span data-ttu-id="8e4aa-102">Icordebugfunction2 Interface1</span><span class="sxs-lookup"><span data-stu-id="8e4aa-102">ICorDebugFunction2 Interface1</span></span>
<span data-ttu-id="8e4aa-103">Mantıksal olarak hangi kullanıcı olmayan kod atlar sadece kendi kodumu adımla için hata ayıklama, destek sağlamak için ICorDebugFunction arabirimi genişletir.</span><span class="sxs-lookup"><span data-stu-id="8e4aa-103">Logically extends the ICorDebugFunction interface to provide support for Just My Code step-through debugging, which skips non-user code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8e4aa-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="8e4aa-104">Methods</span></span>  
  
|<span data-ttu-id="8e4aa-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="8e4aa-105">Method</span></span>|<span data-ttu-id="8e4aa-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8e4aa-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8e4aa-107">EnumerateNativeCode Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8e4aa-107">EnumerateNativeCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-enumeratenativecode-method.md)|<span data-ttu-id="8e4aa-108">(Henüz uygulanmadı.) Bu Icordebugfunction2 nesnesi tarafından başvurulan işlev yerel kod deyimlerinde içeren bir Icordebugcodeenum için bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="8e4aa-108">(Not yet implemented.) Gets an interface pointer to an ICorDebugCodeEnum that contains the native code statements in the function referenced by this ICorDebugFunction2 object.</span></span>|  
|[<span data-ttu-id="8e4aa-109">GetJMCStatus Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8e4aa-109">GetJMCStatus Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-getjmcstatus-method.md)|<span data-ttu-id="8e4aa-110">Bu işlev kullanıcı kodu olarak işaretlenmiş olup olmadığını belirten bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="8e4aa-110">Gets a value that indicates whether this function is marked as user code.</span></span>|  
|[<span data-ttu-id="8e4aa-111">GetVersionNumber Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8e4aa-111">GetVersionNumber Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-getversionnumber-method.md)|<span data-ttu-id="8e4aa-112">Bu işlev Düzenle ve devam et sürümünü alır.</span><span class="sxs-lookup"><span data-stu-id="8e4aa-112">Gets the Edit and Continue version of this function.</span></span>|  
|[<span data-ttu-id="8e4aa-113">SetJMCStatus Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8e4aa-113">SetJMCStatus Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-setjmcstatus-method.md)|<span data-ttu-id="8e4aa-114">Bu işlev sadece kendi kodumu işaretler atlama.</span><span class="sxs-lookup"><span data-stu-id="8e4aa-114">Marks this function for Just My Code stepping.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8e4aa-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8e4aa-115">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8e4aa-116">Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="8e4aa-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8e4aa-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8e4aa-117">Requirements</span></span>  
 <span data-ttu-id="8e4aa-118">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8e4aa-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8e4aa-119">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8e4aa-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8e4aa-120">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8e4aa-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8e4aa-121">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8e4aa-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e4aa-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8e4aa-122">See Also</span></span>  
 [<span data-ttu-id="8e4aa-123">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="8e4aa-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
