---
title: ICorDebugCode::GetVersionNumber Metodu
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
ms.openlocfilehash: a3d4609d79bb424cabc011122480f952f0f877f1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33411240"
---
# <a name="icordebugcodegetversionnumber-method"></a><span data-ttu-id="c3dc5-102">ICorDebugCode::GetVersionNumber Metodu</span><span class="sxs-lookup"><span data-stu-id="c3dc5-102">ICorDebugCode::GetVersionNumber Method</span></span>
<span data-ttu-id="c3dc5-103">Bu "Icordebugcode" temsil eden kodu sürümünü belirleyen tabanlı numarasını alır.</span><span class="sxs-lookup"><span data-stu-id="c3dc5-103">Gets the one-based number that identifies the version of the code that this "ICorDebugCode" represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3dc5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c3dc5-104">Syntax</span></span>  
  
```  
HRESULT GetVersionNumber (  
    [out] ULONG32    *nVersion  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c3dc5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c3dc5-105">Parameters</span></span>  
 `nVersion`  
 <span data-ttu-id="c3dc5-106">[out] Kod sürüm numarasını gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c3dc5-106">[out] A pointer to the version number of the code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c3dc5-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c3dc5-107">Remarks</span></span>  
 <span data-ttu-id="c3dc5-108">Sürüm numarası bir Düzenle ve devam et (Çözücü) işlem kodu gerçekleştirilen her zaman artırılır.</span><span class="sxs-lookup"><span data-stu-id="c3dc5-108">The version number is incremented each time an edit-and-continue (EnC) operation is performed on the code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3dc5-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c3dc5-109">Requirements</span></span>  
 <span data-ttu-id="c3dc5-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3dc5-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3dc5-111">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c3dc5-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c3dc5-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c3dc5-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c3dc5-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3dc5-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3dc5-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c3dc5-114">See Also</span></span>  
 
