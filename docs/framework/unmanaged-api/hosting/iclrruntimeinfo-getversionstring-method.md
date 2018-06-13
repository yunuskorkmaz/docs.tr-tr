---
title: ICLRRuntimeInfo::GetVersionString Metodu
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
ms.openlocfilehash: b18323644220ffdce1caad966b8a0c2a7baddde2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33434643"
---
# <a name="iclrruntimeinfogetversionstring-method"></a><span data-ttu-id="09dc9-102">ICLRRuntimeInfo::GetVersionString Metodu</span><span class="sxs-lookup"><span data-stu-id="09dc9-102">ICLRRuntimeInfo::GetVersionString Method</span></span>
<span data-ttu-id="09dc9-103">Ortak dil çalışma zamanı (CLR) sürüm bilgileri ile ilişkili alır bir verilen [Iclrruntimeınfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="09dc9-103">Gets common language runtime (CLR) version information associated with a given [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface.</span></span>  
  
 <span data-ttu-id="09dc9-104">Bu yöntem, aşağıdaki işlevleri yerine geçiyor:</span><span class="sxs-lookup"><span data-stu-id="09dc9-104">This method supersedes the following functions:</span></span>  
  
-   [<span data-ttu-id="09dc9-105">Getrequestedruntimeınfo</span><span class="sxs-lookup"><span data-stu-id="09dc9-105">GetRequestedRuntimeInfo</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)  
  
-   [<span data-ttu-id="09dc9-106">GetRequestedRuntimeVersion</span><span class="sxs-lookup"><span data-stu-id="09dc9-106">GetRequestedRuntimeVersion</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)  
  
## <a name="syntax"></a><span data-ttu-id="09dc9-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="09dc9-107">Syntax</span></span>  
  
```  
HRESULT GetVersionString(  
    [out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
    [in, out]  DWORD *pcchBuffer);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="09dc9-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="09dc9-108">Parameters</span></span>  
 `pwzBuffer`  
 <span data-ttu-id="09dc9-109">[out] .NET Framework derleme sürüm biçimde "v*A*. *B*[. *X*] ".</span><span class="sxs-lookup"><span data-stu-id="09dc9-109">[out] The .NET Framework compilation version in the format "v*A*.*B*[.*X*]".</span></span> <span data-ttu-id="09dc9-110">*A*, *B*, ve *X* ana sürüm, alt sürüm ve yapı numarası karşılık gelen ondalık sayılar.</span><span class="sxs-lookup"><span data-stu-id="09dc9-110">*A*, *B*, and *X* are decimal numbers that correspond to the major version, the minor version, and the build number.</span></span> <span data-ttu-id="09dc9-111">*X* isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="09dc9-111">*X* is optional.</span></span> <span data-ttu-id="09dc9-112">Varsa *X* olan mevcut yoktur sonuna bir nokta.</span><span class="sxs-lookup"><span data-stu-id="09dc9-112">If *X* is not present, there is no trailing period.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="09dc9-113">Bu parametre C:\Windows\Microsoft.NET\Framework altında göründüğü gibi .NET Framework sürümü için dizin adı eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="09dc9-113">This parameter must match the directory name for the .NET Framework version, as it appears under C:\Windows\Microsoft.NET\Framework.</span></span>  
  
 <span data-ttu-id="09dc9-114">Örnek değerler şunlardır: "v1.0.3705", "v1.1.4322", "v2.0.50727" ve "v4.0. *x*", burada *x* yüklü yapı sayısına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="09dc9-114">Example values are "v1.0.3705", "v1.1.4322", "v2.0.50727", and "v4.0.*x*", where *x* depends on the build number installed.</span></span> <span data-ttu-id="09dc9-115">"V" öneki zorunlu olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="09dc9-115">Note that the "v" prefix is mandatory.</span></span>  
  
 `pchBuffer`  
 <span data-ttu-id="09dc9-116">[içinde out] Boyutunu belirtir `pwzBuffer` arabellek taşmaları önlemek için.</span><span class="sxs-lookup"><span data-stu-id="09dc9-116">[in, out] Specifies the size of `pwzBuffer` to avoid buffer overruns.</span></span> <span data-ttu-id="09dc9-117">Varsa `pwzBuffer` olan `null`, `pchBuffer` gerekli boyutu döndüren `pwzBuffer` ön tahsis izin vermek için.</span><span class="sxs-lookup"><span data-stu-id="09dc9-117">If `pwzBuffer` is `null`, `pchBuffer` returns the required size of `pwzBuffer` to allow preallocation.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="09dc9-118">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="09dc9-118">Return Value</span></span>  
 <span data-ttu-id="09dc9-119">Bu yöntem aşağıdaki belirli HRESULTs yanı sıra HRESULT yöntem hatası olduğunu gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="09dc9-119">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="09dc9-120">HRESULT</span><span class="sxs-lookup"><span data-stu-id="09dc9-120">HRESULT</span></span>|<span data-ttu-id="09dc9-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="09dc9-121">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="09dc9-122">S_OK</span><span class="sxs-lookup"><span data-stu-id="09dc9-122">S_OK</span></span>|<span data-ttu-id="09dc9-123">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="09dc9-123">The method completed successfully.</span></span>|  
|<span data-ttu-id="09dc9-124">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="09dc9-124">E_POINTER</span></span>|<span data-ttu-id="09dc9-125">`pwzBuffer` veya `pchBuffer` null.</span><span class="sxs-lookup"><span data-stu-id="09dc9-125">`pwzBuffer` or `pchBuffer` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="09dc9-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="09dc9-126">Requirements</span></span>  
 <span data-ttu-id="09dc9-127">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="09dc9-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="09dc9-128">**Başlık:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="09dc9-128">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="09dc9-129">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="09dc9-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="09dc9-130">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="09dc9-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09dc9-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="09dc9-131">See Also</span></span>  
 [<span data-ttu-id="09dc9-132">ICLRRuntimeInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="09dc9-132">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [<span data-ttu-id="09dc9-133">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="09dc9-133">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="09dc9-134">.NET Framework 4 ve 4.5'e Eklenen CLR Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="09dc9-134">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)  
 [<span data-ttu-id="09dc9-135">Barındırma</span><span class="sxs-lookup"><span data-stu-id="09dc9-135">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
