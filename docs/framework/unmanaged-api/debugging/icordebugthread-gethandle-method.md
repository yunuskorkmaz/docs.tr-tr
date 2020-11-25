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
ms.openlocfilehash: 5debd09f3ca0b4562f62913f9530cc4fa6f9110b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728036"
---
# <a name="icordebugthreadgethandle-method"></a><span data-ttu-id="72405-102">ICorDebugThread::GetHandle Yöntemi</span><span class="sxs-lookup"><span data-stu-id="72405-102">ICorDebugThread::GetHandle Method</span></span>

<span data-ttu-id="72405-103">Bu ICorDebugThread 'in etkin bölümü için geçerli tanıtıcıyı alır.</span><span class="sxs-lookup"><span data-stu-id="72405-103">Gets the current handle for the active part of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72405-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="72405-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHandle (  
    [out] HTHREAD *phThreadHandle  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="72405-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="72405-105">Parameters</span></span>  

 `phThreadHandle`  
 <span data-ttu-id="72405-106">dışı Bu iş parçacığının etkin bölümünün tanıtıcısı olan bir HTHREAD için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="72405-106">[out] A pointer to an HTHREAD that is the handle of the active part of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="72405-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="72405-107">Remarks</span></span>  

 <span data-ttu-id="72405-108">Tanıtıcı, işlem yürütüldüğü gibi değişebilir ve iş parçacığının farklı parçaları için farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="72405-108">The handle may change as the process executes, and may be different for different parts of the thread.</span></span>  
  
 <span data-ttu-id="72405-109">Bu tanıtıcının sahibi hata ayıklama API 'sidir.</span><span class="sxs-lookup"><span data-stu-id="72405-109">This handle is owned by the debugging API.</span></span> <span data-ttu-id="72405-110">Hata ayıklayıcı, kullanmadan önce onu çoğaltmalıdır.</span><span class="sxs-lookup"><span data-stu-id="72405-110">The debugger should duplicate it before using it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72405-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="72405-111">Requirements</span></span>  

 <span data-ttu-id="72405-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="72405-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72405-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="72405-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="72405-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="72405-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="72405-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72405-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
