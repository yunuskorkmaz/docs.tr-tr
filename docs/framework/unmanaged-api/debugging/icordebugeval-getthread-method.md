---
description: 'Şu konuda daha fazla bilgi edinin: ıcorıbgeval:: GetThread Yöntemi'
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
ms.openlocfilehash: 3e7120f618abce31b9940a886fd6b2b2f8639d2d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99694155"
---
# <a name="icordebugevalgetthread-method"></a><span data-ttu-id="de306-103">ICorDebugEval::GetThread Metodu</span><span class="sxs-lookup"><span data-stu-id="de306-103">ICorDebugEval::GetThread Method</span></span>

<span data-ttu-id="de306-104">Bu değerlendirmenin yürütüldüğü veya yürütüleceği iş parçacığını alır.</span><span class="sxs-lookup"><span data-stu-id="de306-104">Gets the thread in which this evaluation is executing or will execute.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de306-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="de306-105">Syntax</span></span>  
  
```cpp  
HRESULT GetThread (  
    [out] ICorDebugThread   **ppThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="de306-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="de306-106">Parameters</span></span>  

 `ppThread`  
 <span data-ttu-id="de306-107">dışı İş parçacığını temsil eden ICorDebugThread nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="de306-107">[out] A pointer to the address of an ICorDebugThread object that represents the thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de306-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="de306-108">Requirements</span></span>  

 <span data-ttu-id="de306-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="de306-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="de306-110">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="de306-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="de306-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="de306-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="de306-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="de306-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
