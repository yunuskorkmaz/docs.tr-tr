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
ms.workload: dotnet
ms.openlocfilehash: 8b278a791c7e5418322a80bc6478f75791a35af8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrruntimeinfogetdefaultstartupflags-method"></a><span data-ttu-id="21bae-102">ICLRRuntimeInfo::GetDefaultStartupFlags Metodu</span><span class="sxs-lookup"><span data-stu-id="21bae-102">ICLRRuntimeInfo::GetDefaultStartupFlags Method</span></span>
<span data-ttu-id="21bae-103">Başlangıç bayrakları ve çalışma zamanı başlatmak için kullanılan ana bilgisayar yapılandırma dosyası alır.</span><span class="sxs-lookup"><span data-stu-id="21bae-103">Gets the startup flags and host configuration file that will be used to start the runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21bae-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="21bae-104">Syntax</span></span>  
  
```  
HRESULT GetDefaultStartupFlags(  
     [out]  DWORD *pdwStartupFlags,  
     [out, size_is(*pcchHostConfigFile)] LPWSTR pwzHostConfigFile,  
     [in, out]  DWORD *pcchHostConfigFile);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="21bae-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="21bae-105">Parameters</span></span>  
 `pdwStartupFlags`  
 <span data-ttu-id="21bae-106">[out] Şu anda ayarlanmış konak başlangıç bayrakları gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="21bae-106">[out] A pointer to the host startup flags that are currently set.</span></span>  
  
 `pwzHostConfigFile`  
 <span data-ttu-id="21bae-107">[out] Geçerli ana bilgisayar yapılandırma dosyası dizin yolu için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="21bae-107">[out] A pointer to the directory path of the current host configuration file.</span></span>  
  
 `pcchHostConfigFile`  
 <span data-ttu-id="21bae-108">[içinde out] Giriş üzerinde boyutunu `pwzHostConfigFile`, arabellek taşmaları önlemek için.</span><span class="sxs-lookup"><span data-stu-id="21bae-108">[in, out] On input, the size of `pwzHostConfigFile`, to avoid buffer overruns.</span></span> <span data-ttu-id="21bae-109">Varsa `pwzHostConfigFile` olan null yöntemi gerekli boyutu döndüren `pwzHostConfigFile` öncesi ayırma.</span><span class="sxs-lookup"><span data-stu-id="21bae-109">If `pwzHostConfigFile` is null, the method returns the required size of `pwzHostConfigFile` for pre-allocation.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="21bae-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="21bae-110">Return Value</span></span>  
 <span data-ttu-id="21bae-111">Bu yöntem aşağıdaki belirli HRESULT döndürür yöntemi hatayı belirtmek HRESULT hata yanı sıra.</span><span class="sxs-lookup"><span data-stu-id="21bae-111">This method returns the following specific HRESULT as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="21bae-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="21bae-112">HRESULT</span></span>|<span data-ttu-id="21bae-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="21bae-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="21bae-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="21bae-114">S_OK</span></span>|<span data-ttu-id="21bae-115">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="21bae-115">The method completed successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="21bae-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="21bae-116">Remarks</span></span>  
 <span data-ttu-id="21bae-117">Bu yöntem varsayılan bayrak değeri döndürür (`STARTUP_CONCURRENT_GC` ve `NULL`), veya önceki bir çağrı tarafından sağlanan değerler [Iclrruntimeınfo::setdefaultstartupflags yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-setdefaultstartupflags-method.md), veya herhangi biri tarafından ayarlanan değerlerle `CorBind*` Bu çalışma zamanına bağlıysa yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="21bae-117">This method returns the default flag values (`STARTUP_CONCURRENT_GC` and `NULL`), or the values provided by a previous call to the [ICLRRuntimeInfo::SetDefaultStartupFlags method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-setdefaultstartupflags-method.md), or the values set by any of the `CorBind*` methods if they are bound to this runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21bae-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="21bae-118">Requirements</span></span>  
 <span data-ttu-id="21bae-119">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21bae-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21bae-120">**Başlık:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="21bae-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="21bae-121">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="21bae-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="21bae-122">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21bae-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21bae-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="21bae-123">See Also</span></span>  
 [<span data-ttu-id="21bae-124">ICLRRuntimeInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="21bae-124">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [<span data-ttu-id="21bae-125">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="21bae-125">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="21bae-126">Barındırma</span><span class="sxs-lookup"><span data-stu-id="21bae-126">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
