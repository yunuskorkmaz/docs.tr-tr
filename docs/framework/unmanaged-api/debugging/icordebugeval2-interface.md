---
title: Icordebugeval2 Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugEval2
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugEval2
helpviewer_keywords: ICorDebugEval2 interface [.NET Framework debugging]
ms.assetid: fce34531-2687-406d-9131-d6ad94f2ce0e
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: fbcf36ff7aca84299c55083b4ae135ce0a9ec4f3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugeval2-interface1"></a><span data-ttu-id="45ca6-102">Icordebugeval2 Interface1</span><span class="sxs-lookup"><span data-stu-id="45ca6-102">ICorDebugEval2 Interface1</span></span>
<span data-ttu-id="45ca6-103">"ICorDebugEval" genişletir genel türleri için destek sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="45ca6-103">Extends "ICorDebugEval" to provide support for generic types.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="45ca6-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="45ca6-104">Methods</span></span>  
  
|<span data-ttu-id="45ca6-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="45ca6-105">Method</span></span>|<span data-ttu-id="45ca6-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="45ca6-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="45ca6-107">CallParameterizedFunction yöntemi</span><span class="sxs-lookup"><span data-stu-id="45ca6-107">CallParameterizedFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-callparameterizedfunction-method.md)|<span data-ttu-id="45ca6-108">"Hangi Oluşturucusu tür parametreleri alır veya kendisi tür parametreleri sürebilir türü içinde yuvalanmış belirtilen ICorDebugFunction", çağrı ayarlar.</span><span class="sxs-lookup"><span data-stu-id="45ca6-108">Sets up a call to the specified "ICorDebugFunction", which can be nested inside a type whose constructor takes type parameters, or can itself take type parameters.</span></span>|  
|[<span data-ttu-id="45ca6-109">CreateValueForType yöntemi</span><span class="sxs-lookup"><span data-stu-id="45ca6-109">CreateValueForType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md)|<span data-ttu-id="45ca6-110">Bir işaretçi bir yeni "Icordebugvalue için" ilk bir null ya da sıfır değeriyle belirtilen türünü alır.</span><span class="sxs-lookup"><span data-stu-id="45ca6-110">Gets a pointer to a new "ICorDebugValue" of the specified type, with an initial value of null or zero.</span></span>|  
|[<span data-ttu-id="45ca6-111">NewParameterizedArray yöntemi</span><span class="sxs-lookup"><span data-stu-id="45ca6-111">NewParameterizedArray Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedarray-method.md)|<span data-ttu-id="45ca6-112">Belirtilen öğe türü ve boyutları yeni bir dizi ayırır.</span><span class="sxs-lookup"><span data-stu-id="45ca6-112">Allocates a new array of the specified element type and dimensions.</span></span>|  
|[<span data-ttu-id="45ca6-113">NewParameterizedObject yöntemi</span><span class="sxs-lookup"><span data-stu-id="45ca6-113">NewParameterizedObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md)|<span data-ttu-id="45ca6-114">Yeni bir parametreli türü nesnesi oluşturur ve nesnenin oluşturucusu yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="45ca6-114">Instantiates a new parameterized type object and calls the object's constructor method.</span></span>|  
|[<span data-ttu-id="45ca6-115">NewParameterizedObjectNoConstructor yöntemi</span><span class="sxs-lookup"><span data-stu-id="45ca6-115">NewParameterizedObjectNoConstructor Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobjectnoconstructor-method.md)|<span data-ttu-id="45ca6-116">Belirtilen sınıfının yeni bir parametreli türü nesnesi Oluşturucusu yöntemini çağırmak çalışırken olmadan başlatır</span><span class="sxs-lookup"><span data-stu-id="45ca6-116">Instantiates a new parameterized type object of the specified class without attempting to call a constructor method</span></span>|  
|[<span data-ttu-id="45ca6-117">NewStringWithLength yöntemi</span><span class="sxs-lookup"><span data-stu-id="45ca6-117">NewStringWithLength Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newstringwithlength-method.md)|<span data-ttu-id="45ca6-118">Belirtilen uzunlukta yeni bir dize belirtilen içerikle oluşturur.</span><span class="sxs-lookup"><span data-stu-id="45ca6-118">Creates a new string of the specified length with the specified contents.</span></span>|  
|[<span data-ttu-id="45ca6-119">RudeAbort yöntemi</span><span class="sxs-lookup"><span data-stu-id="45ca6-119">RudeAbort Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-rudeabort-method.md)|<span data-ttu-id="45ca6-120">Hesaplama durdurur bu `ICorDebugEval2` şu anda gerçekleştiriyor.</span><span class="sxs-lookup"><span data-stu-id="45ca6-120">Aborts the computation that this `ICorDebugEval2` is currently performing.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="45ca6-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="45ca6-121">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="45ca6-122">Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="45ca6-122">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="45ca6-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="45ca6-123">Requirements</span></span>  
 <span data-ttu-id="45ca6-124">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="45ca6-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45ca6-125">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="45ca6-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="45ca6-126">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="45ca6-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="45ca6-127">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="45ca6-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45ca6-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="45ca6-128">See Also</span></span>  
 [<span data-ttu-id="45ca6-129">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="45ca6-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
