---
description: ': ICorDebugFrame:: GetStackRange metodu hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 1f1278e0c00addc3c14f4e1c8d3ed5aad0381526
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99692907"
---
# <a name="icordebugframegetstackrange-method"></a><span data-ttu-id="06bec-103">ICorDebugFrame::GetStackRange Yöntemi</span><span class="sxs-lookup"><span data-stu-id="06bec-103">ICorDebugFrame::GetStackRange Method</span></span>

<span data-ttu-id="06bec-104">Bu yığın çerçevesinin mutlak adres aralığını alır.</span><span class="sxs-lookup"><span data-stu-id="06bec-104">Gets the absolute address range of this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06bec-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="06bec-105">Syntax</span></span>  
  
```cpp  
HRESULT GetStackRange (  
    [out] CORDB_ADDRESS      *pStart,
    [out] CORDB_ADDRESS      *pEnd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="06bec-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="06bec-106">Parameters</span></span>  

 `pStart`  
 <span data-ttu-id="06bec-107">dışı `CORDB_ADDRESS` Bu nesne tarafından temsil edilen yığın çerçevesinin başlangıç adresini belirten bir işaretçisi `ICorDebugFrame` .</span><span class="sxs-lookup"><span data-stu-id="06bec-107">[out] A pointer to a `CORDB_ADDRESS` that specifies the starting address of the stack frame represented by this `ICorDebugFrame` object.</span></span>  
  
 `pEnd`  
 <span data-ttu-id="06bec-108">dışı `CORDB_ADDRESS` Bu nesne tarafından temsil edilen yığın çerçevesinin bitiş adresini belirten bir işaretçisi `ICorDebugFrame` .</span><span class="sxs-lookup"><span data-stu-id="06bec-108">[out] A pointer to a `CORDB_ADDRESS` that specifies the ending address of the stack frame represented by this `ICorDebugFrame` object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="06bec-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="06bec-109">Remarks</span></span>  

 <span data-ttu-id="06bec-110">Yığının adres aralığı, birden çok hata ayıklama altyapılarından toplanan araya eklemeli yığın izlemeleri piecing için faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="06bec-110">The address range of the stack is useful for piecing together interleaved stack traces gathered from multiple debugging engines.</span></span> <span data-ttu-id="06bec-111">Sayısal Aralık, yığın çerçevesinin içeriğiyle ilgili bilgi sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="06bec-111">The numeric range provides no information about the contents of the stack frame.</span></span> <span data-ttu-id="06bec-112">Yalnızca yığın çerçeve konumlarının karşılaştırılmasının anlamı vardır.</span><span class="sxs-lookup"><span data-stu-id="06bec-112">It is meaningful only for comparison of stack frame locations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="06bec-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="06bec-113">Requirements</span></span>  

 <span data-ttu-id="06bec-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="06bec-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="06bec-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="06bec-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="06bec-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="06bec-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="06bec-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="06bec-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
