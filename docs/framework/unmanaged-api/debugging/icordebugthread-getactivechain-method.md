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
ms.openlocfilehash: 70e79378ad8eb2599199a1f7bc57cf530c9b4dd3
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379690"
---
# <a name="icordebugthreadgetactivechain-method"></a><span data-ttu-id="49d30-102">ICorDebugThread::GetActiveChain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="49d30-102">ICorDebugThread::GetActiveChain Method</span></span>
<span data-ttu-id="49d30-103">Bu ICorDebugThread nesnesindeki etkin (en son) yığın zincirine yönelik bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="49d30-103">Gets an interface pointer to the active (most recent) stack chain on this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49d30-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="49d30-104">Syntax</span></span>  
  
```cpp  
HRESULT GetActiveChain (  
    [out] ICorDebugChain **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="49d30-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="49d30-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="49d30-106">dışı Yığın zincirini temsil eden bir ıcordebugzincirleri nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="49d30-106">[out] A pointer to the address of an ICorDebugChain object that represents the stack chain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="49d30-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="49d30-107">Remarks</span></span>  
 <span data-ttu-id="49d30-108">`ppChain`Şu anda etkin bir yığın zinciri yoksa parametre null.</span><span class="sxs-lookup"><span data-stu-id="49d30-108">The `ppChain` parameter is null if no stack chain is currently active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49d30-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="49d30-109">Requirements</span></span>  
 <span data-ttu-id="49d30-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="49d30-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49d30-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="49d30-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="49d30-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="49d30-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="49d30-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49d30-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
