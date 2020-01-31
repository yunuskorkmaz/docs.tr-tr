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
ms.openlocfilehash: e69b32430651edd0222db874e2659bd959f89549
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788703"
---
# <a name="icordebugeval2-interface"></a><span data-ttu-id="ae85a-102">ICorDebugEval2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ae85a-102">ICorDebugEval2 Interface</span></span>

<span data-ttu-id="ae85a-103">Genel türler için destek sağlamak üzere "ıcorınkınogeval" öğesini genişletir.</span><span class="sxs-lookup"><span data-stu-id="ae85a-103">Extends "ICorDebugEval" to provide support for generic types.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ae85a-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="ae85a-104">Methods</span></span>  
  
|<span data-ttu-id="ae85a-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="ae85a-105">Method</span></span>|<span data-ttu-id="ae85a-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ae85a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ae85a-107">CallParameterizedFunction Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ae85a-107">CallParameterizedFunction Method</span></span>](icordebugeval2-callparameterizedfunction-method.md)|<span data-ttu-id="ae85a-108">Belirtilen "ICorDebugFunction" öğesine bir çağrı yapar, bu, Oluşturucusu tür parametreleri alan bir türün içinde iç içe eklenebilir veya kendisi tür parametreleri alabilir.</span><span class="sxs-lookup"><span data-stu-id="ae85a-108">Sets up a call to the specified "ICorDebugFunction", which can be nested inside a type whose constructor takes type parameters, or can itself take type parameters.</span></span>|  
|[<span data-ttu-id="ae85a-109">CreateValueForType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ae85a-109">CreateValueForType Method</span></span>](icordebugeval2-createvaluefortype-method.md)|<span data-ttu-id="ae85a-110">Belirtilen türün yeni bir "ICorDebugValue" değerine, null veya sıfır başlangıç değerine sahip bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="ae85a-110">Gets a pointer to a new "ICorDebugValue" of the specified type, with an initial value of null or zero.</span></span>|  
|[<span data-ttu-id="ae85a-111">NewParameterizedArray Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ae85a-111">NewParameterizedArray Method</span></span>](icordebugeval2-newparameterizedarray-method.md)|<span data-ttu-id="ae85a-112">Belirtilen öğe türü ve boyutlarının yeni bir dizisini ayırır.</span><span class="sxs-lookup"><span data-stu-id="ae85a-112">Allocates a new array of the specified element type and dimensions.</span></span>|  
|[<span data-ttu-id="ae85a-113">NewParameterizedObject Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ae85a-113">NewParameterizedObject Method</span></span>](icordebugeval2-newparameterizedobject-method.md)|<span data-ttu-id="ae85a-114">Yeni parametreli bir tür nesnesi oluşturur ve nesnenin Oluşturucu yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="ae85a-114">Instantiates a new parameterized type object and calls the object's constructor method.</span></span>|  
|[<span data-ttu-id="ae85a-115">NewParameterizedObjectNoConstructor Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ae85a-115">NewParameterizedObjectNoConstructor Method</span></span>](icordebugeval2-newparameterizedobjectnoconstructor-method.md)|<span data-ttu-id="ae85a-116">Bir Oluşturucu yöntemi çağırmaya çalışmadan, belirtilen sınıfın yeni parametreli tür nesnesini başlatır</span><span class="sxs-lookup"><span data-stu-id="ae85a-116">Instantiates a new parameterized type object of the specified class without attempting to call a constructor method</span></span>|  
|[<span data-ttu-id="ae85a-117">NewStringWithLength Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ae85a-117">NewStringWithLength Method</span></span>](icordebugeval2-newstringwithlength-method.md)|<span data-ttu-id="ae85a-118">Belirtilen içerikle belirtilen uzunluğa sahip yeni bir dize oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ae85a-118">Creates a new string of the specified length with the specified contents.</span></span>|  
|[<span data-ttu-id="ae85a-119">RudeAbort Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ae85a-119">RudeAbort Method</span></span>](icordebugeval2-rudeabort-method.md)|<span data-ttu-id="ae85a-120">Bu `ICorDebugEval2` Şu anda gerçekleştirdiği hesaplamayı iptal eder.</span><span class="sxs-lookup"><span data-stu-id="ae85a-120">Aborts the computation that this `ICorDebugEval2` is currently performing.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ae85a-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ae85a-121">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ae85a-122">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="ae85a-122">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae85a-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ae85a-123">Requirements</span></span>  
 <span data-ttu-id="ae85a-124">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ae85a-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae85a-125">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ae85a-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ae85a-126">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ae85a-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ae85a-127">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae85a-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae85a-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ae85a-128">See also</span></span>

- [<span data-ttu-id="ae85a-129">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ae85a-129">Debugging Interfaces</span></span>](debugging-interfaces.md)
