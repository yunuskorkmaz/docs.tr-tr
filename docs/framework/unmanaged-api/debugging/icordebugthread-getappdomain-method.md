---
title: ICorDebugThread::GetAppDomain Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread.GetAppDomain
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread::GetAppDomain
helpviewer_keywords:
- GetAppDomain method, ICorDebugThread interface [.NET Framework debugging]
- ICorDebugThread::GetAppDomain method [.NET Framework debugging]
ms.assetid: 415b3d34-8b35-4b60-a318-140646cc83f8
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c235bc0294b967e26766a095b85c5acf0f27cff9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugthreadgetappdomain-method"></a><span data-ttu-id="a2df0-102">ICorDebugThread::GetAppDomain Metodu</span><span class="sxs-lookup"><span data-stu-id="a2df0-102">ICorDebugThread::GetAppDomain Method</span></span>
<span data-ttu-id="a2df0-103">Bu Icordebugthread şu anda yürütülmekte uygulama etki alanı için bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="a2df0-103">Gets an interface pointer to the application domain in which this ICorDebugThread is currently executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2df0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a2df0-104">Syntax</span></span>  
  
```  
HRESULT GetAppDomain (  
    [out] ICorDebugAppDomain  **ppAppDomain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a2df0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a2df0-105">Parameters</span></span>  
 `ppAppDomain`  
 <span data-ttu-id="a2df0-106">[out] Bu iş parçacığı şu anda yürütülmekte uygulama etki alanını temsil eden bir Icordebugappdomain nesnesi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a2df0-106">[out] A pointer to an ICorDebugAppDomain object that represents the application domain in which this thread is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2df0-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a2df0-107">Requirements</span></span>  
 <span data-ttu-id="a2df0-108">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a2df0-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2df0-109">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a2df0-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a2df0-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a2df0-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a2df0-111">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2df0-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
