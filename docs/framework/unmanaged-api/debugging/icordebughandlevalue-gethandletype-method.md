---
description: ': IcorıGetHandleType Ghandlivalue:: yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 708d60cd8116cf3f0fdc436a34d863380be2543d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99660966"
---
# <a name="icordebughandlevaluegethandletype-method"></a><span data-ttu-id="22967-103">ICorDebugHandleValue::GetHandleType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="22967-103">ICorDebugHandleValue::GetHandleType Method</span></span>

<span data-ttu-id="22967-104">Bu ıcorıınfo Ghandlivalue nesnesinin başvurduğu tanıtıcı türünü gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="22967-104">Gets a value that indicates the kind of handle referenced by this ICorDebugHandleValue object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22967-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="22967-105">Syntax</span></span>  
  
```cpp  
HRESULT GetHandleType (  
    [out] CorDebugHandleType  *pType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="22967-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="22967-106">Parameters</span></span>  

 `pType`  
 <span data-ttu-id="22967-107">dışı Bu tanıtıcının türünü gösteren Cordebugghandlitype numaralandırması değerine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="22967-107">[out] A pointer to a value of the CorDebugHandleType enumeration that indicates the type of this handle.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="22967-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="22967-108">Requirements</span></span>  

 <span data-ttu-id="22967-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="22967-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22967-110">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="22967-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="22967-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="22967-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="22967-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="22967-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
