---
description: ': ICorDebugCode:: CreateBreakpoint yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: a9285d59da3e3f34ea303413fca67bc39aff9e32
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99711381"
---
# <a name="icordebugcodecreatebreakpoint-method"></a><span data-ttu-id="ed8db-103">ICorDebugCode::CreateBreakpoint Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ed8db-103">ICorDebugCode::CreateBreakpoint Method</span></span>

<span data-ttu-id="ed8db-104">Belirtilen uzaklığında Bu kod kesiminde bir kesme noktası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ed8db-104">Creates a breakpoint in this code segment at the specified offset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed8db-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ed8db-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateBreakpoint (  
    [in] ULONG32     offset,  
    [out] ICorDebugFunctionBreakpoint **ppBreakpoint  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ed8db-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ed8db-106">Parameters</span></span>  

 `offset`  
 <span data-ttu-id="ed8db-107">'ndaki Kesme noktasının oluşturulacağı konum.</span><span class="sxs-lookup"><span data-stu-id="ed8db-107">[in] The offset at which to create the breakpoint.</span></span>  
  
 `ppBreakpoint`  
 <span data-ttu-id="ed8db-108">dışı Kesme noktasını temsil eden bir "ICorDebugFunctionBreakpoint" nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ed8db-108">[out] A pointer to the address of an "ICorDebugFunctionBreakpoint" object that represents the breakpoint.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ed8db-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ed8db-109">Remarks</span></span>  

 <span data-ttu-id="ed8db-110">Kesme noktası etkin olmadan önce, işlem nesnesine eklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="ed8db-110">Before the breakpoint is active, it must be added to the process object.</span></span>  
  
 <span data-ttu-id="ed8db-111">Bu kod Microsoft ara dili (MSIL) kodlarsa ve kodun tam zamanında (JıT) derlenmiş bir sürümü varsa, kesme noktası JıT ile derlenen kodda da uygulanır.</span><span class="sxs-lookup"><span data-stu-id="ed8db-111">If this code is Microsoft intermediate language (MSIL) code, and there is a just-in-time (JIT)-compiled, native version of the code, the breakpoint will be applied in the JIT-compiled code as well.</span></span> <span data-ttu-id="ed8db-112">(Kod JıT olarak derlenmişse, aynı değer de geçerlidir.)</span><span class="sxs-lookup"><span data-stu-id="ed8db-112">(The same is true if the code is JIT-compiled later.)</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ed8db-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ed8db-113">Requirements</span></span>  

 <span data-ttu-id="ed8db-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ed8db-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ed8db-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ed8db-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ed8db-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ed8db-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ed8db-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ed8db-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
