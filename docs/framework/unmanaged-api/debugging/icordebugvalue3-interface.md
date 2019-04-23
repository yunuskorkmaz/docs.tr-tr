---
title: ICorDebugValue3 Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugValue3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue3
helpviewer_keywords:
- ICorDebugValue3 interface [.NET Framework debugging]
ms.assetid: 7d5385d3-f4a5-47c4-8478-a3513b5e9406
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 300d2263c076c9028340863e2f7a3fa27a36ef9d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59221983"
---
# <a name="icordebugvalue3-interface"></a><span data-ttu-id="8a561-102">ICorDebugValue3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8a561-102">ICorDebugValue3 Interface</span></span>
<span data-ttu-id="8a561-103">2 GB'den daha büyük diziler için destek sağlamak için "ICorDebugValue" ve "ICorDebugValue2" arabirimlerini genişletir.</span><span class="sxs-lookup"><span data-stu-id="8a561-103">Extends the "ICorDebugValue" and "ICorDebugValue2" interfaces to provide support for arrays that are larger than 2 GB.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8a561-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="8a561-104">Methods</span></span>  
  
|<span data-ttu-id="8a561-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="8a561-105">Method</span></span>|<span data-ttu-id="8a561-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8a561-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8a561-107">GetSize64 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8a561-107">GetSize64 Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md)|<span data-ttu-id="8a561-108">Bu bayt cinsinden boyutunu alır `ICorDebugValue3` nesne.</span><span class="sxs-lookup"><span data-stu-id="8a561-108">Gets the size, in bytes, of this `ICorDebugValue3` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8a561-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8a561-109">Remarks</span></span>  
 <span data-ttu-id="8a561-110">[Icordebugvalue::getsize](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md) yöntemi 2.147.483.647 bayt 0'dan aralıkları bir nesne boyutu döndürür.</span><span class="sxs-lookup"><span data-stu-id="8a561-110">The [ICorDebugValue::GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md) method returns an object size that ranges from 0 to 2,147,483,647 bytes.</span></span> <span data-ttu-id="8a561-111">İçinde [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], dizi boyutu 2 GB aşabilir.</span><span class="sxs-lookup"><span data-stu-id="8a561-111">In the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], the size of arrays can exceed 2 GB.</span></span> <span data-ttu-id="8a561-112">`ICorDebugValue3` Arabirimi bu dizileri boyutunu belirlemek etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="8a561-112">The `ICorDebugValue3` interface enables you to determine the size of these arrays.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a561-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8a561-113">Requirements</span></span>  
 <span data-ttu-id="8a561-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8a561-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a561-115">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8a561-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8a561-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8a561-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8a561-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a561-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a561-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8a561-118">See also</span></span>

- [<span data-ttu-id="8a561-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="8a561-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="8a561-120">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="8a561-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
