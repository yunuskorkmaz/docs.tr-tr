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
ms.openlocfilehash: 586882ad7577c367576da9b32e6d3b8fe2f806c3
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57501220"
---
# <a name="iclrruntimeinfoisloadable-method"></a><span data-ttu-id="e6430-102">ICLRRuntimeInfo::IsLoadable Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e6430-102">ICLRRuntimeInfo::IsLoadable Method</span></span>
<span data-ttu-id="e6430-103">Bu arabirimi ile ilişkili çalışma zamanı dikkate alarak, geçerli işlem içine yüklenmiş olup olmadığını gösteren zaten işlem içine yüklenmiş diğer çalışma zamanları.</span><span class="sxs-lookup"><span data-stu-id="e6430-103">Indicates whether the runtime associated with this interface can be loaded into the current process, taking into account other runtimes that might already be loaded into the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6430-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e6430-104">Syntax</span></span>  
  
```  
HRESULT IsLoadable(  
        [out, retval] BOOL *pbLoadable);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e6430-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e6430-105">Parameters</span></span>  
 `pbLoadable`  
 <span data-ttu-id="e6430-106">[out] `true` bu çalışma zamanı olabilir, geçerli işlem içine yüklenmiş; Aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="e6430-106">[out] `true` if this runtime could be loaded into the current process; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e6430-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e6430-107">Return Value</span></span>  
 <span data-ttu-id="e6430-108">Bu yöntem aşağıdaki özel HRESULT'ları yanı sıra HRESULT döndürür yöntemi hatayı gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="e6430-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="e6430-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e6430-109">HRESULT</span></span>|<span data-ttu-id="e6430-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e6430-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e6430-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="e6430-111">S_OK</span></span>|<span data-ttu-id="e6430-112">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="e6430-112">The method completed successfully.</span></span>|  
|<span data-ttu-id="e6430-113">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="e6430-113">E_POINTER</span></span>|<span data-ttu-id="e6430-114">`pbLoadable` NULL olur.</span><span class="sxs-lookup"><span data-stu-id="e6430-114">`pbLoadable` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e6430-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e6430-115">Remarks</span></span>  
 <span data-ttu-id="e6430-116">Başka bir çalışma zamanı zaten işlem içine yüklenmiş ve bu arabirimi ile ilişkili çalışma zamanı işlem içi yan yana yürütme için yüklenebilen `pbLoadable` döndürür `true`.</span><span class="sxs-lookup"><span data-stu-id="e6430-116">If another runtime is already loaded into the process and the runtime associated with this interface can be loaded for in-process side-by-side execution, `pbLoadable` returns `true`.</span></span> <span data-ttu-id="e6430-117">İki çalışma zamanları yan yana işlem içinde çalıştırırsanız `pbLoadable` döndürür `false`.</span><span class="sxs-lookup"><span data-stu-id="e6430-117">If the two runtimes cannot run side-by-side in-process, `pbLoadable` returns `false`.</span></span> <span data-ttu-id="e6430-118">Örneğin, ortak dil çalışma zamanı (CLR) sürüm 4 yan yana CLR Version 2.0 sürümü ile aynı işlemde veya CLR sürüm 1.1 çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e6430-118">For example, the common language runtime (CLR) version 4 can run side-by-side in the same process with CLR version 2.0 or CLR version 1.1.</span></span> <span data-ttu-id="e6430-119">Ancak, CLR sürüm 1.1 ve CLR Version 2.0 sürümü yan yana işlemde çalıştırılamaz.</span><span class="sxs-lookup"><span data-stu-id="e6430-119">However, CLR version 1.1 and CLR version 2.0 cannot run side-by-side in-process.</span></span>  
  
 <span data-ttu-id="e6430-120">Çalışma zamanı olmayan işlem içine yüklenmiş ise, bu yöntem her zaman döndürür `true`.</span><span class="sxs-lookup"><span data-stu-id="e6430-120">If no runtimes are loaded into the process, this method always returns `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e6430-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e6430-121">Requirements</span></span>  
 <span data-ttu-id="e6430-122">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e6430-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6430-123">**Üst bilgi:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="e6430-123">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="e6430-124">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="e6430-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e6430-125">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e6430-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6430-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e6430-126">See also</span></span>
- [<span data-ttu-id="e6430-127">ICLRRuntimeInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e6430-127">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="e6430-128">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e6430-128">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="e6430-129">Barındırma</span><span class="sxs-lookup"><span data-stu-id="e6430-129">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
