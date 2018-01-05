---
title: ICorDebugFunction::GetNativeCode Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFunction.GetNativeCode
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugFunction::GetNativeCode
helpviewer_keywords:
- GetNativeCode method [.NET Framework debugging]
- ICorDebugFunction::GetNativeCode method [.NET Framework debugging]
ms.assetid: c8a34916-0eef-4987-8d29-c8bcb4be9cf6
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 15383198da740f536061f1568fb06f042117b19c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugfunctiongetnativecode-method"></a><span data-ttu-id="abf99-102">ICorDebugFunction::GetNativeCode Metodu</span><span class="sxs-lookup"><span data-stu-id="abf99-102">ICorDebugFunction::GetNativeCode Method</span></span>
<span data-ttu-id="abf99-103">Bu ICorDebugFunction örneği tarafından temsil edilen işlevi için yerel kodu alır.</span><span class="sxs-lookup"><span data-stu-id="abf99-103">Gets the native code for the function that is represented by this ICorDebugFunction instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="abf99-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="abf99-104">Syntax</span></span>  
  
```  
HRESULT GetNativeCode (  
    [out] ICorDebugCode **ppCode  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="abf99-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="abf99-105">Parameters</span></span>  
 `ppCode`  
 <span data-ttu-id="abf99-106">[out] Bu işlev yalnızca derlenmiş zamanında (JIT) yapılmamış Microsoft Ara dili (MSIL) kodu ise bu işlev veya null, yerel kodunu temsil eden Icordebugcode örneği için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="abf99-106">[out] A pointer to the ICorDebugCode instance that represents the native code for this function, or null, if this function is Microsoft intermediate language (MSIL) code that has not been just-in-time (JIT) compiled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="abf99-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="abf99-107">Remarks</span></span>  
 <span data-ttu-id="abf99-108">Varsa bu tarafından temsil edilen işlevi `ICorDebugFunction` örneği açıldı JIT derlenmiş birden fazla kez Genel türleri gibi söz konusu olduğunda `GetNativeCode` bir rastgele yerel kod nesnesi döndürür.</span><span class="sxs-lookup"><span data-stu-id="abf99-108">If the function that is represented by this `ICorDebugFunction` instance has been JIT-compiled more than once, as in the case of generic types, `GetNativeCode` returns a random native code object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="abf99-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="abf99-109">Requirements</span></span>  
 <span data-ttu-id="abf99-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="abf99-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="abf99-111">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="abf99-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="abf99-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="abf99-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="abf99-113">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="abf99-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
