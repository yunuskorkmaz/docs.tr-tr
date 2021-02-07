---
description: 'Şu konuda daha fazla bilgi edinin: ıcordebugzincirine:: GetNext Yöntemi'
title: ICorDebugChain::GetNext Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetNext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetNext
helpviewer_keywords:
- GetNext method [.NET Framework debugging]
- ICorDebugChain::GetNext method [.NET Framework debugging]
ms.assetid: 8d9744a5-e08b-4ab2-9855-5c22711cc1e6
topic_type:
- apiref
ms.openlocfilehash: ced7032feffa4c14c07341242b854c08b8c897a5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99661330"
---
# <a name="icordebugchaingetnext-method"></a><span data-ttu-id="876fa-103">ICorDebugChain::GetNext Metodu</span><span class="sxs-lookup"><span data-stu-id="876fa-103">ICorDebugChain::GetNext Method</span></span>

<span data-ttu-id="876fa-104">İş parçacığı için bir sonraki çerçeve zincirini alır.</span><span class="sxs-lookup"><span data-stu-id="876fa-104">Gets the next chain of frames for the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="876fa-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="876fa-105">Syntax</span></span>  
  
```cpp  
HRESULT GetNext (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="876fa-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="876fa-106">Parameters</span></span>  

 `ppChain`  
 <span data-ttu-id="876fa-107">dışı İş parçacığı için bir sonraki çerçeve zincirini temsil eden ıcordebugzincirine ait adrese yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="876fa-107">[out] A pointer to the address of an ICorDebugChain object that represents the next chain of frames for the thread.</span></span> <span data-ttu-id="876fa-108">Bu zincir son zincirdir, `ppChain` null olur.</span><span class="sxs-lookup"><span data-stu-id="876fa-108">If this chain is the last chain, `ppChain` is null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="876fa-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="876fa-109">Requirements</span></span>  

 <span data-ttu-id="876fa-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="876fa-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="876fa-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="876fa-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="876fa-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="876fa-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="876fa-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="876fa-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
