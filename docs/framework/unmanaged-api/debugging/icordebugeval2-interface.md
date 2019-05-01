---
title: ICorDebugEval2 Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugEval2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2
helpviewer_keywords:
- ICorDebugEval2 interface [.NET Framework debugging]
ms.assetid: fce34531-2687-406d-9131-d6ad94f2ce0e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3767368c9da8c97cd081787c0945a15552a1da46
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61995975"
---
# <a name="icordebugeval2-interface"></a><span data-ttu-id="9e829-102">ICorDebugEval2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9e829-102">ICorDebugEval2 Interface</span></span>

<span data-ttu-id="9e829-103">"ICorDebugEval" genişleten genel türler için destek sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="9e829-103">Extends "ICorDebugEval" to provide support for generic types.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9e829-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="9e829-104">Methods</span></span>  
  
|<span data-ttu-id="9e829-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="9e829-105">Method</span></span>|<span data-ttu-id="9e829-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9e829-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9e829-107">CallParameterizedFunction Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9e829-107">CallParameterizedFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-callparameterizedfunction-method.md)|<span data-ttu-id="9e829-108">"Hangi tür parametreleri alır veya kendi tür parametreleri alabilir, Oluşturucusu türü içinde iç içe belirtilen ICorDebugFunction", bir çağrı ayarlar.</span><span class="sxs-lookup"><span data-stu-id="9e829-108">Sets up a call to the specified "ICorDebugFunction", which can be nested inside a type whose constructor takes type parameters, or can itself take type parameters.</span></span>|  
|[<span data-ttu-id="9e829-109">CreateValueForType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9e829-109">CreateValueForType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md)|<span data-ttu-id="9e829-110">Bir işaretçi bir yeni "Icordebugvalue için" bir başlangıç değeri null ya da sıfır ile belirtilen türünü alır.</span><span class="sxs-lookup"><span data-stu-id="9e829-110">Gets a pointer to a new "ICorDebugValue" of the specified type, with an initial value of null or zero.</span></span>|  
|[<span data-ttu-id="9e829-111">NewParameterizedArray Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9e829-111">NewParameterizedArray Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedarray-method.md)|<span data-ttu-id="9e829-112">Belirtilen öğe türü ve boyut yeni bir dizi ayırır.</span><span class="sxs-lookup"><span data-stu-id="9e829-112">Allocates a new array of the specified element type and dimensions.</span></span>|  
|[<span data-ttu-id="9e829-113">NewParameterizedObject Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9e829-113">NewParameterizedObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md)|<span data-ttu-id="9e829-114">Yeni bir parametreli tür nesnesi oluşturur ve nesnenin oluşturucusu yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="9e829-114">Instantiates a new parameterized type object and calls the object's constructor method.</span></span>|  
|[<span data-ttu-id="9e829-115">NewParameterizedObjectNoConstructor Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9e829-115">NewParameterizedObjectNoConstructor Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobjectnoconstructor-method.md)|<span data-ttu-id="9e829-116">Belirtilen sınıfın yeni bir parametreli tür nesnesi bir oluşturucu yöntemini çağırma girişimi olmadan örneğini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9e829-116">Instantiates a new parameterized type object of the specified class without attempting to call a constructor method</span></span>|  
|[<span data-ttu-id="9e829-117">NewStringWithLength Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9e829-117">NewStringWithLength Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newstringwithlength-method.md)|<span data-ttu-id="9e829-118">Belirtilen içerikle belirtilen uzunlukta yeni bir dize oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9e829-118">Creates a new string of the specified length with the specified contents.</span></span>|  
|[<span data-ttu-id="9e829-119">RudeAbort Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9e829-119">RudeAbort Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-rudeabort-method.md)|<span data-ttu-id="9e829-120">Hesaplama durdurur bu `ICorDebugEval2` şu anda gerçekleştiriyor.</span><span class="sxs-lookup"><span data-stu-id="9e829-120">Aborts the computation that this `ICorDebugEval2` is currently performing.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9e829-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9e829-121">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9e829-122">Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="9e829-122">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e829-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9e829-123">Requirements</span></span>  
 <span data-ttu-id="9e829-124">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9e829-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e829-125">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9e829-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9e829-126">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9e829-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9e829-127">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e829-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e829-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9e829-128">See also</span></span>

- [<span data-ttu-id="9e829-129">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="9e829-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
