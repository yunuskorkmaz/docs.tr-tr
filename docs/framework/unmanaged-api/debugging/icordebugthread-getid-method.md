---
description: ': ICorDebugThread:: GetID Yöntemi hakkında daha fazla bilgi edinin'
title: ICorDebugThread::GetID Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetID
helpviewer_keywords:
- ICorDebugThread::GetID method [.NET Framework debugging]
- GetID method, ICorDebugThread interface [.NET Framework debugging]
ms.assetid: f1de4584-92df-42f3-9da4-fca03a1c6821
topic_type:
- apiref
ms.openlocfilehash: d089201527da67299b64cdf074bdd331f22375a1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99659094"
---
# <a name="icordebugthreadgetid-method"></a><span data-ttu-id="ada3f-103">ICorDebugThread::GetID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ada3f-103">ICorDebugThread::GetID Method</span></span>

<span data-ttu-id="ada3f-104">Bu ICorDebugThread 'in etkin bölümünün geçerli işletim sistemi tanımlayıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="ada3f-104">Gets the current operating system identifier of the active part of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ada3f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ada3f-105">Syntax</span></span>  
  
```cpp  
HRESULT GetID (  
    [out] DWORD *pdwThreadId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ada3f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ada3f-106">Parameters</span></span>  

 `pdwThreadId`  
 <span data-ttu-id="ada3f-107">dışı İş parçacığının tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="ada3f-107">[out] The identifier of the thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ada3f-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ada3f-108">Remarks</span></span>  

 <span data-ttu-id="ada3f-109">İşletim sistemi tanımlayıcısı bir işlemin yürütülmesi sırasında muhtemelen değişebilir ve iş parçacığının farklı bölümleri için farklı bir değer olabilir.</span><span class="sxs-lookup"><span data-stu-id="ada3f-109">The operating system identifier can potentially change during execution of a process, and can be a different value for different parts of the thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ada3f-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ada3f-110">Requirements</span></span>  

 <span data-ttu-id="ada3f-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ada3f-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ada3f-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ada3f-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ada3f-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ada3f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ada3f-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ada3f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
