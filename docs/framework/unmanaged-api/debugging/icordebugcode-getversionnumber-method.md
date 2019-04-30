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
ms.openlocfilehash: 003b29501e8f22ed9010a9f16a4f7ee67bce03a8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61750143"
---
# <a name="icordebugcodegetversionnumber-method"></a><span data-ttu-id="f6164-102">ICorDebugCode::GetVersionNumber Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f6164-102">ICorDebugCode::GetVersionNumber Method</span></span>
<span data-ttu-id="f6164-103">Bu "Icordebugcode" temsil eden kodu sürümünü tanımlayan bir tabanlı numarasını alır.</span><span class="sxs-lookup"><span data-stu-id="f6164-103">Gets the one-based number that identifies the version of the code that this "ICorDebugCode" represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6164-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f6164-104">Syntax</span></span>  
  
```  
HRESULT GetVersionNumber (  
    [out] ULONG32    *nVersion  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f6164-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f6164-105">Parameters</span></span>  
 `nVersion`  
 <span data-ttu-id="f6164-106">[out] Sürüm numarası kod için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f6164-106">[out] A pointer to the version number of the code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f6164-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f6164-107">Remarks</span></span>  
 <span data-ttu-id="f6164-108">Düzenle ve devam et (EnC) işlem kod üzerinde gerçekleştirilen her zaman sürüm numarası artırılır.</span><span class="sxs-lookup"><span data-stu-id="f6164-108">The version number is incremented each time an edit-and-continue (EnC) operation is performed on the code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f6164-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f6164-109">Requirements</span></span>  
 <span data-ttu-id="f6164-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f6164-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6164-111">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f6164-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f6164-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f6164-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f6164-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f6164-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6164-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f6164-114">See also</span></span>
