---
description: ': Icordebugzincirine:: GetCaller Yöntemi hakkında daha fazla bilgi edinin'
title: ICorDebugChain::GetCaller Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetCaller
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetCaller
helpviewer_keywords:
- ICorDebugChain::GetCaller method [.NET Framework debugging]
- GetCaller method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: d0b8ab4b-d7d2-4fa0-945f-3d2b87e7e991
topic_type:
- apiref
ms.openlocfilehash: 5af2132b7fec9e70704db980b95221db6eb273f8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99695027"
---
# <a name="icordebugchaingetcaller-method"></a><span data-ttu-id="18c1f-103">ICorDebugChain::GetCaller Metodu</span><span class="sxs-lookup"><span data-stu-id="18c1f-103">ICorDebugChain::GetCaller Method</span></span>

<span data-ttu-id="18c1f-104">Bu zinciri çağıran zinciri alır.</span><span class="sxs-lookup"><span data-stu-id="18c1f-104">Gets the chain that called this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18c1f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="18c1f-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCaller (  
    [out] ICorDebugChain      **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="18c1f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="18c1f-106">Parameters</span></span>  

 `ppChain`  
 <span data-ttu-id="18c1f-107">dışı Çağıran zinciri temsil eden bir ıcordebugzincirleri nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="18c1f-107">[out] A pointer to the address of an ICorDebugChain object that represents the calling chain.</span></span>  
  
 <span data-ttu-id="18c1f-108">Bu zincir daha önce çağrılırsa (Bu zincir veya hata ayıklayıcı çağrı yığınını başlatdıysa olduğu gibi), `ppChain` null olur.</span><span class="sxs-lookup"><span data-stu-id="18c1f-108">If this chain was spontaneously called (as would be the case if this chain or the debugger initialized the call stack), `ppChain` will be null.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="18c1f-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="18c1f-109">Remarks</span></span>  

 <span data-ttu-id="18c1f-110">Çağrı iş parçacıkları arasında sıralandıysa, çağırma zinciri farklı bir iş parçacığında olabilir.</span><span class="sxs-lookup"><span data-stu-id="18c1f-110">The calling chain may be on a different thread, if the call was marshaled across threads.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="18c1f-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="18c1f-111">Requirements</span></span>  

 <span data-ttu-id="18c1f-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="18c1f-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="18c1f-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="18c1f-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="18c1f-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="18c1f-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="18c1f-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="18c1f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
