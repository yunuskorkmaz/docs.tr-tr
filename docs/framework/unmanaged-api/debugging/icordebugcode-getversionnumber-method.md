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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59098955"
---
# <a name="icordebugcodegetversionnumber-method"></a><span data-ttu-id="21cca-102">ICorDebugCode::GetVersionNumber Yöntemi</span><span class="sxs-lookup"><span data-stu-id="21cca-102">ICorDebugCode::GetVersionNumber Method</span></span>
<span data-ttu-id="21cca-103">Bu "Icordebugcode" temsil eden kodu sürümünü tanımlayan bir tabanlı numarasını alır.</span><span class="sxs-lookup"><span data-stu-id="21cca-103">Gets the one-based number that identifies the version of the code that this "ICorDebugCode" represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21cca-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="21cca-104">Syntax</span></span>  
  
```  
HRESULT GetVersionNumber (  
    [out] ULONG32    *nVersion  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="21cca-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="21cca-105">Parameters</span></span>  
 `nVersion`  
 <span data-ttu-id="21cca-106">[out] Sürüm numarası kod için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="21cca-106">[out] A pointer to the version number of the code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="21cca-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="21cca-107">Remarks</span></span>  
 <span data-ttu-id="21cca-108">Düzenle ve devam et (EnC) işlem kod üzerinde gerçekleştirilen her zaman sürüm numarası artırılır.</span><span class="sxs-lookup"><span data-stu-id="21cca-108">The version number is incremented each time an edit-and-continue (EnC) operation is performed on the code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21cca-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="21cca-109">Requirements</span></span>  
 <span data-ttu-id="21cca-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21cca-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21cca-111">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="21cca-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="21cca-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="21cca-112">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="21cca-113">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="21cca-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="21cca-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="21cca-114">See also</span></span>
