---
title: ICorDebugILFrame::GetIP Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugILFrame.GetIP
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugILFrame::GetIP
helpviewer_keywords:
- GetIP method, ICorDebugILFrame interface [.NET Framework debugging]
- ICorDebugILFrame::GetIP method [.NET Framework debugging]
ms.assetid: 18217ba1-1776-4297-a3b9-f77e64b0fead
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 79b18c6fe15e28b2cec07ef9dfaa06ee295ab42d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugilframegetip-method"></a><span data-ttu-id="1bb39-102">ICorDebugILFrame::GetIP Metodu</span><span class="sxs-lookup"><span data-stu-id="1bb39-102">ICorDebugILFrame::GetIP Method</span></span>
<span data-ttu-id="1bb39-103">Yönerge işaretçisi değerini ve nasıl yönerge işaretçisi değerini edinilen açıklayan Bitsel bir birleşimi değeri alır.</span><span class="sxs-lookup"><span data-stu-id="1bb39-103">Gets the value of the instruction pointer and a bitwise combination value that describes how the value of the instruction pointer was obtained.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1bb39-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1bb39-104">Syntax</span></span>  
  
```  
HRESULT GetIP (  
    [out] ULONG32               *pnOffset,   
    [out] CorDebugMappingResult *pMappingResult  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1bb39-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1bb39-105">Parameters</span></span>  
 `pnOffset`  
 <span data-ttu-id="1bb39-106">[out] Yönerge işaretçisi değeri.</span><span class="sxs-lookup"><span data-stu-id="1bb39-106">[out] The value of the instruction pointer.</span></span>  
  
 `pMappingResult`  
 <span data-ttu-id="1bb39-107">[out] Yönerge işaretçisi değerini nasıl edinilen açıklamak CorDebugMappingResult numaralandırma değerlerinin Bitsel bir birleşimi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1bb39-107">[out] A pointer to a bitwise combination of the CorDebugMappingResult enumeration values that describe how the value of the instruction pointer was obtained.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1bb39-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1bb39-108">Remarks</span></span>  
 <span data-ttu-id="1bb39-109">Yönerge işaretçisi işlevin Microsoft Ara dili (MSIL) koda yığın çerçeve uzaklık değeri.</span><span class="sxs-lookup"><span data-stu-id="1bb39-109">The value of the instruction pointer is the stack frame's offset into the function's Microsoft intermediate language (MSIL) code.</span></span> <span data-ttu-id="1bb39-110">Yığın çerçevesi etkin değilse, bu yürütmek için sonraki yönerge adresidir.</span><span class="sxs-lookup"><span data-stu-id="1bb39-110">If the stack frame is active, this address is the next instruction to execute.</span></span> <span data-ttu-id="1bb39-111">Yığın çerçevesi etkin değilse, bu yığın çerçevesi etkinleştirildiğinde yürütmek için sonraki yönerge adresidir.</span><span class="sxs-lookup"><span data-stu-id="1bb39-111">If the stack frame is not active, this address is the next instruction to execute when the stack frame is reactivated.</span></span>  
  
 <span data-ttu-id="1bb39-112">Bu çerçeve tam zamanında (JIT) derlenmiş çerçeve ise, yönerge işaretçisi değerini değeri yalnızca yaklaşık olabilir geriye doğru gerçek yerel yönerge işaretçi eşleme tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="1bb39-112">If this frame is a just-in-time (JIT) compiled frame, the value of the instruction pointer will be determined by mapping backwards from the actual native instruction pointer, so the value may be only approximate.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1bb39-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1bb39-113">Requirements</span></span>  
 <span data-ttu-id="1bb39-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1bb39-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1bb39-115">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1bb39-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1bb39-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1bb39-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1bb39-117">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1bb39-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
