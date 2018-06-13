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
ms.openlocfilehash: d7f000b6e944be7bd2e38f97e40176952cb19605
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33450638"
---
# <a name="icorprofilercallbackassemblyloadfinished-method"></a><span data-ttu-id="6f603-102">ICorProfilerCallback::AssemblyLoadFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6f603-102">ICorProfilerCallback::AssemblyLoadFinished Method</span></span>
<span data-ttu-id="6f603-103">Profil Oluşturucu bütünleştirilmiş yüklenmesini tamamladı bildirir.</span><span class="sxs-lookup"><span data-stu-id="6f603-103">Notifies the profiler that an assembly has finished loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f603-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6f603-104">Syntax</span></span>  
  
```  
HRESULT AssemblyLoadFinished(  
    [in] AssemblyID assemblyId,  
    [in] HRESULT    hrStatus);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6f603-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6f603-105">Parameters</span></span>  
 `assemblyId`  
 <span data-ttu-id="6f603-106">[in] Yüklenen derlemeyi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6f603-106">[in] Identifies the assembly that was loaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="6f603-107">[in] Derleme yüklemesi başarıyla tamamlandı olup olmadığını belirten bir HRESULT.</span><span class="sxs-lookup"><span data-stu-id="6f603-107">[in] An HRESULT that indicates whether the assembly finished loading successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6f603-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6f603-108">Remarks</span></span>  
 <span data-ttu-id="6f603-109">Değeri `assemblyId` kadar bilgi isteği için geçerli değil `AssemblyLoadFinished` yöntemi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="6f603-109">The value of `assemblyId` is not valid for an information request until the `AssemblyLoadFinished` method is called.</span></span>  
  
 <span data-ttu-id="6f603-110">Derleme yükleme bazı bölümleri sonra devam edebilir `AssemblyLoadFinished` geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="6f603-110">Some parts of loading the assembly might continue after the `AssemblyLoadFinished` callback.</span></span> <span data-ttu-id="6f603-111">HRESULT hata içinde `hrStatus` hata gösterir.</span><span class="sxs-lookup"><span data-stu-id="6f603-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="6f603-112">Ancak, bir başarı HRESULT içinde `hrStatus` yalnızca ilk derlemesi yüklenirken parçası başarılı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="6f603-112">However, a success HRESULT in `hrStatus` indicates only that the first part of loading the assembly has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f603-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6f603-113">Requirements</span></span>  
 <span data-ttu-id="6f603-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6f603-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f603-115">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6f603-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6f603-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6f603-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6f603-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f603-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f603-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6f603-118">See Also</span></span>  
 [<span data-ttu-id="6f603-119">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6f603-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
