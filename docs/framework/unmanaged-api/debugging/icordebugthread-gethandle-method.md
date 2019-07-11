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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 54981be7104eb04ac6347ad13b61a69f40d4377c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67770616"
---
# <a name="icordebugthreadgethandle-method"></a><span data-ttu-id="544aa-102">ICorDebugThread::GetHandle Yöntemi</span><span class="sxs-lookup"><span data-stu-id="544aa-102">ICorDebugThread::GetHandle Method</span></span>
<span data-ttu-id="544aa-103">Bu Icordebugthread etkin parçası için geçerli bir tanıtıcı alır.</span><span class="sxs-lookup"><span data-stu-id="544aa-103">Gets the current handle for the active part of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="544aa-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="544aa-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHandle (  
    [out] HTHREAD *phThreadHandle  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="544aa-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="544aa-105">Parameters</span></span>  
 `phThreadHandle`  
 <span data-ttu-id="544aa-106">[out] Bu iş parçacığının etkin bölümünün tanıtıcısı bir HTHREAD işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="544aa-106">[out] A pointer to an HTHREAD that is the handle of the active part of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="544aa-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="544aa-107">Remarks</span></span>  
 <span data-ttu-id="544aa-108">İşlemi yürütür ve iş parçacığı farklı kısımlarını farklı tanıtıcı değişebilir.</span><span class="sxs-lookup"><span data-stu-id="544aa-108">The handle may change as the process executes, and may be different for different parts of the thread.</span></span>  
  
 <span data-ttu-id="544aa-109">Bu işleyici hata ayıklama API'si tarafından sahiplenilir.</span><span class="sxs-lookup"><span data-stu-id="544aa-109">This handle is owned by the debugging API.</span></span> <span data-ttu-id="544aa-110">Hata ayıklayıcı kullanmadan önce çoğaltmalıdır.</span><span class="sxs-lookup"><span data-stu-id="544aa-110">The debugger should duplicate it before using it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="544aa-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="544aa-111">Requirements</span></span>  
 <span data-ttu-id="544aa-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="544aa-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="544aa-113">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="544aa-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="544aa-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="544aa-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="544aa-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="544aa-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
