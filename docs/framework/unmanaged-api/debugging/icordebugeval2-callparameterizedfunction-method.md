---
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
ms.openlocfilehash: b521c96d26202119dad6fedb61cbd9da8b3c2e52
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137635"
---
# <a name="icordebugeval2callparameterizedfunction-method"></a><span data-ttu-id="66605-102">ICorDebugEval2::CallParameterizedFunction Yöntemi</span><span class="sxs-lookup"><span data-stu-id="66605-102">ICorDebugEval2::CallParameterizedFunction Method</span></span>
<span data-ttu-id="66605-103">Oluşturucusu <xref:System.Type> parametreleri geçen bir sınıfın içinde iç içe yerleştirilebilen belirtilen ICorDebugFunction öğesine bir çağrı kurar veya kendisi <xref:System.Type> parametreleri alabilir.</span><span class="sxs-lookup"><span data-stu-id="66605-103">Sets up a call to the specified ICorDebugFunction, which can be nested inside a class whose constructor takes <xref:System.Type> parameters, or can itself take <xref:System.Type> parameters.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66605-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="66605-104">Syntax</span></span>  
  
```cpp  
HRESULT CallParameterizedFunction (  
    [in] ICorDebugFunction     *pFunction,  
    [in] ULONG32               nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType *ppTypeArgs[],  
    [in] ULONG32               nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="66605-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="66605-105">Parameters</span></span>  
 `pFunction`  
 <span data-ttu-id="66605-106">'ndaki Çağrılacak işlevi temsil eden `ICorDebugFunction` nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="66605-106">[in] A pointer to an `ICorDebugFunction` object that represents the function to be called.</span></span>  
  
 `nTypeArgs`  
 <span data-ttu-id="66605-107">'ndaki İşlevin aldığı bağımsız değişken sayısı.</span><span class="sxs-lookup"><span data-stu-id="66605-107">[in] The number of arguments that the function takes.</span></span>  
  
 `ppTypeArgs`  
 <span data-ttu-id="66605-108">'ndaki Her biri bir işlev bağımsız değişkenini temsil eden ICorDebugType nesnesine işaret eden bir işaretçiler dizisi.</span><span class="sxs-lookup"><span data-stu-id="66605-108">[in] An array of pointers, each of which points to an ICorDebugType object that represents a function argument.</span></span>  
  
 `nArgs`  
 <span data-ttu-id="66605-109">'ndaki İşleve geçirilen değer sayısı.</span><span class="sxs-lookup"><span data-stu-id="66605-109">[in] The number of values passed in the function.</span></span>  
  
 `ppArgs`  
 <span data-ttu-id="66605-110">'ndaki Her biri bir işlev bağımsız değişkeninde geçirilen değeri temsil eden ICorDebugValue nesnesine işaret eden bir işaretçiler dizisi.</span><span class="sxs-lookup"><span data-stu-id="66605-110">[in] An array of pointers, each of which points to an ICorDebugValue object that represents a value passed in a function argument.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="66605-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="66605-111">Remarks</span></span>  
 <span data-ttu-id="66605-112">`CallParameterizedFunction` [ıcorınkıonımagegeval:: CallFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-callfunction-method.md) gibidir, çünkü işlev tür parametrelerine sahip bir sınıfın içinde olabilir, kendisi tür parametreleri veya her ikisini de alabilir.</span><span class="sxs-lookup"><span data-stu-id="66605-112">`CallParameterizedFunction` is like [ICorDebugEval::CallFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-callfunction-method.md) except that the function may be inside a class with type parameters, may itself take type parameters, or both.</span></span> <span data-ttu-id="66605-113">Tür bağımsız değişkenleri önce sınıf için, sonra da işlev için verilmelidir.</span><span class="sxs-lookup"><span data-stu-id="66605-113">The type arguments should be given first for the class, and then for the function.</span></span>  
  
 <span data-ttu-id="66605-114">İşlev farklı bir uygulama etki alanında ise, bir geçiş gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="66605-114">If the function is in a different application domain, a transition will occur.</span></span> <span data-ttu-id="66605-115">Ancak, tüm tür ve değer bağımsız değişkenleri hedef uygulama etki alanında olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="66605-115">However, all type and value arguments must be in the target application domain.</span></span>  
  
 <span data-ttu-id="66605-116">İşlev değerlendirmesi yalnızca sınırlı senaryolarda gerçekleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="66605-116">Function evaluation can be performed only in limited scenarios.</span></span> <span data-ttu-id="66605-117">`CallParameterizedFunction` veya `ICorDebugEval::CallFunction` başarısız olursa, döndürülen HRESULT hatanın en genel olası nedenini gösterir.</span><span class="sxs-lookup"><span data-stu-id="66605-117">If `CallParameterizedFunction` or `ICorDebugEval::CallFunction` fails, the returned HRESULT will indicate the most general possible reason for failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66605-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="66605-118">Requirements</span></span>  
 <span data-ttu-id="66605-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="66605-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66605-120">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="66605-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="66605-121">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="66605-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="66605-122">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66605-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
