---
description: ': ICorDebugThread:: GetProcess metodu hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: dac5da30b343ebd17c1b1ebdd6d4cfa38b78f0bd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99658960"
---
# <a name="icordebugthreadgetprocess-method"></a><span data-ttu-id="ce6d2-103">ICorDebugThread::GetProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ce6d2-103">ICorDebugThread::GetProcess Method</span></span>

<span data-ttu-id="ce6d2-104">Bu ICorDebugThread 'in bir parçasını oluşturan işlem için bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="ce6d2-104">Gets an interface pointer to the process of which this ICorDebugThread forms a part.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce6d2-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ce6d2-105">Syntax</span></span>  
  
```cpp  
HRESULT GetProcess (  
    [out] ICorDebugProcess   **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ce6d2-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ce6d2-106">Parameters</span></span>  

 `ppProcess`  
 <span data-ttu-id="ce6d2-107">dışı İşlemi temsil eden ICorDebugProcess arabirimi nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ce6d2-107">[out] A pointer to the address of an ICorDebugProcess interface object that represents the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce6d2-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ce6d2-108">Requirements</span></span>  

 <span data-ttu-id="ce6d2-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ce6d2-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce6d2-110">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ce6d2-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ce6d2-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ce6d2-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ce6d2-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce6d2-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
