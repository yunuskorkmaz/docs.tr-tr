---
title: "ICLRRuntimeInfo::IsLoadable Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRRuntimeInfo.IsLoadable
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRRuntimeInfo::IsLoadable
helpviewer_keywords:
- IsLoadable method [.NET Framework hosting]
- ICLRRuntimeInfo::IsLoadable method [.NET Framework hosting]
ms.assetid: 205ca53b-e78e-49b2-9a46-2a7823e96b8c
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ada33942af97f476de25c2ea3243818808e2dc9d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrruntimeinfoisloadable-method"></a><span data-ttu-id="fa930-102">ICLRRuntimeInfo::IsLoadable Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fa930-102">ICLRRuntimeInfo::IsLoadable Method</span></span>
<span data-ttu-id="fa930-103">Geçerli işlemine dikkate alarak bu arabirimle ilişkili çalışma zamanının yüklü olup olmadığını gösterir işlemine zaten yüklenmiş diğer çalışma zamanları.</span><span class="sxs-lookup"><span data-stu-id="fa930-103">Indicates whether the runtime associated with this interface can be loaded into the current process, taking into account other runtimes that might already be loaded into the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa930-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fa930-104">Syntax</span></span>  
  
```  
HRESULT IsLoadable(  
        [out, retval] BOOL *pbLoadable);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fa930-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fa930-105">Parameters</span></span>  
 `pbLoadable`  
 <span data-ttu-id="fa930-106">[out] `true` bu çalışma zamanı, geçerli işlemin içine yüklenen Aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="fa930-106">[out] `true` if this runtime could be loaded into the current process; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fa930-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="fa930-107">Return Value</span></span>  
 <span data-ttu-id="fa930-108">Bu yöntem aşağıdaki belirli HRESULTs yanı sıra HRESULT yöntem hatası olduğunu gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="fa930-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="fa930-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fa930-109">HRESULT</span></span>|<span data-ttu-id="fa930-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fa930-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fa930-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="fa930-111">S_OK</span></span>|<span data-ttu-id="fa930-112">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="fa930-112">The method completed successfully.</span></span>|  
|<span data-ttu-id="fa930-113">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="fa930-113">E_POINTER</span></span>|<span data-ttu-id="fa930-114">`pbLoadable`null şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="fa930-114">`pbLoadable` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fa930-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fa930-115">Remarks</span></span>  
 <span data-ttu-id="fa930-116">Başka bir çalışma zamanı işlemine zaten yüklü ve bu arabirimle ilişkili çalışma zamanı işlem içi yan yana yürütme için yüklenebilir `pbLoadable` döndürür `true`.</span><span class="sxs-lookup"><span data-stu-id="fa930-116">If another runtime is already loaded into the process and the runtime associated with this interface can be loaded for in-process side-by-side execution, `pbLoadable` returns `true`.</span></span> <span data-ttu-id="fa930-117">İki çalışma zamanları yan yana işlemdeki, çalıştırırsanız `pbLoadable` döndürür `false`.</span><span class="sxs-lookup"><span data-stu-id="fa930-117">If the two runtimes cannot run side-by-side in-process, `pbLoadable` returns `false`.</span></span> <span data-ttu-id="fa930-118">Örneğin, ortak dil çalışma zamanı (CLR) sürüm 4-yana CLR Version 2.0 sürümü ile aynı işlemde veya CLR sürüm 1.1 çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fa930-118">For example, the common language runtime (CLR) version 4 can run side-by-side in the same process with CLR version 2.0 or CLR version 1.1.</span></span> <span data-ttu-id="fa930-119">Ancak, CLR sürüm 1.1 ve CLR Version 2.0 sürümü yan yana işlemdeki çalıştırılamaz.</span><span class="sxs-lookup"><span data-stu-id="fa930-119">However, CLR version 1.1 and CLR version 2.0 cannot run side-by-side in-process.</span></span>  
  
 <span data-ttu-id="fa930-120">Hiç çalışma zamanları işlem içine yüklenmiş ise, bu yöntem her zaman döndürür `true`.</span><span class="sxs-lookup"><span data-stu-id="fa930-120">If no runtimes are loaded into the process, this method always returns `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fa930-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fa930-121">Requirements</span></span>  
 <span data-ttu-id="fa930-122">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fa930-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fa930-123">**Başlık:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="fa930-123">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="fa930-124">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="fa930-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fa930-125">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fa930-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa930-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fa930-126">See Also</span></span>  
 [<span data-ttu-id="fa930-127">Iclrruntimeınfo arabirimi</span><span class="sxs-lookup"><span data-stu-id="fa930-127">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [<span data-ttu-id="fa930-128">Barındırma arabirimleri</span><span class="sxs-lookup"><span data-stu-id="fa930-128">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="fa930-129">Barındırma</span><span class="sxs-lookup"><span data-stu-id="fa930-129">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
