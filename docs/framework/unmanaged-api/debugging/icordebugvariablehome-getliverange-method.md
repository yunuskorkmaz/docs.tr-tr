---
title: 'Icordebugvariablehome:: GetLiveRange yöntemi'
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetLiveRange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetLiveRange
helpviewer_keywords:
- ICorDebugVariableHome::GetLiveRange method [.NET Framework debugging]
- GetLiveRange method, ICorDebugVariableFrame interface [.NET Framework debugging]
ms.assetid: 87277e1a-1595-4729-9e25-d1c3ac18ce5f
topic_type:
- apiref
ms.openlocfilehash: fb198782bb91a8301507fd6cadcffb0378230f0e
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396580"
---
# <a name="icordebugvariablehomegetliverange-method"></a><span data-ttu-id="ee33d-102">Icordebugvariablehome:: GetLiveRange yöntemi</span><span class="sxs-lookup"><span data-stu-id="ee33d-102">IcorDebugVariableHome::GetLiveRange Method</span></span>
<span data-ttu-id="ee33d-103">Bu değişkenin canlı olduğu yerel aralığı alır.</span><span class="sxs-lookup"><span data-stu-id="ee33d-103">Gets the native range over which this variable is live.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee33d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ee33d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLiveRange(  
    [out] ULONG32* pStartOffset,  
    [out] ULONG32 *pEndOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ee33d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ee33d-105">Parameters</span></span>  
 `pStartOffset`  
 <span data-ttu-id="ee33d-106">dışı Değişkenin ilk yaşam olduğu mantıksal fark.</span><span class="sxs-lookup"><span data-stu-id="ee33d-106">[out] The logical offset at which the variable is first live.</span></span>  
  
 `pEndOffset`  
 <span data-ttu-id="ee33d-107">dışı Değişkenin son yaşam olduğu noktadan hemen sonra mantıksal konum.</span><span class="sxs-lookup"><span data-stu-id="ee33d-107">[out] The logical offset immediately after the point at which the variable is last live.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ee33d-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ee33d-108">Requirements</span></span>  
 <span data-ttu-id="ee33d-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ee33d-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ee33d-110">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ee33d-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ee33d-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ee33d-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ee33d-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ee33d-112">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee33d-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ee33d-113">See also</span></span>

- [<span data-ttu-id="ee33d-114">ICorDebugVariableHome Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ee33d-114">ICorDebugVariableHome Interface</span></span>](icordebugvariablehome-interface.md)
