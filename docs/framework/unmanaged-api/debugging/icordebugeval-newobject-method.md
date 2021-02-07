---
description: 'Şu konuda daha fazla bilgi edinin: ıcorıbgeval:: NewObject yöntemi'
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
ms.openlocfilehash: 0f7feb53d061e5dbc453015772b97f2a5a59bbb3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99693960"
---
# <a name="icordebugevalnewobject-method"></a><span data-ttu-id="e0384-103">ICorDebugEval::NewObject Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e0384-103">ICorDebugEval::NewObject Method</span></span>

<span data-ttu-id="e0384-104">Yeni bir nesne örneği ayırır ve belirtilen Oluşturucu yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="e0384-104">Allocates a new object instance and calls the specified constructor method.</span></span>  
  
 <span data-ttu-id="e0384-105">Bu yöntem .NET Framework sürüm 2,0 ' de kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="e0384-105">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="e0384-106">Bunun yerine [ICorDebugEval2:: NewParameterizedObject](icordebugeval2-newparameterizedobject-method.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="e0384-106">Use [ICorDebugEval2::NewParameterizedObject](icordebugeval2-newparameterizedobject-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0384-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e0384-107">Syntax</span></span>  
  
```cpp  
HRESULT NewObject (  
    [in] ICorDebugFunction  *pConstructor,  
    [in] ULONG32            nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e0384-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e0384-108">Parameters</span></span>  

 `pConstructor`  
 <span data-ttu-id="e0384-109">'ndaki Çağrılacak Oluşturucu.</span><span class="sxs-lookup"><span data-stu-id="e0384-109">[in] The constructor to be called.</span></span>  
  
 `nArgs`  
 <span data-ttu-id="e0384-110">'ndaki `ppArgs` Dizinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="e0384-110">[in] The size of the `ppArgs` array.</span></span>  
  
 `ppArgs`  
 <span data-ttu-id="e0384-111">'ndaki Her biri oluşturucuya geçirilecek bir bağımsız değişkeni temsil eden ICorDebugValue nesnelerinin dizisi.</span><span class="sxs-lookup"><span data-stu-id="e0384-111">[in] An array of ICorDebugValue objects, each of which represents an argument to be passed to the constructor.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0384-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e0384-112">Requirements</span></span>  

 <span data-ttu-id="e0384-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e0384-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0384-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e0384-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e0384-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e0384-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e0384-116">**.NET Framework sürümleri:** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="e0384-116">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0384-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e0384-117">See also</span></span>

- [<span data-ttu-id="e0384-118">NewParameterizedObject Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e0384-118">NewParameterizedObject Method</span></span>](icordebugeval2-newparameterizedobject-method.md)
