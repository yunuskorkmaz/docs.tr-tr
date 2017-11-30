---
title: ICorDebugArrayValue::GetElementAtPosition Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugArrayValue.GetElementAtPosition
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugArrayValue::GetElementAtPosition
helpviewer_keywords:
- GetElementAtPosition method [.NET Framework debugging]
- ICorDebugArrayValue::GetElementAtPosition method [.NET Framework debugging]
ms.assetid: 6fd5eaa4-1997-4910-82f5-3887480db764
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 20af0afa395dd69dc8967aa9f39a8bf99eacf530
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugarrayvaluegetelementatposition-method"></a><span data-ttu-id="20fa1-102">ICorDebugArrayValue::GetElementAtPosition Metodu</span><span class="sxs-lookup"><span data-stu-id="20fa1-102">ICorDebugArrayValue::GetElementAtPosition Method</span></span>
<span data-ttu-id="20fa1-103">Verilen konumunda dizinin sıfır tabanlı, tek boyutlu bir dizi olarak davranma öğeyi alır.</span><span class="sxs-lookup"><span data-stu-id="20fa1-103">Gets the element at the given position, treating the array as a zero-based, single-dimensional array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20fa1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="20fa1-104">Syntax</span></span>  
  
```  
HRESULT GetElementAtPosition (  
    [in]  ULONG32          nPosition,  
    [out] ICorDebugValue   **ppValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="20fa1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="20fa1-105">Parameters</span></span>  
 `nPosition`  
 <span data-ttu-id="20fa1-106">[in] Alınacak öğenin konumu.</span><span class="sxs-lookup"><span data-stu-id="20fa1-106">[in] The position of the element to be retrieved.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="20fa1-107">[out] Bir işaretçi adresine Icordebugvalue nesnenin öğenin değerini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="20fa1-107">[out] A pointer to the address of an ICorDebugValue object that represents the value of the element.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="20fa1-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="20fa1-108">Remarks</span></span>  
 <span data-ttu-id="20fa1-109">Dizi düzeni C++ stilini bir çok boyutlu dizi düzenini izler.</span><span class="sxs-lookup"><span data-stu-id="20fa1-109">The layout of a multi-dimension array follows the C++ style of array layout.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20fa1-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="20fa1-110">Requirements</span></span>  
 <span data-ttu-id="20fa1-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="20fa1-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20fa1-112">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="20fa1-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="20fa1-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="20fa1-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="20fa1-114">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20fa1-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
