---
title: ICorDebugFrame::GetStackRange Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFrame.GetStackRange
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugFrame::GetStackRange
helpviewer_keywords:
- GetStackRange method, ICorDebugFrame interface [.NET Framework debugging]
- ICorDebugFrame::GetStackRange method [.NET Framework debugging]
ms.assetid: fab037cb-fda6-40fb-9367-921e435dd5a0
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3c4c9c0a531d93ca2c7c72f50bcd2f7ee98887e9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugframegetstackrange-method"></a><span data-ttu-id="b8d0a-102">ICorDebugFrame::GetStackRange Metodu</span><span class="sxs-lookup"><span data-stu-id="b8d0a-102">ICorDebugFrame::GetStackRange Method</span></span>
<span data-ttu-id="b8d0a-103">Bu yığın çerçevesi mutlak bir adres aralığını alır.</span><span class="sxs-lookup"><span data-stu-id="b8d0a-103">Gets the absolute address range of this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8d0a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b8d0a-104">Syntax</span></span>  
  
```  
HRESULT GetStackRange (  
    [out] CORDB_ADDRESS      *pStart,   
    [out] CORDB_ADDRESS      *pEnd  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b8d0a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b8d0a-105">Parameters</span></span>  
 `pStart`  
 <span data-ttu-id="b8d0a-106">[out] Bir işaretçi bir `CORDB_ADDRESS` bu tarafından temsil edilen yığın çerçevesi başlangıç adresini belirtir `ICorDebugFrame` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="b8d0a-106">[out] A pointer to a `CORDB_ADDRESS` that specifies the starting address of the stack frame represented by this `ICorDebugFrame` object.</span></span>  
  
 `pEnd`  
 <span data-ttu-id="b8d0a-107">[out] Bir işaretçi bir `CORDB_ADDRESS` bu tarafından temsil edilen yığın çerçevesi bitiş adresini belirtir `ICorDebugFrame` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="b8d0a-107">[out] A pointer to a `CORDB_ADDRESS` that specifies the ending address of the stack frame represented by this `ICorDebugFrame` object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b8d0a-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b8d0a-108">Remarks</span></span>  
 <span data-ttu-id="b8d0a-109">Yığın adres aralığı, birden çok hata ayıklama motorlarından toplanan araya eklemeli Yığın izlemeleri birlikte eklemekten için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="b8d0a-109">The address range of the stack is useful for piecing together interleaved stack traces gathered from multiple debugging engines.</span></span> <span data-ttu-id="b8d0a-110">Sayısal aralığın yığın çerçevesi içeriği hakkında hiçbir bilgi verilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b8d0a-110">The numeric range provides no information about the contents of the stack frame.</span></span> <span data-ttu-id="b8d0a-111">Yalnızca yığın çerçeve konumları bir karşılaştırması için anlamlıdır.</span><span class="sxs-lookup"><span data-stu-id="b8d0a-111">It is meaningful only for comparison of stack frame locations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b8d0a-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b8d0a-112">Requirements</span></span>  
 <span data-ttu-id="b8d0a-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b8d0a-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8d0a-114">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b8d0a-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b8d0a-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b8d0a-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b8d0a-116">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b8d0a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
