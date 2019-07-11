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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ad87b6552df25926b5b4184b7884c1d444c4f1be
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67769076"
---
# <a name="icordebugthreadgetprocess-method"></a><span data-ttu-id="f17db-102">ICorDebugThread::GetProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f17db-102">ICorDebugThread::GetProcess Method</span></span>
<span data-ttu-id="f17db-103">Bir parçası olan bu Icordebugthread forms işlemi için bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="f17db-103">Gets an interface pointer to the process of which this ICorDebugThread forms a part.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f17db-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f17db-104">Syntax</span></span>  
  
```cpp  
HRESULT GetProcess (  
    [out] ICorDebugProcess   **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f17db-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f17db-105">Parameters</span></span>  
 `ppProcess`  
 <span data-ttu-id="f17db-106">[out] İşlemi temsil eden bir Icordebugprocess arabirimi nesnesinin adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f17db-106">[out] A pointer to the address of an ICorDebugProcess interface object that represents the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f17db-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f17db-107">Requirements</span></span>  
 <span data-ttu-id="f17db-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f17db-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f17db-109">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f17db-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f17db-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f17db-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f17db-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f17db-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
