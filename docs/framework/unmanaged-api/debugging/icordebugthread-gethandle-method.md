---
description: ': ICorDebugThread:: GetHandle Yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 378bb395e56f0fc287a480d67d2047e082d0796f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99659107"
---
# <a name="icordebugthreadgethandle-method"></a><span data-ttu-id="fc227-103">ICorDebugThread::GetHandle Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fc227-103">ICorDebugThread::GetHandle Method</span></span>

<span data-ttu-id="fc227-104">Bu ICorDebugThread 'in etkin bölümü için geçerli tanıtıcıyı alır.</span><span class="sxs-lookup"><span data-stu-id="fc227-104">Gets the current handle for the active part of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc227-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fc227-105">Syntax</span></span>  
  
```cpp  
HRESULT GetHandle (  
    [out] HTHREAD *phThreadHandle  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fc227-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fc227-106">Parameters</span></span>  

 `phThreadHandle`  
 <span data-ttu-id="fc227-107">dışı Bu iş parçacığının etkin bölümünün tanıtıcısı olan bir HTHREAD için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="fc227-107">[out] A pointer to an HTHREAD that is the handle of the active part of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fc227-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fc227-108">Remarks</span></span>  

 <span data-ttu-id="fc227-109">Tanıtıcı, işlem yürütüldüğü gibi değişebilir ve iş parçacığının farklı parçaları için farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="fc227-109">The handle may change as the process executes, and may be different for different parts of the thread.</span></span>  
  
 <span data-ttu-id="fc227-110">Bu tanıtıcının sahibi hata ayıklama API 'sidir.</span><span class="sxs-lookup"><span data-stu-id="fc227-110">This handle is owned by the debugging API.</span></span> <span data-ttu-id="fc227-111">Hata ayıklayıcı, kullanmadan önce onu çoğaltmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fc227-111">The debugger should duplicate it before using it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc227-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fc227-112">Requirements</span></span>  

 <span data-ttu-id="fc227-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc227-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc227-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="fc227-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fc227-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="fc227-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fc227-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc227-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
