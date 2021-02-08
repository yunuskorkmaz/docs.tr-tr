---
description: ': ICLRRuntimeInfo:: ısyüklenebilir yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: cf63212350bfbd18e2a312add72818b163c32d0c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789794"
---
# <a name="iclrruntimeinfoisloadable-method"></a><span data-ttu-id="0e7f6-103">ICLRRuntimeInfo::IsLoadable Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0e7f6-103">ICLRRuntimeInfo::IsLoadable Method</span></span>

<span data-ttu-id="0e7f6-104">Bu arabirimle ilişkili çalışma zamanının geçerli işleme yüklenip yüklenmediğini, işleme daha önce yüklenmiş olabilecek diğer çalışma zamanlarını hesaba ayırarak gösterir.</span><span class="sxs-lookup"><span data-stu-id="0e7f6-104">Indicates whether the runtime associated with this interface can be loaded into the current process, taking into account other runtimes that might already be loaded into the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e7f6-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0e7f6-105">Syntax</span></span>  
  
```cpp  
HRESULT IsLoadable(  
        [out, retval] BOOL *pbLoadable);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0e7f6-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0e7f6-106">Parameters</span></span>  

 `pbLoadable`  
 <span data-ttu-id="0e7f6-107">[out] `true` Bu çalışma zamanı geçerli işleme yüklenebiliyorsanız, Aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="0e7f6-107">[out] `true` if this runtime could be loaded into the current process; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0e7f6-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="0e7f6-108">Return Value</span></span>  

 <span data-ttu-id="0e7f6-109">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="0e7f6-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="0e7f6-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0e7f6-110">HRESULT</span></span>|<span data-ttu-id="0e7f6-111">Description</span><span class="sxs-lookup"><span data-stu-id="0e7f6-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0e7f6-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="0e7f6-112">S_OK</span></span>|<span data-ttu-id="0e7f6-113">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="0e7f6-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="0e7f6-114">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="0e7f6-114">E_POINTER</span></span>|<span data-ttu-id="0e7f6-115">`pbLoadable` null.</span><span class="sxs-lookup"><span data-stu-id="0e7f6-115">`pbLoadable` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0e7f6-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0e7f6-116">Remarks</span></span>  

 <span data-ttu-id="0e7f6-117">Başka bir çalışma zamanı işleme zaten yüklenmişse ve bu arabirimle ilişkili çalışma zamanı işlem içi yan yana yürütme için yüklenebiliyorsanız, `pbLoadable` döndürür `true` .</span><span class="sxs-lookup"><span data-stu-id="0e7f6-117">If another runtime is already loaded into the process, and the runtime associated with this interface can be loaded for in-process side-by-side execution, `pbLoadable` returns `true`.</span></span> <span data-ttu-id="0e7f6-118">İki çalışma zamanı işlem içi yan yana `pbLoadable` çalıştıramsam, döndürür `false` .</span><span class="sxs-lookup"><span data-stu-id="0e7f6-118">If the two runtimes cannot run side-by-side in-process, `pbLoadable` returns `false`.</span></span> <span data-ttu-id="0e7f6-119">Örneğin, ortak dil çalışma zamanı (CLR) sürüm 4, CLR sürüm 2,0 veya CLR sürüm 1,1 ile aynı işlemde yan yana çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="0e7f6-119">For example, the common language runtime (CLR) version 4 can run side-by-side in the same process with CLR version 2.0 or CLR version 1.1.</span></span> <span data-ttu-id="0e7f6-120">Ancak, CLR sürüm 1,1 ve CLR sürüm 2,0, yan yana işlem içinde çalıştırılamaz.</span><span class="sxs-lookup"><span data-stu-id="0e7f6-120">However, CLR version 1.1 and CLR version 2.0 cannot run side-by-side in-process.</span></span>  
  
 <span data-ttu-id="0e7f6-121">İşleme hiçbir çalışma zamanı yüklü değilse, bu yöntem her zaman döndürülür `true` .</span><span class="sxs-lookup"><span data-stu-id="0e7f6-121">If no runtimes are loaded into the process, this method always returns `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e7f6-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0e7f6-122">Requirements</span></span>  

 <span data-ttu-id="0e7f6-123">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0e7f6-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e7f6-124">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="0e7f6-124">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="0e7f6-125">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="0e7f6-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0e7f6-126">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0e7f6-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e7f6-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0e7f6-127">See also</span></span>

- [<span data-ttu-id="0e7f6-128">ICLRRuntimeInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0e7f6-128">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="0e7f6-129">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="0e7f6-129">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="0e7f6-130">Hosting</span><span class="sxs-lookup"><span data-stu-id="0e7f6-130">Hosting</span></span>](index.md)
