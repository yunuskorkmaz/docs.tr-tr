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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e4deaa3ab4b14fbd32d45841966cfac9e33b9f31
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57487856"
---
# <a name="icordebugthreadgetuserstate-method"></a><span data-ttu-id="53f81-102">ICorDebugThread::GetUserState Metodu</span><span class="sxs-lookup"><span data-stu-id="53f81-102">ICorDebugThread::GetUserState Method</span></span>
<span data-ttu-id="53f81-103">Bu Icordebugthread geçerli kullanıcı durumunu alır.</span><span class="sxs-lookup"><span data-stu-id="53f81-103">Gets the current user state of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53f81-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="53f81-104">Syntax</span></span>  
  
```  
HRESULT GetUserState (  
    [out] CorDebugUserState   *pState  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="53f81-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="53f81-105">Parameters</span></span>  
 `pState`  
 <span data-ttu-id="53f81-106">[out] Bu iş parçacığının geçerli kullanıcı durumunu açıklayan CorDebugUserState numaralandırma değerlerinin Bitsel bir birleşimi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="53f81-106">[out] A pointer to a bitwise combination of CorDebugUserState enumeration values that describe the current user state of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="53f81-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="53f81-107">Remarks</span></span>  
 <span data-ttu-id="53f81-108">Ayıklanmakta olan program tarafından incelenir, kullanıcı durumu iş parçacığının iş parçacığı durumudur.</span><span class="sxs-lookup"><span data-stu-id="53f81-108">The user state of the thread is the state of the thread when it is examined by the program that is being debugged.</span></span> <span data-ttu-id="53f81-109">Bir iş parçacığı, birden çok durum bitler olabilir.</span><span class="sxs-lookup"><span data-stu-id="53f81-109">A thread may have multiple state bits set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="53f81-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="53f81-110">Requirements</span></span>  
 <span data-ttu-id="53f81-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="53f81-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53f81-112">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="53f81-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="53f81-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="53f81-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="53f81-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53f81-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
