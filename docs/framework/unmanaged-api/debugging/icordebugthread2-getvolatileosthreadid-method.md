---
title: ICorDebugThread2::GetVolatileOSThreadID Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugThread2.GetVolatileOSThreadID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2::GetVolatileOSThreadID
helpviewer_keywords:
- GetVolatileOSThreadID method [.NET Framework debugging]
- ICorDebugThread2::GetVolatileOSThreadID method [.NET Framework debugging]
ms.assetid: f0922545-c2cf-40c8-9ef6-ca033563e682
topic_type:
- apiref
ms.openlocfilehash: 2e49dd95cf5d78c0a0f4fa075126eca19dea2693
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138711"
---
# <a name="icordebugthread2getvolatileosthreadid-method"></a><span data-ttu-id="f9fed-102">ICorDebugThread2::GetVolatileOSThreadID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f9fed-102">ICorDebugThread2::GetVolatileOSThreadID Method</span></span>
<span data-ttu-id="f9fed-103">Bu ICorDebugThread2 için işletim sistemi iş parçacığı tanımlayıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="f9fed-103">Gets the operating system thread identifier for this ICorDebugThread2.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9fed-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f9fed-104">Syntax</span></span>  
  
```cpp  
HRESULT GetVolatileOSThreadID (  
    [out] DWORD    *pdwTid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f9fed-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f9fed-105">Parameters</span></span>  
 `pdwTid`  
 <span data-ttu-id="f9fed-106">dışı Bu iş parçacığının işletim sistemi iş parçacığı tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="f9fed-106">[out] The operating system thread identifier for this thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9fed-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f9fed-107">Requirements</span></span>  
 <span data-ttu-id="f9fed-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f9fed-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9fed-109">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f9fed-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f9fed-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="f9fed-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f9fed-111">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f9fed-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
