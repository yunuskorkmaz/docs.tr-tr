---
title: ICorDebugArrayValue::GetElement Metodu
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 500e01955666c7a8e2bd1dcf9d34afe3aeb6b421
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33403350"
---
# <a name="icordebugarrayvaluegetelement-method"></a><span data-ttu-id="5ec37-102">ICorDebugArrayValue::GetElement Metodu</span><span class="sxs-lookup"><span data-stu-id="5ec37-102">ICorDebugArrayValue::GetElement Method</span></span>
<span data-ttu-id="5ec37-103">Verilen dizi öğenin değerini alır.</span><span class="sxs-lookup"><span data-stu-id="5ec37-103">Gets the value of the given array element.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ec37-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5ec37-104">Syntax</span></span>  
  
```  
HRESULT GetElement (  
    [in]  ULONG32          cdim,  
    [in, size_is(cdim), length_is(cdim)]   
         ULONG32           indices[],  
    [out] ICorDebugValue   **ppValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5ec37-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5ec37-105">Parameters</span></span>  
 `cdim`  
 <span data-ttu-id="5ec37-106">[in] Bu boyut sayısını `ICorDebugArrayValue` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="5ec37-106">[in] The number of dimensions of this `ICorDebugArrayValue` object.</span></span>  
  
 <span data-ttu-id="5ec37-107">Bu değer ayrıca boyutudur `indices` boyutuna boyutlarını sayıya eşit olduğundan dizi `ICorDebugArrayValue` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="5ec37-107">This value is also the size of the `indices` array because its size is equal to the number of dimensions of the `ICorDebugArrayValue` object.</span></span>  
  
 `indices`  
 <span data-ttu-id="5ec37-108">[in] Bir dizi dizini değerleri, her biri bir boyut içindeki konumu belirtir `ICorDebugArrayValue` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="5ec37-108">[in] An array of index values, each of which specifies a position within a dimension of the `ICorDebugArrayValue` object.</span></span>  
  
 <span data-ttu-id="5ec37-109">Bu değer null olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="5ec37-109">This value must not be null.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="5ec37-110">[out] Bir işaretçi adresine Icordebugvalue nesnenin belirtilen öğenin değerini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="5ec37-110">[out] A pointer to the address of an ICorDebugValue object that represents the value of the specified element.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ec37-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5ec37-111">Requirements</span></span>  
 <span data-ttu-id="5ec37-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5ec37-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ec37-113">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5ec37-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5ec37-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5ec37-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5ec37-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ec37-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
