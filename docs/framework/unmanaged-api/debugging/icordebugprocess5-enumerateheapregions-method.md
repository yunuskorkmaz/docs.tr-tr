---
title: "ICorDebugProcess5::EnumerateHeapRegions Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugProcess5.EnumerateHeapRegions
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnumerateHeapRegions
helpviewer_keywords:
- EnumerateHeapRegions method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::EnumerateHeapRegions method [.NET Framework debugging]
ms.assetid: b1edba68-9c36-4f69-be9f-678ce0b33480
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 478a8490e57946a08670d9f86e1f6ebcc67703a6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess5enumerateheapregions-method"></a><span data-ttu-id="edcba-102">ICorDebugProcess5::EnumerateHeapRegions Yöntemi</span><span class="sxs-lookup"><span data-stu-id="edcba-102">ICorDebugProcess5::EnumerateHeapRegions Method</span></span>
<span data-ttu-id="edcba-103">Yönetilen yığın bellek aralıkları için bir numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="edcba-103">Gets an enumerator for the memory ranges of the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="edcba-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="edcba-104">Syntax</span></span>  
  
```  
HRESULT EnumerateHeapRegions(  
   [out] ICorDebugHeapSegmentEnum **ppRegions  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="edcba-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="edcba-105">Parameters</span></span>  
 `ppRegions`  
 <span data-ttu-id="edcba-106">[out] Adresine bir işaretçi bir [Icordebugheapsegmentenum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) nesneleri Yönetilen yığın içinde bulunan bellek aralıkları için bir numaralandırıcı arabirimi nesnesi.</span><span class="sxs-lookup"><span data-stu-id="edcba-106">[out] A pointer to the address of an [ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) interface object that is an enumerator for the ranges of memory in which objects reside in the managed heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="edcba-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="edcba-107">Remarks</span></span>  
 <span data-ttu-id="edcba-108">Çağırmadan önce `ICorDebugProcess5::EnumerateHeapRegions` yöntemi çağırın [Icordebugprocess5::getgcheapınformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) yöntemi ve değerini inceleyin `areGCStructuresValid` dönen alan [cor_heapınfo](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) Çöp toplama yığın mevcut durumunda numaralandırılabilir olduğundan emin olmak için nesne.</span><span class="sxs-lookup"><span data-stu-id="edcba-108">Before calling the `ICorDebugProcess5::EnumerateHeapRegions` method, you should call the [ICorDebugProcess5::GetGCHeapInformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) method and examine the value of the `areGCStructuresValid` field of the returned [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) object to ensure that the garbage collection heap in its current state is enumerable.</span></span> <span data-ttu-id="edcba-109">Ayrıca, `ICorDebugProcess5::EnumerateHeapRegions` yöntemi döndürür `E_FAIL` çok erken işlem yaşam süresi içinde eklerseniz, önce bellek bölgeleri oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="edcba-109">In addition, the `ICorDebugProcess5::EnumerateHeapRegions` method returns `E_FAIL` if you attach too early in the lifetime of the process, before memory regions are created.</span></span>  
  
 <span data-ttu-id="edcba-110">Bu yöntem yönetilen nesneleri içerebilir tüm bellek bölümlerinin Numaralandırılacak sağlanır, ancak bu yönetilen nesneler gerçekte bu bölgede bulunan garanti etmez.</span><span class="sxs-lookup"><span data-stu-id="edcba-110">This method is guaranteed to enumerate all memory regions that may contain managed objects, but it does not guarantee that managed objects actually reside in those regions.</span></span> <span data-ttu-id="edcba-111">[Icordebugheapsegmentenum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) koleksiyon nesnesi boş veya ayrılmış bellek bölümlerinin içerebilir.</span><span class="sxs-lookup"><span data-stu-id="edcba-111">The [ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) collection object may include empty or reserved memory regions.</span></span>  
  
 <span data-ttu-id="edcba-112">[Icordebugheapsegmentenum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) arabiriminin nesnesidir Numaralandırılacak izin veren Icordebugenum arabirimden türetilmiş standart bir numaralandırıcı [COR_SEGMENT](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md) nesneleri.</span><span class="sxs-lookup"><span data-stu-id="edcba-112">The [ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) interface object is a standard enumerator derived from the ICorDebugEnum interface that allows you to enumerate [COR_SEGMENT](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md) objects.</span></span> <span data-ttu-id="edcba-113">Her [COR_SEGMENT](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md) nesneyi bu kesimdeki nesneleri nesil yanı sıra belirli bir segmentle bellek aralığı hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="edcba-113">Each [COR_SEGMENT](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md) object provides information about the memory range of a particular segment, along with the generation of the objects in that segment.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="edcba-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="edcba-114">Requirements</span></span>  
 <span data-ttu-id="edcba-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="edcba-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="edcba-116">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="edcba-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="edcba-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="edcba-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="edcba-118">**.NET framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="edcba-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="edcba-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="edcba-119">See Also</span></span>  
 [<span data-ttu-id="edcba-120">ICorDebugProcess5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="edcba-120">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 [<span data-ttu-id="edcba-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="edcba-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
