---
title: ICorDebugEval2::NewParameterizedObject Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.NewParameterizedObject
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::NewParameterizedObject
helpviewer_keywords:
- NewParameterizedObject method [.NET Framework debugging]
- ICorDebugEval2::NewParameterizedObject method [.NET Framework debugging]
ms.assetid: 3d705463-e640-4249-8036-4e8206d03cfe
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aae5f4c79acd6f92d42c2890ba64fa66e1b4bfbe
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67753593"
---
# <a name="icordebugeval2newparameterizedobject-method"></a><span data-ttu-id="6c9ea-102">ICorDebugEval2::NewParameterizedObject Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6c9ea-102">ICorDebugEval2::NewParameterizedObject Method</span></span>
<span data-ttu-id="6c9ea-103">Yeni bir parametreli tür nesnesi oluşturur ve nesnenin oluşturucusu yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="6c9ea-103">Instantiates a new parameterized type object and calls the object's constructor method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c9ea-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6c9ea-104">Syntax</span></span>  
  
```cpp  
HRESULT NewParameterizedObject (  
    [in] ICorDebugFunction     *pConstructor,  
    [in] ULONG32               nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType *ppTypeArgs[],  
    [in] ULONG32               nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6c9ea-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6c9ea-105">Parameters</span></span>  
 `pConstructor`  
 <span data-ttu-id="6c9ea-106">[in] Oluşturulacak nesnenin oluşturucusunun temsil eden bir ICorDebugFunction nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="6c9ea-106">[in] A pointer to an ICorDebugFunction object that represents the constructor of the object to be instantiated.</span></span>  
  
 `nTypeArgs`  
 <span data-ttu-id="6c9ea-107">[in] Tür bağımsız değişkenleri geçirildi.</span><span class="sxs-lookup"><span data-stu-id="6c9ea-107">[in] The number of type arguments passed.</span></span>  
  
 `ppTypeArgs`  
 <span data-ttu-id="6c9ea-108">[in] Her biri örneği oluşturulan nesne için bir tür bağımsız değişkeni temsil eden bir Icordebugtype nesneye işaret eden bir işaretçiler dizisi.</span><span class="sxs-lookup"><span data-stu-id="6c9ea-108">[in] An array of pointers, each of which points to an ICorDebugType object that represents a type argument for the object that is being instantiated.</span></span>  
  
 `nArgs`  
 <span data-ttu-id="6c9ea-109">[in] Bağımsız değişkenlerin sayısı, oluşturucuya geçirilen.</span><span class="sxs-lookup"><span data-stu-id="6c9ea-109">[in] The number of arguments passed to the constructor.</span></span>  
  
 `ppArgs`  
 <span data-ttu-id="6c9ea-110">[in] Oluşturucuya geçirilen bir bağımsız değişken değeri temsil eden bir Icordebugvalue nesne işaret her biri bir işaretçiler dizisi.</span><span class="sxs-lookup"><span data-stu-id="6c9ea-110">[in] An array of pointers, each of which points to an ICorDebugValue object that represents an argument value that is passed to the constructor.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6c9ea-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6c9ea-111">Remarks</span></span>  
 <span data-ttu-id="6c9ea-112">Nesnenin oluşturucusunun sürebilir <xref:System.Type> parametreleri.</span><span class="sxs-lookup"><span data-stu-id="6c9ea-112">The object's constructor may take <xref:System.Type> parameters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c9ea-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6c9ea-113">Requirements</span></span>  
 <span data-ttu-id="6c9ea-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c9ea-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c9ea-115">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6c9ea-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6c9ea-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6c9ea-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6c9ea-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c9ea-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
