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
ms.openlocfilehash: 7c6d1905cdbd12b960014e687034ea9d163b68d7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179033"
---
# <a name="icordebugarrayvaluegetbaseindicies-method"></a><span data-ttu-id="4fc49-102">ICorDebugArrayValue::GetBaseIndicies Metodu</span><span class="sxs-lookup"><span data-stu-id="4fc49-102">ICorDebugArrayValue::GetBaseIndicies Method</span></span>
<span data-ttu-id="4fc49-103">Dizideki her boyutun temel dizisini alır.</span><span class="sxs-lookup"><span data-stu-id="4fc49-103">Gets the base index of each dimension in the array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4fc49-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4fc49-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBaseIndicies (  
    [in] ULONG32          cdim,  
    [out, size_is(cdim), length_is(cdim)]
        ULONG32           indicies[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4fc49-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4fc49-105">Parameters</span></span>  
 `cdim`  
 <span data-ttu-id="4fc49-106">[içinde] Bu `ICorDebugArrayValue` nesnenin boyutlarının sayısı.</span><span class="sxs-lookup"><span data-stu-id="4fc49-106">[in] The number of dimensions of this `ICorDebugArrayValue` object.</span></span> <span data-ttu-id="4fc49-107">Boyutu `indicies` `ICorDebugArrayValue` nesnenin boyut sayısına eşit olduğundan, bu değer de dizinin boyutudur.</span><span class="sxs-lookup"><span data-stu-id="4fc49-107">This value is also the size of the `indicies` array because its size is equal to the number of dimensions of the `ICorDebugArrayValue` object.</span></span>  
  
 `indicies`  
 <span data-ttu-id="4fc49-108">[çıkış] Her biri bu `ICorDebugArrayValue` nesnenin bir boyutunun temel dizini (yani başlangıç dizini) olan bir tamsayı dizisi.</span><span class="sxs-lookup"><span data-stu-id="4fc49-108">[out] An array of integers, each of which is the base index (that is, the starting index) of a dimension of this `ICorDebugArrayValue` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4fc49-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4fc49-109">Requirements</span></span>  
 <span data-ttu-id="4fc49-110">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4fc49-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4fc49-111">**Üstbilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4fc49-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4fc49-112">**Kütüphane:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4fc49-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4fc49-113">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4fc49-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
