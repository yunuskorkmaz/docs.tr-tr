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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6846b866fd47674ca6b5fd187b580fd28e080fd0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59162312"
---
# <a name="icordebugevalnewobjectnoconstructor-method"></a><span data-ttu-id="a6195-102">ICorDebugEval::NewObjectNoConstructor Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a6195-102">ICorDebugEval::NewObjectNoConstructor Method</span></span>
<span data-ttu-id="a6195-103">Yeni bir nesne örneği belirtilen türe ait bir oluşturucu yöntemini çağırma girişimi olmadan ayırır.</span><span class="sxs-lookup"><span data-stu-id="a6195-103">Allocates a new object instance of the specified type, without attempting to call a constructor method.</span></span>  
  
 <span data-ttu-id="a6195-104">Bu yöntem .NET Framework 2.0 sürümünde artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="a6195-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="a6195-105">Kullanım [Icordebugeval2::newparameterizedobjectnoconstructor](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobjectnoconstructor-method.md) yerine.</span><span class="sxs-lookup"><span data-stu-id="a6195-105">Use [ICorDebugEval2::NewParameterizedObjectNoConstructor](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobjectnoconstructor-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6195-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a6195-106">Syntax</span></span>  
  
```  
HRESULT NewObjectNoConstructor (  
    [in] ICorDebugClass     *pClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a6195-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a6195-107">Parameters</span></span>  
 `pClass`  
 <span data-ttu-id="a6195-108">[in] Oluşturulacak nesnenin türünü temsil eden bir Icordebugclass nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="a6195-108">[in] Pointer to an ICorDebugClass object that represents the type of object to be instantiated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a6195-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a6195-109">Requirements</span></span>  
 <span data-ttu-id="a6195-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a6195-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6195-111">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a6195-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a6195-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a6195-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a6195-113">**.NET framework sürümleri:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="a6195-113">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6195-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a6195-114">See also</span></span>

- [<span data-ttu-id="a6195-115">NewParameterizedObjectNoConstructor Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a6195-115">NewParameterizedObjectNoConstructor Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobjectnoconstructor-method.md)
