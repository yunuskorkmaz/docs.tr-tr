---
title: ICorDebugEval2::CreateValueForType Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.CreateValueForType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::CreateValueForType
helpviewer_keywords:
- CreateValueForType method [.NET Framework debugging]
- ICorDebugEval2::CreateValueForType method [.NET Framework debugging]
ms.assetid: ea38ae20-7e0a-427a-be77-d78fae719d82
topic_type:
- apiref
ms.openlocfilehash: 0b17bd729733665fbc4645aecd2e588b7eba14bb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729700"
---
# <a name="icordebugeval2createvaluefortype-method"></a><span data-ttu-id="efb32-102">ICorDebugEval2::CreateValueForType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="efb32-102">ICorDebugEval2::CreateValueForType Method</span></span>

<span data-ttu-id="efb32-103">Belirtilen türdeki yeni bir ICorDebugValue değeri, sıfır veya null değeri olan bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="efb32-103">Gets a pointer to a new ICorDebugValue of the specified type, with an initial value of zero or null.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="efb32-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="efb32-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateValueForType (  
    [in] ICorDebugType         *pType,  
    [out] ICorDebugValue       **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="efb32-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="efb32-105">Parameters</span></span>  

 `pType`  
 <span data-ttu-id="efb32-106">'ndaki Türü temsil eden ICorDebugType nesnesine yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="efb32-106">[in] Pointer to an ICorDebugType object that represents the type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="efb32-107">dışı `ICorDebugValue` Değeri temsil eden bir nesnenin adresine yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="efb32-107">[out] Pointer to the address of an `ICorDebugValue` object that represents the value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="efb32-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="efb32-108">Remarks</span></span>  

 <span data-ttu-id="efb32-109">`CreateValueForType` gibi oluşturulmuş türler de dahil olmak üzere, rastgele bir nesne türü belirtmenize izin vererek [ıcorınkıx Geval:: CreateValue](icordebugeval-createvalue-method.md) öğesini genelleştirir `List<int>` .</span><span class="sxs-lookup"><span data-stu-id="efb32-109">`CreateValueForType` generalizes [ICorDebugEval::CreateValue](icordebugeval-createvalue-method.md) by allowing you to specify an arbitrary object type, including constructed types such as `List<int>`.</span></span> <span data-ttu-id="efb32-110">Bu yöntemin tek amacı, bir işlev değerlendirmesine geçirilebilecek bir değer üretmesidir.</span><span class="sxs-lookup"><span data-stu-id="efb32-110">The only purpose of this method is to generate a value that can be passed to a function evaluation.</span></span>  
  
 <span data-ttu-id="efb32-111">Tür bir sınıf veya değer türü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="efb32-111">The type must be a class or a value type.</span></span> <span data-ttu-id="efb32-112">Dizi değerleri veya dize değerleri oluşturmak için bu yöntemi kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="efb32-112">You cannot use this method to create array values or string values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="efb32-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="efb32-113">Requirements</span></span>  

 <span data-ttu-id="efb32-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="efb32-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="efb32-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="efb32-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="efb32-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="efb32-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="efb32-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="efb32-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
