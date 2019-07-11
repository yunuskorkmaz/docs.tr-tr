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
ms.openlocfilehash: c9f58e66286f5e3e169507efd2f87ce10e9d323b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67754859"
---
# <a name="icordebugframegetstackrange-method"></a><span data-ttu-id="d592e-102">ICorDebugFrame::GetStackRange Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d592e-102">ICorDebugFrame::GetStackRange Method</span></span>
<span data-ttu-id="d592e-103">Bu yığın çerçevesinin mutlak adres aralığını alır.</span><span class="sxs-lookup"><span data-stu-id="d592e-103">Gets the absolute address range of this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d592e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d592e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStackRange (  
    [out] CORDB_ADDRESS      *pStart,   
    [out] CORDB_ADDRESS      *pEnd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d592e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d592e-105">Parameters</span></span>  
 `pStart`  
 <span data-ttu-id="d592e-106">[out] Bir işaretçi bir `CORDB_ADDRESS` bu tarafından temsil edilen yığın çerçevesinin başlangıç adresini belirten `ICorDebugFrame` nesne.</span><span class="sxs-lookup"><span data-stu-id="d592e-106">[out] A pointer to a `CORDB_ADDRESS` that specifies the starting address of the stack frame represented by this `ICorDebugFrame` object.</span></span>  
  
 `pEnd`  
 <span data-ttu-id="d592e-107">[out] Bir işaretçi bir `CORDB_ADDRESS` bitiş adresini bu tarafından temsil edilen yığın çerçevesinin belirten `ICorDebugFrame` nesne.</span><span class="sxs-lookup"><span data-stu-id="d592e-107">[out] A pointer to a `CORDB_ADDRESS` that specifies the ending address of the stack frame represented by this `ICorDebugFrame` object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d592e-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d592e-108">Remarks</span></span>  
 <span data-ttu-id="d592e-109">Yığın adres aralığı, birden çok hata ayıklama motorlarından toplanan Aralanmış yığın izlemelerini birbirine eklemekten için kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="d592e-109">The address range of the stack is useful for piecing together interleaved stack traces gathered from multiple debugging engines.</span></span> <span data-ttu-id="d592e-110">Sayısal Aralık yığın çerçevesi bir içeriği hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="d592e-110">The numeric range provides no information about the contents of the stack frame.</span></span> <span data-ttu-id="d592e-111">Bu, yalnızca yığın çerçeve konumu bir karşılaştırması için anlamlı olur.</span><span class="sxs-lookup"><span data-stu-id="d592e-111">It is meaningful only for comparison of stack frame locations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d592e-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d592e-112">Requirements</span></span>  
 <span data-ttu-id="d592e-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d592e-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d592e-114">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d592e-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d592e-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d592e-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d592e-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d592e-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
