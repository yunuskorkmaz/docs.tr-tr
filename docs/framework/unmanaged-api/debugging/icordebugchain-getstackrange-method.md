---
title: ICorDebugChain::GetStackRange Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugChain.GetStackRange
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugChain::GetStackRange
helpviewer_keywords:
- ICorDebugChain::GetStackRange method [.NET Framework debugging]
- GetStackRange method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 554284e7-3f6c-4d40-8da5-1c9317fbd484
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ce5e42bb9374f22ad29ef0e97a141a796f087a98
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugchaingetstackrange-method"></a><span data-ttu-id="b74cc-102">ICorDebugChain::GetStackRange Metodu</span><span class="sxs-lookup"><span data-stu-id="b74cc-102">ICorDebugChain::GetStackRange Method</span></span>
<span data-ttu-id="b74cc-103">Yığın kesiminin adres aralığı için bu zincirini alır.</span><span class="sxs-lookup"><span data-stu-id="b74cc-103">Gets the address range of the stack segment for this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b74cc-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b74cc-104">Syntax</span></span>  
  
```  
HRESULT GetStackRange (  
    [out] CORDB_ADDRESS      *pStart,   
    [out] CORDB_ADDRESS      *pEnd  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b74cc-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b74cc-105">Parameters</span></span>  
 `pStart`  
 <span data-ttu-id="b74cc-106">[out] Bir işaretçi bir `CORDB_ADDRESS` yığın kesiminin başlangıç adresi değer.</span><span class="sxs-lookup"><span data-stu-id="b74cc-106">[out] A pointer to a `CORDB_ADDRESS` value that is the starting address of the stack segment.</span></span>  
  
 `pEnd`  
 <span data-ttu-id="b74cc-107">[out] Bir işaretçi bir `CORDB_ADDRESS` yığın kesiminin bitiş adresi değer.</span><span class="sxs-lookup"><span data-stu-id="b74cc-107">[out] A pointer to a `CORDB_ADDRESS` value that is the ending address of the stack segment.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b74cc-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b74cc-108">Remarks</span></span>  
 <span data-ttu-id="b74cc-109">Sayısal aralığın yalnızca yığın çerçeve konumları bir karşılaştırması için anlamlıdır.</span><span class="sxs-lookup"><span data-stu-id="b74cc-109">The numeric range is meaningful only for comparison of stack frame locations.</span></span> <span data-ttu-id="b74cc-110">Yığında gerçekte depolanan hakkında varsayımlar yapamazsınız.</span><span class="sxs-lookup"><span data-stu-id="b74cc-110">You cannot make any assumptions about what is actually stored on the stack.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b74cc-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b74cc-111">Requirements</span></span>  
 <span data-ttu-id="b74cc-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b74cc-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b74cc-113">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b74cc-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b74cc-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b74cc-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b74cc-115">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b74cc-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
