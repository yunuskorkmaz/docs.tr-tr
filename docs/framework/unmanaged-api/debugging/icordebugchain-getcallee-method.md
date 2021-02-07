---
description: 'Şu konuda daha fazla bilgi edinin: ıcordebugzincirine:: Getçağrılan yöntemi'
title: ICorDebugChain::GetCallee Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetCallee
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetCallee method
helpviewer_keywords:
- ICorDebugChain::GetCallee method [.NET Framework debugging]
- GetCallee method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 19560c79-abdc-4bdf-a5fe-eb362a59edc0
topic_type:
- apiref
ms.openlocfilehash: 4787893c86804c648dae14bf2e6f7425808104b7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99661434"
---
# <a name="icordebugchaingetcallee-method"></a><span data-ttu-id="b3d19-103">ICorDebugChain::GetCallee Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b3d19-103">ICorDebugChain::GetCallee Method</span></span>

<span data-ttu-id="b3d19-104">Bu zincir tarafından çağrılan zinciri alır.</span><span class="sxs-lookup"><span data-stu-id="b3d19-104">Gets the chain that was called by this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3d19-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b3d19-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCallee (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b3d19-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b3d19-106">Parameters</span></span>  

 `ppChain`  
 <span data-ttu-id="b3d19-107">dışı Çağrılan zinciri temsil eden bir ıcordebugzincirleri nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b3d19-107">[out] A pointer to the address of an ICorDebugChain object that represents the called chain.</span></span> <span data-ttu-id="b3d19-108">Bu zincir Şu anda yürütüliyorsa (yani, bu zincir, çağrılan bir zincirin dönmesi beklenmez), `ppChain` null olur.</span><span class="sxs-lookup"><span data-stu-id="b3d19-108">If this chain is currently executing (that is, if this chain is not waiting for a called chain to return), `ppChain` will be null.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b3d19-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b3d19-109">Remarks</span></span>  

 <span data-ttu-id="b3d19-110">Bu zincir, yürütmeyi devam etmeden önce çağrılan zincirin döndürülmesini bekler.</span><span class="sxs-lookup"><span data-stu-id="b3d19-110">This chain will wait for the called chain to return before it resumes execution.</span></span> <span data-ttu-id="b3d19-111">Çağrılan zincir, çapraz iş parçacığı sıralanmış çağrılar söz konusu olduğunda başka bir iş parçacığında olabilir.</span><span class="sxs-lookup"><span data-stu-id="b3d19-111">The called chain may be on another thread in the case of cross-thread marshaled calls.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3d19-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b3d19-112">Requirements</span></span>  

 <span data-ttu-id="b3d19-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b3d19-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3d19-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b3d19-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b3d19-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b3d19-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b3d19-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3d19-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
