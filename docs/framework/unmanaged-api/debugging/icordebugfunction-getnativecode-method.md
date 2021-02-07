---
description: ': ICorDebugFunction:: GetNativeCode yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 8938e11a5fdc3aa693faf04eec639941475d95ac
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99692452"
---
# <a name="icordebugfunctiongetnativecode-method"></a><span data-ttu-id="9fb74-103">ICorDebugFunction::GetNativeCode Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9fb74-103">ICorDebugFunction::GetNativeCode Method</span></span>

<span data-ttu-id="9fb74-104">Bu ICorDebugFunction örneğiyle temsil edilen işlevin yerel kodunu alır.</span><span class="sxs-lookup"><span data-stu-id="9fb74-104">Gets the native code for the function that is represented by this ICorDebugFunction instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9fb74-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9fb74-105">Syntax</span></span>  
  
```cpp  
HRESULT GetNativeCode (  
    [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9fb74-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9fb74-106">Parameters</span></span>  

 `ppCode`  
 <span data-ttu-id="9fb74-107">dışı Bu işlev için yerel kodu temsil eden ICorDebugCode örneğine yönelik bir işaretçi veya bu işlev tam zamanında (JıT) derlenmiş Microsoft ara dili (MSIL) kodu ise null.</span><span class="sxs-lookup"><span data-stu-id="9fb74-107">[out] A pointer to the ICorDebugCode instance that represents the native code for this function, or null, if this function is Microsoft intermediate language (MSIL) code that has not been just-in-time (JIT) compiled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9fb74-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9fb74-108">Remarks</span></span>  

 <span data-ttu-id="9fb74-109">Bu örnek tarafından temsil edilen işlev `ICorDebugFunction` JIT olarak derlenmişse, genel türler söz konusu olduğunda, `GetNativeCode` rastgele bir yerel kod nesnesi döndürür.</span><span class="sxs-lookup"><span data-stu-id="9fb74-109">If the function that is represented by this `ICorDebugFunction` instance has been JIT-compiled more than once, as in the case of generic types, `GetNativeCode` returns a random native code object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9fb74-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9fb74-110">Requirements</span></span>  

 <span data-ttu-id="9fb74-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9fb74-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9fb74-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="9fb74-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9fb74-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="9fb74-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9fb74-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9fb74-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
