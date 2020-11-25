---
title: ICorDebugEval::NewObjectNoConstructor Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugEval.NewObjectNoConstructor
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::NewObjectNoConstructor
helpviewer_keywords:
- NewObjectNoConstructor method [.NET Framework debugging]
- ICorDebugEval::NewObjectNoConstructor method [.NET Framework debugging]
ms.assetid: 80d509ca-b5e3-4c46-9c14-800db73d9bf7
topic_type:
- apiref
ms.openlocfilehash: bb27ec755fb83dc71af7dd48b5ed6e7699436335
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729735"
---
# <a name="icordebugevalnewobjectnoconstructor-method"></a><span data-ttu-id="c6016-102">ICorDebugEval::NewObjectNoConstructor Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c6016-102">ICorDebugEval::NewObjectNoConstructor Method</span></span>

<span data-ttu-id="c6016-103">Bir Oluşturucu yöntemini çağırmaya çalışmadan, belirtilen türün yeni bir nesne örneğini ayırır.</span><span class="sxs-lookup"><span data-stu-id="c6016-103">Allocates a new object instance of the specified type, without attempting to call a constructor method.</span></span>  
  
 <span data-ttu-id="c6016-104">Bu yöntem .NET Framework sürüm 2,0 ' de kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="c6016-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="c6016-105">Bunun yerine [ICorDebugEval2:: NewParameterizedObjectNoConstructor](icordebugeval2-newparameterizedobjectnoconstructor-method.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="c6016-105">Use [ICorDebugEval2::NewParameterizedObjectNoConstructor](icordebugeval2-newparameterizedobjectnoconstructor-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6016-106">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="c6016-106">Syntax</span></span>  
  
```cpp  
HRESULT NewObjectNoConstructor (  
    [in] ICorDebugClass     *pClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c6016-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c6016-107">Parameters</span></span>  

 `pClass`  
 <span data-ttu-id="c6016-108">'ndaki Örneklendiği nesnenin türünü temsil eden ICorDebugClass nesnesine yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c6016-108">[in] Pointer to an ICorDebugClass object that represents the type of object to be instantiated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c6016-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c6016-109">Requirements</span></span>  

 <span data-ttu-id="c6016-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c6016-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c6016-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c6016-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c6016-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c6016-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c6016-113">**.NET Framework sürümleri:** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="c6016-113">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6016-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c6016-114">See also</span></span>

- [<span data-ttu-id="c6016-115">NewParameterizedObjectNoConstructor Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c6016-115">NewParameterizedObjectNoConstructor Method</span></span>](icordebugeval2-newparameterizedobjectnoconstructor-method.md)
