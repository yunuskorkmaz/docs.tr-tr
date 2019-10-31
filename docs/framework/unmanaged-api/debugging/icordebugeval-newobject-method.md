---
title: ICorDebugEval::NewObject Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugEval.NewObject
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::NewObject
helpviewer_keywords:
- NewObject method [.NET Framework debugging]
- ICorDebugEval::NewObject method [.NET Framework debugging]
ms.assetid: ce3025e8-defa-4c5e-8298-f49d71fa5736
topic_type:
- apiref
ms.openlocfilehash: 68a7e911c2bd1798ea8f34f6a6e24299fe68775d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137616"
---
# <a name="icordebugevalnewobject-method"></a><span data-ttu-id="c94d3-102">ICorDebugEval::NewObject Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c94d3-102">ICorDebugEval::NewObject Method</span></span>
<span data-ttu-id="c94d3-103">Yeni bir nesne örneği ayırır ve belirtilen Oluşturucu yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="c94d3-103">Allocates a new object instance and calls the specified constructor method.</span></span>  
  
 <span data-ttu-id="c94d3-104">Bu yöntem .NET Framework sürüm 2,0 ' de kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="c94d3-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="c94d3-105">Bunun yerine [ICorDebugEval2:: NewParameterizedObject](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="c94d3-105">Use [ICorDebugEval2::NewParameterizedObject](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c94d3-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c94d3-106">Syntax</span></span>  
  
```cpp  
HRESULT NewObject (  
    [in] ICorDebugFunction  *pConstructor,  
    [in] ULONG32            nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c94d3-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c94d3-107">Parameters</span></span>  
 `pConstructor`  
 <span data-ttu-id="c94d3-108">'ndaki Çağrılacak Oluşturucu.</span><span class="sxs-lookup"><span data-stu-id="c94d3-108">[in] The constructor to be called.</span></span>  
  
 `nArgs`  
 <span data-ttu-id="c94d3-109">'ndaki `ppArgs` dizisinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="c94d3-109">[in] The size of the `ppArgs` array.</span></span>  
  
 `ppArgs`  
 <span data-ttu-id="c94d3-110">'ndaki Her biri oluşturucuya geçirilecek bir bağımsız değişkeni temsil eden ICorDebugValue nesnelerinin dizisi.</span><span class="sxs-lookup"><span data-stu-id="c94d3-110">[in] An array of ICorDebugValue objects, each of which represents an argument to be passed to the constructor.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c94d3-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c94d3-111">Requirements</span></span>  
 <span data-ttu-id="c94d3-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c94d3-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c94d3-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c94d3-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c94d3-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c94d3-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c94d3-115">**.NET Framework sürümleri:** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="c94d3-115">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c94d3-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c94d3-116">See also</span></span>

- [<span data-ttu-id="c94d3-117">NewParameterizedObject Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c94d3-117">NewParameterizedObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md)
