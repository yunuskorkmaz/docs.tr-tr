---
description: 'Şu konuda daha fazla bilgi edinin: ICorDebugThread2:: GetVolatileOSThreadID yöntemi'
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
ms.openlocfilehash: 2c198577195c9b1e4a3a74fae686e405b22120eb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99658600"
---
# <a name="icordebugthread2getvolatileosthreadid-method"></a><span data-ttu-id="7e6f5-103">ICorDebugThread2::GetVolatileOSThreadID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7e6f5-103">ICorDebugThread2::GetVolatileOSThreadID Method</span></span>

<span data-ttu-id="7e6f5-104">Bu ICorDebugThread2 için işletim sistemi iş parçacığı tanımlayıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="7e6f5-104">Gets the operating system thread identifier for this ICorDebugThread2.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e6f5-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7e6f5-105">Syntax</span></span>  
  
```cpp  
HRESULT GetVolatileOSThreadID (  
    [out] DWORD    *pdwTid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7e6f5-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7e6f5-106">Parameters</span></span>  

 `pdwTid`  
 <span data-ttu-id="7e6f5-107">dışı Bu iş parçacığının işletim sistemi iş parçacığı tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="7e6f5-107">[out] The operating system thread identifier for this thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e6f5-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7e6f5-108">Requirements</span></span>  

 <span data-ttu-id="7e6f5-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e6f5-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e6f5-110">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7e6f5-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7e6f5-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="7e6f5-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7e6f5-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e6f5-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
