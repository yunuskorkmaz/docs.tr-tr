---
description: ': ICorDebugInternalFrame:: GetFrameType yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: ea96f032ebfa5914503287d124242b74a84ea11f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791185"
---
# <a name="icordebuginternalframegetframetype-method"></a><span data-ttu-id="c0a6e-103">ICorDebugInternalFrame::GetFrameType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c0a6e-103">ICorDebugInternalFrame::GetFrameType Method</span></span>

<span data-ttu-id="c0a6e-104">Bu iç çerçevenin türünü alır.</span><span class="sxs-lookup"><span data-stu-id="c0a6e-104">Gets the type of this internal frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0a6e-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c0a6e-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFrameType (  
    [out] CorDebugInternalFrameType  *pType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c0a6e-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c0a6e-106">Parameters</span></span>  

 `pType`  
 <span data-ttu-id="c0a6e-107">dışı Bu nesne tarafından temsil edilen iç çerçeve türünü gösteren CorDebugInternalFrameType numaralandırması değerine yönelik bir işaretçi `ICorDebugInternalFrame` .</span><span class="sxs-lookup"><span data-stu-id="c0a6e-107">[out] A pointer to a value of the CorDebugInternalFrameType enumeration that indicates the type of internal frame represented by this `ICorDebugInternalFrame` object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c0a6e-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c0a6e-108">Remarks</span></span>  

 <span data-ttu-id="c0a6e-109">İç çerçeve türü hiçbir STUBFRAME_NONE olmaz.</span><span class="sxs-lookup"><span data-stu-id="c0a6e-109">The internal frame type will never be STUBFRAME_NONE.</span></span> <span data-ttu-id="c0a6e-110">Hata ayıklayıcılar, tanınmayan iç çerçeve türlerini düzgün şekilde yoksaymalıdır.</span><span class="sxs-lookup"><span data-stu-id="c0a6e-110">Debuggers should gracefully ignore unrecognized internal frame types.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c0a6e-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c0a6e-111">Requirements</span></span>  

 <span data-ttu-id="c0a6e-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c0a6e-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c0a6e-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c0a6e-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c0a6e-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c0a6e-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c0a6e-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c0a6e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
