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
ms.openlocfilehash: 5cb95fb7cf70dbf7616e9bc59ebf44de090de883
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133440"
---
# <a name="icordebugthreadgetobject-method"></a><span data-ttu-id="175cc-102">ICorDebugThread::GetObject Yöntemi</span><span class="sxs-lookup"><span data-stu-id="175cc-102">ICorDebugThread::GetObject Method</span></span>
<span data-ttu-id="175cc-103">Ortak dil çalışma zamanı (CLR) iş parçacığına bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="175cc-103">Gets an interface pointer to the common language runtime (CLR) thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="175cc-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="175cc-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObject (  
    [out] ICorDebugValue   **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="175cc-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="175cc-105">Parameters</span></span>  
 `ppObject`  
 <span data-ttu-id="175cc-106">dışı CLR iş parçacığını temsil eden ICorDebugValue arabirimi nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="175cc-106">[out] A pointer to the address of an ICorDebugValue interface object that represents the CLR thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="175cc-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="175cc-107">Requirements</span></span>  
 <span data-ttu-id="175cc-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="175cc-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="175cc-109">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="175cc-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="175cc-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="175cc-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="175cc-111">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="175cc-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="175cc-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="175cc-112">See also</span></span>

- <xref:System.Threading.Thread>
