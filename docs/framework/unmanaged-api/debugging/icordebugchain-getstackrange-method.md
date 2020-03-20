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
ms.openlocfilehash: 64e697323377d664b7b1e36bbf5931a44465cc51
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178951"
---
# <a name="icordebugchaingetstackrange-method"></a><span data-ttu-id="a68d6-102">ICorDebugChain::GetStackRange Metodu</span><span class="sxs-lookup"><span data-stu-id="a68d6-102">ICorDebugChain::GetStackRange Method</span></span>
<span data-ttu-id="a68d6-103">Bu zincirin yığın kesiminin adres aralığını alır.</span><span class="sxs-lookup"><span data-stu-id="a68d6-103">Gets the address range of the stack segment for this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a68d6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a68d6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStackRange (  
    [out] CORDB_ADDRESS      *pStart,
    [out] CORDB_ADDRESS      *pEnd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a68d6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a68d6-105">Parameters</span></span>  
 `pStart`  
 <span data-ttu-id="a68d6-106">[çıkış] Yığın kesiminin `CORDB_ADDRESS` başlangıç adresi olan bir değeriçin işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a68d6-106">[out] A pointer to a `CORDB_ADDRESS` value that is the starting address of the stack segment.</span></span>  
  
 `pEnd`  
 <span data-ttu-id="a68d6-107">[çıkış] Yığın kesiminin `CORDB_ADDRESS` bitiş adresi olan bir değerin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="a68d6-107">[out] A pointer to a `CORDB_ADDRESS` value that is the ending address of the stack segment.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a68d6-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a68d6-108">Remarks</span></span>  
 <span data-ttu-id="a68d6-109">Sayısal aralık yalnızca yığın çerçeve konumlarının karşılaştırılması için anlamlıdır.</span><span class="sxs-lookup"><span data-stu-id="a68d6-109">The numeric range is meaningful only for comparison of stack frame locations.</span></span> <span data-ttu-id="a68d6-110">Yığında gerçekte nelerin depolanmış olduğu hakkında herhangi bir varsayımda bulunamazsınız.</span><span class="sxs-lookup"><span data-stu-id="a68d6-110">You cannot make any assumptions about what is actually stored on the stack.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a68d6-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a68d6-111">Requirements</span></span>  
 <span data-ttu-id="a68d6-112">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a68d6-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a68d6-113">**Üstbilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a68d6-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a68d6-114">**Kütüphane:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a68d6-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a68d6-115">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a68d6-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
