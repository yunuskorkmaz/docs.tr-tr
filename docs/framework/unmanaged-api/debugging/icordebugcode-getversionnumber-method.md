---
description: ': ICorDebugCode:: GetVersionNumber yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 901342333bea3d455407602dde78bdccd0140d77
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99764911"
---
# <a name="icordebugcodegetversionnumber-method"></a><span data-ttu-id="9aaf0-103">ICorDebugCode::GetVersionNumber Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9aaf0-103">ICorDebugCode::GetVersionNumber Method</span></span>

<span data-ttu-id="9aaf0-104">Bu "ICorDebugCode" öğesinin gösterdiği kodun sürümünü tanımlayan tek tabanlı bir sayı alır.</span><span class="sxs-lookup"><span data-stu-id="9aaf0-104">Gets the one-based number that identifies the version of the code that this "ICorDebugCode" represents.</span></span>

## <a name="syntax"></a><span data-ttu-id="9aaf0-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9aaf0-105">Syntax</span></span>

```cpp
HRESULT GetVersionNumber (
    [out] ULONG32    *nVersion
);
```

## <a name="parameters"></a><span data-ttu-id="9aaf0-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9aaf0-106">Parameters</span></span>

 `nVersion`  
 <span data-ttu-id="9aaf0-107">dışı Kodun sürüm numarasına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9aaf0-107">[out] A pointer to the version number of the code.</span></span>

## <a name="remarks"></a><span data-ttu-id="9aaf0-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9aaf0-108">Remarks</span></span>

 <span data-ttu-id="9aaf0-109">Kod üzerinde bir Düzenle ve devam et (EnC) işlemi gerçekleştirildiğinde sürüm numarası artırılır.</span><span class="sxs-lookup"><span data-stu-id="9aaf0-109">The version number is incremented each time an edit-and-continue (EnC) operation is performed on the code.</span></span>

## <a name="requirements"></a><span data-ttu-id="9aaf0-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9aaf0-110">Requirements</span></span>

 <span data-ttu-id="9aaf0-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9aaf0-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9aaf0-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="9aaf0-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9aaf0-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="9aaf0-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9aaf0-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9aaf0-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
