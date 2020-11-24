---
title: ICorProfilerFunctionEnum::Next Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionEnum.Next Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionEnum::Next
helpviewer_keywords:
- ICorProfilerFunctionEnum::Next method [.NET Framework profiling]
- Next method, ICorProfilerFunctionEnum interface [.NET Framework profiling]
ms.assetid: 5ed4aa83-ce56-4b9f-9237-5da7587787fe
topic_type:
- apiref
ms.openlocfilehash: 76e0fe011769217f3cecb40c8d2ba83904b26706
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95669240"
---
# <a name="icorprofilerfunctionenumnext-method"></a><span data-ttu-id="e34a8-102">ICorProfilerFunctionEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e34a8-102">ICorProfilerFunctionEnum::Next Method</span></span>

<span data-ttu-id="e34a8-103">Numaralandırıcının dizideki geçerli konumundan başlayarak sıralı bir işlevler koleksiyonundan belirtilen sayıda bitişik işlevi alır.</span><span class="sxs-lookup"><span data-stu-id="e34a8-103">Gets the specified number of contiguous functions from a sequential collection of functions, starting at the enumerator's current position in the sequence.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e34a8-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="e34a8-104">Syntax</span></span>  
  
```cpp  
HRESULT Next([in]  ULONG      celt,  
             [out, size_is(celt), length_is(*pceltFetched)]  
                    COR_PRF_FUNCTION ids[],  
             [out] ULONG *   pceltFetched);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e34a8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e34a8-105">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="e34a8-106">'ndaki Alınacak işlevlerin sayısı.</span><span class="sxs-lookup"><span data-stu-id="e34a8-106">[in] The number of functions to retrieve.</span></span>  
  
 `ids`  
 <span data-ttu-id="e34a8-107">dışı `COR_PRF_FUNCTION` Her biri alınan bir işlevi temsil eden bir değer dizisi.</span><span class="sxs-lookup"><span data-stu-id="e34a8-107">[out] An array of `COR_PRF_FUNCTION` values, each of which represents a retrieved function.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="e34a8-108">dışı Aslında dizide döndürülen işlev sayısına yönelik bir işaretçi `ids` .</span><span class="sxs-lookup"><span data-stu-id="e34a8-108">[out] A pointer to the number of functions actually returned in the `ids` array.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e34a8-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e34a8-109">Return Value</span></span>  

 <span data-ttu-id="e34a8-110">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="e34a8-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="e34a8-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e34a8-111">HRESULT</span></span>|<span data-ttu-id="e34a8-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e34a8-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e34a8-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="e34a8-113">S_OK</span></span>|<span data-ttu-id="e34a8-114">`celt` öğeler döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="e34a8-114">`celt` elements were returned.</span></span>|  
|<span data-ttu-id="e34a8-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="e34a8-115">S_FALSE</span></span>|<span data-ttu-id="e34a8-116">Daha az `celt` öğe döndürüldü, bu, numaralandırmanın tamamlandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e34a8-116">Fewer than `celt` elements were returned, which indicates that the enumeration is complete.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e34a8-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e34a8-117">Requirements</span></span>  

 <span data-ttu-id="e34a8-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e34a8-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e34a8-119">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="e34a8-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e34a8-120">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e34a8-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e34a8-121">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e34a8-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e34a8-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e34a8-122">See also</span></span>

- [<span data-ttu-id="e34a8-123">ICorProfilerFunctionEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e34a8-123">ICorProfilerFunctionEnum Interface</span></span>](icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="e34a8-124">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e34a8-124">Profiling Interfaces</span></span>](profiling-interfaces.md)
