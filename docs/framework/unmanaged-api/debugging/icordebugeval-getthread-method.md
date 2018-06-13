---
title: ICorDebugEval::GetThread Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugEval.GetThread
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::GetThread
helpviewer_keywords:
- GetThread method, ICorDebugEval interface [.NET Framework debugging]
- ICorDebugEval::GetThread method [.NET Framework debugging]
ms.assetid: 57163b0d-c8a7-44af-9078-e7a895d29f9a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e64bc173717c3121d6c2b101f734ee325a0ced53
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33413767"
---
# <a name="icordebugevalgetthread-method"></a><span data-ttu-id="84eac-102">ICorDebugEval::GetThread Metodu</span><span class="sxs-lookup"><span data-stu-id="84eac-102">ICorDebugEval::GetThread Method</span></span>
<span data-ttu-id="84eac-103">Bu değerlendirme yürütüyor veya yürütecek iş parçacığı alır.</span><span class="sxs-lookup"><span data-stu-id="84eac-103">Gets the thread in which this evaluation is executing or will execute.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84eac-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="84eac-104">Syntax</span></span>  
  
```  
HRESULT GetThread (  
    [out] ICorDebugThread   **ppThread  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="84eac-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="84eac-105">Parameters</span></span>  
 `ppThread`  
 <span data-ttu-id="84eac-106">[out] Bir işaretçi adresine Icordebugthread nesnenin iş parçacığı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="84eac-106">[out] A pointer to the address of an ICorDebugThread object that represents the thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84eac-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="84eac-107">Requirements</span></span>  
 <span data-ttu-id="84eac-108">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="84eac-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84eac-109">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="84eac-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="84eac-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="84eac-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="84eac-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84eac-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
