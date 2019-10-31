---
title: ICorDebugAppDomain2::GetFunctionPointerType Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain2.GetFunctionPointerType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain2::GetFunctionPointerType
helpviewer_keywords:
- ICorDebugAppDomain2::GetFunctionPointerType method [.NET Framework debugging]
- GetFunctionPointerType method [.NET Framework debugging]
ms.assetid: 0aba6096-5b38-435c-a72a-86d35db4daef
topic_type:
- apiref
ms.openlocfilehash: 5a6e0b009674ff52595aaa0ae4a060f1cdfd1398
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73089055"
---
# <a name="icordebugappdomain2getfunctionpointertype-method"></a><span data-ttu-id="ea9e0-102">ICorDebugAppDomain2::GetFunctionPointerType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ea9e0-102">ICorDebugAppDomain2::GetFunctionPointerType Method</span></span>
<span data-ttu-id="ea9e0-103">Belirli bir imzaya sahip bir işleve yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="ea9e0-103">Gets a pointer to a function that has a given signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea9e0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ea9e0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionPointerType (  
    [in] ULONG32                             nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType   *ppTypeArgs[],  
    [out] ICorDebugType                      **ppType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ea9e0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ea9e0-105">Parameters</span></span>  
 `nTypeArgs`  
 <span data-ttu-id="ea9e0-106">'ndaki İşlevin tür bağımsız değişkenlerinin sayısı.</span><span class="sxs-lookup"><span data-stu-id="ea9e0-106">[in] The number of type arguments for the function.</span></span>  
  
 `ppTypeArgs`  
 <span data-ttu-id="ea9e0-107">'ndaki Her biri işlevin tür bağımsız değişkenini temsil eden bir ICorDebugType nesnesine işaret eden bir işaretçiler dizisi.</span><span class="sxs-lookup"><span data-stu-id="ea9e0-107">[in] An array of pointers, each of which points to an ICorDebugType object that represents a type argument of the function.</span></span> <span data-ttu-id="ea9e0-108">İlk öğe dönüş türüdür; diğer öğelerin her biri bir parametre türüdür.</span><span class="sxs-lookup"><span data-stu-id="ea9e0-108">The first element is the return type; each of the other elements is a parameter type.</span></span>  
  
 `ppType`  
 <span data-ttu-id="ea9e0-109">dışı İşlevin işaretçisini temsil eden bir `ICorDebugType` nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ea9e0-109">[out] A pointer to the address of an `ICorDebugType` object that represents the pointer to the function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea9e0-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ea9e0-110">Requirements</span></span>  
 <span data-ttu-id="ea9e0-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ea9e0-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea9e0-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ea9e0-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ea9e0-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ea9e0-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ea9e0-114">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea9e0-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
