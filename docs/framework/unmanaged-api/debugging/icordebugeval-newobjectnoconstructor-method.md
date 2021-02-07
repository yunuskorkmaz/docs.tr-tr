---
description: 'Şu konuda daha fazla bilgi edinin: ıcorıbgeval:: NewObjectNoConstructor yöntemi'
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
ms.openlocfilehash: 4bc8f95da1a554091052dc7e7f49aef4f494578d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99693817"
---
# <a name="icordebugevalnewobjectnoconstructor-method"></a><span data-ttu-id="a4f6a-103">ICorDebugEval::NewObjectNoConstructor Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a4f6a-103">ICorDebugEval::NewObjectNoConstructor Method</span></span>

<span data-ttu-id="a4f6a-104">Bir Oluşturucu yöntemini çağırmaya çalışmadan, belirtilen türün yeni bir nesne örneğini ayırır.</span><span class="sxs-lookup"><span data-stu-id="a4f6a-104">Allocates a new object instance of the specified type, without attempting to call a constructor method.</span></span>  
  
 <span data-ttu-id="a4f6a-105">Bu yöntem .NET Framework sürüm 2,0 ' de kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="a4f6a-105">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="a4f6a-106">Bunun yerine [ICorDebugEval2:: NewParameterizedObjectNoConstructor](icordebugeval2-newparameterizedobjectnoconstructor-method.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="a4f6a-106">Use [ICorDebugEval2::NewParameterizedObjectNoConstructor](icordebugeval2-newparameterizedobjectnoconstructor-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4f6a-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a4f6a-107">Syntax</span></span>  
  
```cpp  
HRESULT NewObjectNoConstructor (  
    [in] ICorDebugClass     *pClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a4f6a-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a4f6a-108">Parameters</span></span>  

 `pClass`  
 <span data-ttu-id="a4f6a-109">'ndaki Örneklendiği nesnenin türünü temsil eden ICorDebugClass nesnesine yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a4f6a-109">[in] Pointer to an ICorDebugClass object that represents the type of object to be instantiated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a4f6a-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a4f6a-110">Requirements</span></span>  

 <span data-ttu-id="a4f6a-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a4f6a-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a4f6a-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a4f6a-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a4f6a-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a4f6a-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a4f6a-114">**.NET Framework sürümleri:** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="a4f6a-114">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4f6a-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a4f6a-115">See also</span></span>

- [<span data-ttu-id="a4f6a-116">NewParameterizedObjectNoConstructor Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a4f6a-116">NewParameterizedObjectNoConstructor Method</span></span>](icordebugeval2-newparameterizedobjectnoconstructor-method.md)
