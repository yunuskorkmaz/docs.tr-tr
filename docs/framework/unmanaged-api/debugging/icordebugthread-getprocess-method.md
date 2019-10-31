---
title: ICorDebugThread::GetProcess Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetProcess
helpviewer_keywords:
- ICorDebugThread::GetProcess method [.NET Framework debugging]
- GetProcess method, ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 163816e7-0739-4566-b3df-cd256be8b8a4
topic_type:
- apiref
ms.openlocfilehash: 8928e22b70af0360660c30289ee999a3e4c5e99e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133469"
---
# <a name="icordebugthreadgetprocess-method"></a><span data-ttu-id="5a7fe-102">ICorDebugThread::GetProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5a7fe-102">ICorDebugThread::GetProcess Method</span></span>
<span data-ttu-id="5a7fe-103">Bu ICorDebugThread 'in bir parçasını oluşturan işlem için bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="5a7fe-103">Gets an interface pointer to the process of which this ICorDebugThread forms a part.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a7fe-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5a7fe-104">Syntax</span></span>  
  
```cpp  
HRESULT GetProcess (  
    [out] ICorDebugProcess   **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5a7fe-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5a7fe-105">Parameters</span></span>  
 `ppProcess`  
 <span data-ttu-id="5a7fe-106">dışı İşlemi temsil eden ICorDebugProcess arabirimi nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5a7fe-106">[out] A pointer to the address of an ICorDebugProcess interface object that represents the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a7fe-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5a7fe-107">Requirements</span></span>  
 <span data-ttu-id="5a7fe-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5a7fe-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a7fe-109">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="5a7fe-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5a7fe-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="5a7fe-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5a7fe-111">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5a7fe-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
