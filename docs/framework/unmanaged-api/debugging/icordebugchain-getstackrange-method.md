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
ms.openlocfilehash: 40ecc183c32500ad9e88ceb1bfc0528d717430e8
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894463"
---
# <a name="icordebugchaingetstackrange-method"></a><span data-ttu-id="ce300-102">ICorDebugChain::GetStackRange Metodu</span><span class="sxs-lookup"><span data-stu-id="ce300-102">ICorDebugChain::GetStackRange Method</span></span>
<span data-ttu-id="ce300-103">Bu zincir için yığın segmentinin adres aralığını alır.</span><span class="sxs-lookup"><span data-stu-id="ce300-103">Gets the address range of the stack segment for this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce300-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ce300-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStackRange (  
    [out] CORDB_ADDRESS      *pStart,
    [out] CORDB_ADDRESS      *pEnd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ce300-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ce300-105">Parameters</span></span>  
 `pStart`  
 <span data-ttu-id="ce300-106">dışı Yığın segmentinin başlangıç `CORDB_ADDRESS` adresi olan değere yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ce300-106">[out] A pointer to a `CORDB_ADDRESS` value that is the starting address of the stack segment.</span></span>  
  
 `pEnd`  
 <span data-ttu-id="ce300-107">dışı Yığın kesiminin bitiş adresi `CORDB_ADDRESS` olan değere yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ce300-107">[out] A pointer to a `CORDB_ADDRESS` value that is the ending address of the stack segment.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ce300-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ce300-108">Remarks</span></span>  
 <span data-ttu-id="ce300-109">Sayısal Aralık yalnızca yığın çerçeve konumlarının karşılaştırılmasının anlamı vardır.</span><span class="sxs-lookup"><span data-stu-id="ce300-109">The numeric range is meaningful only for comparison of stack frame locations.</span></span> <span data-ttu-id="ce300-110">Aslında yığında depolandıkları hakkında varsayımlar yapamazsınız.</span><span class="sxs-lookup"><span data-stu-id="ce300-110">You cannot make any assumptions about what is actually stored on the stack.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce300-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ce300-111">Requirements</span></span>  
 <span data-ttu-id="ce300-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ce300-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce300-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ce300-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ce300-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ce300-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ce300-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce300-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
