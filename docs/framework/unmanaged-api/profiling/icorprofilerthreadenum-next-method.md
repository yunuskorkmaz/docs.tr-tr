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
ms.openlocfilehash: e78285c915938c553a9b4012ba57257ac43492ad
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447600"
---
# <a name="icorprofilerthreadenumnext-method"></a><span data-ttu-id="ae615-102">ICorProfilerThreadEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ae615-102">ICorProfilerThreadEnum::Next Method</span></span>
<span data-ttu-id="ae615-103">Numaralandırıcının dizideki geçerli konumundan başlayarak ardışık iş parçacığı koleksiyonundan belirtilen sayıda bitişik iş parçacığı alır.</span><span class="sxs-lookup"><span data-stu-id="ae615-103">Gets the specified number of contiguous threads from a sequential collection of threads, starting at the enumerator's current position in the sequence.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae615-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ae615-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (    [in]  ULONG      celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
                    ThreadID ids[],  
    [out] ULONG *   pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ae615-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ae615-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="ae615-106">'ndaki Alınacak iş parçacıklarının sayısı.</span><span class="sxs-lookup"><span data-stu-id="ae615-106">[in] The number of threads to retrieve.</span></span>  
  
 `ids`  
 <span data-ttu-id="ae615-107">dışı Her biri alınan bir iş parçacığını temsil eden `ThreadID` değerleri dizisi.</span><span class="sxs-lookup"><span data-stu-id="ae615-107">[out] An array of `ThreadID` values, each of which represents a retrieved thread.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="ae615-108">dışı Gerçekten `ids` dizisinde döndürülen iş parçacığı sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ae615-108">[out] A pointer to the number of threads actually returned in the `ids` array.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ae615-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ae615-109">Return Value</span></span>  
 <span data-ttu-id="ae615-110">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="ae615-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="ae615-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ae615-111">HRESULT</span></span>|<span data-ttu-id="ae615-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ae615-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ae615-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="ae615-113">S_OK</span></span>|<span data-ttu-id="ae615-114">`celt` öğeler döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="ae615-114">`celt` elements were returned.</span></span>|  
|<span data-ttu-id="ae615-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="ae615-115">S_FALSE</span></span>|<span data-ttu-id="ae615-116">`celt` öğelerinden daha azı döndürüldü, bu, numaralandırmanın tamamlandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ae615-116">Fewer than `celt` elements were returned, which indicates that the enumeration is complete.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ae615-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ae615-117">Requirements</span></span>  
 <span data-ttu-id="ae615-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ae615-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae615-119">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="ae615-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ae615-120">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ae615-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ae615-121">**.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae615-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae615-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ae615-122">See also</span></span>

- [<span data-ttu-id="ae615-123">ICorProfilerThreadEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ae615-123">ICorProfilerThreadEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)
- [<span data-ttu-id="ae615-124">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ae615-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
