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
ms.openlocfilehash: 8a6db1990df2ed6b29d548c147ed40b5bc98254d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67745681"
---
# <a name="icordebugchaingetstackrange-method"></a><span data-ttu-id="b86f1-102">ICorDebugChain::GetStackRange Metodu</span><span class="sxs-lookup"><span data-stu-id="b86f1-102">ICorDebugChain::GetStackRange Method</span></span>
<span data-ttu-id="b86f1-103">Yığın kesiminin adres aralığı için bu zincir alır.</span><span class="sxs-lookup"><span data-stu-id="b86f1-103">Gets the address range of the stack segment for this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b86f1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b86f1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStackRange (  
    [out] CORDB_ADDRESS      *pStart,   
    [out] CORDB_ADDRESS      *pEnd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b86f1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b86f1-105">Parameters</span></span>  
 `pStart`  
 <span data-ttu-id="b86f1-106">[out] Bir işaretçi bir `CORDB_ADDRESS` yığın kesimin başlangıç adresi olan değer.</span><span class="sxs-lookup"><span data-stu-id="b86f1-106">[out] A pointer to a `CORDB_ADDRESS` value that is the starting address of the stack segment.</span></span>  
  
 `pEnd`  
 <span data-ttu-id="b86f1-107">[out] Bir işaretçi bir `CORDB_ADDRESS` yığın kesiminin bitiş adresi olan değer.</span><span class="sxs-lookup"><span data-stu-id="b86f1-107">[out] A pointer to a `CORDB_ADDRESS` value that is the ending address of the stack segment.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b86f1-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b86f1-108">Remarks</span></span>  
 <span data-ttu-id="b86f1-109">Sayısal Aralık yalnızca yığın çerçeve konumu bir karşılaştırması için anlamlı.</span><span class="sxs-lookup"><span data-stu-id="b86f1-109">The numeric range is meaningful only for comparison of stack frame locations.</span></span> <span data-ttu-id="b86f1-110">Aslında yığın üzerinde depolanan hakkında varsayımlar yapamazsınız.</span><span class="sxs-lookup"><span data-stu-id="b86f1-110">You cannot make any assumptions about what is actually stored on the stack.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b86f1-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b86f1-111">Requirements</span></span>  
 <span data-ttu-id="b86f1-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b86f1-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b86f1-113">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b86f1-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b86f1-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b86f1-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b86f1-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b86f1-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
