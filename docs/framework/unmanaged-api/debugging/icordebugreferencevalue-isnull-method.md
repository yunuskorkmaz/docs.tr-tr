---
title: "ICorDebugReferenceValue::IsNull Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugReferenceValue.IsNull
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugReferenceValue::IsNull
helpviewer_keywords:
- IsNull method, ICorDebugReferenceValue interface [.NET Framework debugging]
- ICorDebugReferenceValue::IsNull method [.NET Framework debugging]
ms.assetid: 99e8c8d7-a1c0-47c8-9dbd-03e0b2bcb4d5
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f8a7892900149380c979f0bee1a4229407af8c9c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugreferencevalueisnull-method"></a><span data-ttu-id="d8e34-102">ICorDebugReferenceValue::IsNull Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d8e34-102">ICorDebugReferenceValue::IsNull Method</span></span>
<span data-ttu-id="d8e34-103">Bu Icordebugreferencevalue bir null değer; bu durumda olup olmadığını belirten bir değer alır `ICorDebugReferenceValue` bir nesneye işaret etmiyor.</span><span class="sxs-lookup"><span data-stu-id="d8e34-103">Gets a value that indicates whether this ICorDebugReferenceValue is a null value, in which case the `ICorDebugReferenceValue` does not point to an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8e34-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d8e34-104">Syntax</span></span>  
  
```  
HRESULT IsNull (  
    [out] BOOL   *pbNull  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d8e34-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d8e34-105">Parameters</span></span>  
 `pbNull`  
 <span data-ttu-id="d8e34-106">[out] Boolean bir değer için bir işaretçi `true` bu `ICorDebugReferenceValue` nesnesi, null Aksi takdirde `pbNull` olan `false`.</span><span class="sxs-lookup"><span data-stu-id="d8e34-106">[out] A pointer to a Boolean value that is `true` if this `ICorDebugReferenceValue` object is null; otherwise, `pbNull` is `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8e34-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d8e34-107">Requirements</span></span>  
 <span data-ttu-id="d8e34-108">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8e34-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8e34-109">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d8e34-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d8e34-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d8e34-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d8e34-111">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8e34-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
