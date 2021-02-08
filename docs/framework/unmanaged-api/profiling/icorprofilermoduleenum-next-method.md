---
description: 'Şu konuda daha fazla bilgi edinin: ICorProfilerModuleEnum:: Next yöntemi'
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
ms.openlocfilehash: 06c9528d5468847a905e84fe38591c9b5ef3ee44
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99798998"
---
# <a name="icorprofilermoduleenumnext-method"></a><span data-ttu-id="89ede-103">ICorProfilerModuleEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="89ede-103">ICorProfilerModuleEnum::Next Method</span></span>

<span data-ttu-id="89ede-104">Numaralandırıcının dizideki geçerli konumundan başlayarak sıralı bir modül koleksiyonundan belirtilen sayıda bitişik modülü alır.</span><span class="sxs-lookup"><span data-stu-id="89ede-104">Gets the specified number of contiguous modules from a sequential collection of modules, starting at the enumerator's current position in the sequence.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89ede-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="89ede-105">Syntax</span></span>  
  
```cpp  
HRESULT Next([in]  ULONG      celt,  
             [out, size_is(celt), length_is(*pceltFetched)]  
                    ModuleID ids[],  
             [out] ULONG *   pceltFetched);  
```  
  
## <a name="parameters"></a><span data-ttu-id="89ede-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="89ede-106">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="89ede-107">'ndaki Alınacak modül sayısı.</span><span class="sxs-lookup"><span data-stu-id="89ede-107">[in] The number of modules to retrieve.</span></span>  
  
 `ids`  
 <span data-ttu-id="89ede-108">dışı `ModuleID` Her biri alınan bir modülü temsil eden bir değer dizisi.</span><span class="sxs-lookup"><span data-stu-id="89ede-108">[out] An array of `ModuleID` values, each of which represents a retrieved module.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="89ede-109">dışı Dizide gerçekten döndürülen öğe sayısına yönelik bir işaretçi `ids` .</span><span class="sxs-lookup"><span data-stu-id="89ede-109">[out] A pointer to the number of elements actually returned in the `ids` array.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="89ede-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="89ede-110">Return Value</span></span>  

 <span data-ttu-id="89ede-111">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="89ede-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="89ede-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="89ede-112">HRESULT</span></span>|<span data-ttu-id="89ede-113">Description</span><span class="sxs-lookup"><span data-stu-id="89ede-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="89ede-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="89ede-114">S_OK</span></span>|<span data-ttu-id="89ede-115">`celt` öğeler döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="89ede-115">`celt` elements were returned.</span></span>|  
|<span data-ttu-id="89ede-116">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="89ede-116">S_FALSE</span></span>|<span data-ttu-id="89ede-117">Daha az `celt` öğe döndürüldü, bu, numaralandırmanın tamamlandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="89ede-117">Fewer than `celt` elements were returned, which indicates that the enumeration is complete.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="89ede-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="89ede-118">Requirements</span></span>  

 <span data-ttu-id="89ede-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="89ede-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89ede-120">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="89ede-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="89ede-121">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="89ede-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="89ede-122">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89ede-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89ede-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="89ede-123">See also</span></span>

- [<span data-ttu-id="89ede-124">ICorProfilerModuleEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="89ede-124">ICorProfilerModuleEnum Interface</span></span>](icorprofilermoduleenum-interface.md)
- [<span data-ttu-id="89ede-125">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="89ede-125">Profiling Interfaces</span></span>](profiling-interfaces.md)
