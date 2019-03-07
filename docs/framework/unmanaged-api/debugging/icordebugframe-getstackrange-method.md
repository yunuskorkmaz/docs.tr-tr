---
title: ICorDebugFrame::GetStackRange Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetStackRange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetStackRange
helpviewer_keywords:
- GetStackRange method, ICorDebugFrame interface [.NET Framework debugging]
- ICorDebugFrame::GetStackRange method [.NET Framework debugging]
ms.assetid: fab037cb-fda6-40fb-9367-921e435dd5a0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 43532888d181adcb7a7e3760f2a5e3d8f664a35c
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57492289"
---
# <a name="icordebugframegetstackrange-method"></a><span data-ttu-id="6d88e-102">ICorDebugFrame::GetStackRange Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6d88e-102">ICorDebugFrame::GetStackRange Method</span></span>
<span data-ttu-id="6d88e-103">Bu yığın çerçevesinin mutlak adres aralığını alır.</span><span class="sxs-lookup"><span data-stu-id="6d88e-103">Gets the absolute address range of this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d88e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6d88e-104">Syntax</span></span>  
  
```  
HRESULT GetStackRange (  
    [out] CORDB_ADDRESS      *pStart,   
    [out] CORDB_ADDRESS      *pEnd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6d88e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6d88e-105">Parameters</span></span>  
 `pStart`  
 <span data-ttu-id="6d88e-106">[out] Bir işaretçi bir `CORDB_ADDRESS` bu tarafından temsil edilen yığın çerçevesinin başlangıç adresini belirten `ICorDebugFrame` nesne.</span><span class="sxs-lookup"><span data-stu-id="6d88e-106">[out] A pointer to a `CORDB_ADDRESS` that specifies the starting address of the stack frame represented by this `ICorDebugFrame` object.</span></span>  
  
 `pEnd`  
 <span data-ttu-id="6d88e-107">[out] Bir işaretçi bir `CORDB_ADDRESS` bitiş adresini bu tarafından temsil edilen yığın çerçevesinin belirten `ICorDebugFrame` nesne.</span><span class="sxs-lookup"><span data-stu-id="6d88e-107">[out] A pointer to a `CORDB_ADDRESS` that specifies the ending address of the stack frame represented by this `ICorDebugFrame` object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6d88e-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6d88e-108">Remarks</span></span>  
 <span data-ttu-id="6d88e-109">Yığın adres aralığı, birden çok hata ayıklama motorlarından toplanan Aralanmış yığın izlemelerini birbirine eklemekten için kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="6d88e-109">The address range of the stack is useful for piecing together interleaved stack traces gathered from multiple debugging engines.</span></span> <span data-ttu-id="6d88e-110">Sayısal Aralık yığın çerçevesi bir içeriği hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="6d88e-110">The numeric range provides no information about the contents of the stack frame.</span></span> <span data-ttu-id="6d88e-111">Bu, yalnızca yığın çerçeve konumu bir karşılaştırması için anlamlı olur.</span><span class="sxs-lookup"><span data-stu-id="6d88e-111">It is meaningful only for comparison of stack frame locations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d88e-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6d88e-112">Requirements</span></span>  
 <span data-ttu-id="6d88e-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6d88e-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d88e-114">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6d88e-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6d88e-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6d88e-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6d88e-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d88e-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
