---
title: ICorDebugChain::GetStackRange Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugChain.GetStackRange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetStackRange
helpviewer_keywords:
- ICorDebugChain::GetStackRange method [.NET Framework debugging]
- GetStackRange method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 554284e7-3f6c-4d40-8da5-1c9317fbd484
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 37a9be7924a6d9c1f1d78bd10f9642fff22036bb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugchaingetstackrange-method"></a><span data-ttu-id="414d9-102">ICorDebugChain::GetStackRange Metodu</span><span class="sxs-lookup"><span data-stu-id="414d9-102">ICorDebugChain::GetStackRange Method</span></span>
<span data-ttu-id="414d9-103">Yığın kesiminin adres aralığı için bu zincirini alır.</span><span class="sxs-lookup"><span data-stu-id="414d9-103">Gets the address range of the stack segment for this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="414d9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="414d9-104">Syntax</span></span>  
  
```  
HRESULT GetStackRange (  
    [out] CORDB_ADDRESS      *pStart,   
    [out] CORDB_ADDRESS      *pEnd  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="414d9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="414d9-105">Parameters</span></span>  
 `pStart`  
 <span data-ttu-id="414d9-106">[out] Bir işaretçi bir `CORDB_ADDRESS` yığın kesiminin başlangıç adresi değer.</span><span class="sxs-lookup"><span data-stu-id="414d9-106">[out] A pointer to a `CORDB_ADDRESS` value that is the starting address of the stack segment.</span></span>  
  
 `pEnd`  
 <span data-ttu-id="414d9-107">[out] Bir işaretçi bir `CORDB_ADDRESS` yığın kesiminin bitiş adresi değer.</span><span class="sxs-lookup"><span data-stu-id="414d9-107">[out] A pointer to a `CORDB_ADDRESS` value that is the ending address of the stack segment.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="414d9-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="414d9-108">Remarks</span></span>  
 <span data-ttu-id="414d9-109">Sayısal aralığın yalnızca yığın çerçeve konumları bir karşılaştırması için anlamlıdır.</span><span class="sxs-lookup"><span data-stu-id="414d9-109">The numeric range is meaningful only for comparison of stack frame locations.</span></span> <span data-ttu-id="414d9-110">Yığında gerçekte depolanan hakkında varsayımlar yapamazsınız.</span><span class="sxs-lookup"><span data-stu-id="414d9-110">You cannot make any assumptions about what is actually stored on the stack.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="414d9-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="414d9-111">Requirements</span></span>  
 <span data-ttu-id="414d9-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="414d9-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="414d9-113">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="414d9-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="414d9-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="414d9-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="414d9-115">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="414d9-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
