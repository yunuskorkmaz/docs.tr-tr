---
title: ICorDebugFunction2 Arabirimi
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
ms.openlocfilehash: 159cebc76f732629ed84a3b6c9041cc15f8bbb69
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59199381"
---
# <a name="icordebugfunction2-interface"></a><span data-ttu-id="ff2c5-102">ICorDebugFunction2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ff2c5-102">ICorDebugFunction2 Interface</span></span>

<span data-ttu-id="ff2c5-103">Kullanıcı olmayan kod atlar, yalnızca kendi kodum adım adım hata ayıklama için destek sağlamak üzere ICorDebugFunction arabirimi mantıksal olarak genişletir.</span><span class="sxs-lookup"><span data-stu-id="ff2c5-103">Logically extends the ICorDebugFunction interface to provide support for Just My Code step-through debugging, which skips non-user code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ff2c5-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="ff2c5-104">Methods</span></span>  
  
|<span data-ttu-id="ff2c5-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="ff2c5-105">Method</span></span>|<span data-ttu-id="ff2c5-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ff2c5-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ff2c5-107">EnumerateNativeCode Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ff2c5-107">EnumerateNativeCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-enumeratenativecode-method.md)|<span data-ttu-id="ff2c5-108">(Henüz uygulanmadı.) Bu Icordebugfunction2 nesne tarafından başvurulan işlevinde yerel kod deyimlerini içeren bir Icordebugcodeenum için bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="ff2c5-108">(Not yet implemented.) Gets an interface pointer to an ICorDebugCodeEnum that contains the native code statements in the function referenced by this ICorDebugFunction2 object.</span></span>|  
|[<span data-ttu-id="ff2c5-109">GetJMCStatus Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ff2c5-109">GetJMCStatus Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-getjmcstatus-method.md)|<span data-ttu-id="ff2c5-110">Bu işlev, kullanıcı kodu işaretlenmiş olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="ff2c5-110">Gets a value that indicates whether this function is marked as user code.</span></span>|  
|[<span data-ttu-id="ff2c5-111">GetVersionNumber Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ff2c5-111">GetVersionNumber Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-getversionnumber-method.md)|<span data-ttu-id="ff2c5-112">Bu işlev Düzenle ve devam et sürümünü alır.</span><span class="sxs-lookup"><span data-stu-id="ff2c5-112">Gets the Edit and Continue version of this function.</span></span>|  
|[<span data-ttu-id="ff2c5-113">SetJMCStatus Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ff2c5-113">SetJMCStatus Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-setjmcstatus-method.md)|<span data-ttu-id="ff2c5-114">Bu işlev için sadece benim kodumu işaretler Adımlama.</span><span class="sxs-lookup"><span data-stu-id="ff2c5-114">Marks this function for Just My Code stepping.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ff2c5-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ff2c5-115">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ff2c5-116">Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="ff2c5-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff2c5-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ff2c5-117">Requirements</span></span>  
 <span data-ttu-id="ff2c5-118">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ff2c5-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff2c5-119">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ff2c5-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ff2c5-120">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ff2c5-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ff2c5-121">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff2c5-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff2c5-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ff2c5-122">See also</span></span>

- [<span data-ttu-id="ff2c5-123">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ff2c5-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
