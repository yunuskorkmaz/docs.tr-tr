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
ms.openlocfilehash: cacdccf5c27cd1d115134d49e754b4ace2870b72
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83205157"
---
# <a name="icordebugframegetstackrange-method"></a><span data-ttu-id="f5d9e-102">ICorDebugFrame::GetStackRange Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f5d9e-102">ICorDebugFrame::GetStackRange Method</span></span>
<span data-ttu-id="f5d9e-103">Bu yığın çerçevesinin mutlak adres aralığını alır.</span><span class="sxs-lookup"><span data-stu-id="f5d9e-103">Gets the absolute address range of this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5d9e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f5d9e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStackRange (  
    [out] CORDB_ADDRESS      *pStart,
    [out] CORDB_ADDRESS      *pEnd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f5d9e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f5d9e-105">Parameters</span></span>  
 `pStart`  
 <span data-ttu-id="f5d9e-106">dışı `CORDB_ADDRESS`Bu nesne tarafından temsil edilen yığın çerçevesinin başlangıç adresini belirten bir işaretçisi `ICorDebugFrame` .</span><span class="sxs-lookup"><span data-stu-id="f5d9e-106">[out] A pointer to a `CORDB_ADDRESS` that specifies the starting address of the stack frame represented by this `ICorDebugFrame` object.</span></span>  
  
 `pEnd`  
 <span data-ttu-id="f5d9e-107">dışı `CORDB_ADDRESS`Bu nesne tarafından temsil edilen yığın çerçevesinin bitiş adresini belirten bir işaretçisi `ICorDebugFrame` .</span><span class="sxs-lookup"><span data-stu-id="f5d9e-107">[out] A pointer to a `CORDB_ADDRESS` that specifies the ending address of the stack frame represented by this `ICorDebugFrame` object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f5d9e-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f5d9e-108">Remarks</span></span>  
 <span data-ttu-id="f5d9e-109">Yığının adres aralığı, birden çok hata ayıklama altyapılarından toplanan araya eklemeli yığın izlemeleri piecing için faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="f5d9e-109">The address range of the stack is useful for piecing together interleaved stack traces gathered from multiple debugging engines.</span></span> <span data-ttu-id="f5d9e-110">Sayısal Aralık, yığın çerçevesinin içeriğiyle ilgili bilgi sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="f5d9e-110">The numeric range provides no information about the contents of the stack frame.</span></span> <span data-ttu-id="f5d9e-111">Yalnızca yığın çerçeve konumlarının karşılaştırılmasının anlamı vardır.</span><span class="sxs-lookup"><span data-stu-id="f5d9e-111">It is meaningful only for comparison of stack frame locations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5d9e-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f5d9e-112">Requirements</span></span>  
 <span data-ttu-id="f5d9e-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5d9e-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5d9e-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f5d9e-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f5d9e-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="f5d9e-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f5d9e-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5d9e-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
