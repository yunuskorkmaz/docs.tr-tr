---
description: ': ICorDebugReferenceValue:: SetValue yöntemi hakkında daha fazla bilgi edinin'
title: ICorDebugReferenceValue::SetValue Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugReferenceValue.SetValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugReferenceValue::SetValue
helpviewer_keywords:
- SetValue method, ICorDebugReferenceValue interface [.NET Framework debugging]
- ICorDebugReferenceValue::SetValue method [.NET Framework debugging]
ms.assetid: 3d3f6eec-d772-401f-a028-1a2ecdc31e95
topic_type:
- apiref
ms.openlocfilehash: 44909962d2716ddb606d98a2f6b3804247c581cd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99690918"
---
# <a name="icordebugreferencevaluesetvalue-method"></a><span data-ttu-id="cc4f0-103">ICorDebugReferenceValue::SetValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cc4f0-103">ICorDebugReferenceValue::SetValue Method</span></span>

<span data-ttu-id="cc4f0-104">Belirtilen bellek adresini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="cc4f0-104">Sets the specified memory address.</span></span> <span data-ttu-id="cc4f0-105">Yani bu yöntem, bu ICorDebugReferenceValue öğesini bir nesneyi işaret etmek üzere ayarlar.</span><span class="sxs-lookup"><span data-stu-id="cc4f0-105">That is, this method sets this ICorDebugReferenceValue to point to an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc4f0-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cc4f0-106">Syntax</span></span>  
  
```cpp  
HRESULT SetValue (  
    [in] CORDB_ADDRESS    value  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cc4f0-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cc4f0-107">Parameters</span></span>  

 `value`  
 <span data-ttu-id="cc4f0-108">'ndaki `CORDB_ADDRESS` Bu noktaların gösterdiği nesnenin adresini belirten bir değer `ICorDebugReferenceValue` .</span><span class="sxs-lookup"><span data-stu-id="cc4f0-108">[in] A `CORDB_ADDRESS` value that specifies the address of the object to which this `ICorDebugReferenceValue` points.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc4f0-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cc4f0-109">Requirements</span></span>  

 <span data-ttu-id="cc4f0-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cc4f0-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc4f0-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="cc4f0-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cc4f0-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="cc4f0-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cc4f0-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc4f0-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
