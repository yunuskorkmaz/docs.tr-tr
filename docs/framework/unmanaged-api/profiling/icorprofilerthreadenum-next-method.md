---
title: ICorProfilerThreadEnum::Next Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerThreadEnum.Next
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerThreadEnum::Next
helpviewer_keywords:
- ICorProfilerThreadEnum::Next method [.NET Framework profiling]
- Next method, ICorProfilerThreadEnum interface [.NET Framework profiling]
ms.assetid: f3535279-3c63-41a2-ab0e-a129dc5a01e8
topic_type:
- apiref
ms.openlocfilehash: 37d1acfa70a1a2b2c18fb34fb5d6024f3b61e2ab
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84494351"
---
# <a name="icorprofilerthreadenumnext-method"></a><span data-ttu-id="379ec-102">ICorProfilerThreadEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="379ec-102">ICorProfilerThreadEnum::Next Method</span></span>
<span data-ttu-id="379ec-103">Numaralandırıcının dizideki geçerli konumundan başlayarak ardışık iş parçacığı koleksiyonundan belirtilen sayıda bitişik iş parçacığı alır.</span><span class="sxs-lookup"><span data-stu-id="379ec-103">Gets the specified number of contiguous threads from a sequential collection of threads, starting at the enumerator's current position in the sequence.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="379ec-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="379ec-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (    [in]  ULONG      celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
                    ThreadID ids[],  
    [out] ULONG *   pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="379ec-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="379ec-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="379ec-106">'ndaki Alınacak iş parçacıklarının sayısı.</span><span class="sxs-lookup"><span data-stu-id="379ec-106">[in] The number of threads to retrieve.</span></span>  
  
 `ids`  
 <span data-ttu-id="379ec-107">dışı `ThreadID`Her biri alınan bir iş parçacığını temsil eden bir değer dizisi.</span><span class="sxs-lookup"><span data-stu-id="379ec-107">[out] An array of `ThreadID` values, each of which represents a retrieved thread.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="379ec-108">dışı Gerçekten dizide döndürülen iş parçacığı sayısına yönelik bir işaretçi `ids` .</span><span class="sxs-lookup"><span data-stu-id="379ec-108">[out] A pointer to the number of threads actually returned in the `ids` array.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="379ec-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="379ec-109">Return Value</span></span>  
 <span data-ttu-id="379ec-110">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="379ec-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="379ec-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="379ec-111">HRESULT</span></span>|<span data-ttu-id="379ec-112">Description</span><span class="sxs-lookup"><span data-stu-id="379ec-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="379ec-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="379ec-113">S_OK</span></span>|<span data-ttu-id="379ec-114">`celt`öğeler döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="379ec-114">`celt` elements were returned.</span></span>|  
|<span data-ttu-id="379ec-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="379ec-115">S_FALSE</span></span>|<span data-ttu-id="379ec-116">Daha az `celt` öğe döndürüldü, bu, numaralandırmanın tamamlandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="379ec-116">Fewer than `celt` elements were returned, which indicates that the enumeration is complete.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="379ec-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="379ec-117">Requirements</span></span>  
 <span data-ttu-id="379ec-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="379ec-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="379ec-119">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="379ec-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="379ec-120">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="379ec-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="379ec-121">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="379ec-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="379ec-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="379ec-122">See also</span></span>

- [<span data-ttu-id="379ec-123">ICorProfilerThreadEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="379ec-123">ICorProfilerThreadEnum Interface</span></span>](icorprofilerthreadenum-interface.md)
- [<span data-ttu-id="379ec-124">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="379ec-124">Profiling Interfaces</span></span>](profiling-interfaces.md)
