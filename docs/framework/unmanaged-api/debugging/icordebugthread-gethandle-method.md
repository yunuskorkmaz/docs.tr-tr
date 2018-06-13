---
title: ICorDebugThread::GetHandle Metodu
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
ms.openlocfilehash: 358597edc9fbc5203e5c00a5fb4d04019281060d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33418278"
---
# <a name="icordebugthreadgethandle-method"></a><span data-ttu-id="65137-102">ICorDebugThread::GetHandle Metodu</span><span class="sxs-lookup"><span data-stu-id="65137-102">ICorDebugThread::GetHandle Method</span></span>
<span data-ttu-id="65137-103">Geçerli işleme etkin bir kısmı bu Icordebugthread için alır.</span><span class="sxs-lookup"><span data-stu-id="65137-103">Gets the current handle for the active part of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65137-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="65137-104">Syntax</span></span>  
  
```  
HRESULT GetHandle (  
    [out] HTHREAD *phThreadHandle  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="65137-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="65137-105">Parameters</span></span>  
 `phThreadHandle`  
 <span data-ttu-id="65137-106">[out] Bu iş parçacığının etkin parçası tanıtıcısı bir HTHREAD gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="65137-106">[out] A pointer to an HTHREAD that is the handle of the active part of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="65137-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="65137-107">Remarks</span></span>  
 <span data-ttu-id="65137-108">İşlemi yürütür ve iş parçacığı farklı bölümleri için farklı olarak tanıtıcı değişebilir.</span><span class="sxs-lookup"><span data-stu-id="65137-108">The handle may change as the process executes, and may be different for different parts of the thread.</span></span>  
  
 <span data-ttu-id="65137-109">Bu işleyici hata ayıklama API'si tarafından sahiplenilmiş.</span><span class="sxs-lookup"><span data-stu-id="65137-109">This handle is owned by the debugging API.</span></span> <span data-ttu-id="65137-110">Hata ayıklayıcı kullanmadan önce çoğaltmalıdır.</span><span class="sxs-lookup"><span data-stu-id="65137-110">The debugger should duplicate it before using it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65137-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="65137-111">Requirements</span></span>  
 <span data-ttu-id="65137-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65137-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65137-113">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="65137-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="65137-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="65137-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="65137-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65137-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
