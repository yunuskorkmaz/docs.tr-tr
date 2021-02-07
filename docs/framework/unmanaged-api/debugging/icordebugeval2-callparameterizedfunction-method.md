---
description: 'Şu konuda daha fazla bilgi edinin: ICorDebugEval2:: CallParameterizedFunction yöntemi'
title: ICorDebugEval2::CallParameterizedFunction Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.CallParameterizedFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::CallParameterizedFunction
helpviewer_keywords:
- ICorDebugEval2::CallParameterizedFunction method [.NET Framework debugging]
- CallParameterizedFunction method [.NET Framework debugging]
ms.assetid: 72f54a45-dbe6-4bb4-8c99-e879a27368e5
topic_type:
- apiref
ms.openlocfilehash: f3947d819caf42bc174dbbba4f5054b9fc4ab1f1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99693830"
---
# <a name="icordebugeval2callparameterizedfunction-method"></a><span data-ttu-id="a8428-103">ICorDebugEval2::CallParameterizedFunction Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a8428-103">ICorDebugEval2::CallParameterizedFunction Method</span></span>

<span data-ttu-id="a8428-104">Belirtilen ICorDebugFunction öğesine bir çağrı kurar, bu, Oluşturucusu parametreleri alan bir sınıfın içinde iç içe eklenebilir <xref:System.Type> veya kendisi <xref:System.Type> parametre alabilir.</span><span class="sxs-lookup"><span data-stu-id="a8428-104">Sets up a call to the specified ICorDebugFunction, which can be nested inside a class whose constructor takes <xref:System.Type> parameters, or can itself take <xref:System.Type> parameters.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8428-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a8428-105">Syntax</span></span>  
  
```cpp  
HRESULT CallParameterizedFunction (  
    [in] ICorDebugFunction     *pFunction,  
    [in] ULONG32               nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType *ppTypeArgs[],  
    [in] ULONG32               nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a8428-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a8428-106">Parameters</span></span>  

 `pFunction`  
 <span data-ttu-id="a8428-107">'ndaki `ICorDebugFunction` Çağrılacak işlevi temsil eden nesneye yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a8428-107">[in] A pointer to an `ICorDebugFunction` object that represents the function to be called.</span></span>  
  
 `nTypeArgs`  
 <span data-ttu-id="a8428-108">'ndaki İşlevin aldığı bağımsız değişken sayısı.</span><span class="sxs-lookup"><span data-stu-id="a8428-108">[in] The number of arguments that the function takes.</span></span>  
  
 `ppTypeArgs`  
 <span data-ttu-id="a8428-109">'ndaki Her biri bir işlev bağımsız değişkenini temsil eden ICorDebugType nesnesine işaret eden bir işaretçiler dizisi.</span><span class="sxs-lookup"><span data-stu-id="a8428-109">[in] An array of pointers, each of which points to an ICorDebugType object that represents a function argument.</span></span>  
  
 `nArgs`  
 <span data-ttu-id="a8428-110">'ndaki İşleve geçirilen değer sayısı.</span><span class="sxs-lookup"><span data-stu-id="a8428-110">[in] The number of values passed in the function.</span></span>  
  
 `ppArgs`  
 <span data-ttu-id="a8428-111">'ndaki Her biri bir işlev bağımsız değişkeninde geçirilen değeri temsil eden ICorDebugValue nesnesine işaret eden bir işaretçiler dizisi.</span><span class="sxs-lookup"><span data-stu-id="a8428-111">[in] An array of pointers, each of which points to an ICorDebugValue object that represents a value passed in a function argument.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a8428-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a8428-112">Remarks</span></span>  

 <span data-ttu-id="a8428-113">`CallParameterizedFunction` , işlevin tür parametrelerine sahip bir sınıfın içinde olabileceği, kendi tür parametreleri veya her ikisini de içermesi dışında [ıcorınıtınkıonıval:: CallFunction](icordebugeval-callfunction-method.md) gibidir.</span><span class="sxs-lookup"><span data-stu-id="a8428-113">`CallParameterizedFunction` is like [ICorDebugEval::CallFunction](icordebugeval-callfunction-method.md) except that the function may be inside a class with type parameters, may itself take type parameters, or both.</span></span> <span data-ttu-id="a8428-114">Tür bağımsız değişkenleri önce sınıf için, sonra da işlev için verilmelidir.</span><span class="sxs-lookup"><span data-stu-id="a8428-114">The type arguments should be given first for the class, and then for the function.</span></span>  
  
 <span data-ttu-id="a8428-115">İşlev farklı bir uygulama etki alanında ise, bir geçiş gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="a8428-115">If the function is in a different application domain, a transition will occur.</span></span> <span data-ttu-id="a8428-116">Ancak, tüm tür ve değer bağımsız değişkenleri hedef uygulama etki alanında olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a8428-116">However, all type and value arguments must be in the target application domain.</span></span>  
  
 <span data-ttu-id="a8428-117">İşlev değerlendirmesi yalnızca sınırlı senaryolarda gerçekleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="a8428-117">Function evaluation can be performed only in limited scenarios.</span></span> <span data-ttu-id="a8428-118">`CallParameterizedFunction`Veya `ICorDebugEval::CallFunction` başarısız olursa, döndürülen HRESULT hatanın en genel olası nedenini gösterir.</span><span class="sxs-lookup"><span data-stu-id="a8428-118">If `CallParameterizedFunction` or `ICorDebugEval::CallFunction` fails, the returned HRESULT will indicate the most general possible reason for failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a8428-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a8428-119">Requirements</span></span>  

 <span data-ttu-id="a8428-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a8428-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a8428-121">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a8428-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a8428-122">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a8428-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a8428-123">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8428-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
