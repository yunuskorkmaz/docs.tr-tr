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
ms.workload: dotnet
ms.openlocfilehash: ac816d2b2dce6c9c76813bf4247bac7ca40da5f4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugeval2-interface1"></a><span data-ttu-id="c88fd-102">Icordebugeval2 Interface1</span><span class="sxs-lookup"><span data-stu-id="c88fd-102">ICorDebugEval2 Interface1</span></span>
<span data-ttu-id="c88fd-103">"ICorDebugEval" genişletir genel türleri için destek sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="c88fd-103">Extends "ICorDebugEval" to provide support for generic types.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c88fd-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="c88fd-104">Methods</span></span>  
  
|<span data-ttu-id="c88fd-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="c88fd-105">Method</span></span>|<span data-ttu-id="c88fd-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c88fd-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c88fd-107">CallParameterizedFunction Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c88fd-107">CallParameterizedFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-callparameterizedfunction-method.md)|<span data-ttu-id="c88fd-108">"Hangi Oluşturucusu tür parametreleri alır veya kendisi tür parametreleri sürebilir türü içinde yuvalanmış belirtilen ICorDebugFunction", çağrı ayarlar.</span><span class="sxs-lookup"><span data-stu-id="c88fd-108">Sets up a call to the specified "ICorDebugFunction", which can be nested inside a type whose constructor takes type parameters, or can itself take type parameters.</span></span>|  
|[<span data-ttu-id="c88fd-109">CreateValueForType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c88fd-109">CreateValueForType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md)|<span data-ttu-id="c88fd-110">Bir işaretçi bir yeni "Icordebugvalue için" ilk bir null ya da sıfır değeriyle belirtilen türünü alır.</span><span class="sxs-lookup"><span data-stu-id="c88fd-110">Gets a pointer to a new "ICorDebugValue" of the specified type, with an initial value of null or zero.</span></span>|  
|[<span data-ttu-id="c88fd-111">NewParameterizedArray Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c88fd-111">NewParameterizedArray Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedarray-method.md)|<span data-ttu-id="c88fd-112">Belirtilen öğe türü ve boyutları yeni bir dizi ayırır.</span><span class="sxs-lookup"><span data-stu-id="c88fd-112">Allocates a new array of the specified element type and dimensions.</span></span>|  
|[<span data-ttu-id="c88fd-113">NewParameterizedObject Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c88fd-113">NewParameterizedObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md)|<span data-ttu-id="c88fd-114">Yeni bir parametreli türü nesnesi oluşturur ve nesnenin oluşturucusu yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="c88fd-114">Instantiates a new parameterized type object and calls the object's constructor method.</span></span>|  
|[<span data-ttu-id="c88fd-115">NewParameterizedObjectNoConstructor Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c88fd-115">NewParameterizedObjectNoConstructor Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobjectnoconstructor-method.md)|<span data-ttu-id="c88fd-116">Belirtilen sınıfının yeni bir parametreli türü nesnesi Oluşturucusu yöntemini çağırmak çalışırken olmadan başlatır</span><span class="sxs-lookup"><span data-stu-id="c88fd-116">Instantiates a new parameterized type object of the specified class without attempting to call a constructor method</span></span>|  
|[<span data-ttu-id="c88fd-117">NewStringWithLength Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c88fd-117">NewStringWithLength Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newstringwithlength-method.md)|<span data-ttu-id="c88fd-118">Belirtilen uzunlukta yeni bir dize belirtilen içerikle oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c88fd-118">Creates a new string of the specified length with the specified contents.</span></span>|  
|[<span data-ttu-id="c88fd-119">RudeAbort Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c88fd-119">RudeAbort Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-rudeabort-method.md)|<span data-ttu-id="c88fd-120">Hesaplama durdurur bu `ICorDebugEval2` şu anda gerçekleştiriyor.</span><span class="sxs-lookup"><span data-stu-id="c88fd-120">Aborts the computation that this `ICorDebugEval2` is currently performing.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c88fd-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c88fd-121">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c88fd-122">Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="c88fd-122">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c88fd-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c88fd-123">Requirements</span></span>  
 <span data-ttu-id="c88fd-124">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c88fd-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c88fd-125">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c88fd-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c88fd-126">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c88fd-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c88fd-127">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c88fd-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c88fd-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c88fd-128">See Also</span></span>  
 [<span data-ttu-id="c88fd-129">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c88fd-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
