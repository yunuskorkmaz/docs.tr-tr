---
title: ICLRRuntimeInfo::IsLoadable Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.IsLoadable
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::IsLoadable
helpviewer_keywords:
- IsLoadable method [.NET Framework hosting]
- ICLRRuntimeInfo::IsLoadable method [.NET Framework hosting]
ms.assetid: 205ca53b-e78e-49b2-9a46-2a7823e96b8c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e60c3b06453e0f447249bddf5d4da5c240576577
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33432966"
---
# <a name="iclrruntimeinfoisloadable-method"></a><span data-ttu-id="77b25-102">ICLRRuntimeInfo::IsLoadable Yöntemi</span><span class="sxs-lookup"><span data-stu-id="77b25-102">ICLRRuntimeInfo::IsLoadable Method</span></span>
<span data-ttu-id="77b25-103">Geçerli işlemine dikkate alarak bu arabirimle ilişkili çalışma zamanının yüklü olup olmadığını gösterir işlemine zaten yüklenmiş diğer çalışma zamanları.</span><span class="sxs-lookup"><span data-stu-id="77b25-103">Indicates whether the runtime associated with this interface can be loaded into the current process, taking into account other runtimes that might already be loaded into the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77b25-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="77b25-104">Syntax</span></span>  
  
```  
HRESULT IsLoadable(  
        [out, retval] BOOL *pbLoadable);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="77b25-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="77b25-105">Parameters</span></span>  
 `pbLoadable`  
 <span data-ttu-id="77b25-106">[out] `true` bu çalışma zamanı, geçerli işlemin içine yüklenen Aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="77b25-106">[out] `true` if this runtime could be loaded into the current process; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="77b25-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="77b25-107">Return Value</span></span>  
 <span data-ttu-id="77b25-108">Bu yöntem aşağıdaki belirli HRESULTs yanı sıra HRESULT yöntem hatası olduğunu gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="77b25-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="77b25-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="77b25-109">HRESULT</span></span>|<span data-ttu-id="77b25-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="77b25-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="77b25-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="77b25-111">S_OK</span></span>|<span data-ttu-id="77b25-112">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="77b25-112">The method completed successfully.</span></span>|  
|<span data-ttu-id="77b25-113">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="77b25-113">E_POINTER</span></span>|<span data-ttu-id="77b25-114">`pbLoadable` null şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="77b25-114">`pbLoadable` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="77b25-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="77b25-115">Remarks</span></span>  
 <span data-ttu-id="77b25-116">Başka bir çalışma zamanı işlemine zaten yüklü ve bu arabirimle ilişkili çalışma zamanı işlem içi yan yana yürütme için yüklenebilir `pbLoadable` döndürür `true`.</span><span class="sxs-lookup"><span data-stu-id="77b25-116">If another runtime is already loaded into the process and the runtime associated with this interface can be loaded for in-process side-by-side execution, `pbLoadable` returns `true`.</span></span> <span data-ttu-id="77b25-117">İki çalışma zamanları yan yana işlemdeki, çalıştırırsanız `pbLoadable` döndürür `false`.</span><span class="sxs-lookup"><span data-stu-id="77b25-117">If the two runtimes cannot run side-by-side in-process, `pbLoadable` returns `false`.</span></span> <span data-ttu-id="77b25-118">Örneğin, ortak dil çalışma zamanı (CLR) sürüm 4-yana CLR Version 2.0 sürümü ile aynı işlemde veya CLR sürüm 1.1 çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="77b25-118">For example, the common language runtime (CLR) version 4 can run side-by-side in the same process with CLR version 2.0 or CLR version 1.1.</span></span> <span data-ttu-id="77b25-119">Ancak, CLR sürüm 1.1 ve CLR Version 2.0 sürümü yan yana işlemdeki çalıştırılamaz.</span><span class="sxs-lookup"><span data-stu-id="77b25-119">However, CLR version 1.1 and CLR version 2.0 cannot run side-by-side in-process.</span></span>  
  
 <span data-ttu-id="77b25-120">Hiç çalışma zamanları işlem içine yüklenmiş ise, bu yöntem her zaman döndürür `true`.</span><span class="sxs-lookup"><span data-stu-id="77b25-120">If no runtimes are loaded into the process, this method always returns `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77b25-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="77b25-121">Requirements</span></span>  
 <span data-ttu-id="77b25-122">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="77b25-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77b25-123">**Başlık:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="77b25-123">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="77b25-124">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="77b25-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="77b25-125">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77b25-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77b25-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="77b25-126">See Also</span></span>  
 [<span data-ttu-id="77b25-127">ICLRRuntimeInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="77b25-127">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [<span data-ttu-id="77b25-128">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="77b25-128">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="77b25-129">Barındırma</span><span class="sxs-lookup"><span data-stu-id="77b25-129">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
