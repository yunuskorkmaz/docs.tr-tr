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
ms.openlocfilehash: 9339bb974c261e62502c760dfaf45651573cbe1a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136368"
---
# <a name="iclrruntimeinfoisloadable-method"></a><span data-ttu-id="d41a9-102">ICLRRuntimeInfo::IsLoadable Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d41a9-102">ICLRRuntimeInfo::IsLoadable Method</span></span>
<span data-ttu-id="d41a9-103">Bu arabirimle ilişkili çalışma zamanının geçerli işleme yüklenip yüklenmediğini, işleme daha önce yüklenmiş olabilecek diğer çalışma zamanlarını hesaba ayırarak gösterir.</span><span class="sxs-lookup"><span data-stu-id="d41a9-103">Indicates whether the runtime associated with this interface can be loaded into the current process, taking into account other runtimes that might already be loaded into the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d41a9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d41a9-104">Syntax</span></span>  
  
```cpp  
HRESULT IsLoadable(  
        [out, retval] BOOL *pbLoadable);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d41a9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d41a9-105">Parameters</span></span>  
 `pbLoadable`  
 <span data-ttu-id="d41a9-106">[out] Bu çalışma zamanı geçerli işleme yüklenebiliyorsanız `true`; Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="d41a9-106">[out] `true` if this runtime could be loaded into the current process; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d41a9-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d41a9-107">Return Value</span></span>  
 <span data-ttu-id="d41a9-108">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="d41a9-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="d41a9-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d41a9-109">HRESULT</span></span>|<span data-ttu-id="d41a9-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d41a9-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d41a9-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="d41a9-111">S_OK</span></span>|<span data-ttu-id="d41a9-112">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="d41a9-112">The method completed successfully.</span></span>|  
|<span data-ttu-id="d41a9-113">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="d41a9-113">E_POINTER</span></span>|<span data-ttu-id="d41a9-114">`pbLoadable` null.</span><span class="sxs-lookup"><span data-stu-id="d41a9-114">`pbLoadable` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d41a9-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d41a9-115">Remarks</span></span>  
 <span data-ttu-id="d41a9-116">Başka bir çalışma zamanı işleme zaten yüklenmişse ve bu arabirimle ilişkili çalışma zamanı işlem içi yan yana yürütme için yüklenebiliyorsanız, `pbLoadable` `true`döndürür.</span><span class="sxs-lookup"><span data-stu-id="d41a9-116">If another runtime is already loaded into the process and the runtime associated with this interface can be loaded for in-process side-by-side execution, `pbLoadable` returns `true`.</span></span> <span data-ttu-id="d41a9-117">İki çalışma zamanı işlem içi yan yana çalıştırılamaz `pbLoadable` `false`döndürür.</span><span class="sxs-lookup"><span data-stu-id="d41a9-117">If the two runtimes cannot run side-by-side in-process, `pbLoadable` returns `false`.</span></span> <span data-ttu-id="d41a9-118">Örneğin, ortak dil çalışma zamanı (CLR) sürüm 4, CLR sürüm 2,0 veya CLR sürüm 1,1 ile aynı işlemde yan yana çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="d41a9-118">For example, the common language runtime (CLR) version 4 can run side-by-side in the same process with CLR version 2.0 or CLR version 1.1.</span></span> <span data-ttu-id="d41a9-119">Ancak, CLR sürüm 1,1 ve CLR sürüm 2,0, yan yana işlem içinde çalıştırılamaz.</span><span class="sxs-lookup"><span data-stu-id="d41a9-119">However, CLR version 1.1 and CLR version 2.0 cannot run side-by-side in-process.</span></span>  
  
 <span data-ttu-id="d41a9-120">İşleme hiçbir çalışma zamanı yüklenmediyse, bu yöntem her zaman `true`döndürür.</span><span class="sxs-lookup"><span data-stu-id="d41a9-120">If no runtimes are loaded into the process, this method always returns `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d41a9-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d41a9-121">Requirements</span></span>  
 <span data-ttu-id="d41a9-122">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d41a9-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d41a9-123">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="d41a9-123">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="d41a9-124">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="d41a9-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d41a9-125">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d41a9-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d41a9-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d41a9-126">See also</span></span>

- [<span data-ttu-id="d41a9-127">ICLRRuntimeInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d41a9-127">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="d41a9-128">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d41a9-128">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="d41a9-129">Barındırma</span><span class="sxs-lookup"><span data-stu-id="d41a9-129">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
