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
ms.openlocfilehash: d9430c5a1f37a0507b383ea5437f7d7fed706c43
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123857"
---
# <a name="icordebugchaingetstackrange-method"></a><span data-ttu-id="0eff0-102">ICorDebugChain::GetStackRange Metodu</span><span class="sxs-lookup"><span data-stu-id="0eff0-102">ICorDebugChain::GetStackRange Method</span></span>
<span data-ttu-id="0eff0-103">Bu zincir için yığın segmentinin adres aralığını alır.</span><span class="sxs-lookup"><span data-stu-id="0eff0-103">Gets the address range of the stack segment for this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0eff0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0eff0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStackRange (  
    [out] CORDB_ADDRESS      *pStart,   
    [out] CORDB_ADDRESS      *pEnd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0eff0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0eff0-105">Parameters</span></span>  
 `pStart`  
 <span data-ttu-id="0eff0-106">dışı Yığın segmentinin başlangıç adresi olan `CORDB_ADDRESS` değere yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0eff0-106">[out] A pointer to a `CORDB_ADDRESS` value that is the starting address of the stack segment.</span></span>  
  
 `pEnd`  
 <span data-ttu-id="0eff0-107">dışı Yığın segmentinin bitiş adresi olan `CORDB_ADDRESS` değere yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0eff0-107">[out] A pointer to a `CORDB_ADDRESS` value that is the ending address of the stack segment.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0eff0-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0eff0-108">Remarks</span></span>  
 <span data-ttu-id="0eff0-109">Sayısal Aralık yalnızca yığın çerçeve konumlarının karşılaştırılmasının anlamı vardır.</span><span class="sxs-lookup"><span data-stu-id="0eff0-109">The numeric range is meaningful only for comparison of stack frame locations.</span></span> <span data-ttu-id="0eff0-110">Aslında yığında depolandıkları hakkında varsayımlar yapamazsınız.</span><span class="sxs-lookup"><span data-stu-id="0eff0-110">You cannot make any assumptions about what is actually stored on the stack.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0eff0-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0eff0-111">Requirements</span></span>  
 <span data-ttu-id="0eff0-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0eff0-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0eff0-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="0eff0-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0eff0-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="0eff0-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0eff0-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0eff0-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
