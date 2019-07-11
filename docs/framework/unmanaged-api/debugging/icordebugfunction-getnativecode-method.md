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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c0507d59011f6b584ecb1ae11c35c456c80793af
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67754592"
---
# <a name="icordebugfunctiongetnativecode-method"></a><span data-ttu-id="83155-102">ICorDebugFunction::GetNativeCode Yöntemi</span><span class="sxs-lookup"><span data-stu-id="83155-102">ICorDebugFunction::GetNativeCode Method</span></span>
<span data-ttu-id="83155-103">Bu ICorDebugFunction örneği tarafından temsil edilen işlev için yerel kodu alır.</span><span class="sxs-lookup"><span data-stu-id="83155-103">Gets the native code for the function that is represented by this ICorDebugFunction instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83155-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="83155-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNativeCode (  
    [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="83155-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="83155-105">Parameters</span></span>  
 `ppCode`  
 <span data-ttu-id="83155-106">[out] Bu işlev, yalnızca derlenmiş zamanında (JIT) ayarlanmadı Microsoft Ara dili (MSIL) kodu ise bu işlev ya da null, yerel kodunu temsil eden Icordebugcode örneğine bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="83155-106">[out] A pointer to the ICorDebugCode instance that represents the native code for this function, or null, if this function is Microsoft intermediate language (MSIL) code that has not been just-in-time (JIT) compiled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="83155-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="83155-107">Remarks</span></span>  
 <span data-ttu-id="83155-108">Varsa bu tarafından temsil edilen işlevi `ICorDebugFunction` örneği JIT olarak derlenmiş birden çok kez, genel türler gibi söz konusu olduğunda `GetNativeCode` bir rastgele yerel kod nesnesi döndürür.</span><span class="sxs-lookup"><span data-stu-id="83155-108">If the function that is represented by this `ICorDebugFunction` instance has been JIT-compiled more than once, as in the case of generic types, `GetNativeCode` returns a random native code object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83155-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="83155-109">Requirements</span></span>  
 <span data-ttu-id="83155-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83155-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83155-111">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="83155-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="83155-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="83155-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="83155-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83155-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
