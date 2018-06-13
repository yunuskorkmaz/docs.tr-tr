---
title: ICorDebugThread::GetObject Metodu
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
ms.openlocfilehash: ad2dd4cded6800ce016d821f8e3ffe01dcb6264b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33418265"
---
# <a name="icordebugthreadgetobject-method"></a><span data-ttu-id="9b8e5-102">ICorDebugThread::GetObject Metodu</span><span class="sxs-lookup"><span data-stu-id="9b8e5-102">ICorDebugThread::GetObject Method</span></span>
<span data-ttu-id="9b8e5-103">Arabirim işaretçisi ortak dil çalışma zamanı (CLR) iş parçacığına alır.</span><span class="sxs-lookup"><span data-stu-id="9b8e5-103">Gets an interface pointer to the common language runtime (CLR) thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b8e5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9b8e5-104">Syntax</span></span>  
  
```  
HRESULT GetObject (  
    [out] ICorDebugValue   **ppObject  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9b8e5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9b8e5-105">Parameters</span></span>  
 `ppObject`  
 <span data-ttu-id="9b8e5-106">[out] CLR iş parçacığı temsil eden bir Icordebugvalue arabirimi nesnesi adresini gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9b8e5-106">[out] A pointer to the address of an ICorDebugValue interface object that represents the CLR thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b8e5-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9b8e5-107">Requirements</span></span>  
 <span data-ttu-id="9b8e5-108">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9b8e5-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b8e5-109">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9b8e5-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9b8e5-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9b8e5-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9b8e5-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b8e5-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b8e5-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9b8e5-112">See Also</span></span>  
 <xref:System.Threading.Thread>
