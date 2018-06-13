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
ms.openlocfilehash: 3e99cafe39a030a412bf33aeb9d96d5006ca02df
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33415967"
---
# <a name="icordebugevalnewobjectnoconstructor-method"></a><span data-ttu-id="228ba-102">ICorDebugEval::NewObjectNoConstructor Yöntemi</span><span class="sxs-lookup"><span data-stu-id="228ba-102">ICorDebugEval::NewObjectNoConstructor Method</span></span>
<span data-ttu-id="228ba-103">Yeni bir nesne örneği belirtilen türde bir oluşturucu yöntemi çağrı girişimi olmadan ayırır.</span><span class="sxs-lookup"><span data-stu-id="228ba-103">Allocates a new object instance of the specified type, without attempting to call a constructor method.</span></span>  
  
 <span data-ttu-id="228ba-104">Bu yöntem .NET Framework 2.0 sürümünde kullanımdan kalkmıştır.</span><span class="sxs-lookup"><span data-stu-id="228ba-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="228ba-105">Kullanım [Icordebugeval2::newparameterizedobjectnoconstructor](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobjectnoconstructor-method.md) yerine.</span><span class="sxs-lookup"><span data-stu-id="228ba-105">Use [ICorDebugEval2::NewParameterizedObjectNoConstructor](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobjectnoconstructor-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="228ba-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="228ba-106">Syntax</span></span>  
  
```  
HRESULT NewObjectNoConstructor (  
    [in] ICorDebugClass     *pClass  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="228ba-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="228ba-107">Parameters</span></span>  
 `pClass`  
 <span data-ttu-id="228ba-108">[in] İşaretçi Icordebugclass nesneye örneğinin oluşturulması için nesne türünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="228ba-108">[in] Pointer to an ICorDebugClass object that represents the type of object to be instantiated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="228ba-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="228ba-109">Requirements</span></span>  
 <span data-ttu-id="228ba-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="228ba-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="228ba-111">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="228ba-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="228ba-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="228ba-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="228ba-113">**.NET framework sürümleri:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="228ba-113">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="228ba-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="228ba-114">See Also</span></span>  
 [<span data-ttu-id="228ba-115">NewParameterizedObjectNoConstructor Yöntemi</span><span class="sxs-lookup"><span data-stu-id="228ba-115">NewParameterizedObjectNoConstructor Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobjectnoconstructor-method.md)
