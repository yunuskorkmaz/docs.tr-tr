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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4d7eca3c2825707c9190436377bba7e4bb0d5447
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67757965"
---
# <a name="icordebugilframegetip-method"></a><span data-ttu-id="10b79-102">ICorDebugILFrame::GetIP Metodu</span><span class="sxs-lookup"><span data-stu-id="10b79-102">ICorDebugILFrame::GetIP Method</span></span>
<span data-ttu-id="10b79-103">Yönerge işaretçisi değerini ve nasıl yönerge işaretçisini değerini edinilen açıklayan bir karşılaştırmaya değerini alır.</span><span class="sxs-lookup"><span data-stu-id="10b79-103">Gets the value of the instruction pointer and a bitwise combination value that describes how the value of the instruction pointer was obtained.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10b79-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="10b79-104">Syntax</span></span>  
  
```cpp  
HRESULT GetIP (  
    [out] ULONG32               *pnOffset,   
    [out] CorDebugMappingResult *pMappingResult  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="10b79-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="10b79-105">Parameters</span></span>  
 `pnOffset`  
 <span data-ttu-id="10b79-106">[out] Yönerge işaretçisi değeri.</span><span class="sxs-lookup"><span data-stu-id="10b79-106">[out] The value of the instruction pointer.</span></span>  
  
 `pMappingResult`  
 <span data-ttu-id="10b79-107">[out] Yönerge işaretçisinin değeri nasıl edinilen açıklayan CorDebugMappingResult numaralandırma değerlerinin Bitsel bir birleşimi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="10b79-107">[out] A pointer to a bitwise combination of the CorDebugMappingResult enumeration values that describe how the value of the instruction pointer was obtained.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="10b79-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="10b79-108">Remarks</span></span>  
 <span data-ttu-id="10b79-109">Yönerge işaretçisi işlev Microsoft Ara dili (MSIL) kodu yığın çerçeve uzaklık değeri.</span><span class="sxs-lookup"><span data-stu-id="10b79-109">The value of the instruction pointer is the stack frame's offset into the function's Microsoft intermediate language (MSIL) code.</span></span> <span data-ttu-id="10b79-110">Yığın çerçevesinin etkin olursa, bu adresi yürütülecek sonraki yönergedir.</span><span class="sxs-lookup"><span data-stu-id="10b79-110">If the stack frame is active, this address is the next instruction to execute.</span></span> <span data-ttu-id="10b79-111">Yığın çerçevesinin etkin değilse, bu yığın çerçevesinin yeniden etkinleştirildiğinde yürütülecek sonraki yönergeyi adresidir.</span><span class="sxs-lookup"><span data-stu-id="10b79-111">If the stack frame is not active, this address is the next instruction to execute when the stack frame is reactivated.</span></span>  
  
 <span data-ttu-id="10b79-112">Bu çerçeve, just-ın-time (JIT) derlenmiş çerçeve ise, yönerge işaretçisini değerini değeri yalnızca yaklaşık olabilir geriye doğru gerçek yerel yönerge işaretçisinden eşleme tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="10b79-112">If this frame is a just-in-time (JIT) compiled frame, the value of the instruction pointer will be determined by mapping backwards from the actual native instruction pointer, so the value may be only approximate.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="10b79-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="10b79-113">Requirements</span></span>  
 <span data-ttu-id="10b79-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="10b79-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10b79-115">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="10b79-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="10b79-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="10b79-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="10b79-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="10b79-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
