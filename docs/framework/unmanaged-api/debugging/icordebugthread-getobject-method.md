---
title: ICorDebugThread::GetObject Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetObject
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetObject
helpviewer_keywords:
- GetObject method, ICorDebugThread interface [.NET Framework debugging]
- ICorDebugThread::GetObject method [.NET Framework debugging]
ms.assetid: 1590febe-96c2-4046-97db-d81d81d67e01
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3695f150797e6a59a2fb1d58c99f233a35d687ce
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67771836"
---
# <a name="icordebugthreadgetobject-method"></a><span data-ttu-id="15128-102">ICorDebugThread::GetObject Yöntemi</span><span class="sxs-lookup"><span data-stu-id="15128-102">ICorDebugThread::GetObject Method</span></span>
<span data-ttu-id="15128-103">Ortak dil çalışma zamanı (CLR) iş parçacığına bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="15128-103">Gets an interface pointer to the common language runtime (CLR) thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15128-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="15128-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObject (  
    [out] ICorDebugValue   **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="15128-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="15128-105">Parameters</span></span>  
 `ppObject`  
 <span data-ttu-id="15128-106">[out] CLR iş parçacığı temsil eden bir Icordebugvalue arabirimi nesnesinin adresine yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="15128-106">[out] A pointer to the address of an ICorDebugValue interface object that represents the CLR thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="15128-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="15128-107">Requirements</span></span>  
 <span data-ttu-id="15128-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="15128-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15128-109">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="15128-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="15128-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="15128-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="15128-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="15128-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15128-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="15128-112">See also</span></span>

- <xref:System.Threading.Thread>
