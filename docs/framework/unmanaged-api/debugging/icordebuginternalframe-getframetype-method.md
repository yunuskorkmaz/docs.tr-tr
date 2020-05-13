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
ms.openlocfilehash: 6b598352f734cf47514a82de1d0fca65d430a9ab
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209974"
---
# <a name="icordebuginternalframegetframetype-method"></a><span data-ttu-id="7497d-102">ICorDebugInternalFrame::GetFrameType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7497d-102">ICorDebugInternalFrame::GetFrameType Method</span></span>
<span data-ttu-id="7497d-103">Bu iç çerçevenin türünü alır.</span><span class="sxs-lookup"><span data-stu-id="7497d-103">Gets the type of this internal frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7497d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7497d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFrameType (  
    [out] CorDebugInternalFrameType  *pType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7497d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7497d-105">Parameters</span></span>  
 `pType`  
 <span data-ttu-id="7497d-106">dışı Bu nesne tarafından temsil edilen iç çerçeve türünü gösteren CorDebugInternalFrameType numaralandırması değerine yönelik bir işaretçi `ICorDebugInternalFrame` .</span><span class="sxs-lookup"><span data-stu-id="7497d-106">[out] A pointer to a value of the CorDebugInternalFrameType enumeration that indicates the type of internal frame represented by this `ICorDebugInternalFrame` object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7497d-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7497d-107">Remarks</span></span>  
 <span data-ttu-id="7497d-108">İç çerçeve türü hiçbir STUBFRAME_NONE olmaz.</span><span class="sxs-lookup"><span data-stu-id="7497d-108">The internal frame type will never be STUBFRAME_NONE.</span></span> <span data-ttu-id="7497d-109">Hata ayıklayıcılar, tanınmayan iç çerçeve türlerini düzgün şekilde yoksaymalıdır.</span><span class="sxs-lookup"><span data-stu-id="7497d-109">Debuggers should gracefully ignore unrecognized internal frame types.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7497d-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7497d-110">Requirements</span></span>  
 <span data-ttu-id="7497d-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7497d-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7497d-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7497d-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7497d-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="7497d-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7497d-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7497d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
