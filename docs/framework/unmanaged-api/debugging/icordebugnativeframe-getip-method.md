---
title: ICorDebugNativeFrame::GetIP Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.GetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetIP
helpviewer_keywords:
- GetIP method, ICorDebugNativeFrame interface [.NET Framework debugging]
- ICorDebugNativeFrame::GetIP method [.NET Framework debugging]
ms.assetid: 99f693f3-d3b9-4fd8-9d09-b8efd03f7b67
topic_type:
- apiref
ms.openlocfilehash: 3011a8c7e5cf278768587633967b2e9491cf87ac
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137332"
---
# <a name="icordebugnativeframegetip-method"></a><span data-ttu-id="e4295-102">ICorDebugNativeFrame::GetIP Metodu</span><span class="sxs-lookup"><span data-stu-id="e4295-102">ICorDebugNativeFrame::GetIP Method</span></span>
<span data-ttu-id="e4295-103">Yönerge işaretçisinin Şu anda ayarlandığı yerel kod konumu konumunu alır.</span><span class="sxs-lookup"><span data-stu-id="e4295-103">Gets the native code offset location to which the instruction pointer is currently set.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4295-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e4295-104">Syntax</span></span>  
  
```cpp  
HRESULT GetIP (  
    [out] ULONG32           *pnOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e4295-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e4295-105">Parameters</span></span>  
 `pnOffset`  
 <span data-ttu-id="e4295-106">dışı Yerel koddaki konum konumunu gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e4295-106">[out] A pointer to the offset location in the native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e4295-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e4295-107">Remarks</span></span>  
 <span data-ttu-id="e4295-108">Bu "ICorDebugNativeFrame" tarafından temsil edilen yığın çerçevesi etkin ise, konum yürütülecek sonraki yönergenin adresidir.</span><span class="sxs-lookup"><span data-stu-id="e4295-108">If the stack frame that is represented by this "ICorDebugNativeFrame" is active, the offset is the address of the next instruction to be executed.</span></span> <span data-ttu-id="e4295-109">Bu yığın çerçevesi etkin değilse, Aralık, yığın çerçevesi yeniden etkinleştirildiğinde yürütülecek sonraki yönergenin adresidir.</span><span class="sxs-lookup"><span data-stu-id="e4295-109">If this stack frame is not active, the offset is the address of the next instruction to be executed when the stack frame is reactivated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4295-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e4295-110">Requirements</span></span>  
 <span data-ttu-id="e4295-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e4295-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4295-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e4295-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e4295-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e4295-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e4295-114">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4295-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4295-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e4295-115">See also</span></span>
