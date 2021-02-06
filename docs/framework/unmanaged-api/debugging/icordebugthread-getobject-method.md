---
description: ': ICorDebugThread:: GetObject yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: db5760be0ef4230b2dccec9d1836ea0eee56f231
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99658964"
---
# <a name="icordebugthreadgetobject-method"></a><span data-ttu-id="97c0a-103">ICorDebugThread::GetObject Yöntemi</span><span class="sxs-lookup"><span data-stu-id="97c0a-103">ICorDebugThread::GetObject Method</span></span>

<span data-ttu-id="97c0a-104">Ortak dil çalışma zamanı (CLR) iş parçacığına bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="97c0a-104">Gets an interface pointer to the common language runtime (CLR) thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97c0a-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="97c0a-105">Syntax</span></span>  
  
```cpp  
HRESULT GetObject (  
    [out] ICorDebugValue   **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="97c0a-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="97c0a-106">Parameters</span></span>  

 `ppObject`  
 <span data-ttu-id="97c0a-107">dışı CLR iş parçacığını temsil eden ICorDebugValue arabirimi nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="97c0a-107">[out] A pointer to the address of an ICorDebugValue interface object that represents the CLR thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="97c0a-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="97c0a-108">Requirements</span></span>  

 <span data-ttu-id="97c0a-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="97c0a-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="97c0a-110">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="97c0a-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="97c0a-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="97c0a-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="97c0a-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="97c0a-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97c0a-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="97c0a-113">See also</span></span>

- <xref:System.Threading.Thread>
