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
ms.openlocfilehash: f30516a8f59b90de9b4c052d92a8c88575ace3c4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178832"
---
# <a name="icordebugilframegetip-method"></a><span data-ttu-id="32391-102">ICorDebugILFrame::GetIP Metodu</span><span class="sxs-lookup"><span data-stu-id="32391-102">ICorDebugILFrame::GetIP Method</span></span>
<span data-ttu-id="32391-103">Yönerge işaretçisinin değerini ve yönerge işaretçisinin değerinin nasıl elde edildiğini açıklayan bitwise birleşim değerini alır.</span><span class="sxs-lookup"><span data-stu-id="32391-103">Gets the value of the instruction pointer and a bitwise combination value that describes how the value of the instruction pointer was obtained.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32391-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="32391-104">Syntax</span></span>  
  
```cpp  
HRESULT GetIP (  
    [out] ULONG32               *pnOffset,
    [out] CorDebugMappingResult *pMappingResult  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="32391-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="32391-105">Parameters</span></span>  
 `pnOffset`  
 <span data-ttu-id="32391-106">[çıkış] Yönerge işaretçisinin değeri.</span><span class="sxs-lookup"><span data-stu-id="32391-106">[out] The value of the instruction pointer.</span></span>  
  
 `pMappingResult`  
 <span data-ttu-id="32391-107">[çıkış] Yönerge işaretçisinin değerinin nasıl elde edildiğini açıklayan CorDebugMappingResult numaralandırma değerlerinin bitwise birleşimine işaretçi.</span><span class="sxs-lookup"><span data-stu-id="32391-107">[out] A pointer to a bitwise combination of the CorDebugMappingResult enumeration values that describe how the value of the instruction pointer was obtained.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="32391-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="32391-108">Remarks</span></span>  
 <span data-ttu-id="32391-109">Yönerge işaretçisinin değeri, yığın çerçevesinin işlevin Microsoft ara dili (MSIL) koduna mahsup çalışmasıdır.</span><span class="sxs-lookup"><span data-stu-id="32391-109">The value of the instruction pointer is the stack frame's offset into the function's Microsoft intermediate language (MSIL) code.</span></span> <span data-ttu-id="32391-110">Yığın çerçevesi etkinse, bu adres yürütülecek bir sonraki yönergedir.</span><span class="sxs-lookup"><span data-stu-id="32391-110">If the stack frame is active, this address is the next instruction to execute.</span></span> <span data-ttu-id="32391-111">Yığın çerçevesi etkin değilse, bu adres, yığın çerçevesi yeniden etkinleştirildiğinde yürütülecek sonraki yönergedir.</span><span class="sxs-lookup"><span data-stu-id="32391-111">If the stack frame is not active, this address is the next instruction to execute when the stack frame is reactivated.</span></span>  
  
 <span data-ttu-id="32391-112">Bu çerçeve tam zamanında (JIT) derlenmiş bir çerçeveyse, yönerge işaretçisinin değeri gerçek yerel yönerge işaretçisinden geriye doğru eşlenerek belirlenir, böylece değer yalnızca yaklaşık olabilir.</span><span class="sxs-lookup"><span data-stu-id="32391-112">If this frame is a just-in-time (JIT) compiled frame, the value of the instruction pointer will be determined by mapping backwards from the actual native instruction pointer, so the value may be only approximate.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32391-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="32391-113">Requirements</span></span>  
 <span data-ttu-id="32391-114">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="32391-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32391-115">**Üstbilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="32391-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="32391-116">**Kütüphane:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="32391-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="32391-117">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32391-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
