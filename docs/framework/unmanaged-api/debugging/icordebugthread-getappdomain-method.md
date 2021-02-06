---
description: ': ICorDebugThread:: GetAppDomain Yöntemi hakkında daha fazla bilgi edinin'
title: ICorDebugThread::GetAppDomain Yöntemi
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
ms.openlocfilehash: 416ab80fa08786fb5e95776b164723317fa59ca6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99659211"
---
# <a name="icordebugthreadgetappdomain-method"></a><span data-ttu-id="d9264-103">ICorDebugThread::GetAppDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d9264-103">ICorDebugThread::GetAppDomain Method</span></span>

<span data-ttu-id="d9264-104">Bu ICorDebugThread 'in Şu anda yürütüldüğü uygulama etki alanına bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="d9264-104">Gets an interface pointer to the application domain in which this ICorDebugThread is currently executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9264-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d9264-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAppDomain (  
    [out] ICorDebugAppDomain  **ppAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d9264-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d9264-106">Parameters</span></span>  

 `ppAppDomain`  
 <span data-ttu-id="d9264-107">dışı Bu iş parçacığının Şu anda yürütüldüğü uygulama etki alanını temsil eden ICorDebugAppDomain nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d9264-107">[out] A pointer to an ICorDebugAppDomain object that represents the application domain in which this thread is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9264-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d9264-108">Requirements</span></span>  

 <span data-ttu-id="d9264-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d9264-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9264-110">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d9264-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d9264-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d9264-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d9264-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9264-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
