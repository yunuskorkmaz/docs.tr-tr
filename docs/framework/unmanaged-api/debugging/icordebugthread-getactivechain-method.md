---
title: ICorDebugThread::GetActiveChain Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetActiveChain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetActiveChain
helpviewer_keywords:
- ICorDebugThread::GetActiveChain method [.NET Framework debugging]
- GetActiveChain method [.NET Framework debugging]
ms.assetid: f50de1f7-40ef-4949-b542-1d9a61f7bfef
topic_type:
- apiref
ms.openlocfilehash: e6b1d78b2bd95ea27f4b19a045cd2680342e8a80
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728101"
---
# <a name="icordebugthreadgetactivechain-method"></a><span data-ttu-id="95956-102">ICorDebugThread::GetActiveChain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="95956-102">ICorDebugThread::GetActiveChain Method</span></span>

<span data-ttu-id="95956-103">Bu ICorDebugThread nesnesindeki etkin (en son) yığın zincirine yönelik bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="95956-103">Gets an interface pointer to the active (most recent) stack chain on this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95956-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="95956-104">Syntax</span></span>  
  
```cpp  
HRESULT GetActiveChain (  
    [out] ICorDebugChain **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="95956-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="95956-105">Parameters</span></span>  

 `ppChain`  
 <span data-ttu-id="95956-106">dışı Yığın zincirini temsil eden bir ıcordebugzincirleri nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="95956-106">[out] A pointer to the address of an ICorDebugChain object that represents the stack chain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="95956-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="95956-107">Remarks</span></span>  

 <span data-ttu-id="95956-108">`ppChain`Şu anda etkin bir yığın zinciri yoksa parametre null.</span><span class="sxs-lookup"><span data-stu-id="95956-108">The `ppChain` parameter is null if no stack chain is currently active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="95956-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="95956-109">Requirements</span></span>  

 <span data-ttu-id="95956-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="95956-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95956-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="95956-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="95956-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="95956-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="95956-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95956-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
