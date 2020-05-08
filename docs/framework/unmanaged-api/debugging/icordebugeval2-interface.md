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
ms.openlocfilehash: b597d95b5b25e5ebf04fac48e4f3fda312a9594c
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976128"
---
# <a name="icordebugeval2-interface"></a><span data-ttu-id="0a96f-102">ICorDebugEval2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0a96f-102">ICorDebugEval2 Interface</span></span>

<span data-ttu-id="0a96f-103">Genel türler için destek sağlamak üzere "ıcorınkınogeval" öğesini genişletir.</span><span class="sxs-lookup"><span data-stu-id="0a96f-103">Extends "ICorDebugEval" to provide support for generic types.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0a96f-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="0a96f-104">Methods</span></span>  
  
|<span data-ttu-id="0a96f-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="0a96f-105">Method</span></span>|<span data-ttu-id="0a96f-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0a96f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0a96f-107">CallParameterizedFunction Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0a96f-107">CallParameterizedFunction Method</span></span>](icordebugeval2-callparameterizedfunction-method.md)|<span data-ttu-id="0a96f-108">Belirtilen "ICorDebugFunction" öğesine bir çağrı yapar, bu, Oluşturucusu tür parametreleri alan bir türün içinde iç içe eklenebilir veya kendisi tür parametreleri alabilir.</span><span class="sxs-lookup"><span data-stu-id="0a96f-108">Sets up a call to the specified "ICorDebugFunction", which can be nested inside a type whose constructor takes type parameters, or can itself take type parameters.</span></span>|  
|[<span data-ttu-id="0a96f-109">CreateValueForType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0a96f-109">CreateValueForType Method</span></span>](icordebugeval2-createvaluefortype-method.md)|<span data-ttu-id="0a96f-110">Belirtilen türün yeni bir "ICorDebugValue" değerine, null veya sıfır başlangıç değerine sahip bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="0a96f-110">Gets a pointer to a new "ICorDebugValue" of the specified type, with an initial value of null or zero.</span></span>|  
|[<span data-ttu-id="0a96f-111">NewParameterizedArray Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0a96f-111">NewParameterizedArray Method</span></span>](icordebugeval2-newparameterizedarray-method.md)|<span data-ttu-id="0a96f-112">Belirtilen öğe türü ve boyutlarının yeni bir dizisini ayırır.</span><span class="sxs-lookup"><span data-stu-id="0a96f-112">Allocates a new array of the specified element type and dimensions.</span></span>|  
|[<span data-ttu-id="0a96f-113">NewParameterizedObject Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0a96f-113">NewParameterizedObject Method</span></span>](icordebugeval2-newparameterizedobject-method.md)|<span data-ttu-id="0a96f-114">Yeni parametreli bir tür nesnesi oluşturur ve nesnenin Oluşturucu yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="0a96f-114">Instantiates a new parameterized type object and calls the object's constructor method.</span></span>|  
|[<span data-ttu-id="0a96f-115">NewParameterizedObjectNoConstructor Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0a96f-115">NewParameterizedObjectNoConstructor Method</span></span>](icordebugeval2-newparameterizedobjectnoconstructor-method.md)|<span data-ttu-id="0a96f-116">Bir Oluşturucu yöntemi çağırmaya çalışmadan, belirtilen sınıfın yeni parametreli tür nesnesini başlatır</span><span class="sxs-lookup"><span data-stu-id="0a96f-116">Instantiates a new parameterized type object of the specified class without attempting to call a constructor method</span></span>|  
|[<span data-ttu-id="0a96f-117">NewStringWithLength Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0a96f-117">NewStringWithLength Method</span></span>](icordebugeval2-newstringwithlength-method.md)|<span data-ttu-id="0a96f-118">Belirtilen içerikle belirtilen uzunluğa sahip yeni bir dize oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0a96f-118">Creates a new string of the specified length with the specified contents.</span></span>|  
|[<span data-ttu-id="0a96f-119">RudeAbort Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0a96f-119">RudeAbort Method</span></span>](icordebugeval2-rudeabort-method.md)|<span data-ttu-id="0a96f-120">Şu anda gerçekleştirdiği hesaplamayı `ICorDebugEval2` iptal eder.</span><span class="sxs-lookup"><span data-stu-id="0a96f-120">Aborts the computation that this `ICorDebugEval2` is currently performing.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0a96f-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0a96f-121">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0a96f-122">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="0a96f-122">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0a96f-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0a96f-123">Requirements</span></span>  
 <span data-ttu-id="0a96f-124">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0a96f-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a96f-125">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="0a96f-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0a96f-126">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="0a96f-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0a96f-127">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0a96f-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a96f-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0a96f-128">See also</span></span>

- [<span data-ttu-id="0a96f-129">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="0a96f-129">Debugging Interfaces</span></span>](debugging-interfaces.md)
