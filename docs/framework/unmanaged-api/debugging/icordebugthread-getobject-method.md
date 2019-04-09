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
ms.openlocfilehash: 7fa90aff73d94baf2cbf7d01f41710cb2aa10213
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59178743"
---
# <a name="icordebugthreadgetobject-method"></a><span data-ttu-id="ca283-102">ICorDebugThread::GetObject Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ca283-102">ICorDebugThread::GetObject Method</span></span>
<span data-ttu-id="ca283-103">Ortak dil çalışma zamanı (CLR) iş parçacığına bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="ca283-103">Gets an interface pointer to the common language runtime (CLR) thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca283-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ca283-104">Syntax</span></span>  
  
```  
HRESULT GetObject (  
    [out] ICorDebugValue   **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ca283-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ca283-105">Parameters</span></span>  
 `ppObject`  
 <span data-ttu-id="ca283-106">[out] CLR iş parçacığı temsil eden bir Icordebugvalue arabirimi nesnesinin adresine yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ca283-106">[out] A pointer to the address of an ICorDebugValue interface object that represents the CLR thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca283-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ca283-107">Requirements</span></span>  
 <span data-ttu-id="ca283-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ca283-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca283-109">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ca283-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ca283-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ca283-110">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="ca283-111">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="ca283-111">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ca283-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ca283-112">See also</span></span>

- <xref:System.Threading.Thread>
