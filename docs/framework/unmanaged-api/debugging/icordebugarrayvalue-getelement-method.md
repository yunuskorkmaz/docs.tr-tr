---
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
ms.openlocfilehash: adcb7b5a27f3b8c63dbbb660a23b5c891f84ac46
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179005"
---
# <a name="icordebugarrayvaluegetelement-method"></a><span data-ttu-id="0db20-102">ICorDebugArrayValue::GetElement Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0db20-102">ICorDebugArrayValue::GetElement Method</span></span>
<span data-ttu-id="0db20-103">Verilen dizi öğesinin değerini alır.</span><span class="sxs-lookup"><span data-stu-id="0db20-103">Gets the value of the given array element.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0db20-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0db20-104">Syntax</span></span>  
  
```cpp  
HRESULT GetElement (  
    [in]  ULONG32          cdim,  
    [in, size_is(cdim), length_is(cdim)]
         ULONG32           indices[],  
    [out] ICorDebugValue   **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0db20-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0db20-105">Parameters</span></span>  
 `cdim`  
 <span data-ttu-id="0db20-106">[içinde] Bu `ICorDebugArrayValue` nesnenin boyutlarının sayısı.</span><span class="sxs-lookup"><span data-stu-id="0db20-106">[in] The number of dimensions of this `ICorDebugArrayValue` object.</span></span>  
  
 <span data-ttu-id="0db20-107">Boyutu `indices` `ICorDebugArrayValue` nesnenin boyut sayısına eşit olduğundan, bu değer de dizinin boyutudur.</span><span class="sxs-lookup"><span data-stu-id="0db20-107">This value is also the size of the `indices` array because its size is equal to the number of dimensions of the `ICorDebugArrayValue` object.</span></span>  
  
 `indices`  
 <span data-ttu-id="0db20-108">[içinde] Her biri `ICorDebugArrayValue` nesnenin bir boyutu içinde bir konum belirtir dizin değerleri dizisi.</span><span class="sxs-lookup"><span data-stu-id="0db20-108">[in] An array of index values, each of which specifies a position within a dimension of the `ICorDebugArrayValue` object.</span></span>  
  
 <span data-ttu-id="0db20-109">Bu değer null olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="0db20-109">This value must not be null.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="0db20-110">[çıkış] Belirtilen öğenin değerini temsil eden bir ICorDebugValue nesnesinin adresine işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0db20-110">[out] A pointer to the address of an ICorDebugValue object that represents the value of the specified element.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0db20-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0db20-111">Requirements</span></span>  
 <span data-ttu-id="0db20-112">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0db20-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0db20-113">**Üstbilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0db20-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0db20-114">**Kütüphane:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0db20-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0db20-115">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0db20-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
