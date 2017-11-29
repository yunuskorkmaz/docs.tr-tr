---
title: ICorDebugThread4::GetBlockingObjects Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread4.GetBlockingObjects Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread4::GetBlockingObjects
helpviewer_keywords:
- GetBlockingObjects method [.NET Framework debugging]
- ICorDebugThread4::GetBlockingObjects method [.NET Framework debugging]
ms.assetid: a7e6c54e-7be9-4e52-bbb4-95f52458e8e4
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6783d7f9af67acdff147cc46ea4f856f9b10bf3a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugthread4getblockingobjects-method"></a><span data-ttu-id="c5dd5-102">ICorDebugThread4::GetBlockingObjects Metodu</span><span class="sxs-lookup"><span data-stu-id="c5dd5-102">ICorDebugThread4::GetBlockingObjects Method</span></span>
<span data-ttu-id="c5dd5-103">Sıralanmış numaralandırması sağlar [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) sağlamak yapıları iş parçacığı engelleme bilgi.</span><span class="sxs-lookup"><span data-stu-id="c5dd5-103">Provides an ordered enumeration of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures that provide thread blocking information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5dd5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c5dd5-104">Syntax</span></span>  
  
```  
HRESULT GetBlockingObjects (  
    [out] ICorDebugBlockingObjectEnum **ppBlockingObjectEnum  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c5dd5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c5dd5-105">Parameters</span></span>  
 `ppBlockingObjectEnum`  
 <span data-ttu-id="c5dd5-106">[out] Sıralanmış numaralandırması için bir işaretçi [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) yapıları.</span><span class="sxs-lookup"><span data-stu-id="c5dd5-106">[out] A pointer to an ordered enumeration of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c5dd5-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c5dd5-107">Remarks</span></span>  
 <span data-ttu-id="c5dd5-108">Döndürülen listedeki ilk öğe iş parçacığı engelleme ilk yapısına karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="c5dd5-108">The first element in the returned enumeration corresponds to the first structure that is blocking the thread.</span></span> <span data-ttu-id="c5dd5-109">İkinci öğe ilk ve benzeri engellenen zaman uyumsuz yordam çağrısı (APC) çalışırken karşılaşılan bir engelleme öğesi karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="c5dd5-109">The second element corresponds to a blocking item that is encountered while running an asynchronous procedure call (APC) when blocked on the first, and so on.</span></span>  
  
 <span data-ttu-id="c5dd5-110">Numaralandırma yalnızca geçerli eşitlenmiş durumuna süre için geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="c5dd5-110">The enumeration is valid only for the duration of the current synchronized state.</span></span>  
  
 <span data-ttu-id="c5dd5-111">Ayıklayıcı eşitlenmiş durumda olsa da bu yöntemi çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c5dd5-111">This method must be called while the debuggee is in a synchronized state.</span></span>  
  
 <span data-ttu-id="c5dd5-112">Varsa `ppBlockingObjectEnum` geçerli bir işaretçi değil sonucu tanımlanmadı.</span><span class="sxs-lookup"><span data-stu-id="c5dd5-112">If `ppBlockingObjectEnum` is not a valid pointer, the result is undefined.</span></span>  
  
 <span data-ttu-id="c5dd5-113">Bir iş parçacığı engellenir ve hata belirlenemiyor olursa yöntemi hata olduğunu gösteren bir HRESULT verir; Aksi takdirde, S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="c5dd5-113">If a thread is blocked and the error cannot be determined, the method returns an HRESULT that indicates failure; otherwise, it returns S_OK.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5dd5-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c5dd5-114">Requirements</span></span>  
 <span data-ttu-id="c5dd5-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c5dd5-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5dd5-116">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c5dd5-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c5dd5-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c5dd5-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c5dd5-118">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5dd5-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5dd5-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c5dd5-119">See Also</span></span>  
 [<span data-ttu-id="c5dd5-120">Icordebugthread4 arabirimi</span><span class="sxs-lookup"><span data-stu-id="c5dd5-120">ICorDebugThread4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)  
 [<span data-ttu-id="c5dd5-121">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c5dd5-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="c5dd5-122">Hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="c5dd5-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
