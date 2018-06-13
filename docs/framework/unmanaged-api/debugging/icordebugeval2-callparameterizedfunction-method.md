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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 77d9ec0cf1cbca63382e7f29de85c2f9566dc2bb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33416172"
---
# <a name="icordebugeval2callparameterizedfunction-method"></a><span data-ttu-id="66a77-102">ICorDebugEval2::CallParameterizedFunction Yöntemi</span><span class="sxs-lookup"><span data-stu-id="66a77-102">ICorDebugEval2::CallParameterizedFunction Method</span></span>
<span data-ttu-id="66a77-103">Oluşturucusu geçen bir sınıf içinde yuvalanmış belirtilen ICorDebugFunction çağrısı ayarlar <xref:System.Type> parametreleri veya can kendisini alın <xref:System.Type> parametreleri.</span><span class="sxs-lookup"><span data-stu-id="66a77-103">Sets up a call to the specified ICorDebugFunction, which can be nested inside a class whose constructor takes <xref:System.Type> parameters, or can itself take <xref:System.Type> parameters.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66a77-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="66a77-104">Syntax</span></span>  
  
```  
HRESULT CallParameterizedFunction (  
    [in] ICorDebugFunction     *pFunction,  
    [in] ULONG32               nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType *ppTypeArgs[],  
    [in] ULONG32               nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="66a77-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="66a77-105">Parameters</span></span>  
 `pFunction`  
 <span data-ttu-id="66a77-106">[in] Bir işaretçi bir `ICorDebugFunction` çağrılacak işlev temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="66a77-106">[in] A pointer to an `ICorDebugFunction` object that represents the function to be called.</span></span>  
  
 `nTypeArgs`  
 <span data-ttu-id="66a77-107">[in] İşlev alır bağımsız değişken sayısı.</span><span class="sxs-lookup"><span data-stu-id="66a77-107">[in] The number of arguments that the function takes.</span></span>  
  
 `ppTypeArgs`  
 <span data-ttu-id="66a77-108">[in] Her biri bir işlev bağımsız değişkeni temsil eden bir Icordebugtype bir nesneye işaret etmiyor dizisi işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="66a77-108">[in] An array of pointers, each of which points to an ICorDebugType object that represents a function argument.</span></span>  
  
 `nArgs`  
 <span data-ttu-id="66a77-109">[in] Değerlerin sayısını işlevinde geçirildi.</span><span class="sxs-lookup"><span data-stu-id="66a77-109">[in] The number of values passed in the function.</span></span>  
  
 `ppArgs`  
 <span data-ttu-id="66a77-110">[in] İşaretçileri, her biri bir değeri temsil eden bir Icordebugvalue bir nesneye işaret etmiyor dizisi işlevi bağımsız değişken geçirildi.</span><span class="sxs-lookup"><span data-stu-id="66a77-110">[in] An array of pointers, each of which points to an ICorDebugValue object that represents a value passed in a function argument.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="66a77-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="66a77-111">Remarks</span></span>  
 <span data-ttu-id="66a77-112">`CallParameterizedFunction` benzer [Icordebugeval::CallFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-callfunction-method.md) işlev türü parametrelere sahip bir sınıf içinde olabilir ancak bu, kendisini tür parametreleri ya da her ikisini de alabilir.</span><span class="sxs-lookup"><span data-stu-id="66a77-112">`CallParameterizedFunction` is like [ICorDebugEval::CallFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-callfunction-method.md) except that the function may be inside a class with type parameters, may itself take type parameters, or both.</span></span> <span data-ttu-id="66a77-113">Tür bağımsız değişkenleri sınıfı ve ardından işlevi için önce verilmelidir.</span><span class="sxs-lookup"><span data-stu-id="66a77-113">The type arguments should be given first for the class, and then for the function.</span></span>  
  
 <span data-ttu-id="66a77-114">İşlev farklı uygulama etki alanında ise, bir geçiş meydana gelir.</span><span class="sxs-lookup"><span data-stu-id="66a77-114">If the function is in a different application domain, a transition will occur.</span></span> <span data-ttu-id="66a77-115">Ancak, tüm türü ve değeri bağımsız değişkenleri hedef uygulama etki alanında olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="66a77-115">However, all type and value arguments must be in the target application domain.</span></span>  
  
 <span data-ttu-id="66a77-116">İşlev değerlendirmesi yalnızca sınırlı senaryolarda gerçekleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="66a77-116">Function evaluation can be performed only in limited scenarios.</span></span> <span data-ttu-id="66a77-117">Varsa `CallParameterizedFunction` veya `ICorDebugEval::CallFunction` başarısız olduğunda, döndürülen HRESULT hata olası en genel nedeni gösterilir.</span><span class="sxs-lookup"><span data-stu-id="66a77-117">If `CallParameterizedFunction` or `ICorDebugEval::CallFunction` fails, the returned HRESULT will indicate the most general possible reason for failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66a77-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="66a77-118">Requirements</span></span>  
 <span data-ttu-id="66a77-119">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="66a77-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66a77-120">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="66a77-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="66a77-121">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="66a77-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="66a77-122">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66a77-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
