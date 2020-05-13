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
ms.openlocfilehash: 624469ca1ae4c96b4143f8768b4c5ff9c2601a2f
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378879"
---
# <a name="icordebugthreadgetobject-method"></a><span data-ttu-id="e6f71-102">ICorDebugThread::GetObject Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e6f71-102">ICorDebugThread::GetObject Method</span></span>
<span data-ttu-id="e6f71-103">Ortak dil çalışma zamanı (CLR) iş parçacığına bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="e6f71-103">Gets an interface pointer to the common language runtime (CLR) thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6f71-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e6f71-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObject (  
    [out] ICorDebugValue   **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e6f71-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e6f71-105">Parameters</span></span>  
 `ppObject`  
 <span data-ttu-id="e6f71-106">dışı CLR iş parçacığını temsil eden ICorDebugValue arabirimi nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e6f71-106">[out] A pointer to the address of an ICorDebugValue interface object that represents the CLR thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e6f71-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e6f71-107">Requirements</span></span>  
 <span data-ttu-id="e6f71-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e6f71-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6f71-109">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e6f71-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e6f71-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e6f71-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e6f71-111">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e6f71-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6f71-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e6f71-112">See also</span></span>

- <xref:System.Threading.Thread>
