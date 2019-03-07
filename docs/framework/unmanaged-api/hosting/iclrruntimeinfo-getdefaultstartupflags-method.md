---
title: ICLRRuntimeInfo::GetDefaultStartupFlags Metodu
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.GetDefaultStartupFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::GetDefaultStartupFlags
helpviewer_keywords:
- ICLRRuntimeInfo::GetDefaultStartupFlags method [.NET Framework hosting]
- GetDefaultStartupFlags method [.NET Framework hosting]
ms.assetid: 35c2173e-3b0b-4b2a-950d-e0a01c6df052
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b7ef61c8ae1d8c2e5cf1fee80d8900a0e0e7f73b
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57493433"
---
# <a name="iclrruntimeinfogetdefaultstartupflags-method"></a><span data-ttu-id="47e09-102">ICLRRuntimeInfo::GetDefaultStartupFlags Metodu</span><span class="sxs-lookup"><span data-stu-id="47e09-102">ICLRRuntimeInfo::GetDefaultStartupFlags Method</span></span>
<span data-ttu-id="47e09-103">Başlangıç bayrakları ve çalışma zamanı'nı başlatmak için kullanılacak ana bilgisayar yapılandırma dosyası alır.</span><span class="sxs-lookup"><span data-stu-id="47e09-103">Gets the startup flags and host configuration file that will be used to start the runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47e09-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="47e09-104">Syntax</span></span>  
  
```  
HRESULT GetDefaultStartupFlags(  
     [out]  DWORD *pdwStartupFlags,  
     [out, size_is(*pcchHostConfigFile)] LPWSTR pwzHostConfigFile,  
     [in, out]  DWORD *pcchHostConfigFile);  
```  
  
## <a name="parameters"></a><span data-ttu-id="47e09-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="47e09-105">Parameters</span></span>  
 `pdwStartupFlags`  
 <span data-ttu-id="47e09-106">[out] Şu anda ayarlanmış ana başlangıç bayrakları için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="47e09-106">[out] A pointer to the host startup flags that are currently set.</span></span>  
  
 `pwzHostConfigFile`  
 <span data-ttu-id="47e09-107">[out] Dizin yolu geçerli ana bilgisayar yapılandırma dosyasının bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="47e09-107">[out] A pointer to the directory path of the current host configuration file.</span></span>  
  
 `pcchHostConfigFile`  
 <span data-ttu-id="47e09-108">[out içinde] Giriş üzerinde boyutunu `pwzHostConfigFile`, arabellek taşması önlemek için.</span><span class="sxs-lookup"><span data-stu-id="47e09-108">[in, out] On input, the size of `pwzHostConfigFile`, to avoid buffer overruns.</span></span> <span data-ttu-id="47e09-109">Varsa `pwzHostConfigFile` olduğu null yöntem gerekli boyutunu döndürür `pwzHostConfigFile` ön ayırması için.</span><span class="sxs-lookup"><span data-stu-id="47e09-109">If `pwzHostConfigFile` is null, the method returns the required size of `pwzHostConfigFile` for pre-allocation.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="47e09-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="47e09-110">Return Value</span></span>  
 <span data-ttu-id="47e09-111">Bu yöntem aşağıdaki özel HRESULT döndürür yöntemi hatayı belirtmek HRESULT hata yanı sıra.</span><span class="sxs-lookup"><span data-stu-id="47e09-111">This method returns the following specific HRESULT as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="47e09-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="47e09-112">HRESULT</span></span>|<span data-ttu-id="47e09-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="47e09-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="47e09-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="47e09-114">S_OK</span></span>|<span data-ttu-id="47e09-115">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="47e09-115">The method completed successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="47e09-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="47e09-116">Remarks</span></span>  
 <span data-ttu-id="47e09-117">Bu yöntem varsayılan bayrak değerleri döndürür (`STARTUP_CONCURRENT_GC` ve `NULL`), veya önceki bir çağrı tarafından sağlanan değerleri [Iclrruntimeınfo::setdefaultstartupflags yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-setdefaultstartupflags-method.md), veya herhangi biri tarafından ayarlanan değerlerle `CorBind*` Bu çalışma zamanına bağlıysa yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="47e09-117">This method returns the default flag values (`STARTUP_CONCURRENT_GC` and `NULL`), or the values provided by a previous call to the [ICLRRuntimeInfo::SetDefaultStartupFlags method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-setdefaultstartupflags-method.md), or the values set by any of the `CorBind*` methods if they are bound to this runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47e09-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="47e09-118">Requirements</span></span>  
 <span data-ttu-id="47e09-119">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="47e09-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="47e09-120">**Üst bilgi:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="47e09-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="47e09-121">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="47e09-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="47e09-122">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="47e09-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47e09-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="47e09-123">See also</span></span>
- [<span data-ttu-id="47e09-124">ICLRRuntimeInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="47e09-124">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="47e09-125">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="47e09-125">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="47e09-126">Barındırma</span><span class="sxs-lookup"><span data-stu-id="47e09-126">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
