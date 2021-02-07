---
description: ': ICorProfilerFunctionEnum:: Next yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: ff525cfa4cc1ea1dee63b8bbd2e37eaf89fc3e74
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99737525"
---
# <a name="icorprofilerfunctionenumnext-method"></a><span data-ttu-id="d68b6-103">ICorProfilerFunctionEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d68b6-103">ICorProfilerFunctionEnum::Next Method</span></span>

<span data-ttu-id="d68b6-104">Numaralandırıcının dizideki geçerli konumundan başlayarak sıralı bir işlevler koleksiyonundan belirtilen sayıda bitişik işlevi alır.</span><span class="sxs-lookup"><span data-stu-id="d68b6-104">Gets the specified number of contiguous functions from a sequential collection of functions, starting at the enumerator's current position in the sequence.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d68b6-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d68b6-105">Syntax</span></span>  
  
```cpp  
HRESULT Next([in]  ULONG      celt,  
             [out, size_is(celt), length_is(*pceltFetched)]  
                    COR_PRF_FUNCTION ids[],  
             [out] ULONG *   pceltFetched);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d68b6-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d68b6-106">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="d68b6-107">'ndaki Alınacak işlevlerin sayısı.</span><span class="sxs-lookup"><span data-stu-id="d68b6-107">[in] The number of functions to retrieve.</span></span>  
  
 `ids`  
 <span data-ttu-id="d68b6-108">dışı `COR_PRF_FUNCTION` Her biri alınan bir işlevi temsil eden bir değer dizisi.</span><span class="sxs-lookup"><span data-stu-id="d68b6-108">[out] An array of `COR_PRF_FUNCTION` values, each of which represents a retrieved function.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="d68b6-109">dışı Aslında dizide döndürülen işlev sayısına yönelik bir işaretçi `ids` .</span><span class="sxs-lookup"><span data-stu-id="d68b6-109">[out] A pointer to the number of functions actually returned in the `ids` array.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d68b6-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d68b6-110">Return Value</span></span>  

 <span data-ttu-id="d68b6-111">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="d68b6-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="d68b6-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d68b6-112">HRESULT</span></span>|<span data-ttu-id="d68b6-113">Description</span><span class="sxs-lookup"><span data-stu-id="d68b6-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d68b6-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="d68b6-114">S_OK</span></span>|<span data-ttu-id="d68b6-115">`celt` öğeler döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="d68b6-115">`celt` elements were returned.</span></span>|  
|<span data-ttu-id="d68b6-116">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="d68b6-116">S_FALSE</span></span>|<span data-ttu-id="d68b6-117">Daha az `celt` öğe döndürüldü, bu, numaralandırmanın tamamlandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d68b6-117">Fewer than `celt` elements were returned, which indicates that the enumeration is complete.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d68b6-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d68b6-118">Requirements</span></span>  

 <span data-ttu-id="d68b6-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d68b6-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d68b6-120">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="d68b6-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d68b6-121">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d68b6-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d68b6-122">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d68b6-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d68b6-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d68b6-123">See also</span></span>

- [<span data-ttu-id="d68b6-124">ICorProfilerFunctionEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d68b6-124">ICorProfilerFunctionEnum Interface</span></span>](icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="d68b6-125">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d68b6-125">Profiling Interfaces</span></span>](profiling-interfaces.md)
