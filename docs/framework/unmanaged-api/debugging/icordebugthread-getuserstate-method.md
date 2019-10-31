---
title: ICorDebugThread::GetUserState Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetUserState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetUserState
helpviewer_keywords:
- GetUserState method, ICorDebugThread interface [.NET Framework debugging]
- ICorDebugThread::GetUserState method [.NET Framework debugging]
ms.assetid: ae0cfd73-8ead-4d36-9310-dccaac9db0bd
topic_type:
- apiref
ms.openlocfilehash: f3511ff5ee9b9221037c64a5e17d61f6bf52e5f3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133409"
---
# <a name="icordebugthreadgetuserstate-method"></a><span data-ttu-id="cc6e4-102">ICorDebugThread::GetUserState Metodu</span><span class="sxs-lookup"><span data-stu-id="cc6e4-102">ICorDebugThread::GetUserState Method</span></span>
<span data-ttu-id="cc6e4-103">Bu ICorDebugThread 'in geçerli kullanıcı durumunu alır.</span><span class="sxs-lookup"><span data-stu-id="cc6e4-103">Gets the current user state of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc6e4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cc6e4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetUserState (  
    [out] CorDebugUserState   *pState  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cc6e4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cc6e4-105">Parameters</span></span>  
 `pState`  
 <span data-ttu-id="cc6e4-106">dışı Bu iş parçacığının geçerli kullanıcı durumunu tanımlayan, CorDebugUserState numaralandırma değerlerinin bit düzeyinde birleşimine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="cc6e4-106">[out] A pointer to a bitwise combination of CorDebugUserState enumeration values that describe the current user state of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cc6e4-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cc6e4-107">Remarks</span></span>  
 <span data-ttu-id="cc6e4-108">İş parçacığının kullanıcı durumu, hata ayıklamakta olan program tarafından incelenmekte olan iş parçacığının durumudur.</span><span class="sxs-lookup"><span data-stu-id="cc6e4-108">The user state of the thread is the state of the thread when it is examined by the program that is being debugged.</span></span> <span data-ttu-id="cc6e4-109">Bir iş parçacığında birden fazla durum bitleri ayarlanmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="cc6e4-109">A thread may have multiple state bits set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc6e4-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cc6e4-110">Requirements</span></span>  
 <span data-ttu-id="cc6e4-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cc6e4-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc6e4-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="cc6e4-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cc6e4-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="cc6e4-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cc6e4-114">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc6e4-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
