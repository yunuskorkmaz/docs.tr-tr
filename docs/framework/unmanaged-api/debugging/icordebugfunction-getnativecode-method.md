---
title: ICorDebugFunction::GetNativeCode Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetNativeCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetNativeCode
helpviewer_keywords:
- GetNativeCode method [.NET Framework debugging]
- ICorDebugFunction::GetNativeCode method [.NET Framework debugging]
ms.assetid: c8a34916-0eef-4987-8d29-c8bcb4be9cf6
topic_type:
- apiref
ms.openlocfilehash: 98aee38415709974d84873df50c39263490f2f23
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213276"
---
# <a name="icordebugfunctiongetnativecode-method"></a><span data-ttu-id="66c21-102">ICorDebugFunction::GetNativeCode Yöntemi</span><span class="sxs-lookup"><span data-stu-id="66c21-102">ICorDebugFunction::GetNativeCode Method</span></span>
<span data-ttu-id="66c21-103">Bu ICorDebugFunction örneğiyle temsil edilen işlevin yerel kodunu alır.</span><span class="sxs-lookup"><span data-stu-id="66c21-103">Gets the native code for the function that is represented by this ICorDebugFunction instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66c21-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="66c21-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNativeCode (  
    [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="66c21-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="66c21-105">Parameters</span></span>  
 `ppCode`  
 <span data-ttu-id="66c21-106">dışı Bu işlev için yerel kodu temsil eden ICorDebugCode örneğine yönelik bir işaretçi veya bu işlev tam zamanında (JıT) derlenmiş Microsoft ara dili (MSIL) kodu ise null.</span><span class="sxs-lookup"><span data-stu-id="66c21-106">[out] A pointer to the ICorDebugCode instance that represents the native code for this function, or null, if this function is Microsoft intermediate language (MSIL) code that has not been just-in-time (JIT) compiled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="66c21-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="66c21-107">Remarks</span></span>  
 <span data-ttu-id="66c21-108">Bu örnek tarafından temsil edilen işlev `ICorDebugFunction` JIT olarak derlenmişse, genel türler söz konusu olduğunda, `GetNativeCode` rastgele bir yerel kod nesnesi döndürür.</span><span class="sxs-lookup"><span data-stu-id="66c21-108">If the function that is represented by this `ICorDebugFunction` instance has been JIT-compiled more than once, as in the case of generic types, `GetNativeCode` returns a random native code object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66c21-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="66c21-109">Requirements</span></span>  
 <span data-ttu-id="66c21-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="66c21-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66c21-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="66c21-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="66c21-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="66c21-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="66c21-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66c21-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
