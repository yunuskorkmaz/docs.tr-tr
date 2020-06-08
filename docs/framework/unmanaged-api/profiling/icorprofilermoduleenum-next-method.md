---
title: ICorProfilerModuleEnum::Next Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerModuleEnum.Next Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerModuleEnum::Next
helpviewer_keywords:
- ICorProfilerModuleEnum::Next method [.NET Framework profiling]
- Next method, ICorProfilerModuleEnum interface [.NET Framework profiling]
ms.assetid: a3cea59d-7622-4323-897a-0a464c40f77f
topic_type:
- apiref
ms.openlocfilehash: 7a3ad94a4149d6ebb70e077926771e28d7f82779
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84494845"
---
# <a name="icorprofilermoduleenumnext-method"></a><span data-ttu-id="f94c6-102">ICorProfilerModuleEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f94c6-102">ICorProfilerModuleEnum::Next Method</span></span>
<span data-ttu-id="f94c6-103">Numaralandırıcının dizideki geçerli konumundan başlayarak sıralı bir modül koleksiyonundan belirtilen sayıda bitişik modülü alır.</span><span class="sxs-lookup"><span data-stu-id="f94c6-103">Gets the specified number of contiguous modules from a sequential collection of modules, starting at the enumerator's current position in the sequence.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f94c6-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="f94c6-104">Syntax</span></span>  
  
```cpp  
HRESULT Next([in]  ULONG      celt,  
             [out, size_is(celt), length_is(*pceltFetched)]  
                    ModuleID ids[],  
             [out] ULONG *   pceltFetched);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f94c6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f94c6-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="f94c6-106">'ndaki Alınacak modül sayısı.</span><span class="sxs-lookup"><span data-stu-id="f94c6-106">[in] The number of modules to retrieve.</span></span>  
  
 `ids`  
 <span data-ttu-id="f94c6-107">dışı `ModuleID`Her biri alınan bir modülü temsil eden bir değer dizisi.</span><span class="sxs-lookup"><span data-stu-id="f94c6-107">[out] An array of `ModuleID` values, each of which represents a retrieved module.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="f94c6-108">dışı Dizide gerçekten döndürülen öğe sayısına yönelik bir işaretçi `ids` .</span><span class="sxs-lookup"><span data-stu-id="f94c6-108">[out] A pointer to the number of elements actually returned in the `ids` array.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f94c6-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="f94c6-109">Return Value</span></span>  
 <span data-ttu-id="f94c6-110">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="f94c6-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="f94c6-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f94c6-111">HRESULT</span></span>|<span data-ttu-id="f94c6-112">Description</span><span class="sxs-lookup"><span data-stu-id="f94c6-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f94c6-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="f94c6-113">S_OK</span></span>|<span data-ttu-id="f94c6-114">`celt`öğeler döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="f94c6-114">`celt` elements were returned.</span></span>|  
|<span data-ttu-id="f94c6-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="f94c6-115">S_FALSE</span></span>|<span data-ttu-id="f94c6-116">Daha az `celt` öğe döndürüldü, bu, numaralandırmanın tamamlandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f94c6-116">Fewer than `celt` elements were returned, which indicates that the enumeration is complete.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f94c6-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f94c6-117">Requirements</span></span>  
 <span data-ttu-id="f94c6-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f94c6-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f94c6-119">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="f94c6-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f94c6-120">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="f94c6-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f94c6-121">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f94c6-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f94c6-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f94c6-122">See also</span></span>

- [<span data-ttu-id="f94c6-123">ICorProfilerModuleEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f94c6-123">ICorProfilerModuleEnum Interface</span></span>](icorprofilermoduleenum-interface.md)
- [<span data-ttu-id="f94c6-124">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="f94c6-124">Profiling Interfaces</span></span>](profiling-interfaces.md)
