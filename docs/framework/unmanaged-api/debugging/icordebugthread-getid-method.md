---
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
ms.openlocfilehash: d01936481ec139757566d5b96cb95ea887cb8c20
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378065"
---
# <a name="icordebugthreadgetid-method"></a><span data-ttu-id="59a5a-102">ICorDebugThread::GetID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="59a5a-102">ICorDebugThread::GetID Method</span></span>
<span data-ttu-id="59a5a-103">Bu ICorDebugThread 'in etkin bölümünün geçerli işletim sistemi tanımlayıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="59a5a-103">Gets the current operating system identifier of the active part of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59a5a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="59a5a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetID (  
    [out] DWORD *pdwThreadId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="59a5a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="59a5a-105">Parameters</span></span>  
 `pdwThreadId`  
 <span data-ttu-id="59a5a-106">dışı İş parçacığının tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="59a5a-106">[out] The identifier of the thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="59a5a-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="59a5a-107">Remarks</span></span>  
 <span data-ttu-id="59a5a-108">İşletim sistemi tanımlayıcısı bir işlemin yürütülmesi sırasında muhtemelen değişebilir ve iş parçacığının farklı bölümleri için farklı bir değer olabilir.</span><span class="sxs-lookup"><span data-stu-id="59a5a-108">The operating system identifier can potentially change during execution of a process, and can be a different value for different parts of the thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59a5a-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="59a5a-109">Requirements</span></span>  
 <span data-ttu-id="59a5a-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="59a5a-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59a5a-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="59a5a-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="59a5a-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="59a5a-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="59a5a-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="59a5a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
