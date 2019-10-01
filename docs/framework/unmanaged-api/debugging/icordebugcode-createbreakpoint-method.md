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
ms.openlocfilehash: 1ec7d615b99ac301948d7ea25318115713ce06ea
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700851"
---
# <a name="icordebugcodecreatebreakpoint-method"></a><span data-ttu-id="4a893-102">ICorDebugCode::CreateBreakpoint Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4a893-102">ICorDebugCode::CreateBreakpoint Method</span></span>
<span data-ttu-id="4a893-103">Belirtilen uzaklığında Bu kod kesiminde bir kesme noktası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4a893-103">Creates a breakpoint in this code segment at the specified offset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a893-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4a893-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateBreakpoint (  
    [in] ULONG32     offset,  
    [out] ICorDebugFunctionBreakpoint **ppBreakpoint  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4a893-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4a893-105">Parameters</span></span>  
 `offset`  
 <span data-ttu-id="4a893-106">'ndaki Kesme noktasının oluşturulacağı konum.</span><span class="sxs-lookup"><span data-stu-id="4a893-106">[in] The offset at which to create the breakpoint.</span></span>  
  
 `ppBreakpoint`  
 <span data-ttu-id="4a893-107">dışı Kesme noktasını temsil eden bir "ICorDebugFunctionBreakpoint" nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="4a893-107">[out] A pointer to the address of an "ICorDebugFunctionBreakpoint" object that represents the breakpoint.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4a893-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4a893-108">Remarks</span></span>  
 <span data-ttu-id="4a893-109">Kesme noktası etkin olmadan önce, işlem nesnesine eklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="4a893-109">Before the breakpoint is active, it must be added to the process object.</span></span>  
  
 <span data-ttu-id="4a893-110">Bu kod Microsoft ara dili (MSIL) kodlarsa ve kodun tam zamanında (JıT) derlenmiş bir sürümü varsa, kesme noktası JıT ile derlenen kodda da uygulanır.</span><span class="sxs-lookup"><span data-stu-id="4a893-110">If this code is Microsoft intermediate language (MSIL) code, and there is a just-in-time (JIT)-compiled, native version of the code, the breakpoint will be applied in the JIT-compiled code as well.</span></span> <span data-ttu-id="4a893-111">(Kod JıT olarak derlenmişse, aynı değer de geçerlidir.)</span><span class="sxs-lookup"><span data-stu-id="4a893-111">(The same is true if the code is JIT-compiled later.)</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a893-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4a893-112">Requirements</span></span>  
 <span data-ttu-id="4a893-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4a893-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a893-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="4a893-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4a893-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="4a893-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4a893-116">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a893-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
