---
title: ICorDebugThread::GetAppDomain Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetAppDomain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetAppDomain
helpviewer_keywords:
- GetAppDomain method, ICorDebugThread interface [.NET Framework debugging]
- ICorDebugThread::GetAppDomain method [.NET Framework debugging]
ms.assetid: 415b3d34-8b35-4b60-a318-140646cc83f8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 51878f0334afe52608b60ca540e49c86fded148e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33418052"
---
# <a name="icordebugthreadgetappdomain-method"></a><span data-ttu-id="be4b7-102">ICorDebugThread::GetAppDomain Metodu</span><span class="sxs-lookup"><span data-stu-id="be4b7-102">ICorDebugThread::GetAppDomain Method</span></span>
<span data-ttu-id="be4b7-103">Bu Icordebugthread şu anda yürütülmekte uygulama etki alanı için bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="be4b7-103">Gets an interface pointer to the application domain in which this ICorDebugThread is currently executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be4b7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="be4b7-104">Syntax</span></span>  
  
```  
HRESULT GetAppDomain (  
    [out] ICorDebugAppDomain  **ppAppDomain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="be4b7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="be4b7-105">Parameters</span></span>  
 `ppAppDomain`  
 <span data-ttu-id="be4b7-106">[out] Bu iş parçacığı şu anda yürütülmekte uygulama etki alanını temsil eden bir Icordebugappdomain nesnesi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="be4b7-106">[out] A pointer to an ICorDebugAppDomain object that represents the application domain in which this thread is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be4b7-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="be4b7-107">Requirements</span></span>  
 <span data-ttu-id="be4b7-108">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="be4b7-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be4b7-109">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="be4b7-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="be4b7-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="be4b7-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="be4b7-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be4b7-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
