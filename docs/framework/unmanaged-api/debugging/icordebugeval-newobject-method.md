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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5ff378602fc7338263ef49aee6802d2138bab9d2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33413178"
---
# <a name="icordebugevalnewobject-method"></a><span data-ttu-id="3f43f-102">ICorDebugEval::NewObject Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3f43f-102">ICorDebugEval::NewObject Method</span></span>
<span data-ttu-id="3f43f-103">Yeni bir nesne örneği ayırır ve belirtilen Oluşturucusu yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="3f43f-103">Allocates a new object instance and calls the specified constructor method.</span></span>  
  
 <span data-ttu-id="3f43f-104">Bu yöntem .NET Framework 2.0 sürümünde kullanımdan kalkmıştır.</span><span class="sxs-lookup"><span data-stu-id="3f43f-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="3f43f-105">Kullanım [Icordebugeval2::newparameterizedobject](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md) yerine.</span><span class="sxs-lookup"><span data-stu-id="3f43f-105">Use [ICorDebugEval2::NewParameterizedObject](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f43f-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3f43f-106">Syntax</span></span>  
  
```  
HRESULT NewObject (  
    [in] ICorDebugFunction  *pConstructor,  
    [in] ULONG32            nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3f43f-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3f43f-107">Parameters</span></span>  
 `pConstructor`  
 <span data-ttu-id="3f43f-108">[in] Çağrılacak Oluşturucusu.</span><span class="sxs-lookup"><span data-stu-id="3f43f-108">[in] The constructor to be called.</span></span>  
  
 `nArgs`  
 <span data-ttu-id="3f43f-109">[in] Boyutunu `ppArgs` dizi.</span><span class="sxs-lookup"><span data-stu-id="3f43f-109">[in] The size of the `ppArgs` array.</span></span>  
  
 `ppArgs`  
 <span data-ttu-id="3f43f-110">[in] Her biri bir bağımsız değişken oluşturucuya geçirilen temsil eden bir Icordebugvalue nesneler dizisi.</span><span class="sxs-lookup"><span data-stu-id="3f43f-110">[in] An array of ICorDebugValue objects, each of which represents an argument to be passed to the constructor.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f43f-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3f43f-111">Requirements</span></span>  
 <span data-ttu-id="3f43f-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3f43f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f43f-113">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3f43f-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3f43f-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3f43f-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3f43f-115">**.NET framework sürümleri:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="3f43f-115">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f43f-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3f43f-116">See Also</span></span>  
 [<span data-ttu-id="3f43f-117">NewParameterizedObject Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3f43f-117">NewParameterizedObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md)
