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
ms.openlocfilehash: 546a26306a1faaeceb1337b79bd2d27970d9f5be
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33434219"
---
# <a name="iclrruntimeinfogetdefaultstartupflags-method"></a><span data-ttu-id="aa9e5-102">ICLRRuntimeInfo::GetDefaultStartupFlags Metodu</span><span class="sxs-lookup"><span data-stu-id="aa9e5-102">ICLRRuntimeInfo::GetDefaultStartupFlags Method</span></span>
<span data-ttu-id="aa9e5-103">Başlangıç bayrakları ve çalışma zamanı başlatmak için kullanılan ana bilgisayar yapılandırma dosyası alır.</span><span class="sxs-lookup"><span data-stu-id="aa9e5-103">Gets the startup flags and host configuration file that will be used to start the runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa9e5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="aa9e5-104">Syntax</span></span>  
  
```  
HRESULT GetDefaultStartupFlags(  
     [out]  DWORD *pdwStartupFlags,  
     [out, size_is(*pcchHostConfigFile)] LPWSTR pwzHostConfigFile,  
     [in, out]  DWORD *pcchHostConfigFile);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="aa9e5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="aa9e5-105">Parameters</span></span>  
 `pdwStartupFlags`  
 <span data-ttu-id="aa9e5-106">[out] Şu anda ayarlanmış konak başlangıç bayrakları gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="aa9e5-106">[out] A pointer to the host startup flags that are currently set.</span></span>  
  
 `pwzHostConfigFile`  
 <span data-ttu-id="aa9e5-107">[out] Geçerli ana bilgisayar yapılandırma dosyası dizin yolu için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="aa9e5-107">[out] A pointer to the directory path of the current host configuration file.</span></span>  
  
 `pcchHostConfigFile`  
 <span data-ttu-id="aa9e5-108">[içinde out] Giriş üzerinde boyutunu `pwzHostConfigFile`, arabellek taşmaları önlemek için.</span><span class="sxs-lookup"><span data-stu-id="aa9e5-108">[in, out] On input, the size of `pwzHostConfigFile`, to avoid buffer overruns.</span></span> <span data-ttu-id="aa9e5-109">Varsa `pwzHostConfigFile` olan null yöntemi gerekli boyutu döndüren `pwzHostConfigFile` öncesi ayırma.</span><span class="sxs-lookup"><span data-stu-id="aa9e5-109">If `pwzHostConfigFile` is null, the method returns the required size of `pwzHostConfigFile` for pre-allocation.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="aa9e5-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="aa9e5-110">Return Value</span></span>  
 <span data-ttu-id="aa9e5-111">Bu yöntem aşağıdaki belirli HRESULT döndürür yöntemi hatayı belirtmek HRESULT hata yanı sıra.</span><span class="sxs-lookup"><span data-stu-id="aa9e5-111">This method returns the following specific HRESULT as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="aa9e5-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="aa9e5-112">HRESULT</span></span>|<span data-ttu-id="aa9e5-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aa9e5-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="aa9e5-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="aa9e5-114">S_OK</span></span>|<span data-ttu-id="aa9e5-115">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="aa9e5-115">The method completed successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aa9e5-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="aa9e5-116">Remarks</span></span>  
 <span data-ttu-id="aa9e5-117">Bu yöntem varsayılan bayrak değeri döndürür (`STARTUP_CONCURRENT_GC` ve `NULL`), veya önceki bir çağrı tarafından sağlanan değerler [Iclrruntimeınfo::setdefaultstartupflags yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-setdefaultstartupflags-method.md), veya herhangi biri tarafından ayarlanan değerlerle `CorBind*` Bu çalışma zamanına bağlıysa yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="aa9e5-117">This method returns the default flag values (`STARTUP_CONCURRENT_GC` and `NULL`), or the values provided by a previous call to the [ICLRRuntimeInfo::SetDefaultStartupFlags method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-setdefaultstartupflags-method.md), or the values set by any of the `CorBind*` methods if they are bound to this runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aa9e5-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="aa9e5-118">Requirements</span></span>  
 <span data-ttu-id="aa9e5-119">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aa9e5-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aa9e5-120">**Başlık:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="aa9e5-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="aa9e5-121">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="aa9e5-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="aa9e5-122">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aa9e5-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa9e5-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="aa9e5-123">See Also</span></span>  
 [<span data-ttu-id="aa9e5-124">ICLRRuntimeInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="aa9e5-124">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [<span data-ttu-id="aa9e5-125">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="aa9e5-125">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="aa9e5-126">Barındırma</span><span class="sxs-lookup"><span data-stu-id="aa9e5-126">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
