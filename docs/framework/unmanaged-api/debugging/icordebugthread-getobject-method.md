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
ms.openlocfilehash: 2c13ead228296525b57245be8b3bdbcdf38ae173
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728010"
---
# <a name="icordebugthreadgetobject-method"></a><span data-ttu-id="51016-102">ICorDebugThread::GetObject Yöntemi</span><span class="sxs-lookup"><span data-stu-id="51016-102">ICorDebugThread::GetObject Method</span></span>

<span data-ttu-id="51016-103">Ortak dil çalışma zamanı (CLR) iş parçacığına bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="51016-103">Gets an interface pointer to the common language runtime (CLR) thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51016-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="51016-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObject (  
    [out] ICorDebugValue   **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="51016-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="51016-105">Parameters</span></span>  

 `ppObject`  
 <span data-ttu-id="51016-106">dışı CLR iş parçacığını temsil eden ICorDebugValue arabirimi nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="51016-106">[out] A pointer to the address of an ICorDebugValue interface object that represents the CLR thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51016-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="51016-107">Requirements</span></span>  

 <span data-ttu-id="51016-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="51016-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51016-109">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="51016-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="51016-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="51016-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="51016-111">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="51016-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51016-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="51016-112">See also</span></span>

- <xref:System.Threading.Thread>
