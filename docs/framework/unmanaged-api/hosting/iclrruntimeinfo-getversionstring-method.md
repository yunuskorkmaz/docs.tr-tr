---
title: ICLRRuntimeInfo::GetVersionString Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.GetVersionString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::GetVersionString
helpviewer_keywords:
- ICLRRuntimeInfo::GetVersionString method [.NET Framework hosting]
- GetVersionString method, ICLRRuntimeInfo interface [.NET Framework hosting]
ms.assetid: 98b097ef-2276-4dd9-8551-b03c972e8179
topic_type:
- apiref
ms.openlocfilehash: 0b6ac83cdd0c88e87fdfd552c76c906a334f8928
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120297"
---
# <a name="iclrruntimeinfogetversionstring-method"></a><span data-ttu-id="15f5c-102">ICLRRuntimeInfo::GetVersionString Yöntemi</span><span class="sxs-lookup"><span data-stu-id="15f5c-102">ICLRRuntimeInfo::GetVersionString Method</span></span>
<span data-ttu-id="15f5c-103">Belirli bir [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) arabirimiyle ilişkili ortak dil çalışma zamanı (CLR) sürüm bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="15f5c-103">Gets common language runtime (CLR) version information associated with a given [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface.</span></span>  
  
 <span data-ttu-id="15f5c-104">Bu yöntem aşağıdaki işlevlerin yerini alır:</span><span class="sxs-lookup"><span data-stu-id="15f5c-104">This method supersedes the following functions:</span></span>  
  
- [<span data-ttu-id="15f5c-105">GetRequestedRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="15f5c-105">GetRequestedRuntimeInfo</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)  
  
- [<span data-ttu-id="15f5c-106">GetRequestedRuntimeVersion</span><span class="sxs-lookup"><span data-stu-id="15f5c-106">GetRequestedRuntimeVersion</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)  
  
## <a name="syntax"></a><span data-ttu-id="15f5c-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="15f5c-107">Syntax</span></span>  
  
```cpp  
HRESULT GetVersionString(  
    [out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
    [in, out]  DWORD *pcchBuffer);  
```  
  
## <a name="parameters"></a><span data-ttu-id="15f5c-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="15f5c-108">Parameters</span></span>  
 `pwzBuffer`  
 <span data-ttu-id="15f5c-109">dışı "V*A*" biçimindeki derleme sürümü .NET Framework. *B*[. *X*] ".</span><span class="sxs-lookup"><span data-stu-id="15f5c-109">[out] The .NET Framework compilation version in the format "v*A*.*B*[.*X*]".</span></span> <span data-ttu-id="15f5c-110">*A*, *B*ve *X* , ana sürüme, ikincil sürüme ve yapı numarasına karşılık gelen ondalık sayılardır.</span><span class="sxs-lookup"><span data-stu-id="15f5c-110">*A*, *B*, and *X* are decimal numbers that correspond to the major version, the minor version, and the build number.</span></span> <span data-ttu-id="15f5c-111">*X* isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="15f5c-111">*X* is optional.</span></span> <span data-ttu-id="15f5c-112">*X* yoksa, izleyen bir dönem yoktur.</span><span class="sxs-lookup"><span data-stu-id="15f5c-112">If *X* is not present, there is no trailing period.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="15f5c-113">Bu parametrenin .NET Framework sürümünün dizin adıyla eşleşmesi gerekir, çünkü C:\Windows\Microsoft.NET\Framework. altında görünür.</span><span class="sxs-lookup"><span data-stu-id="15f5c-113">This parameter must match the directory name for the .NET Framework version, as it appears under C:\Windows\Microsoft.NET\Framework.</span></span>  
  
 <span data-ttu-id="15f5c-114">Örnek değerler şunlardır "v 1.0.3705", "v 1.1.4322", "v 2.0.50727" ve "v 4.0. *x*", burada *x* , yüklü yapı numarasına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="15f5c-114">Example values are "v1.0.3705", "v1.1.4322", "v2.0.50727", and "v4.0.*x*", where *x* depends on the build number installed.</span></span> <span data-ttu-id="15f5c-115">"V" ön ekinin zorunlu olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="15f5c-115">Note that the "v" prefix is mandatory.</span></span>  
  
 `pchBuffer`  
 <span data-ttu-id="15f5c-116">[in, out] Arabellek taşmalarını önlemek için `pwzBuffer` boyutunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="15f5c-116">[in, out] Specifies the size of `pwzBuffer` to avoid buffer overruns.</span></span> <span data-ttu-id="15f5c-117">`pwzBuffer` `null`, `pchBuffer`, ön ayırmaya izin vermek için gereken `pwzBuffer` boyutunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="15f5c-117">If `pwzBuffer` is `null`, `pchBuffer` returns the required size of `pwzBuffer` to allow preallocation.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="15f5c-118">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="15f5c-118">Return Value</span></span>  
 <span data-ttu-id="15f5c-119">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="15f5c-119">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="15f5c-120">HRESULT</span><span class="sxs-lookup"><span data-stu-id="15f5c-120">HRESULT</span></span>|<span data-ttu-id="15f5c-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="15f5c-121">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="15f5c-122">S_OK</span><span class="sxs-lookup"><span data-stu-id="15f5c-122">S_OK</span></span>|<span data-ttu-id="15f5c-123">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="15f5c-123">The method completed successfully.</span></span>|  
|<span data-ttu-id="15f5c-124">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="15f5c-124">E_POINTER</span></span>|<span data-ttu-id="15f5c-125">`pwzBuffer` veya `pchBuffer` null.</span><span class="sxs-lookup"><span data-stu-id="15f5c-125">`pwzBuffer` or `pchBuffer` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="15f5c-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="15f5c-126">Requirements</span></span>  
 <span data-ttu-id="15f5c-127">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="15f5c-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15f5c-128">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="15f5c-128">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="15f5c-129">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="15f5c-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="15f5c-130">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="15f5c-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15f5c-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="15f5c-131">See also</span></span>

- [<span data-ttu-id="15f5c-132">ICLRRuntimeInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="15f5c-132">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="15f5c-133">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="15f5c-133">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="15f5c-134">.NET Framework 4 ve 4.5'e Eklenen CLR Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="15f5c-134">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)
- [<span data-ttu-id="15f5c-135">Barındırma</span><span class="sxs-lookup"><span data-stu-id="15f5c-135">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
