---
description: 'Şu konuda daha fazla bilgi edinin: ICorDebugProcess5:: Enumerateheapregion yöntemi'
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
ms.openlocfilehash: 034b1ebcd003e6854fa4f308b0464aac0a8c4839
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99649851"
---
# <a name="icordebugprocess5enumerateheapregions-method"></a><span data-ttu-id="c5221-103">ICorDebugProcess5::EnumerateHeapRegions Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c5221-103">ICorDebugProcess5::EnumerateHeapRegions Method</span></span>

<span data-ttu-id="c5221-104">Yönetilen yığının bellek aralıkları için bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="c5221-104">Gets an enumerator for the memory ranges of the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5221-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c5221-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateHeapRegions(  
   [out] ICorDebugHeapSegmentEnum **ppRegions  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c5221-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c5221-106">Parameters</span></span>  

 `ppRegions`  
 <span data-ttu-id="c5221-107">dışı Nesnelerin yönetilen yığında bulunduğu bellek aralıklarına yönelik bir Numaralandırıcı olan [ICorDebugHeapSegmentEnum](icordebugheapsegmentenum-interface.md) arabirimi nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c5221-107">[out] A pointer to the address of an [ICorDebugHeapSegmentEnum](icordebugheapsegmentenum-interface.md) interface object that is an enumerator for the ranges of memory in which objects reside in the managed heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c5221-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c5221-108">Remarks</span></span>  

 <span data-ttu-id="c5221-109">Yöntemi çağırmadan önce `ICorDebugProcess5::EnumerateHeapRegions` , [ICorDebugProcess5:: GetGCHeapInformation](icordebugprocess5-getgcheapinformation-method.md) metodunu çağırmanız ve `areGCStructuresValid` döndürülen [COR_HEAPINFO](cor-heapinfo-structure.md) nesnesinin alanının değerini inceleyerek, atık toplama yığınının geçerli durumunda sıralanabilir olduğundan emin olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c5221-109">Before calling the `ICorDebugProcess5::EnumerateHeapRegions` method, you should call the [ICorDebugProcess5::GetGCHeapInformation](icordebugprocess5-getgcheapinformation-method.md) method and examine the value of the `areGCStructuresValid` field of the returned [COR_HEAPINFO](cor-heapinfo-structure.md) object to ensure that the garbage collection heap in its current state is enumerable.</span></span> <span data-ttu-id="c5221-110">Ayrıca, yöntemi, `ICorDebugProcess5::EnumerateHeapRegions` `E_FAIL` bellek bölgelerini oluşturmadan önce, işlemin kullanım ömrü içinde çok erken bir şekilde iliştirse de döndürülür.</span><span class="sxs-lookup"><span data-stu-id="c5221-110">In addition, the `ICorDebugProcess5::EnumerateHeapRegions` method returns `E_FAIL` if you attach too early in the lifetime of the process, before memory regions are created.</span></span>  
  
 <span data-ttu-id="c5221-111">Bu yöntem, yönetilen nesneler içerebilen tüm bellek bölgelerini numaralandırmak için garanti edilir, ancak yönetilen nesnelerin gerçekten bu bölgelerde yer aldığı garanti etmez.</span><span class="sxs-lookup"><span data-stu-id="c5221-111">This method is guaranteed to enumerate all memory regions that may contain managed objects, but it does not guarantee that managed objects actually reside in those regions.</span></span> <span data-ttu-id="c5221-112">[ICorDebugHeapSegmentEnum](icordebugheapsegmentenum-interface.md) Collection nesnesi boş veya ayrılmış bellek bölgeleri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="c5221-112">The [ICorDebugHeapSegmentEnum](icordebugheapsegmentenum-interface.md) collection object may include empty or reserved memory regions.</span></span>  
  
 <span data-ttu-id="c5221-113">[ICorDebugHeapSegmentEnum](icordebugheapsegmentenum-interface.md) Interface nesnesi, [cor_segment](cor-segment-structure.md) nesneleri Listeletmanızı sağlayan ıcorı, genum arabiriminden türetilmiş standart bir Numaralandırıcı.</span><span class="sxs-lookup"><span data-stu-id="c5221-113">The [ICorDebugHeapSegmentEnum](icordebugheapsegmentenum-interface.md) interface object is a standard enumerator derived from the ICorDebugEnum interface that allows you to enumerate [COR_SEGMENT](cor-segment-structure.md) objects.</span></span> <span data-ttu-id="c5221-114">Her [cor_segment](cor-segment-structure.md) nesnesi, belirli bir segmentin bellek aralığı hakkında, bu kesimdeki nesnelerin nestiyle birlikte bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="c5221-114">Each [COR_SEGMENT](cor-segment-structure.md) object provides information about the memory range of a particular segment, along with the generation of the objects in that segment.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5221-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c5221-115">Requirements</span></span>  

 <span data-ttu-id="c5221-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c5221-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5221-117">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c5221-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c5221-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c5221-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c5221-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5221-119">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5221-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c5221-120">See also</span></span>

- [<span data-ttu-id="c5221-121">ICorDebugProcess5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c5221-121">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="c5221-122">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c5221-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
