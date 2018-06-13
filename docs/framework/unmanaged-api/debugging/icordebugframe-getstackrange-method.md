---
title: ICorDebugFrame::GetStackRange Metodu
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
ms.openlocfilehash: 5da87071bc23ac17a3077049cd77f0fb8611439f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33413026"
---
# <a name="icordebugframegetstackrange-method"></a><span data-ttu-id="af741-102">ICorDebugFrame::GetStackRange Metodu</span><span class="sxs-lookup"><span data-stu-id="af741-102">ICorDebugFrame::GetStackRange Method</span></span>
<span data-ttu-id="af741-103">Bu yığın çerçevesi mutlak bir adres aralığını alır.</span><span class="sxs-lookup"><span data-stu-id="af741-103">Gets the absolute address range of this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af741-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="af741-104">Syntax</span></span>  
  
```  
HRESULT GetStackRange (  
    [out] CORDB_ADDRESS      *pStart,   
    [out] CORDB_ADDRESS      *pEnd  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="af741-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="af741-105">Parameters</span></span>  
 `pStart`  
 <span data-ttu-id="af741-106">[out] Bir işaretçi bir `CORDB_ADDRESS` bu tarafından temsil edilen yığın çerçevesi başlangıç adresini belirtir `ICorDebugFrame` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="af741-106">[out] A pointer to a `CORDB_ADDRESS` that specifies the starting address of the stack frame represented by this `ICorDebugFrame` object.</span></span>  
  
 `pEnd`  
 <span data-ttu-id="af741-107">[out] Bir işaretçi bir `CORDB_ADDRESS` bu tarafından temsil edilen yığın çerçevesi bitiş adresini belirtir `ICorDebugFrame` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="af741-107">[out] A pointer to a `CORDB_ADDRESS` that specifies the ending address of the stack frame represented by this `ICorDebugFrame` object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="af741-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="af741-108">Remarks</span></span>  
 <span data-ttu-id="af741-109">Yığın adres aralığı, birden çok hata ayıklama motorlarından toplanan araya eklemeli Yığın izlemeleri birlikte eklemekten için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="af741-109">The address range of the stack is useful for piecing together interleaved stack traces gathered from multiple debugging engines.</span></span> <span data-ttu-id="af741-110">Sayısal aralığın yığın çerçevesi içeriği hakkında hiçbir bilgi verilmektedir.</span><span class="sxs-lookup"><span data-stu-id="af741-110">The numeric range provides no information about the contents of the stack frame.</span></span> <span data-ttu-id="af741-111">Yalnızca yığın çerçeve konumları bir karşılaştırması için anlamlıdır.</span><span class="sxs-lookup"><span data-stu-id="af741-111">It is meaningful only for comparison of stack frame locations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af741-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="af741-112">Requirements</span></span>  
 <span data-ttu-id="af741-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="af741-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af741-114">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="af741-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="af741-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="af741-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="af741-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af741-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
