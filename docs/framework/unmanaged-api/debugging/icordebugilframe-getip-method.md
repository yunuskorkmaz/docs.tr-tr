---
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
ms.openlocfilehash: 3890cb4236f113bc6efc23bfb606d19a525ec234
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210273"
---
# <a name="icordebugilframegetip-method"></a><span data-ttu-id="354f1-102">ICorDebugILFrame::GetIP Metodu</span><span class="sxs-lookup"><span data-stu-id="354f1-102">ICorDebugILFrame::GetIP Method</span></span>
<span data-ttu-id="354f1-103">Yönerge işaretçisinin değerini ve yönerge işaretçisi değerinin nasıl elde edileceğini açıklayan bit düzeyinde birleşim değerini alır.</span><span class="sxs-lookup"><span data-stu-id="354f1-103">Gets the value of the instruction pointer and a bitwise combination value that describes how the value of the instruction pointer was obtained.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="354f1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="354f1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetIP (  
    [out] ULONG32               *pnOffset,
    [out] CorDebugMappingResult *pMappingResult  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="354f1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="354f1-105">Parameters</span></span>  
 `pnOffset`  
 <span data-ttu-id="354f1-106">dışı Yönerge işaretçisinin değeri.</span><span class="sxs-lookup"><span data-stu-id="354f1-106">[out] The value of the instruction pointer.</span></span>  
  
 `pMappingResult`  
 <span data-ttu-id="354f1-107">dışı Yönerge işaretçisinin değerinin nasıl elde edildiğini tanımlayan CorDebugMappingResult numaralandırma değerlerinin bit düzeyinde birleşimine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="354f1-107">[out] A pointer to a bitwise combination of the CorDebugMappingResult enumeration values that describe how the value of the instruction pointer was obtained.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="354f1-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="354f1-108">Remarks</span></span>  
 <span data-ttu-id="354f1-109">Yönerge işaretçisinin değeri, yığın çerçevesinin işlevin Microsoft ara dil (MSIL) koduna olan aralıkdır.</span><span class="sxs-lookup"><span data-stu-id="354f1-109">The value of the instruction pointer is the stack frame's offset into the function's Microsoft intermediate language (MSIL) code.</span></span> <span data-ttu-id="354f1-110">Yığın çerçevesi etkinse, bu adres yürütülecek sonraki yönergedir.</span><span class="sxs-lookup"><span data-stu-id="354f1-110">If the stack frame is active, this address is the next instruction to execute.</span></span> <span data-ttu-id="354f1-111">Yığın çerçevesi etkin değilse, bu adres yığın çerçevesi yeniden etkinleştirildiğinde yürütülecek sonraki yönergedir.</span><span class="sxs-lookup"><span data-stu-id="354f1-111">If the stack frame is not active, this address is the next instruction to execute when the stack frame is reactivated.</span></span>  
  
 <span data-ttu-id="354f1-112">Bu çerçeve tam zamanında (JıT) derlenmiş bir çerçevedir, yönerge işaretçisinin değeri gerçek yerel yönerge işaretçisinden geriye doğru eşleme yaparak belirlenir, bu nedenle değer yalnızca yaklaşık olabilir.</span><span class="sxs-lookup"><span data-stu-id="354f1-112">If this frame is a just-in-time (JIT) compiled frame, the value of the instruction pointer will be determined by mapping backwards from the actual native instruction pointer, so the value may be only approximate.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="354f1-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="354f1-113">Requirements</span></span>  
 <span data-ttu-id="354f1-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="354f1-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="354f1-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="354f1-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="354f1-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="354f1-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="354f1-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="354f1-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
