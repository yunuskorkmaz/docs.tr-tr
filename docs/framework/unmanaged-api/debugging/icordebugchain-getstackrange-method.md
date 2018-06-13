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
ms.openlocfilehash: 226f8c431b90d53366aa5e504101e7de581ec570
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402476"
---
# <a name="icordebugchaingetstackrange-method"></a><span data-ttu-id="beb6b-102">ICorDebugChain::GetStackRange Metodu</span><span class="sxs-lookup"><span data-stu-id="beb6b-102">ICorDebugChain::GetStackRange Method</span></span>
<span data-ttu-id="beb6b-103">Yığın kesiminin adres aralığı için bu zincirini alır.</span><span class="sxs-lookup"><span data-stu-id="beb6b-103">Gets the address range of the stack segment for this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="beb6b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="beb6b-104">Syntax</span></span>  
  
```  
HRESULT GetStackRange (  
    [out] CORDB_ADDRESS      *pStart,   
    [out] CORDB_ADDRESS      *pEnd  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="beb6b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="beb6b-105">Parameters</span></span>  
 `pStart`  
 <span data-ttu-id="beb6b-106">[out] Bir işaretçi bir `CORDB_ADDRESS` yığın kesiminin başlangıç adresi değer.</span><span class="sxs-lookup"><span data-stu-id="beb6b-106">[out] A pointer to a `CORDB_ADDRESS` value that is the starting address of the stack segment.</span></span>  
  
 `pEnd`  
 <span data-ttu-id="beb6b-107">[out] Bir işaretçi bir `CORDB_ADDRESS` yığın kesiminin bitiş adresi değer.</span><span class="sxs-lookup"><span data-stu-id="beb6b-107">[out] A pointer to a `CORDB_ADDRESS` value that is the ending address of the stack segment.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="beb6b-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="beb6b-108">Remarks</span></span>  
 <span data-ttu-id="beb6b-109">Sayısal aralığın yalnızca yığın çerçeve konumları bir karşılaştırması için anlamlıdır.</span><span class="sxs-lookup"><span data-stu-id="beb6b-109">The numeric range is meaningful only for comparison of stack frame locations.</span></span> <span data-ttu-id="beb6b-110">Yığında gerçekte depolanan hakkında varsayımlar yapamazsınız.</span><span class="sxs-lookup"><span data-stu-id="beb6b-110">You cannot make any assumptions about what is actually stored on the stack.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="beb6b-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="beb6b-111">Requirements</span></span>  
 <span data-ttu-id="beb6b-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="beb6b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="beb6b-113">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="beb6b-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="beb6b-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="beb6b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="beb6b-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="beb6b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
