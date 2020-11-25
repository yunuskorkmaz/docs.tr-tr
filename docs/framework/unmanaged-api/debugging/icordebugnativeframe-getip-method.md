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
ms.openlocfilehash: c9c0598f8e7b3e8654124f50663c912f3cd61659
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95709316"
---
# <a name="icordebugnativeframegetip-method"></a><span data-ttu-id="1dbd2-102">ICorDebugNativeFrame::GetIP Metodu</span><span class="sxs-lookup"><span data-stu-id="1dbd2-102">ICorDebugNativeFrame::GetIP Method</span></span>

<span data-ttu-id="1dbd2-103">Yönerge işaretçisinin Şu anda ayarlandığı yerel kod konumu konumunu alır.</span><span class="sxs-lookup"><span data-stu-id="1dbd2-103">Gets the native code offset location to which the instruction pointer is currently set.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1dbd2-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="1dbd2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetIP (  
    [out] ULONG32           *pnOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1dbd2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1dbd2-105">Parameters</span></span>  

 `pnOffset`  
 <span data-ttu-id="1dbd2-106">dışı Yerel koddaki konum konumunu gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1dbd2-106">[out] A pointer to the offset location in the native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1dbd2-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1dbd2-107">Remarks</span></span>  

 <span data-ttu-id="1dbd2-108">Bu "ICorDebugNativeFrame" tarafından temsil edilen yığın çerçevesi etkin ise, konum yürütülecek sonraki yönergenin adresidir.</span><span class="sxs-lookup"><span data-stu-id="1dbd2-108">If the stack frame that is represented by this "ICorDebugNativeFrame" is active, the offset is the address of the next instruction to be executed.</span></span> <span data-ttu-id="1dbd2-109">Bu yığın çerçevesi etkin değilse, Aralık, yığın çerçevesi yeniden etkinleştirildiğinde yürütülecek sonraki yönergenin adresidir.</span><span class="sxs-lookup"><span data-stu-id="1dbd2-109">If this stack frame is not active, the offset is the address of the next instruction to be executed when the stack frame is reactivated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1dbd2-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1dbd2-110">Requirements</span></span>  

 <span data-ttu-id="1dbd2-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1dbd2-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1dbd2-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="1dbd2-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1dbd2-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="1dbd2-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1dbd2-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1dbd2-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1dbd2-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1dbd2-115">See also</span></span>
