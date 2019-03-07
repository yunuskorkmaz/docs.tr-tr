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
ms.openlocfilehash: 4cd5a7696e7630b21c8bdfa7e4d2f902d6f36995
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57490261"
---
# <a name="icordebugthreadgetobject-method"></a><span data-ttu-id="68498-102">ICorDebugThread::GetObject Yöntemi</span><span class="sxs-lookup"><span data-stu-id="68498-102">ICorDebugThread::GetObject Method</span></span>
<span data-ttu-id="68498-103">Ortak dil çalışma zamanı (CLR) iş parçacığına bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="68498-103">Gets an interface pointer to the common language runtime (CLR) thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68498-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="68498-104">Syntax</span></span>  
  
```  
HRESULT GetObject (  
    [out] ICorDebugValue   **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="68498-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="68498-105">Parameters</span></span>  
 `ppObject`  
 <span data-ttu-id="68498-106">[out] CLR iş parçacığı temsil eden bir Icordebugvalue arabirimi nesnesinin adresine yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="68498-106">[out] A pointer to the address of an ICorDebugValue interface object that represents the CLR thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68498-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="68498-107">Requirements</span></span>  
 <span data-ttu-id="68498-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="68498-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68498-109">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="68498-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="68498-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="68498-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="68498-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68498-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68498-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="68498-112">See also</span></span>
- <xref:System.Threading.Thread>
