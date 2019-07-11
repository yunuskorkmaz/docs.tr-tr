---
title: ICorDebugEval2::NewParameterizedObjectNoConstructor Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.NewParameterizedObjectNoConstructor
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::NewParameterizedObjectNoConstructor
helpviewer_keywords:
- NewParameterizedObjectNoConstructor method [.NET Framework debugging]
- ICorDebugEval2::NewParameterizedObjectNoConstructor method [.NET Framework debugging]
ms.assetid: f15b5b78-94f4-4eb9-b3b3-a621272f357c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e4434f5d0eaa45c9cfcbadb20b29564f0643a2dc
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67754438"
---
# <a name="icordebugeval2newparameterizedobjectnoconstructor-method"></a><span data-ttu-id="f79ba-102">ICorDebugEval2::NewParameterizedObjectNoConstructor Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f79ba-102">ICorDebugEval2::NewParameterizedObjectNoConstructor Method</span></span>
<span data-ttu-id="f79ba-103">Belirtilen sınıfın yeni bir parametreli tür nesnesi, bir yapıcı yöntemini çağırma girişimi olmadan başlatır.</span><span class="sxs-lookup"><span data-stu-id="f79ba-103">Instantiates a new parameterized type object of the specified class without attempting to call a constructor method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f79ba-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f79ba-104">Syntax</span></span>  
  
```cpp  
HRESULT NewParameterizedObjectNoConstructor (  
    [in] ICorDebugClass        *pClass,  
    [in] ULONG32               nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType *ppTypeArgs[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f79ba-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f79ba-105">Parameters</span></span>  
 `pClass`  
 <span data-ttu-id="f79ba-106">[in] Oluşturulacak nesnenin sınıfını temsil eden bir Icordebugclass nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="f79ba-106">[in] A pointer to an ICorDebugClass object that represents the class of the object to be instantiated.</span></span>  
  
 `nTypeArgs`  
 <span data-ttu-id="f79ba-107">[in] Tür bağımsız değişkenleri geçirildi.</span><span class="sxs-lookup"><span data-stu-id="f79ba-107">[in] The number of type arguments passed.</span></span>  
  
 `ppTypeArgs`  
 <span data-ttu-id="f79ba-108">[in] Her biri örneği oluşturulan nesne için bir tür bağımsız değişkeni temsil eden bir Icordebugtype nesneye işaret eden bir işaretçiler dizisi.</span><span class="sxs-lookup"><span data-stu-id="f79ba-108">[in] An array of pointers, each of which points to an ICorDebugType object that represents a type argument for the object that is being instantiated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f79ba-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f79ba-109">Remarks</span></span>  
 <span data-ttu-id="f79ba-110">`NewParameterizedObjectNoConstructor` Yanlış sayıda tür bağımsız değişkenleri varsa yöntemi başarısız olur ya da tür bağımsız değişkeni yanlış tür geçirildi.</span><span class="sxs-lookup"><span data-stu-id="f79ba-110">The `NewParameterizedObjectNoConstructor` method will fail if an incorrect number of type arguments or the wrong types of type arguments are passed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f79ba-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f79ba-111">Requirements</span></span>  
 <span data-ttu-id="f79ba-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f79ba-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f79ba-113">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f79ba-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f79ba-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f79ba-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f79ba-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f79ba-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
