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
ms.openlocfilehash: 9c2d6a66eca080b480b508afea36c33b3e0aeec0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59178236"
---
# <a name="icordebugevalnewobject-method"></a><span data-ttu-id="187d9-102">ICorDebugEval::NewObject Yöntemi</span><span class="sxs-lookup"><span data-stu-id="187d9-102">ICorDebugEval::NewObject Method</span></span>
<span data-ttu-id="187d9-103">Yeni bir nesne örneğini tahsis eder ve belirtilen yapıcı yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="187d9-103">Allocates a new object instance and calls the specified constructor method.</span></span>  
  
 <span data-ttu-id="187d9-104">Bu yöntem .NET Framework 2.0 sürümünde artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="187d9-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="187d9-105">Kullanım [Icordebugeval2::newparameterizedobject](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md) yerine.</span><span class="sxs-lookup"><span data-stu-id="187d9-105">Use [ICorDebugEval2::NewParameterizedObject](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="187d9-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="187d9-106">Syntax</span></span>  
  
```  
HRESULT NewObject (  
    [in] ICorDebugFunction  *pConstructor,  
    [in] ULONG32            nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="187d9-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="187d9-107">Parameters</span></span>  
 `pConstructor`  
 <span data-ttu-id="187d9-108">[in] Çağrılacak Oluşturucusu.</span><span class="sxs-lookup"><span data-stu-id="187d9-108">[in] The constructor to be called.</span></span>  
  
 `nArgs`  
 <span data-ttu-id="187d9-109">[in] Boyutu `ppArgs` dizisi.</span><span class="sxs-lookup"><span data-stu-id="187d9-109">[in] The size of the `ppArgs` array.</span></span>  
  
 `ppArgs`  
 <span data-ttu-id="187d9-110">[in] Oluşturucuya geçirilecek bağımsız değişken her biri temsil eden Icordebugvalue nesnelerin dizisi.</span><span class="sxs-lookup"><span data-stu-id="187d9-110">[in] An array of ICorDebugValue objects, each of which represents an argument to be passed to the constructor.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="187d9-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="187d9-111">Requirements</span></span>  
 <span data-ttu-id="187d9-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="187d9-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="187d9-113">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="187d9-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="187d9-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="187d9-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="187d9-115">**.NET framework sürümleri:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="187d9-115">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="187d9-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="187d9-116">See also</span></span>

- [<span data-ttu-id="187d9-117">NewParameterizedObject Yöntemi</span><span class="sxs-lookup"><span data-stu-id="187d9-117">NewParameterizedObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md)
