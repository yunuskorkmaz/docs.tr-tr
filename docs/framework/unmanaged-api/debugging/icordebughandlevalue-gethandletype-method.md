---
title: ICorDebugHandleValue::GetHandleType Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugHandleValue.GetHandleType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHandleValue::GetHandleType
helpviewer_keywords:
- GetHandleType method [.NET Framework debugging]
- ICorDebugHandleValue::GetHandleType method [.NET Framework debugging]
ms.assetid: d5e7b12d-835a-4e86-ae2f-d658d4f1c67c
topic_type:
- apiref
ms.openlocfilehash: 72ef9a0fe4cd08ce67594600375953c249243d4f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734159"
---
# <a name="icordebughandlevaluegethandletype-method"></a><span data-ttu-id="21afc-102">ICorDebugHandleValue::GetHandleType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="21afc-102">ICorDebugHandleValue::GetHandleType Method</span></span>

<span data-ttu-id="21afc-103">Bu ıcorıınfo Ghandlivalue nesnesinin başvurduğu tanıtıcı türünü gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="21afc-103">Gets a value that indicates the kind of handle referenced by this ICorDebugHandleValue object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21afc-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="21afc-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHandleType (  
    [out] CorDebugHandleType  *pType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="21afc-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="21afc-105">Parameters</span></span>  

 `pType`  
 <span data-ttu-id="21afc-106">dışı Bu tanıtıcının türünü gösteren Cordebugghandlitype numaralandırması değerine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="21afc-106">[out] A pointer to a value of the CorDebugHandleType enumeration that indicates the type of this handle.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21afc-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="21afc-107">Requirements</span></span>  

 <span data-ttu-id="21afc-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21afc-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21afc-109">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="21afc-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="21afc-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="21afc-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="21afc-111">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21afc-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
