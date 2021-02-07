---
description: ': ICorDebugReferenceValue:: IsNull Yöntemi hakkında daha fazla bilgi edinin'
title: ICorDebugReferenceValue::IsNull Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugReferenceValue.IsNull
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugReferenceValue::IsNull
helpviewer_keywords:
- IsNull method, ICorDebugReferenceValue interface [.NET Framework debugging]
- ICorDebugReferenceValue::IsNull method [.NET Framework debugging]
ms.assetid: 99e8c8d7-a1c0-47c8-9dbd-03e0b2bcb4d5
topic_type:
- apiref
ms.openlocfilehash: 9fffc869e20d1d3aa3a347ff2e026e6b55e6bd4f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99691035"
---
# <a name="icordebugreferencevalueisnull-method"></a><span data-ttu-id="e0d0b-103">ICorDebugReferenceValue::IsNull Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e0d0b-103">ICorDebugReferenceValue::IsNull Method</span></span>

<span data-ttu-id="e0d0b-104">Bu ICorDebugReferenceValue değerinin null bir değer olup olmadığını belirten bir değer alır, bu durumda `ICorDebugReferenceValue` bir nesneyi işaret etmez.</span><span class="sxs-lookup"><span data-stu-id="e0d0b-104">Gets a value that indicates whether this ICorDebugReferenceValue is a null value, in which case the `ICorDebugReferenceValue` does not point to an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0d0b-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e0d0b-105">Syntax</span></span>  
  
```cpp  
HRESULT IsNull (  
    [out] BOOL   *pbNull  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e0d0b-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e0d0b-106">Parameters</span></span>  

 `pbNull`  
 <span data-ttu-id="e0d0b-107">dışı Bu nesne null ise bir Boolean değeri işaretçisi `true` `ICorDebugReferenceValue` ; Aksi durumda, `pbNull` `false` .</span><span class="sxs-lookup"><span data-stu-id="e0d0b-107">[out] A pointer to a Boolean value that is `true` if this `ICorDebugReferenceValue` object is null; otherwise, `pbNull` is `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0d0b-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e0d0b-108">Requirements</span></span>  

 <span data-ttu-id="e0d0b-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e0d0b-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0d0b-110">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e0d0b-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e0d0b-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e0d0b-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e0d0b-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0d0b-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
