---
title: ICLRRuntimeInfo::GetDefaultStartupFlags Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRRuntimeInfo.GetDefaultStartupFlags
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRRuntimeInfo::GetDefaultStartupFlags
helpviewer_keywords:
- ICLRRuntimeInfo::GetDefaultStartupFlags method [.NET Framework hosting]
- GetDefaultStartupFlags method [.NET Framework hosting]
ms.assetid: 35c2173e-3b0b-4b2a-950d-e0a01c6df052
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 73ad12e99a1ba98f6ea61775155cf1389118f754
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrruntimeinfogetdefaultstartupflags-method"></a><span data-ttu-id="7d4a8-102">ICLRRuntimeInfo::GetDefaultStartupFlags Metodu</span><span class="sxs-lookup"><span data-stu-id="7d4a8-102">ICLRRuntimeInfo::GetDefaultStartupFlags Method</span></span>
<span data-ttu-id="7d4a8-103">Başlangıç bayrakları ve çalışma zamanı başlatmak için kullanılan ana bilgisayar yapılandırma dosyası alır.</span><span class="sxs-lookup"><span data-stu-id="7d4a8-103">Gets the startup flags and host configuration file that will be used to start the runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d4a8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7d4a8-104">Syntax</span></span>  
  
```  
HRESULT GetDefaultStartupFlags(  
     [out]  DWORD *pdwStartupFlags,  
     [out, size_is(*pcchHostConfigFile)] LPWSTR pwzHostConfigFile,  
     [in, out]  DWORD *pcchHostConfigFile);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7d4a8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7d4a8-105">Parameters</span></span>  
 `pdwStartupFlags`  
 <span data-ttu-id="7d4a8-106">[out] Şu anda ayarlanmış konak başlangıç bayrakları gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7d4a8-106">[out] A pointer to the host startup flags that are currently set.</span></span>  
  
 `pwzHostConfigFile`  
 <span data-ttu-id="7d4a8-107">[out] Geçerli ana bilgisayar yapılandırma dosyası dizin yolu için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7d4a8-107">[out] A pointer to the directory path of the current host configuration file.</span></span>  
  
 `pcchHostConfigFile`  
 <span data-ttu-id="7d4a8-108">[içinde out] Giriş üzerinde boyutunu `pwzHostConfigFile`, arabellek taşmaları önlemek için.</span><span class="sxs-lookup"><span data-stu-id="7d4a8-108">[in, out] On input, the size of `pwzHostConfigFile`, to avoid buffer overruns.</span></span> <span data-ttu-id="7d4a8-109">Varsa `pwzHostConfigFile` olan null yöntemi gerekli boyutu döndüren `pwzHostConfigFile` öncesi ayırma.</span><span class="sxs-lookup"><span data-stu-id="7d4a8-109">If `pwzHostConfigFile` is null, the method returns the required size of `pwzHostConfigFile` for pre-allocation.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7d4a8-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="7d4a8-110">Return Value</span></span>  
 <span data-ttu-id="7d4a8-111">Bu yöntem aşağıdaki belirli HRESULT döndürür yöntemi hatayı belirtmek HRESULT hata yanı sıra.</span><span class="sxs-lookup"><span data-stu-id="7d4a8-111">This method returns the following specific HRESULT as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="7d4a8-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7d4a8-112">HRESULT</span></span>|<span data-ttu-id="7d4a8-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7d4a8-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7d4a8-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="7d4a8-114">S_OK</span></span>|<span data-ttu-id="7d4a8-115">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="7d4a8-115">The method completed successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7d4a8-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7d4a8-116">Remarks</span></span>  
 <span data-ttu-id="7d4a8-117">Bu yöntem varsayılan bayrak değeri döndürür (`STARTUP_CONCURRENT_GC` ve `NULL`), veya önceki bir çağrı tarafından sağlanan değerler [Iclrruntimeınfo::setdefaultstartupflags yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-setdefaultstartupflags-method.md), veya herhangi biri tarafından ayarlanan değerlerle `CorBind*` Bu çalışma zamanına bağlıysa yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="7d4a8-117">This method returns the default flag values (`STARTUP_CONCURRENT_GC` and `NULL`), or the values provided by a previous call to the [ICLRRuntimeInfo::SetDefaultStartupFlags method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-setdefaultstartupflags-method.md), or the values set by any of the `CorBind*` methods if they are bound to this runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d4a8-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7d4a8-118">Requirements</span></span>  
 <span data-ttu-id="7d4a8-119">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7d4a8-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d4a8-120">**Başlık:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="7d4a8-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="7d4a8-121">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="7d4a8-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7d4a8-122">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d4a8-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d4a8-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7d4a8-123">See Also</span></span>  
 [<span data-ttu-id="7d4a8-124">Iclrruntimeınfo arabirimi</span><span class="sxs-lookup"><span data-stu-id="7d4a8-124">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [<span data-ttu-id="7d4a8-125">Barındırma arabirimleri</span><span class="sxs-lookup"><span data-stu-id="7d4a8-125">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="7d4a8-126">Barındırma</span><span class="sxs-lookup"><span data-stu-id="7d4a8-126">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
