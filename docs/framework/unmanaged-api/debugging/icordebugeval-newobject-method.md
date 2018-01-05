---
title: "ICorDebugEval::NewObject Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugEval.NewObject
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugEval::NewObject
helpviewer_keywords:
- NewObject method [.NET Framework debugging]
- ICorDebugEval::NewObject method [.NET Framework debugging]
ms.assetid: ce3025e8-defa-4c5e-8298-f49d71fa5736
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 98c885e7ffd4b35bcc3af34757509910c78c0c90
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugevalnewobject-method"></a><span data-ttu-id="376b1-102">ICorDebugEval::NewObject Yöntemi</span><span class="sxs-lookup"><span data-stu-id="376b1-102">ICorDebugEval::NewObject Method</span></span>
<span data-ttu-id="376b1-103">Yeni bir nesne örneği ayırır ve belirtilen Oluşturucusu yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="376b1-103">Allocates a new object instance and calls the specified constructor method.</span></span>  
  
 <span data-ttu-id="376b1-104">Bu yöntem .NET Framework 2.0 sürümünde kullanımdan kalkmıştır.</span><span class="sxs-lookup"><span data-stu-id="376b1-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="376b1-105">Kullanım [Icordebugeval2::newparameterizedobject](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md) yerine.</span><span class="sxs-lookup"><span data-stu-id="376b1-105">Use [ICorDebugEval2::NewParameterizedObject](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="376b1-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="376b1-106">Syntax</span></span>  
  
```  
HRESULT NewObject (  
    [in] ICorDebugFunction  *pConstructor,  
    [in] ULONG32            nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="376b1-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="376b1-107">Parameters</span></span>  
 `pConstructor`  
 <span data-ttu-id="376b1-108">[in] Çağrılacak Oluşturucusu.</span><span class="sxs-lookup"><span data-stu-id="376b1-108">[in] The constructor to be called.</span></span>  
  
 `nArgs`  
 <span data-ttu-id="376b1-109">[in] Boyutunu `ppArgs` dizi.</span><span class="sxs-lookup"><span data-stu-id="376b1-109">[in] The size of the `ppArgs` array.</span></span>  
  
 `ppArgs`  
 <span data-ttu-id="376b1-110">[in] Her biri bir bağımsız değişken oluşturucuya geçirilen temsil eden bir Icordebugvalue nesneler dizisi.</span><span class="sxs-lookup"><span data-stu-id="376b1-110">[in] An array of ICorDebugValue objects, each of which represents an argument to be passed to the constructor.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="376b1-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="376b1-111">Requirements</span></span>  
 <span data-ttu-id="376b1-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="376b1-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="376b1-113">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="376b1-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="376b1-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="376b1-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="376b1-115">**.NET framework sürümleri:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="376b1-115">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="376b1-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="376b1-116">See Also</span></span>  
 [<span data-ttu-id="376b1-117">NewParameterizedObject Yöntemi</span><span class="sxs-lookup"><span data-stu-id="376b1-117">NewParameterizedObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md)
