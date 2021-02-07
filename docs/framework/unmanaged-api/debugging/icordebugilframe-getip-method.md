---
description: ': ICorDebugILFrame:: GetIP Yöntemi hakkında daha fazla bilgi edinin'
title: ICorDebugILFrame::GetIP Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.GetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::GetIP
helpviewer_keywords:
- GetIP method, ICorDebugILFrame interface [.NET Framework debugging]
- ICorDebugILFrame::GetIP method [.NET Framework debugging]
ms.assetid: 18217ba1-1776-4297-a3b9-f77e64b0fead
topic_type:
- apiref
ms.openlocfilehash: f3977d4fbe57b24e7b98b7a597b0db7ad171eb1c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99691880"
---
# <a name="icordebugilframegetip-method"></a><span data-ttu-id="bbb6e-103">ICorDebugILFrame::GetIP Metodu</span><span class="sxs-lookup"><span data-stu-id="bbb6e-103">ICorDebugILFrame::GetIP Method</span></span>

<span data-ttu-id="bbb6e-104">Yönerge işaretçisinin değerini ve yönerge işaretçisi değerinin nasıl elde edileceğini açıklayan bit düzeyinde birleşim değerini alır.</span><span class="sxs-lookup"><span data-stu-id="bbb6e-104">Gets the value of the instruction pointer and a bitwise combination value that describes how the value of the instruction pointer was obtained.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bbb6e-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bbb6e-105">Syntax</span></span>  
  
```cpp  
HRESULT GetIP (  
    [out] ULONG32               *pnOffset,
    [out] CorDebugMappingResult *pMappingResult  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bbb6e-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bbb6e-106">Parameters</span></span>  

 `pnOffset`  
 <span data-ttu-id="bbb6e-107">dışı Yönerge işaretçisinin değeri.</span><span class="sxs-lookup"><span data-stu-id="bbb6e-107">[out] The value of the instruction pointer.</span></span>  
  
 `pMappingResult`  
 <span data-ttu-id="bbb6e-108">dışı Yönerge işaretçisinin değerinin nasıl elde edildiğini tanımlayan CorDebugMappingResult numaralandırma değerlerinin bit düzeyinde birleşimine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="bbb6e-108">[out] A pointer to a bitwise combination of the CorDebugMappingResult enumeration values that describe how the value of the instruction pointer was obtained.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bbb6e-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bbb6e-109">Remarks</span></span>  

 <span data-ttu-id="bbb6e-110">Yönerge işaretçisinin değeri, yığın çerçevesinin işlevin Microsoft ara dil (MSIL) koduna olan aralıkdır.</span><span class="sxs-lookup"><span data-stu-id="bbb6e-110">The value of the instruction pointer is the stack frame's offset into the function's Microsoft intermediate language (MSIL) code.</span></span> <span data-ttu-id="bbb6e-111">Yığın çerçevesi etkinse, bu adres yürütülecek sonraki yönergedir.</span><span class="sxs-lookup"><span data-stu-id="bbb6e-111">If the stack frame is active, this address is the next instruction to execute.</span></span> <span data-ttu-id="bbb6e-112">Yığın çerçevesi etkin değilse, bu adres yığın çerçevesi yeniden etkinleştirildiğinde yürütülecek sonraki yönergedir.</span><span class="sxs-lookup"><span data-stu-id="bbb6e-112">If the stack frame is not active, this address is the next instruction to execute when the stack frame is reactivated.</span></span>  
  
 <span data-ttu-id="bbb6e-113">Bu çerçeve tam zamanında (JıT) derlenmiş bir çerçevedir, yönerge işaretçisinin değeri gerçek yerel yönerge işaretçisinden geriye doğru eşleme yaparak belirlenir, bu nedenle değer yalnızca yaklaşık olabilir.</span><span class="sxs-lookup"><span data-stu-id="bbb6e-113">If this frame is a just-in-time (JIT) compiled frame, the value of the instruction pointer will be determined by mapping backwards from the actual native instruction pointer, so the value may be only approximate.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bbb6e-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bbb6e-114">Requirements</span></span>  

 <span data-ttu-id="bbb6e-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bbb6e-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bbb6e-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="bbb6e-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bbb6e-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="bbb6e-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bbb6e-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bbb6e-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
