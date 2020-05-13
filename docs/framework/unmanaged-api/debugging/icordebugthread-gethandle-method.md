---
title: ICorDebugThread::GetHandle Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetHandle
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetHandle
helpviewer_keywords:
- GetHandle method, ICorDebugThread interface [.NET Framework debugging]
- ICorDebugThread::GetHandle method [.NET Framework debugging]
ms.assetid: 172ef8c4-2ead-4cfc-bd2e-dee4fb7191cd
topic_type:
- apiref
ms.openlocfilehash: 16aafa439fc81c3606f98ca2ba860316ec46e0db
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379747"
---
# <a name="icordebugthreadgethandle-method"></a><span data-ttu-id="6f46b-102">ICorDebugThread::GetHandle Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6f46b-102">ICorDebugThread::GetHandle Method</span></span>
<span data-ttu-id="6f46b-103">Bu ICorDebugThread 'in etkin bölümü için geçerli tanıtıcıyı alır.</span><span class="sxs-lookup"><span data-stu-id="6f46b-103">Gets the current handle for the active part of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f46b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6f46b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHandle (  
    [out] HTHREAD *phThreadHandle  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6f46b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6f46b-105">Parameters</span></span>  
 `phThreadHandle`  
 <span data-ttu-id="6f46b-106">dışı Bu iş parçacığının etkin bölümünün tanıtıcısı olan bir HTHREAD için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6f46b-106">[out] A pointer to an HTHREAD that is the handle of the active part of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6f46b-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6f46b-107">Remarks</span></span>  
 <span data-ttu-id="6f46b-108">Tanıtıcı, işlem yürütüldüğü gibi değişebilir ve iş parçacığının farklı parçaları için farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="6f46b-108">The handle may change as the process executes, and may be different for different parts of the thread.</span></span>  
  
 <span data-ttu-id="6f46b-109">Bu tanıtıcının sahibi hata ayıklama API 'sidir.</span><span class="sxs-lookup"><span data-stu-id="6f46b-109">This handle is owned by the debugging API.</span></span> <span data-ttu-id="6f46b-110">Hata ayıklayıcı, kullanmadan önce onu çoğaltmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6f46b-110">The debugger should duplicate it before using it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f46b-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6f46b-111">Requirements</span></span>  
 <span data-ttu-id="6f46b-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6f46b-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f46b-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6f46b-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6f46b-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="6f46b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6f46b-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f46b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
