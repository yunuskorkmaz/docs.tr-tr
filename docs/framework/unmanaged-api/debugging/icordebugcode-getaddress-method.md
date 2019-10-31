---
title: ICorDebugCode::GetAddress Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetAddress
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetAddress
helpviewer_keywords:
- GetAddress method, ICorDebugCode interface [.NET Framework debugging]
- ICorDebugCode::GetAddress method [.NET Framework debugging]
ms.assetid: cc507cb0-df2e-49c2-b32e-0c3271a8df9a
topic_type:
- apiref
ms.openlocfilehash: df73663f714b0c1c3d3ae5dfb53e8e84196a8f37
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125676"
---
# <a name="icordebugcodegetaddress-method"></a><span data-ttu-id="79c71-102">ICorDebugCode::GetAddress Yöntemi</span><span class="sxs-lookup"><span data-stu-id="79c71-102">ICorDebugCode::GetAddress Method</span></span>
<span data-ttu-id="79c71-103">Bu "ICorDebugCode" arabiriminin gösterdiği kod kesiminin göreli sanal adresini (RVA) alır.</span><span class="sxs-lookup"><span data-stu-id="79c71-103">Gets the relative virtual address (RVA) of the code segment that this "ICorDebugCode" interface represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79c71-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="79c71-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAddress (  
    [out] CORDB_ADDRESS *pStart  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="79c71-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="79c71-105">Parameters</span></span>  
 `pStart`  
 <span data-ttu-id="79c71-106">dışı Kod parçasının RVA 'Sı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="79c71-106">[out] A pointer to the RVA of the code segment.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79c71-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="79c71-107">Requirements</span></span>  
 <span data-ttu-id="79c71-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="79c71-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79c71-109">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="79c71-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="79c71-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="79c71-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="79c71-111">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="79c71-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
