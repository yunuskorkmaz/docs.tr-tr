---
title: ICorDebugThread4::GetBlockingObjects Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugThread4.GetBlockingObjects Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread4::GetBlockingObjects
helpviewer_keywords:
- GetBlockingObjects method [.NET Framework debugging]
- ICorDebugThread4::GetBlockingObjects method [.NET Framework debugging]
ms.assetid: a7e6c54e-7be9-4e52-bbb4-95f52458e8e4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5095dc04b118e782b00bb385427ad23a2786343c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54740170"
---
# <a name="icordebugthread4getblockingobjects-method"></a><span data-ttu-id="0c500-102">ICorDebugThread4::GetBlockingObjects Metodu</span><span class="sxs-lookup"><span data-stu-id="0c500-102">ICorDebugThread4::GetBlockingObjects Method</span></span>
<span data-ttu-id="0c500-103">Sıralı sabit listesi sağlar [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) sağlayan yapıları iş parçacığı engelleme bilgileri.</span><span class="sxs-lookup"><span data-stu-id="0c500-103">Provides an ordered enumeration of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures that provide thread blocking information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c500-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0c500-104">Syntax</span></span>  
  
```  
HRESULT GetBlockingObjects (  
    [out] ICorDebugBlockingObjectEnum **ppBlockingObjectEnum  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0c500-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0c500-105">Parameters</span></span>  
 `ppBlockingObjectEnum`  
 <span data-ttu-id="0c500-106">[out] Sıralı sabit listesi için bir işaretçi [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) yapıları.</span><span class="sxs-lookup"><span data-stu-id="0c500-106">[out] A pointer to an ordered enumeration of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0c500-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0c500-107">Remarks</span></span>  
 <span data-ttu-id="0c500-108">Döndürülen listedeki ilk öğeyi iş parçacığının engellenmesi ilk yapısına karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="0c500-108">The first element in the returned enumeration corresponds to the first structure that is blocking the thread.</span></span> <span data-ttu-id="0c500-109">İkinci öğe, bir zaman uyumsuz bir yordam çağrısı (APC) ilk ve benzeri engellendiğinde çalıştırılırken karşılaşılan engelleme öğesine karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="0c500-109">The second element corresponds to a blocking item that is encountered while running an asynchronous procedure call (APC) when blocked on the first, and so on.</span></span>  
  
 <span data-ttu-id="0c500-110">Sabit listesi yalnızca geçerli eşitleme durumunun süresi boyunca geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="0c500-110">The enumeration is valid only for the duration of the current synchronized state.</span></span>  
  
 <span data-ttu-id="0c500-111">Hata ayıklanan eşitlenmiş bir durumda olsa da, bu yöntem çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0c500-111">This method must be called while the debuggee is in a synchronized state.</span></span>  
  
 <span data-ttu-id="0c500-112">Varsa `ppBlockingObjectEnum` geçerli bir işaretçi değil sonuç tanımsızdır.</span><span class="sxs-lookup"><span data-stu-id="0c500-112">If `ppBlockingObjectEnum` is not a valid pointer, the result is undefined.</span></span>  
  
 <span data-ttu-id="0c500-113">Yöntemi, bir iş parçacığı engellenir ve hata belirlenemiyor, hata olduğunu gösteren bir HRESULT döndürür; Aksi takdirde S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="0c500-113">If a thread is blocked and the error cannot be determined, the method returns an HRESULT that indicates failure; otherwise, it returns S_OK.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c500-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0c500-114">Requirements</span></span>  
 <span data-ttu-id="0c500-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0c500-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c500-116">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0c500-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0c500-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0c500-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0c500-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c500-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c500-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0c500-119">See also</span></span>
- [<span data-ttu-id="0c500-120">ICorDebugThread4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0c500-120">ICorDebugThread4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)
- [<span data-ttu-id="0c500-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="0c500-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="0c500-122">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="0c500-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
