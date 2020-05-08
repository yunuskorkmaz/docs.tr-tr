---
title: ICorDebugArrayValue::GetBaseIndicies Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.GetBaseIndicies
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::GetBaseIndicies
helpviewer_keywords:
- ICorDebugArrayValue::GetBaseIndicies method [.NET Framework debugging]
- GetBaseIndicies method [.NET Framework debugging]
ms.assetid: 868b339b-acdb-4fe0-91c7-b85f4fba99eb
topic_type:
- apiref
ms.openlocfilehash: 9aadbe7c6f18c6b15350267d1f9ecaa3a23cdd20
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895065"
---
# <a name="icordebugarrayvaluegetbaseindicies-method"></a><span data-ttu-id="ca588-102">ICorDebugArrayValue::GetBaseIndicies Metodu</span><span class="sxs-lookup"><span data-stu-id="ca588-102">ICorDebugArrayValue::GetBaseIndicies Method</span></span>
<span data-ttu-id="ca588-103">Dizideki her boyutun temel dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="ca588-103">Gets the base index of each dimension in the array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca588-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ca588-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBaseIndicies (  
    [in] ULONG32          cdim,  
    [out, size_is(cdim), length_is(cdim)]
        ULONG32           indicies[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ca588-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ca588-105">Parameters</span></span>  
 `cdim`  
 <span data-ttu-id="ca588-106">'ndaki Bu `ICorDebugArrayValue` nesnenin boyut sayısı.</span><span class="sxs-lookup"><span data-stu-id="ca588-106">[in] The number of dimensions of this `ICorDebugArrayValue` object.</span></span> <span data-ttu-id="ca588-107">Bu değer Ayrıca, boyutu `indicies` `ICorDebugArrayValue` nesnenin boyut sayısına eşit olduğundan dizinin boyutudur.</span><span class="sxs-lookup"><span data-stu-id="ca588-107">This value is also the size of the `indicies` array because its size is equal to the number of dimensions of the `ICorDebugArrayValue` object.</span></span>  
  
 `indicies`  
 <span data-ttu-id="ca588-108">dışı Her biri, bu `ICorDebugArrayValue` nesnenin bir boyutunun temel dizini (yani, başlangıç dizini) olan tamsayılar dizisi.</span><span class="sxs-lookup"><span data-stu-id="ca588-108">[out] An array of integers, each of which is the base index (that is, the starting index) of a dimension of this `ICorDebugArrayValue` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca588-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ca588-109">Requirements</span></span>  
 <span data-ttu-id="ca588-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ca588-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca588-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ca588-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ca588-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ca588-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ca588-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca588-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
