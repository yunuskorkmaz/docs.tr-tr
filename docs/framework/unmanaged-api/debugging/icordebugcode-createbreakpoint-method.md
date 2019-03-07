---
title: ICorDebugCode::CreateBreakpoint Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugCode.CreateBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::CreateBreakpoint
helpviewer_keywords:
- ICorDebugCode::CreateBreakpoint method [.NET Framework debugging]
- CreateBreakpoint method, ICorDebugCode interface [.NET Framework debugging]
ms.assetid: 46842618-0fe4-480b-871c-82fba82d23d9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: df27d2ab609551bb7a7f6f4b0ff8c7118c9f93f8
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57478683"
---
# <a name="icordebugcodecreatebreakpoint-method"></a><span data-ttu-id="0b274-102">ICorDebugCode::CreateBreakpoint Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0b274-102">ICorDebugCode::CreateBreakpoint Method</span></span>
<span data-ttu-id="0b274-103">Bu kod kesimi belirtilen uzaklık içinde bir kesme noktası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0b274-103">Creates a breakpoint in this code segment at the specified offset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b274-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0b274-104">Syntax</span></span>  
  
```  
HRESULT CreateBreakpoint (  
    [in] ULONG32     offset,  
    [out] ICorDebugFunctionBreakpoint **ppBreakpoint  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0b274-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0b274-105">Parameters</span></span>  
 `offset`  
 <span data-ttu-id="0b274-106">[in] Uzaklığı bir kesme noktası oluşturmak.</span><span class="sxs-lookup"><span data-stu-id="0b274-106">[in] The offset at which to create the breakpoint.</span></span>  
  
 `ppBreakpoint`  
 <span data-ttu-id="0b274-107">[out] Kesme noktasını temsil eden bir "ICorDebugFunctionBreakpoint" nesnenin adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0b274-107">[out] A pointer to the address of an "ICorDebugFunctionBreakpoint" object that represents the breakpoint.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0b274-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0b274-108">Remarks</span></span>  
 <span data-ttu-id="0b274-109">Kesme noktası büyük/küçük harfe etkinleştirilmeden önce işlem nesnesine eklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="0b274-109">Before the breakpoint is active, it must be added to the process object.</span></span>  
  
 <span data-ttu-id="0b274-110">Microsoft Ara dil (MSIL) kodu bu koddur ve bir tam zamanında (JIT),-kesme noktası kod derlenmiş ve yerel sürümü JIT olarak derlenmiş kodda de uygulanır.</span><span class="sxs-lookup"><span data-stu-id="0b274-110">If this code is Microsoft intermediate language (MSIL) code, and there is a just-in-time (JIT)-compiled, native version of the code, the breakpoint will be applied in the JIT-compiled code as well.</span></span> <span data-ttu-id="0b274-111">(Aynı JIT olarak derlenmiş kodu daha sonra, geçerlidir.)</span><span class="sxs-lookup"><span data-stu-id="0b274-111">(The same is true if the code is JIT-compiled later.)</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b274-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0b274-112">Requirements</span></span>  
 <span data-ttu-id="0b274-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b274-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b274-114">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0b274-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0b274-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0b274-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0b274-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b274-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b274-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0b274-117">See also</span></span>

