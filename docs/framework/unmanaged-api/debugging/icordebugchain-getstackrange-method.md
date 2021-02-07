---
description: ': Icordebugzincirine:: GetStackRange metodu hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 066dda06564655350d799dabb54acd622b828172
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99694937"
---
# <a name="icordebugchaingetstackrange-method"></a><span data-ttu-id="62e12-103">ICorDebugChain::GetStackRange Metodu</span><span class="sxs-lookup"><span data-stu-id="62e12-103">ICorDebugChain::GetStackRange Method</span></span>

<span data-ttu-id="62e12-104">Bu zincir için yığın segmentinin adres aralığını alır.</span><span class="sxs-lookup"><span data-stu-id="62e12-104">Gets the address range of the stack segment for this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62e12-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="62e12-105">Syntax</span></span>  
  
```cpp  
HRESULT GetStackRange (  
    [out] CORDB_ADDRESS      *pStart,
    [out] CORDB_ADDRESS      *pEnd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="62e12-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="62e12-106">Parameters</span></span>  

 `pStart`  
 <span data-ttu-id="62e12-107">dışı `CORDB_ADDRESS` Yığın segmentinin başlangıç adresi olan değere yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="62e12-107">[out] A pointer to a `CORDB_ADDRESS` value that is the starting address of the stack segment.</span></span>  
  
 `pEnd`  
 <span data-ttu-id="62e12-108">dışı `CORDB_ADDRESS` Yığın kesiminin bitiş adresi olan değere yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="62e12-108">[out] A pointer to a `CORDB_ADDRESS` value that is the ending address of the stack segment.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="62e12-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="62e12-109">Remarks</span></span>  

 <span data-ttu-id="62e12-110">Sayısal Aralık yalnızca yığın çerçeve konumlarının karşılaştırılmasının anlamı vardır.</span><span class="sxs-lookup"><span data-stu-id="62e12-110">The numeric range is meaningful only for comparison of stack frame locations.</span></span> <span data-ttu-id="62e12-111">Aslında yığında depolandıkları hakkında varsayımlar yapamazsınız.</span><span class="sxs-lookup"><span data-stu-id="62e12-111">You cannot make any assumptions about what is actually stored on the stack.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62e12-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="62e12-112">Requirements</span></span>  

 <span data-ttu-id="62e12-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="62e12-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62e12-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="62e12-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="62e12-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="62e12-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="62e12-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62e12-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
