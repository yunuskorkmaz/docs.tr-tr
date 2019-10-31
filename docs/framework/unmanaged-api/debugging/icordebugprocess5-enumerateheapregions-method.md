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
ms.openlocfilehash: 3ab4da3fcf43731587dae6f3a8e82ea48c5ee1ec
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129637"
---
# <a name="icordebugprocess5enumerateheapregions-method"></a><span data-ttu-id="725cc-102">ICorDebugProcess5::EnumerateHeapRegions Yöntemi</span><span class="sxs-lookup"><span data-stu-id="725cc-102">ICorDebugProcess5::EnumerateHeapRegions Method</span></span>
<span data-ttu-id="725cc-103">Yönetilen yığının bellek aralıkları için bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="725cc-103">Gets an enumerator for the memory ranges of the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="725cc-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="725cc-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateHeapRegions(  
   [out] ICorDebugHeapSegmentEnum **ppRegions  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="725cc-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="725cc-105">Parameters</span></span>  
 `ppRegions`  
 <span data-ttu-id="725cc-106">dışı Nesnelerin yönetilen yığında bulunduğu bellek aralıklarına yönelik bir Numaralandırıcı olan [ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) arabirimi nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="725cc-106">[out] A pointer to the address of an [ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) interface object that is an enumerator for the ranges of memory in which objects reside in the managed heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="725cc-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="725cc-107">Remarks</span></span>  
 <span data-ttu-id="725cc-108">`ICorDebugProcess5::EnumerateHeapRegions` yöntemi çağrılmadan önce, [ICorDebugProcess5:: GetGCHeapInformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) metodunu çağırmanız ve döndürülen [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) nesnesinin `areGCStructuresValid` alanının değerini inceleyerek, çöp toplama işleminin geçerli durum Numaralandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="725cc-108">Before calling the `ICorDebugProcess5::EnumerateHeapRegions` method, you should call the [ICorDebugProcess5::GetGCHeapInformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) method and examine the value of the `areGCStructuresValid` field of the returned [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) object to ensure that the garbage collection heap in its current state is enumerable.</span></span> <span data-ttu-id="725cc-109">Ayrıca, `ICorDebugProcess5::EnumerateHeapRegions` yöntemi, işlem kullanım ömrü içinde çok erken iliştirmeye, bellek bölgeleri oluşturulmadan önce `E_FAIL` döndürür.</span><span class="sxs-lookup"><span data-stu-id="725cc-109">In addition, the `ICorDebugProcess5::EnumerateHeapRegions` method returns `E_FAIL` if you attach too early in the lifetime of the process, before memory regions are created.</span></span>  
  
 <span data-ttu-id="725cc-110">Bu yöntem, yönetilen nesneler içerebilen tüm bellek bölgelerini numaralandırmak için garanti edilir, ancak yönetilen nesnelerin gerçekten bu bölgelerde yer aldığı garanti etmez.</span><span class="sxs-lookup"><span data-stu-id="725cc-110">This method is guaranteed to enumerate all memory regions that may contain managed objects, but it does not guarantee that managed objects actually reside in those regions.</span></span> <span data-ttu-id="725cc-111">[ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) Collection nesnesi boş veya ayrılmış bellek bölgeleri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="725cc-111">The [ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) collection object may include empty or reserved memory regions.</span></span>  
  
 <span data-ttu-id="725cc-112">[ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) Interface nesnesi, [cor_segment](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md) nesnelerini Listeletmanızı sağlayan ıcorhata ayıklama genum arabiriminden türetilmiş standart bir Numaralandırıcı.</span><span class="sxs-lookup"><span data-stu-id="725cc-112">The [ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) interface object is a standard enumerator derived from the ICorDebugEnum interface that allows you to enumerate [COR_SEGMENT](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md) objects.</span></span> <span data-ttu-id="725cc-113">Her [cor_segment](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md) nesnesi, belirli bir segmentin bellek aralığı ve bu kesimdeki nesnelerin nestiyle birlikte hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="725cc-113">Each [COR_SEGMENT](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md) object provides information about the memory range of a particular segment, along with the generation of the objects in that segment.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="725cc-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="725cc-114">Requirements</span></span>  
 <span data-ttu-id="725cc-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="725cc-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="725cc-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="725cc-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="725cc-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="725cc-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="725cc-118">**.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="725cc-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="725cc-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="725cc-119">See also</span></span>

- [<span data-ttu-id="725cc-120">ICorDebugProcess5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="725cc-120">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [<span data-ttu-id="725cc-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="725cc-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
