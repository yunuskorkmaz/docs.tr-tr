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
ms.openlocfilehash: 0cfc734e3c2d250bba045a926f5b178b6cbc1ba4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728205"
---
# <a name="icordebugframegetstackrange-method"></a><span data-ttu-id="97aee-102">ICorDebugFrame::GetStackRange Yöntemi</span><span class="sxs-lookup"><span data-stu-id="97aee-102">ICorDebugFrame::GetStackRange Method</span></span>

<span data-ttu-id="97aee-103">Bu yığın çerçevesinin mutlak adres aralığını alır.</span><span class="sxs-lookup"><span data-stu-id="97aee-103">Gets the absolute address range of this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97aee-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="97aee-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStackRange (  
    [out] CORDB_ADDRESS      *pStart,
    [out] CORDB_ADDRESS      *pEnd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="97aee-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="97aee-105">Parameters</span></span>  

 `pStart`  
 <span data-ttu-id="97aee-106">dışı `CORDB_ADDRESS` Bu nesne tarafından temsil edilen yığın çerçevesinin başlangıç adresini belirten bir işaretçisi `ICorDebugFrame` .</span><span class="sxs-lookup"><span data-stu-id="97aee-106">[out] A pointer to a `CORDB_ADDRESS` that specifies the starting address of the stack frame represented by this `ICorDebugFrame` object.</span></span>  
  
 `pEnd`  
 <span data-ttu-id="97aee-107">dışı `CORDB_ADDRESS` Bu nesne tarafından temsil edilen yığın çerçevesinin bitiş adresini belirten bir işaretçisi `ICorDebugFrame` .</span><span class="sxs-lookup"><span data-stu-id="97aee-107">[out] A pointer to a `CORDB_ADDRESS` that specifies the ending address of the stack frame represented by this `ICorDebugFrame` object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="97aee-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="97aee-108">Remarks</span></span>  

 <span data-ttu-id="97aee-109">Yığının adres aralığı, birden çok hata ayıklama altyapılarından toplanan araya eklemeli yığın izlemeleri piecing için faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="97aee-109">The address range of the stack is useful for piecing together interleaved stack traces gathered from multiple debugging engines.</span></span> <span data-ttu-id="97aee-110">Sayısal Aralık, yığın çerçevesinin içeriğiyle ilgili bilgi sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="97aee-110">The numeric range provides no information about the contents of the stack frame.</span></span> <span data-ttu-id="97aee-111">Yalnızca yığın çerçeve konumlarının karşılaştırılmasının anlamı vardır.</span><span class="sxs-lookup"><span data-stu-id="97aee-111">It is meaningful only for comparison of stack frame locations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="97aee-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="97aee-112">Requirements</span></span>  

 <span data-ttu-id="97aee-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="97aee-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="97aee-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="97aee-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="97aee-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="97aee-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="97aee-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="97aee-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
