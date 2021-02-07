---
description: 'Şu konuda daha fazla bilgi edinin: ıcorıbgarrayvalue:: GetElement Yöntemi'
title: ICorDebugArrayValue::GetElement Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.GetElement
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::GetElement
helpviewer_keywords:
- GetElement method [.NET Framework debugging]
- ICorDebugArrayValue::GetElement method [.NET Framework debugging]
ms.assetid: 7ac3cba5-c282-402e-b7ef-b46634f5176b
topic_type:
- apiref
ms.openlocfilehash: dfae074b78735934d1e71b13ce01c24741a5f2ed
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99723068"
---
# <a name="icordebugarrayvaluegetelement-method"></a><span data-ttu-id="a7b62-103">ICorDebugArrayValue::GetElement Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a7b62-103">ICorDebugArrayValue::GetElement Method</span></span>

<span data-ttu-id="a7b62-104">Verilen dizi öğesinin değerini alır.</span><span class="sxs-lookup"><span data-stu-id="a7b62-104">Gets the value of the given array element.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7b62-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a7b62-105">Syntax</span></span>  
  
```cpp  
HRESULT GetElement (  
    [in]  ULONG32          cdim,  
    [in, size_is(cdim), length_is(cdim)]
         ULONG32           indices[],  
    [out] ICorDebugValue   **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a7b62-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a7b62-106">Parameters</span></span>  

 `cdim`  
 <span data-ttu-id="a7b62-107">'ndaki Bu nesnenin boyut sayısı `ICorDebugArrayValue` .</span><span class="sxs-lookup"><span data-stu-id="a7b62-107">[in] The number of dimensions of this `ICorDebugArrayValue` object.</span></span>  
  
 <span data-ttu-id="a7b62-108">Bu değer Ayrıca, `indices` boyutu nesnenin boyut sayısına eşit olduğundan dizinin boyutudur `ICorDebugArrayValue` .</span><span class="sxs-lookup"><span data-stu-id="a7b62-108">This value is also the size of the `indices` array because its size is equal to the number of dimensions of the `ICorDebugArrayValue` object.</span></span>  
  
 `indices`  
 <span data-ttu-id="a7b62-109">'ndaki Her biri nesnenin boyutu içinde bir konum belirten Dizin değerleri dizisi `ICorDebugArrayValue` .</span><span class="sxs-lookup"><span data-stu-id="a7b62-109">[in] An array of index values, each of which specifies a position within a dimension of the `ICorDebugArrayValue` object.</span></span>  
  
 <span data-ttu-id="a7b62-110">Bu değer null olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="a7b62-110">This value must not be null.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="a7b62-111">dışı Belirtilen öğenin değerini temsil eden ICorDebugValue nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a7b62-111">[out] A pointer to the address of an ICorDebugValue object that represents the value of the specified element.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7b62-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a7b62-112">Requirements</span></span>  

 <span data-ttu-id="a7b62-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a7b62-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7b62-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a7b62-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a7b62-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a7b62-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a7b62-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7b62-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
