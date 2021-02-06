---
description: ': ICorDebugNativeFrame:: GetIP Yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: f36a14c38aa6c3754cf78eca8c657adc76469067
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637858"
---
# <a name="icordebugnativeframegetip-method"></a><span data-ttu-id="bbfbc-103">ICorDebugNativeFrame::GetIP Metodu</span><span class="sxs-lookup"><span data-stu-id="bbfbc-103">ICorDebugNativeFrame::GetIP Method</span></span>

<span data-ttu-id="bbfbc-104">Yönerge işaretçisinin Şu anda ayarlandığı yerel kod konumu konumunu alır.</span><span class="sxs-lookup"><span data-stu-id="bbfbc-104">Gets the native code offset location to which the instruction pointer is currently set.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bbfbc-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bbfbc-105">Syntax</span></span>  
  
```cpp  
HRESULT GetIP (  
    [out] ULONG32           *pnOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bbfbc-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bbfbc-106">Parameters</span></span>  

 `pnOffset`  
 <span data-ttu-id="bbfbc-107">dışı Yerel koddaki konum konumunu gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="bbfbc-107">[out] A pointer to the offset location in the native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bbfbc-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bbfbc-108">Remarks</span></span>  

 <span data-ttu-id="bbfbc-109">Bu "ICorDebugNativeFrame" tarafından temsil edilen yığın çerçevesi etkin ise, konum yürütülecek sonraki yönergenin adresidir.</span><span class="sxs-lookup"><span data-stu-id="bbfbc-109">If the stack frame that is represented by this "ICorDebugNativeFrame" is active, the offset is the address of the next instruction to be executed.</span></span> <span data-ttu-id="bbfbc-110">Bu yığın çerçevesi etkin değilse, Aralık, yığın çerçevesi yeniden etkinleştirildiğinde yürütülecek sonraki yönergenin adresidir.</span><span class="sxs-lookup"><span data-stu-id="bbfbc-110">If this stack frame is not active, the offset is the address of the next instruction to be executed when the stack frame is reactivated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bbfbc-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bbfbc-111">Requirements</span></span>  

 <span data-ttu-id="bbfbc-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bbfbc-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bbfbc-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="bbfbc-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bbfbc-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="bbfbc-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bbfbc-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bbfbc-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbfbc-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bbfbc-116">See also</span></span>
