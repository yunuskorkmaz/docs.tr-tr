---
description: 'Şu konuda daha fazla bilgi edinin: ICorProfilerThreadEnum:: Next yöntemi'
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
ms.openlocfilehash: 74567624cbe5042b8ab63a28e7fb07e9f708a959
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99636349"
---
# <a name="icorprofilerthreadenumnext-method"></a><span data-ttu-id="79d06-103">ICorProfilerThreadEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="79d06-103">ICorProfilerThreadEnum::Next Method</span></span>

<span data-ttu-id="79d06-104">Numaralandırıcının dizideki geçerli konumundan başlayarak ardışık iş parçacığı koleksiyonundan belirtilen sayıda bitişik iş parçacığı alır.</span><span class="sxs-lookup"><span data-stu-id="79d06-104">Gets the specified number of contiguous threads from a sequential collection of threads, starting at the enumerator's current position in the sequence.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79d06-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="79d06-105">Syntax</span></span>  
  
```cpp  
HRESULT Next (    [in]  ULONG      celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
                    ThreadID ids[],  
    [out] ULONG *   pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="79d06-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="79d06-106">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="79d06-107">'ndaki Alınacak iş parçacıklarının sayısı.</span><span class="sxs-lookup"><span data-stu-id="79d06-107">[in] The number of threads to retrieve.</span></span>  
  
 `ids`  
 <span data-ttu-id="79d06-108">dışı `ThreadID` Her biri alınan bir iş parçacığını temsil eden bir değer dizisi.</span><span class="sxs-lookup"><span data-stu-id="79d06-108">[out] An array of `ThreadID` values, each of which represents a retrieved thread.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="79d06-109">dışı Gerçekten dizide döndürülen iş parçacığı sayısına yönelik bir işaretçi `ids` .</span><span class="sxs-lookup"><span data-stu-id="79d06-109">[out] A pointer to the number of threads actually returned in the `ids` array.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="79d06-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="79d06-110">Return Value</span></span>  

 <span data-ttu-id="79d06-111">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="79d06-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="79d06-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="79d06-112">HRESULT</span></span>|<span data-ttu-id="79d06-113">Description</span><span class="sxs-lookup"><span data-stu-id="79d06-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="79d06-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="79d06-114">S_OK</span></span>|<span data-ttu-id="79d06-115">`celt` öğeler döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="79d06-115">`celt` elements were returned.</span></span>|  
|<span data-ttu-id="79d06-116">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="79d06-116">S_FALSE</span></span>|<span data-ttu-id="79d06-117">Daha az `celt` öğe döndürüldü, bu, numaralandırmanın tamamlandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="79d06-117">Fewer than `celt` elements were returned, which indicates that the enumeration is complete.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="79d06-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="79d06-118">Requirements</span></span>  

 <span data-ttu-id="79d06-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="79d06-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79d06-120">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="79d06-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="79d06-121">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="79d06-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="79d06-122">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="79d06-122">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79d06-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="79d06-123">See also</span></span>

- [<span data-ttu-id="79d06-124">ICorProfilerThreadEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="79d06-124">ICorProfilerThreadEnum Interface</span></span>](icorprofilerthreadenum-interface.md)
- [<span data-ttu-id="79d06-125">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="79d06-125">Profiling Interfaces</span></span>](profiling-interfaces.md)
