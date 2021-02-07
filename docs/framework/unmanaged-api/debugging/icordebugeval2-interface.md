---
description: 'Daha fazla bilgi edinin: ICorDebugEval2 Interface'
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
ms.openlocfilehash: 2c279335bdd30b8dc2698f348d9537443b236a45
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99693765"
---
# <a name="icordebugeval2-interface"></a><span data-ttu-id="69df3-103">ICorDebugEval2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="69df3-103">ICorDebugEval2 Interface</span></span>

<span data-ttu-id="69df3-104">Genel türler için destek sağlamak üzere "ıcorınkınogeval" öğesini genişletir.</span><span class="sxs-lookup"><span data-stu-id="69df3-104">Extends "ICorDebugEval" to provide support for generic types.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="69df3-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="69df3-105">Methods</span></span>  
  
|<span data-ttu-id="69df3-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="69df3-106">Method</span></span>|<span data-ttu-id="69df3-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="69df3-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="69df3-108">CallParameterizedFunction Yöntemi</span><span class="sxs-lookup"><span data-stu-id="69df3-108">CallParameterizedFunction Method</span></span>](icordebugeval2-callparameterizedfunction-method.md)|<span data-ttu-id="69df3-109">Belirtilen "ICorDebugFunction" öğesine bir çağrı yapar, bu, Oluşturucusu tür parametreleri alan bir türün içinde iç içe eklenebilir veya kendisi tür parametreleri alabilir.</span><span class="sxs-lookup"><span data-stu-id="69df3-109">Sets up a call to the specified "ICorDebugFunction", which can be nested inside a type whose constructor takes type parameters, or can itself take type parameters.</span></span>|  
|[<span data-ttu-id="69df3-110">CreateValueForType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="69df3-110">CreateValueForType Method</span></span>](icordebugeval2-createvaluefortype-method.md)|<span data-ttu-id="69df3-111">Belirtilen türün yeni bir "ICorDebugValue" değerine, null veya sıfır başlangıç değerine sahip bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="69df3-111">Gets a pointer to a new "ICorDebugValue" of the specified type, with an initial value of null or zero.</span></span>|  
|[<span data-ttu-id="69df3-112">NewParameterizedArray Yöntemi</span><span class="sxs-lookup"><span data-stu-id="69df3-112">NewParameterizedArray Method</span></span>](icordebugeval2-newparameterizedarray-method.md)|<span data-ttu-id="69df3-113">Belirtilen öğe türü ve boyutlarının yeni bir dizisini ayırır.</span><span class="sxs-lookup"><span data-stu-id="69df3-113">Allocates a new array of the specified element type and dimensions.</span></span>|  
|[<span data-ttu-id="69df3-114">NewParameterizedObject Yöntemi</span><span class="sxs-lookup"><span data-stu-id="69df3-114">NewParameterizedObject Method</span></span>](icordebugeval2-newparameterizedobject-method.md)|<span data-ttu-id="69df3-115">Yeni parametreli bir tür nesnesi oluşturur ve nesnenin Oluşturucu yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="69df3-115">Instantiates a new parameterized type object and calls the object's constructor method.</span></span>|  
|[<span data-ttu-id="69df3-116">NewParameterizedObjectNoConstructor Yöntemi</span><span class="sxs-lookup"><span data-stu-id="69df3-116">NewParameterizedObjectNoConstructor Method</span></span>](icordebugeval2-newparameterizedobjectnoconstructor-method.md)|<span data-ttu-id="69df3-117">Bir Oluşturucu yöntemi çağırmaya çalışmadan, belirtilen sınıfın yeni parametreli tür nesnesini başlatır</span><span class="sxs-lookup"><span data-stu-id="69df3-117">Instantiates a new parameterized type object of the specified class without attempting to call a constructor method</span></span>|  
|[<span data-ttu-id="69df3-118">NewStringWithLength Yöntemi</span><span class="sxs-lookup"><span data-stu-id="69df3-118">NewStringWithLength Method</span></span>](icordebugeval2-newstringwithlength-method.md)|<span data-ttu-id="69df3-119">Belirtilen içerikle belirtilen uzunluğa sahip yeni bir dize oluşturur.</span><span class="sxs-lookup"><span data-stu-id="69df3-119">Creates a new string of the specified length with the specified contents.</span></span>|  
|[<span data-ttu-id="69df3-120">RudeAbort Yöntemi</span><span class="sxs-lookup"><span data-stu-id="69df3-120">RudeAbort Method</span></span>](icordebugeval2-rudeabort-method.md)|<span data-ttu-id="69df3-121">`ICorDebugEval2`Şu anda gerçekleştirdiği hesaplamayı iptal eder.</span><span class="sxs-lookup"><span data-stu-id="69df3-121">Aborts the computation that this `ICorDebugEval2` is currently performing.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="69df3-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="69df3-122">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="69df3-123">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="69df3-123">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69df3-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="69df3-124">Requirements</span></span>  

 <span data-ttu-id="69df3-125">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="69df3-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="69df3-126">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="69df3-126">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="69df3-127">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="69df3-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="69df3-128">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="69df3-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69df3-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="69df3-129">See also</span></span>

- [<span data-ttu-id="69df3-130">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="69df3-130">Debugging Interfaces</span></span>](debugging-interfaces.md)
