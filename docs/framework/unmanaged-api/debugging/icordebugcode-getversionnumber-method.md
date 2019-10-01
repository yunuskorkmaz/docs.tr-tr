---
title: ICorDebugCode::GetVersionNumber Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetVersionNumber
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetVersionNumber
helpviewer_keywords:
- GetVersionNumber method, ICorDebugCode interface [.NET Framework debugging]
- ICorDebugCode::GetVersionNumber method [.NET Framework debugging]
ms.assetid: c8e02518-679f-4e9f-8a28-ba4a89a3876f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4b6fd6e8043f1c62da8994b43a9b9af45fb2e3c0
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700817"
---
# <a name="icordebugcodegetversionnumber-method"></a><span data-ttu-id="a0eeb-102">ICorDebugCode::GetVersionNumber Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a0eeb-102">ICorDebugCode::GetVersionNumber Method</span></span>

<span data-ttu-id="a0eeb-103">Bu "ICorDebugCode" öğesinin gösterdiği kodun sürümünü tanımlayan tek tabanlı bir sayı alır.</span><span class="sxs-lookup"><span data-stu-id="a0eeb-103">Gets the one-based number that identifies the version of the code that this "ICorDebugCode" represents.</span></span>

## <a name="syntax"></a><span data-ttu-id="a0eeb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a0eeb-104">Syntax</span></span>

```cpp
HRESULT GetVersionNumber (
    [out] ULONG32    *nVersion
);
```

## <a name="parameters"></a><span data-ttu-id="a0eeb-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a0eeb-105">Parameters</span></span>

 `nVersion`  
 <span data-ttu-id="a0eeb-106">dışı Kodun sürüm numarasına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a0eeb-106">[out] A pointer to the version number of the code.</span></span>

## <a name="remarks"></a><span data-ttu-id="a0eeb-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a0eeb-107">Remarks</span></span>

 <span data-ttu-id="a0eeb-108">Kod üzerinde bir Düzenle ve devam et (EnC) işlemi gerçekleştirildiğinde sürüm numarası artırılır.</span><span class="sxs-lookup"><span data-stu-id="a0eeb-108">The version number is incremented each time an edit-and-continue (EnC) operation is performed on the code.</span></span>

## <a name="requirements"></a><span data-ttu-id="a0eeb-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a0eeb-109">Requirements</span></span>

 <span data-ttu-id="a0eeb-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a0eeb-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0eeb-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a0eeb-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a0eeb-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a0eeb-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a0eeb-113">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a0eeb-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
