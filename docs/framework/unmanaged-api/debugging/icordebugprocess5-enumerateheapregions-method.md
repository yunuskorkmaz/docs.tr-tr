---
title: ICorDebugProcess5::EnumerateHeapRegions Yöntemi
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cf9340977c55c54b9a4683115000293d1c98dfcf
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67767463"
---
# <a name="icordebugprocess5enumerateheapregions-method"></a><span data-ttu-id="dba84-102">ICorDebugProcess5::EnumerateHeapRegions Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dba84-102">ICorDebugProcess5::EnumerateHeapRegions Method</span></span>
<span data-ttu-id="dba84-103">Yönetilen yığının bellek aralığı için bir numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="dba84-103">Gets an enumerator for the memory ranges of the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dba84-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dba84-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateHeapRegions(  
   [out] ICorDebugHeapSegmentEnum **ppRegions  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dba84-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="dba84-105">Parameters</span></span>  
 `ppRegions`  
 <span data-ttu-id="dba84-106">[out] Adresine bir işaretçi bir [Icordebugheapsegmentenum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) nesneler yönetilen yığında bulunan bellek aralığı için bir numaralandırıcı arabirimi nesnesi.</span><span class="sxs-lookup"><span data-stu-id="dba84-106">[out] A pointer to the address of an [ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) interface object that is an enumerator for the ranges of memory in which objects reside in the managed heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dba84-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dba84-107">Remarks</span></span>  
 <span data-ttu-id="dba84-108">Çağırmadan önce `ICorDebugProcess5::EnumerateHeapRegions` yöntemini çağırmalıdır [Icordebugprocess5::getgcheapınformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) yöntemi ve değerini incelemek `areGCStructuresValid` alan döndürülen [cor_heapınfo](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) nesnenin numaralandırılabilir çöp toplama yığınındaki geçerli durumda olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="dba84-108">Before calling the `ICorDebugProcess5::EnumerateHeapRegions` method, you should call the [ICorDebugProcess5::GetGCHeapInformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) method and examine the value of the `areGCStructuresValid` field of the returned [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) object to ensure that the garbage collection heap in its current state is enumerable.</span></span> <span data-ttu-id="dba84-109">Ayrıca, `ICorDebugProcess5::EnumerateHeapRegions` yöntemi döndürür `E_FAIL` çok erken işlem yaşam süresi içinde eklerseniz, önce bellek bölgeleri oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="dba84-109">In addition, the `ICorDebugProcess5::EnumerateHeapRegions` method returns `E_FAIL` if you attach too early in the lifetime of the process, before memory regions are created.</span></span>  
  
 <span data-ttu-id="dba84-110">Bu yöntem, yönetilen nesneleri içerebilir tüm bellek bölümlerinin numaralandırmak için garanti edilir, ancak yönetilen nesneleri aslında bu bölgelerde bulunan garantilemez.</span><span class="sxs-lookup"><span data-stu-id="dba84-110">This method is guaranteed to enumerate all memory regions that may contain managed objects, but it does not guarantee that managed objects actually reside in those regions.</span></span> <span data-ttu-id="dba84-111">[Icordebugheapsegmentenum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) koleksiyon nesnesi boş veya ayrılmış bellek bölümlerinin içerebilir.</span><span class="sxs-lookup"><span data-stu-id="dba84-111">The [ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) collection object may include empty or reserved memory regions.</span></span>  
  
 <span data-ttu-id="dba84-112">[Icordebugheapsegmentenum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) arabirimi nesnedir listeleme olanak tanıyan Icordebugenum arabirimden türetilmiş standart bir numaralandırıcı [COR_SEGMENT](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md) nesneleri.</span><span class="sxs-lookup"><span data-stu-id="dba84-112">The [ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) interface object is a standard enumerator derived from the ICorDebugEnum interface that allows you to enumerate [COR_SEGMENT](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md) objects.</span></span> <span data-ttu-id="dba84-113">Her [COR_SEGMENT](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md) nesne kesiminin nesneleri nesil yanı sıra belirli bir kesim bellek aralığı hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="dba84-113">Each [COR_SEGMENT](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md) object provides information about the memory range of a particular segment, along with the generation of the objects in that segment.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dba84-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dba84-114">Requirements</span></span>  
 <span data-ttu-id="dba84-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dba84-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dba84-116">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dba84-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dba84-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dba84-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dba84-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dba84-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dba84-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dba84-119">See also</span></span>

- [<span data-ttu-id="dba84-120">ICorDebugProcess5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dba84-120">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [<span data-ttu-id="dba84-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="dba84-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
