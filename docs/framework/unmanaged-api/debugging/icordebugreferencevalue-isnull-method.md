---
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 972df4613255dc1b71801e02d387a735dfc632c0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61782941"
---
# <a name="icordebugreferencevalueisnull-method"></a><span data-ttu-id="4ea96-102">ICorDebugReferenceValue::IsNull Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4ea96-102">ICorDebugReferenceValue::IsNull Method</span></span>
<span data-ttu-id="4ea96-103">Bu Icordebugreferencevalue null değeri, bu durumda olup olmadığını belirten bir değer alır `ICorDebugReferenceValue` bir nesneye işaret etmiyor.</span><span class="sxs-lookup"><span data-stu-id="4ea96-103">Gets a value that indicates whether this ICorDebugReferenceValue is a null value, in which case the `ICorDebugReferenceValue` does not point to an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ea96-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4ea96-104">Syntax</span></span>  
  
```  
HRESULT IsNull (  
    [out] BOOL   *pbNull  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4ea96-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4ea96-105">Parameters</span></span>  
 `pbNull`  
 <span data-ttu-id="4ea96-106">[out] Boolean bir değer için bir işaretçi `true` bu `ICorDebugReferenceValue` nesnesi null; Aksi takdirde `pbNull` olduğu `false`.</span><span class="sxs-lookup"><span data-stu-id="4ea96-106">[out] A pointer to a Boolean value that is `true` if this `ICorDebugReferenceValue` object is null; otherwise, `pbNull` is `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4ea96-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4ea96-107">Requirements</span></span>  
 <span data-ttu-id="4ea96-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4ea96-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4ea96-109">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4ea96-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4ea96-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4ea96-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4ea96-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4ea96-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
