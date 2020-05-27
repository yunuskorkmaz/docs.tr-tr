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
ms.openlocfilehash: a1cd169fc4be5b1dd3ab1a83f4ad143ba2e2442b
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007370"
---
# <a name="iclrruntimeinfoisloadable-method"></a><span data-ttu-id="c7277-102">ICLRRuntimeInfo::IsLoadable Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c7277-102">ICLRRuntimeInfo::IsLoadable Method</span></span>
<span data-ttu-id="c7277-103">Bu arabirimle ilişkili çalışma zamanının geçerli işleme yüklenip yüklenmediğini, işleme daha önce yüklenmiş olabilecek diğer çalışma zamanlarını hesaba ayırarak gösterir.</span><span class="sxs-lookup"><span data-stu-id="c7277-103">Indicates whether the runtime associated with this interface can be loaded into the current process, taking into account other runtimes that might already be loaded into the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7277-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="c7277-104">Syntax</span></span>  
  
```cpp  
HRESULT IsLoadable(  
        [out, retval] BOOL *pbLoadable);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c7277-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c7277-105">Parameters</span></span>  
 `pbLoadable`  
 <span data-ttu-id="c7277-106">[out] `true` Bu çalışma zamanı geçerli işleme yüklenebiliyorsanız, Aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="c7277-106">[out] `true` if this runtime could be loaded into the current process; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c7277-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c7277-107">Return Value</span></span>  
 <span data-ttu-id="c7277-108">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="c7277-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="c7277-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c7277-109">HRESULT</span></span>|<span data-ttu-id="c7277-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c7277-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c7277-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="c7277-111">S_OK</span></span>|<span data-ttu-id="c7277-112">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="c7277-112">The method completed successfully.</span></span>|  
|<span data-ttu-id="c7277-113">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="c7277-113">E_POINTER</span></span>|<span data-ttu-id="c7277-114">`pbLoadable`null.</span><span class="sxs-lookup"><span data-stu-id="c7277-114">`pbLoadable` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c7277-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c7277-115">Remarks</span></span>  
 <span data-ttu-id="c7277-116">Başka bir çalışma zamanı işleme zaten yüklenmişse ve bu arabirimle ilişkili çalışma zamanı işlem içi yan yana yürütme için yüklenebiliyorsanız, `pbLoadable` döndürür `true` .</span><span class="sxs-lookup"><span data-stu-id="c7277-116">If another runtime is already loaded into the process, and the runtime associated with this interface can be loaded for in-process side-by-side execution, `pbLoadable` returns `true`.</span></span> <span data-ttu-id="c7277-117">İki çalışma zamanı işlem içi yan yana `pbLoadable` çalıştıramsam, döndürür `false` .</span><span class="sxs-lookup"><span data-stu-id="c7277-117">If the two runtimes cannot run side-by-side in-process, `pbLoadable` returns `false`.</span></span> <span data-ttu-id="c7277-118">Örneğin, ortak dil çalışma zamanı (CLR) sürüm 4, CLR sürüm 2,0 veya CLR sürüm 1,1 ile aynı işlemde yan yana çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="c7277-118">For example, the common language runtime (CLR) version 4 can run side-by-side in the same process with CLR version 2.0 or CLR version 1.1.</span></span> <span data-ttu-id="c7277-119">Ancak, CLR sürüm 1,1 ve CLR sürüm 2,0, yan yana işlem içinde çalıştırılamaz.</span><span class="sxs-lookup"><span data-stu-id="c7277-119">However, CLR version 1.1 and CLR version 2.0 cannot run side-by-side in-process.</span></span>  
  
 <span data-ttu-id="c7277-120">İşleme hiçbir çalışma zamanı yüklü değilse, bu yöntem her zaman döndürülür `true` .</span><span class="sxs-lookup"><span data-stu-id="c7277-120">If no runtimes are loaded into the process, this method always returns `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7277-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c7277-121">Requirements</span></span>  
 <span data-ttu-id="c7277-122">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c7277-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7277-123">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="c7277-123">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="c7277-124">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="c7277-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c7277-125">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7277-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7277-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c7277-126">See also</span></span>

- [<span data-ttu-id="c7277-127">ICLRRuntimeInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c7277-127">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="c7277-128">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c7277-128">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="c7277-129">Barındırma</span><span class="sxs-lookup"><span data-stu-id="c7277-129">Hosting</span></span>](index.md)
