---
title: ICorDebugInternalFrame::GetFrameType Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugInternalFrame.GetFrameType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugInternalFrame::GetFrameType
helpviewer_keywords:
- GetFrameType method [.NET Framework debugging]
- ICorDebugInternalFrame::GetFrameType method [.NET Framework debugging]
ms.assetid: da278a29-dc2e-4bf7-96ce-801bdc4d7025
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2a5461cc6a78347cdbe0d0b13f8111cb24c11006
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760050"
---
# <a name="icordebuginternalframegetframetype-method"></a><span data-ttu-id="68e05-102">ICorDebugInternalFrame::GetFrameType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="68e05-102">ICorDebugInternalFrame::GetFrameType Method</span></span>
<span data-ttu-id="68e05-103">Bu iç çerçeve türünü alır.</span><span class="sxs-lookup"><span data-stu-id="68e05-103">Gets the type of this internal frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68e05-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="68e05-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFrameType (  
    [out] CorDebugInternalFrameType  *pType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="68e05-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="68e05-105">Parameters</span></span>  
 `pType`  
 <span data-ttu-id="68e05-106">[out] Bu tarafından temsil edilen iç çerçeve türünü belirten Cordebugınternalframetype sabit bir değere bir işaretçi `ICorDebugInternalFrame` nesne.</span><span class="sxs-lookup"><span data-stu-id="68e05-106">[out] A pointer to a value of the CorDebugInternalFrameType enumeration that indicates the type of internal frame represented by this `ICorDebugInternalFrame` object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="68e05-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="68e05-107">Remarks</span></span>  
 <span data-ttu-id="68e05-108">İç çerçeve türü hiçbir zaman STUBFRAME_NONE olmaz.</span><span class="sxs-lookup"><span data-stu-id="68e05-108">The internal frame type will never be STUBFRAME_NONE.</span></span> <span data-ttu-id="68e05-109">Düzgün bir şekilde hata ayıklayıcıları tanınmayan iç çerçeve türleri yok saymanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="68e05-109">Debuggers should gracefully ignore unrecognized internal frame types.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68e05-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="68e05-110">Requirements</span></span>  
 <span data-ttu-id="68e05-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="68e05-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68e05-112">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="68e05-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="68e05-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="68e05-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="68e05-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68e05-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
