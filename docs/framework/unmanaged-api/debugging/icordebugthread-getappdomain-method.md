---
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
ms.openlocfilehash: 52efebf8a2786afaabe87b96b35a13c5fa1eb578
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379776"
---
# <a name="icordebugthreadgetappdomain-method"></a><span data-ttu-id="88d9c-102">ICorDebugThread::GetAppDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="88d9c-102">ICorDebugThread::GetAppDomain Method</span></span>
<span data-ttu-id="88d9c-103">Bu ICorDebugThread 'in Şu anda yürütüldüğü uygulama etki alanına bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="88d9c-103">Gets an interface pointer to the application domain in which this ICorDebugThread is currently executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88d9c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="88d9c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAppDomain (  
    [out] ICorDebugAppDomain  **ppAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="88d9c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="88d9c-105">Parameters</span></span>  
 `ppAppDomain`  
 <span data-ttu-id="88d9c-106">dışı Bu iş parçacığının Şu anda yürütüldüğü uygulama etki alanını temsil eden ICorDebugAppDomain nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="88d9c-106">[out] A pointer to an ICorDebugAppDomain object that represents the application domain in which this thread is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="88d9c-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="88d9c-107">Requirements</span></span>  
 <span data-ttu-id="88d9c-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="88d9c-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="88d9c-109">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="88d9c-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="88d9c-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="88d9c-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="88d9c-111">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="88d9c-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
