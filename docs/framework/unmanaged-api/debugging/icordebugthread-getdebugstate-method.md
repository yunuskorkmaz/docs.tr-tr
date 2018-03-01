---
title: ICorDebugThread::GetDebugState Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugThread.GetDebugState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetDebugState
helpviewer_keywords:
- GetDebugState method [.NET Framework debugging]
- ICorDebugThread::GetDebugState method [.NET Framework debugging]
ms.assetid: 9be27b0c-1d99-4722-b0d4-40cf6753ce5c
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7b9d310cdc088e4b2fc9c6850accc3576a6147ae
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugthreadgetdebugstate-method"></a><span data-ttu-id="7f96d-102">ICorDebugThread::GetDebugState Metodu</span><span class="sxs-lookup"><span data-stu-id="7f96d-102">ICorDebugThread::GetDebugState Method</span></span>
<span data-ttu-id="7f96d-103">Bu Icordebugthread nesne geçerli hata ayıklama durumunu alır.</span><span class="sxs-lookup"><span data-stu-id="7f96d-103">Gets the current debug state of this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f96d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7f96d-104">Syntax</span></span>  
  
```  
HRESULT GetDebugState (  
    [out] CorDebugThreadState   *pState  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7f96d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7f96d-105">Parameters</span></span>  
 `pState`  
 <span data-ttu-id="7f96d-106">[out] Bu iş parçacığı geçerli hata ayıklama durumunu açıklayan CorDebugThreadState numaralandırma değerlerinin Bitsel birleşimine gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7f96d-106">[out] A pointer to a bitwise combination of CorDebugThreadState enumeration values that describes the current debug state of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7f96d-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7f96d-107">Remarks</span></span>  
 <span data-ttu-id="7f96d-108">İşlem şu anda durursa, `pState` işlemi devam için bu iş parçacığının gerçek geçerli durumu olsaydı bu iş parçacığı için var olan hata ayıklama durumuna temsil eder.</span><span class="sxs-lookup"><span data-stu-id="7f96d-108">If the process is currently stopped, `pState` represents the debug state that would exist for this thread if the process were to be continued, not the actual current state of this thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f96d-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7f96d-109">Requirements</span></span>  
 <span data-ttu-id="7f96d-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7f96d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f96d-111">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7f96d-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7f96d-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7f96d-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7f96d-113">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f96d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
