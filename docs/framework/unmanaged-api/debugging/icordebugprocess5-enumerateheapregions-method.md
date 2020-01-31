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
ms.openlocfilehash: 8070b0693b5718ad8b4cbeb9bf5792cb7f4a0a85
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792398"
---
# <a name="icordebugprocess5enumerateheapregions-method"></a><span data-ttu-id="7cf2b-102">ICorDebugProcess5::EnumerateHeapRegions Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7cf2b-102">ICorDebugProcess5::EnumerateHeapRegions Method</span></span>
<span data-ttu-id="7cf2b-103">Yönetilen yığının bellek aralıkları için bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="7cf2b-103">Gets an enumerator for the memory ranges of the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7cf2b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7cf2b-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateHeapRegions(  
   [out] ICorDebugHeapSegmentEnum **ppRegions  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7cf2b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7cf2b-105">Parameters</span></span>  
 `ppRegions`  
 <span data-ttu-id="7cf2b-106">dışı Nesnelerin yönetilen yığında bulunduğu bellek aralıklarına yönelik bir Numaralandırıcı olan [ICorDebugHeapSegmentEnum](icordebugheapsegmentenum-interface.md) arabirimi nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7cf2b-106">[out] A pointer to the address of an [ICorDebugHeapSegmentEnum](icordebugheapsegmentenum-interface.md) interface object that is an enumerator for the ranges of memory in which objects reside in the managed heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7cf2b-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7cf2b-107">Remarks</span></span>  
 <span data-ttu-id="7cf2b-108">`ICorDebugProcess5::EnumerateHeapRegions` yöntemi çağrılmadan önce, [ICorDebugProcess5:: GetGCHeapInformation](icordebugprocess5-getgcheapinformation-method.md) metodunu çağırmanız ve döndürülen [COR_HEAPINFO](cor-heapinfo-structure.md) nesnesinin `areGCStructuresValid` alanının değerini inceleyerek geçerli durumunda çöp toplama yığınının numaralandırılanmış olduğundan emin olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="7cf2b-108">Before calling the `ICorDebugProcess5::EnumerateHeapRegions` method, you should call the [ICorDebugProcess5::GetGCHeapInformation](icordebugprocess5-getgcheapinformation-method.md) method and examine the value of the `areGCStructuresValid` field of the returned [COR_HEAPINFO](cor-heapinfo-structure.md) object to ensure that the garbage collection heap in its current state is enumerable.</span></span> <span data-ttu-id="7cf2b-109">Ayrıca, `ICorDebugProcess5::EnumerateHeapRegions` yöntemi, işlem kullanım ömrü içinde çok erken iliştirmeye, bellek bölgeleri oluşturulmadan önce `E_FAIL` döndürür.</span><span class="sxs-lookup"><span data-stu-id="7cf2b-109">In addition, the `ICorDebugProcess5::EnumerateHeapRegions` method returns `E_FAIL` if you attach too early in the lifetime of the process, before memory regions are created.</span></span>  
  
 <span data-ttu-id="7cf2b-110">Bu yöntem, yönetilen nesneler içerebilen tüm bellek bölgelerini numaralandırmak için garanti edilir, ancak yönetilen nesnelerin gerçekten bu bölgelerde yer aldığı garanti etmez.</span><span class="sxs-lookup"><span data-stu-id="7cf2b-110">This method is guaranteed to enumerate all memory regions that may contain managed objects, but it does not guarantee that managed objects actually reside in those regions.</span></span> <span data-ttu-id="7cf2b-111">[ICorDebugHeapSegmentEnum](icordebugheapsegmentenum-interface.md) Collection nesnesi boş veya ayrılmış bellek bölgeleri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="7cf2b-111">The [ICorDebugHeapSegmentEnum](icordebugheapsegmentenum-interface.md) collection object may include empty or reserved memory regions.</span></span>  
  
 <span data-ttu-id="7cf2b-112">[ICorDebugHeapSegmentEnum](icordebugheapsegmentenum-interface.md) Interface nesnesi, [cor_segment](cor-segment-structure.md) nesneleri Listeletmanızı sağlayan ıcorı, genum arabiriminden türetilmiş standart bir Numaralandırıcı.</span><span class="sxs-lookup"><span data-stu-id="7cf2b-112">The [ICorDebugHeapSegmentEnum](icordebugheapsegmentenum-interface.md) interface object is a standard enumerator derived from the ICorDebugEnum interface that allows you to enumerate [COR_SEGMENT](cor-segment-structure.md) objects.</span></span> <span data-ttu-id="7cf2b-113">Her [cor_segment](cor-segment-structure.md) nesnesi, belirli bir segmentin bellek aralığı hakkında, bu kesimdeki nesnelerin nestiyle birlikte bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="7cf2b-113">Each [COR_SEGMENT](cor-segment-structure.md) object provides information about the memory range of a particular segment, along with the generation of the objects in that segment.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7cf2b-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7cf2b-114">Requirements</span></span>  
 <span data-ttu-id="7cf2b-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7cf2b-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7cf2b-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7cf2b-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7cf2b-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="7cf2b-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7cf2b-118">**.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7cf2b-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cf2b-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7cf2b-119">See also</span></span>

- [<span data-ttu-id="7cf2b-120">ICorDebugProcess5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7cf2b-120">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="7cf2b-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="7cf2b-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
