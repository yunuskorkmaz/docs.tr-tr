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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a9bf96371798b38bc392bc6bbd8f6fe8f97c7969
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61946319"
---
# <a name="icordebugthread2getvolatileosthreadid-method"></a><span data-ttu-id="04ead-102">ICorDebugThread2::GetVolatileOSThreadID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="04ead-102">ICorDebugThread2::GetVolatileOSThreadID Method</span></span>
<span data-ttu-id="04ead-103">Bu Icordebugthread2 için işletim sistemi iş parçacığı tanımlayıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="04ead-103">Gets the operating system thread identifier for this ICorDebugThread2.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04ead-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="04ead-104">Syntax</span></span>  
  
```  
HRESULT GetVolatileOSThreadID (  
    [out] DWORD    *pdwTid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="04ead-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="04ead-105">Parameters</span></span>  
 `pdwTid`  
 <span data-ttu-id="04ead-106">[out] Bu iş parçacığı için işletim sistemi iş parçacığı tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="04ead-106">[out] The operating system thread identifier for this thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04ead-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="04ead-107">Requirements</span></span>  
 <span data-ttu-id="04ead-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="04ead-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04ead-109">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="04ead-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="04ead-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="04ead-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="04ead-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04ead-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
