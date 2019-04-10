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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d6e320936430307dab066eecc835ac5c84bd22bc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59202332"
---
# <a name="iclrruntimeinfogetversionstring-method"></a><span data-ttu-id="2ef7c-102">ICLRRuntimeInfo::GetVersionString Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2ef7c-102">ICLRRuntimeInfo::GetVersionString Method</span></span>
<span data-ttu-id="2ef7c-103">Ortak dil çalışma zamanı (CLR) sürüm bilgileri ile ilişkili alır bir verilen [Iclrruntimeınfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="2ef7c-103">Gets common language runtime (CLR) version information associated with a given [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface.</span></span>  
  
 <span data-ttu-id="2ef7c-104">Bu yöntem, aşağıdaki işlevleri yerine geçer:</span><span class="sxs-lookup"><span data-stu-id="2ef7c-104">This method supersedes the following functions:</span></span>  
  
-   [<span data-ttu-id="2ef7c-105">GetRequestedRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="2ef7c-105">GetRequestedRuntimeInfo</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)  
  
-   [<span data-ttu-id="2ef7c-106">GetRequestedRuntimeVersion</span><span class="sxs-lookup"><span data-stu-id="2ef7c-106">GetRequestedRuntimeVersion</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)  
  
## <a name="syntax"></a><span data-ttu-id="2ef7c-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2ef7c-107">Syntax</span></span>  
  
```  
HRESULT GetVersionString(  
    [out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
    [in, out]  DWORD *pcchBuffer);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2ef7c-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2ef7c-108">Parameters</span></span>  
 `pwzBuffer`  
 <span data-ttu-id="2ef7c-109">[out] .NET Framework derleme sürümü biçimi "v*A*. *B*[. *X*] ".</span><span class="sxs-lookup"><span data-stu-id="2ef7c-109">[out] The .NET Framework compilation version in the format "v*A*.*B*[.*X*]".</span></span> <span data-ttu-id="2ef7c-110">*A*, *B*, ve *X* ana sürüm, ikincil sürüm ve derleme numarasını karşılık gelen ondalık sayılardır.</span><span class="sxs-lookup"><span data-stu-id="2ef7c-110">*A*, *B*, and *X* are decimal numbers that correspond to the major version, the minor version, and the build number.</span></span> <span data-ttu-id="2ef7c-111">*X* isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="2ef7c-111">*X* is optional.</span></span> <span data-ttu-id="2ef7c-112">Varsa *X* olan mevcut yoktur sonuna bir nokta.</span><span class="sxs-lookup"><span data-stu-id="2ef7c-112">If *X* is not present, there is no trailing period.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2ef7c-113">C:\Windows\Microsoft.NET\Framework altında göründüğü gibi bu parametre .NET Framework sürümü için dizin adı eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="2ef7c-113">This parameter must match the directory name for the .NET Framework version, as it appears under C:\Windows\Microsoft.NET\Framework.</span></span>  
  
 <span data-ttu-id="2ef7c-114">Örnek değerler şunlardır: "v1.0.3705", "v1.1.4322", "v2.0.50727" ve "v4.0. *x*"burada *x* yüklü derleme sayısına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="2ef7c-114">Example values are "v1.0.3705", "v1.1.4322", "v2.0.50727", and "v4.0.*x*", where *x* depends on the build number installed.</span></span> <span data-ttu-id="2ef7c-115">"V" ön eki zorunlu olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="2ef7c-115">Note that the "v" prefix is mandatory.</span></span>  
  
 `pchBuffer`  
 <span data-ttu-id="2ef7c-116">[out içinde] Boyutunu belirtir `pwzBuffer` arabellek taşması önlemek için.</span><span class="sxs-lookup"><span data-stu-id="2ef7c-116">[in, out] Specifies the size of `pwzBuffer` to avoid buffer overruns.</span></span> <span data-ttu-id="2ef7c-117">Varsa `pwzBuffer` olduğu `null`, `pchBuffer` gerekli boyutunu döndürür `pwzBuffer` serilerindeki izin vermek için.</span><span class="sxs-lookup"><span data-stu-id="2ef7c-117">If `pwzBuffer` is `null`, `pchBuffer` returns the required size of `pwzBuffer` to allow preallocation.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2ef7c-118">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="2ef7c-118">Return Value</span></span>  
 <span data-ttu-id="2ef7c-119">Bu yöntem aşağıdaki özel HRESULT'ları yanı sıra HRESULT döndürür yöntemi hatayı gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="2ef7c-119">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="2ef7c-120">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2ef7c-120">HRESULT</span></span>|<span data-ttu-id="2ef7c-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2ef7c-121">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2ef7c-122">S_OK</span><span class="sxs-lookup"><span data-stu-id="2ef7c-122">S_OK</span></span>|<span data-ttu-id="2ef7c-123">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="2ef7c-123">The method completed successfully.</span></span>|  
|<span data-ttu-id="2ef7c-124">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="2ef7c-124">E_POINTER</span></span>|`pwzBuffer` <span data-ttu-id="2ef7c-125">veya `pchBuffer` null.</span><span class="sxs-lookup"><span data-stu-id="2ef7c-125">or `pchBuffer` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2ef7c-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2ef7c-126">Requirements</span></span>  
 <span data-ttu-id="2ef7c-127">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2ef7c-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ef7c-128">**Üst bilgi:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="2ef7c-128">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="2ef7c-129">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="2ef7c-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="2ef7c-130">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="2ef7c-130">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="2ef7c-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2ef7c-131">See also</span></span>

- [<span data-ttu-id="2ef7c-132">ICLRRuntimeInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2ef7c-132">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="2ef7c-133">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="2ef7c-133">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="2ef7c-134">.NET Framework 4 ve 4.5'e Eklenen CLR Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="2ef7c-134">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)
- [<span data-ttu-id="2ef7c-135">Barındırma</span><span class="sxs-lookup"><span data-stu-id="2ef7c-135">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
