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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 38f913b742f7ece2f136454f801ae780124aed87
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61987980"
---
# <a name="icordebugnativeframegetip-method"></a><span data-ttu-id="6c615-102">ICorDebugNativeFrame::GetIP Metodu</span><span class="sxs-lookup"><span data-stu-id="6c615-102">ICorDebugNativeFrame::GetIP Method</span></span>
<span data-ttu-id="6c615-103">Alır yerel kod, yönerge işaretçisini şu anda ayarlanmış konumu uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="6c615-103">Gets the native code offset location to which the instruction pointer is currently set.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c615-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6c615-104">Syntax</span></span>  
  
```  
HRESULT GetIP (  
    [out] ULONG32           *pnOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6c615-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6c615-105">Parameters</span></span>  
 `pnOffset`  
 <span data-ttu-id="6c615-106">[out] Yerel kod uzaklık konumunda bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6c615-106">[out] A pointer to the offset location in the native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6c615-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6c615-107">Remarks</span></span>  
 <span data-ttu-id="6c615-108">Bu "Icordebugnativeframe" tarafından temsil edilen yığın çerçevesini etkin olursa, uzaklık yürütülmesi gereken sonraki yönergeyi adresidir.</span><span class="sxs-lookup"><span data-stu-id="6c615-108">If the stack frame that is represented by this "ICorDebugNativeFrame" is active, the offset is the address of the next instruction to be executed.</span></span> <span data-ttu-id="6c615-109">Bu yığın çerçevesi etkin değilse, uzaklık yığın çerçevesinin yeniden etkinleştirildiğinde yürütülecek sonraki yönergeyi adresidir.</span><span class="sxs-lookup"><span data-stu-id="6c615-109">If this stack frame is not active, the offset is the address of the next instruction to be executed when the stack frame is reactivated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c615-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6c615-110">Requirements</span></span>  
 <span data-ttu-id="6c615-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c615-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c615-112">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6c615-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6c615-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6c615-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6c615-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c615-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c615-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6c615-115">See also</span></span>
