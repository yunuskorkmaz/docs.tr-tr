---
title: ICorDebugChain::GetStackRange Metodu
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ac40927ac9469e4a2fb74fb550287130b9bb9f83
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57481566"
---
# <a name="icordebugchaingetstackrange-method"></a><span data-ttu-id="1cdc8-102">ICorDebugChain::GetStackRange Metodu</span><span class="sxs-lookup"><span data-stu-id="1cdc8-102">ICorDebugChain::GetStackRange Method</span></span>
<span data-ttu-id="1cdc8-103">Yığın kesiminin adres aralığı için bu zincir alır.</span><span class="sxs-lookup"><span data-stu-id="1cdc8-103">Gets the address range of the stack segment for this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1cdc8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1cdc8-104">Syntax</span></span>  
  
```  
HRESULT GetStackRange (  
    [out] CORDB_ADDRESS      *pStart,   
    [out] CORDB_ADDRESS      *pEnd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1cdc8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1cdc8-105">Parameters</span></span>  
 `pStart`  
 <span data-ttu-id="1cdc8-106">[out] Bir işaretçi bir `CORDB_ADDRESS` yığın kesimin başlangıç adresi olan değer.</span><span class="sxs-lookup"><span data-stu-id="1cdc8-106">[out] A pointer to a `CORDB_ADDRESS` value that is the starting address of the stack segment.</span></span>  
  
 `pEnd`  
 <span data-ttu-id="1cdc8-107">[out] Bir işaretçi bir `CORDB_ADDRESS` yığın kesiminin bitiş adresi olan değer.</span><span class="sxs-lookup"><span data-stu-id="1cdc8-107">[out] A pointer to a `CORDB_ADDRESS` value that is the ending address of the stack segment.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1cdc8-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1cdc8-108">Remarks</span></span>  
 <span data-ttu-id="1cdc8-109">Sayısal Aralık yalnızca yığın çerçeve konumu bir karşılaştırması için anlamlı.</span><span class="sxs-lookup"><span data-stu-id="1cdc8-109">The numeric range is meaningful only for comparison of stack frame locations.</span></span> <span data-ttu-id="1cdc8-110">Aslında yığın üzerinde depolanan hakkında varsayımlar yapamazsınız.</span><span class="sxs-lookup"><span data-stu-id="1cdc8-110">You cannot make any assumptions about what is actually stored on the stack.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1cdc8-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1cdc8-111">Requirements</span></span>  
 <span data-ttu-id="1cdc8-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1cdc8-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1cdc8-113">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1cdc8-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1cdc8-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1cdc8-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1cdc8-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1cdc8-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
