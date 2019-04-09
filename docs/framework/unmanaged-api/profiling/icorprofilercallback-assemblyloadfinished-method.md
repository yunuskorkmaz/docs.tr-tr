---
title: ICorProfilerCallback::AssemblyLoadFinished Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AssemblyLoadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AssemblyLoadFinished
helpviewer_keywords:
- ICorProfilerCallback::AssemblyLoadFinished method [.NET Framework profiling]
- AssemblyLoadFinished method [.NET Framework profiling]
ms.assetid: 86d98f39-52e6-4c61-a625-9760f695ff12
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e32af790c755f65b5435455c326d011656da19ed
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59198380"
---
# <a name="icorprofilercallbackassemblyloadfinished-method"></a><span data-ttu-id="c66e1-102">ICorProfilerCallback::AssemblyLoadFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c66e1-102">ICorProfilerCallback::AssemblyLoadFinished Method</span></span>
<span data-ttu-id="c66e1-103">Profil Oluşturucu bir bütünleştirilmiş kod yükleme işleminin tamamlandığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="c66e1-103">Notifies the profiler that an assembly has finished loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c66e1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c66e1-104">Syntax</span></span>  
  
```  
HRESULT AssemblyLoadFinished(  
    [in] AssemblyID assemblyId,  
    [in] HRESULT    hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c66e1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c66e1-105">Parameters</span></span>  
 `assemblyId`  
 <span data-ttu-id="c66e1-106">[in] Yüklenen derleme tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c66e1-106">[in] Identifies the assembly that was loaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="c66e1-107">[in] Derleme yükleme başarıyla tamamlandı olup olmadığını gösteren bir HRESULT.</span><span class="sxs-lookup"><span data-stu-id="c66e1-107">[in] An HRESULT that indicates whether the assembly finished loading successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c66e1-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c66e1-108">Remarks</span></span>  
 <span data-ttu-id="c66e1-109">Değerini `assemblyId` kadar bir bilgi isteği için geçerli değil `AssemblyLoadFinished` yöntemi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="c66e1-109">The value of `assemblyId` is not valid for an information request until the `AssemblyLoadFinished` method is called.</span></span>  
  
 <span data-ttu-id="c66e1-110">Derleme yükleme bazı bölümleri sonra devam edebilir `AssemblyLoadFinished` geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="c66e1-110">Some parts of loading the assembly might continue after the `AssemblyLoadFinished` callback.</span></span> <span data-ttu-id="c66e1-111">Bir hata HRESULT içinde `hrStatus` hata gösterir.</span><span class="sxs-lookup"><span data-stu-id="c66e1-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="c66e1-112">Ancak, bir başarı HRESULT içinde `hrStatus` yalnızca ilk bölümü bütünleştirilmiş kod yükleme işleminin başarılı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="c66e1-112">However, a success HRESULT in `hrStatus` indicates only that the first part of loading the assembly has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c66e1-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c66e1-113">Requirements</span></span>  
 <span data-ttu-id="c66e1-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c66e1-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c66e1-115">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c66e1-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c66e1-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c66e1-116">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="c66e1-117">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="c66e1-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c66e1-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c66e1-118">See also</span></span>

- [<span data-ttu-id="c66e1-119">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c66e1-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
