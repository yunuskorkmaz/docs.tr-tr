---
description: ': ICLRRuntimeInfo:: GetVersionString metodu hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 1c7603f4e9bb1142c415ba9da7a05a52d2d5e776
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753880"
---
# <a name="iclrruntimeinfogetversionstring-method"></a><span data-ttu-id="8f8bf-103">ICLRRuntimeInfo::GetVersionString Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8f8bf-103">ICLRRuntimeInfo::GetVersionString Method</span></span>

<span data-ttu-id="8f8bf-104">Belirli bir [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) arabirimiyle ilişkili ortak dil çalışma zamanı (CLR) sürüm bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="8f8bf-104">Gets common language runtime (CLR) version information associated with a given [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface.</span></span>  
  
 <span data-ttu-id="8f8bf-105">Bu yöntem aşağıdaki işlevlerin yerini alır:</span><span class="sxs-lookup"><span data-stu-id="8f8bf-105">This method supersedes the following functions:</span></span>  
  
- [<span data-ttu-id="8f8bf-106">GetRequestedRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="8f8bf-106">GetRequestedRuntimeInfo</span></span>](getrequestedruntimeinfo-function.md)  
  
- [<span data-ttu-id="8f8bf-107">GetRequestedRuntimeVersion</span><span class="sxs-lookup"><span data-stu-id="8f8bf-107">GetRequestedRuntimeVersion</span></span>](getrequestedruntimeversion-function.md)  
  
## <a name="syntax"></a><span data-ttu-id="8f8bf-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8f8bf-108">Syntax</span></span>  
  
```cpp  
HRESULT GetVersionString(  
    [out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
    [in, out]  DWORD *pcchBuffer);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8f8bf-109">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8f8bf-109">Parameters</span></span>  

 `pwzBuffer`  
 <span data-ttu-id="8f8bf-110">dışı "V *A*" biçimindeki derleme sürümü .NET Framework. *B*[.*X*] ".</span><span class="sxs-lookup"><span data-stu-id="8f8bf-110">[out] The .NET Framework compilation version in the format "v *A*.*B*[.*X*]".</span></span> <span data-ttu-id="8f8bf-111">*A*, *B* ve *X* , ana sürüme, ikincil sürüme ve yapı numarasına karşılık gelen ondalık sayılardır.</span><span class="sxs-lookup"><span data-stu-id="8f8bf-111">*A*, *B*, and *X* are decimal numbers that correspond to the major version, the minor version, and the build number.</span></span> <span data-ttu-id="8f8bf-112">*X* isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="8f8bf-112">*X* is optional.</span></span> <span data-ttu-id="8f8bf-113">*X* yoksa, izleyen bir dönem yoktur.</span><span class="sxs-lookup"><span data-stu-id="8f8bf-113">If *X* is not present, there is no trailing period.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8f8bf-114">Bu parametrenin .NET Framework sürümünün dizin adıyla eşleşmesi gerekir, çünkü C:\Windows\Microsoft.NET\Framework. altında görünür.</span><span class="sxs-lookup"><span data-stu-id="8f8bf-114">This parameter must match the directory name for the .NET Framework version, as it appears under C:\Windows\Microsoft.NET\Framework.</span></span>  
  
 <span data-ttu-id="8f8bf-115">Örnek değerler şunlardır "v 1.0.3705", "v 1.1.4322", "v 2.0.50727" ve "v 4.0. *x*", burada *x* , yüklü yapı numarasına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="8f8bf-115">Example values are "v1.0.3705", "v1.1.4322", "v2.0.50727", and "v4.0.*x*", where *x* depends on the build number installed.</span></span> <span data-ttu-id="8f8bf-116">"V" ön ekinin zorunlu olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="8f8bf-116">Note that the "v" prefix is mandatory.</span></span>  
  
 `pchBuffer`  
 <span data-ttu-id="8f8bf-117">[in, out] `pwzBuffer` Arabellek taşmalarını önlemek için boyutunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="8f8bf-117">[in, out] Specifies the size of `pwzBuffer` to avoid buffer overruns.</span></span> <span data-ttu-id="8f8bf-118">İse `pwzBuffer` `null` , `pchBuffer` `pwzBuffer` ön ayırmaya izin vermek için gereken boyutunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="8f8bf-118">If `pwzBuffer` is `null`, `pchBuffer` returns the required size of `pwzBuffer` to allow preallocation.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8f8bf-119">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8f8bf-119">Return Value</span></span>  

 <span data-ttu-id="8f8bf-120">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="8f8bf-120">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="8f8bf-121">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8f8bf-121">HRESULT</span></span>|<span data-ttu-id="8f8bf-122">Description</span><span class="sxs-lookup"><span data-stu-id="8f8bf-122">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8f8bf-123">S_OK</span><span class="sxs-lookup"><span data-stu-id="8f8bf-123">S_OK</span></span>|<span data-ttu-id="8f8bf-124">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="8f8bf-124">The method completed successfully.</span></span>|  
|<span data-ttu-id="8f8bf-125">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="8f8bf-125">E_POINTER</span></span>|<span data-ttu-id="8f8bf-126">`pwzBuffer` ya da `pchBuffer` null.</span><span class="sxs-lookup"><span data-stu-id="8f8bf-126">`pwzBuffer` or `pchBuffer` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8f8bf-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8f8bf-127">Requirements</span></span>  

 <span data-ttu-id="8f8bf-128">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8f8bf-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f8bf-129">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="8f8bf-129">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="8f8bf-130">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="8f8bf-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8f8bf-131">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f8bf-131">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f8bf-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8f8bf-132">See also</span></span>

- [<span data-ttu-id="8f8bf-133">ICLRRuntimeInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8f8bf-133">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="8f8bf-134">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="8f8bf-134">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="8f8bf-135">.NET Framework 4 ve 4.5'e Eklenen CLR Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="8f8bf-135">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)
- [<span data-ttu-id="8f8bf-136">Hosting</span><span class="sxs-lookup"><span data-stu-id="8f8bf-136">Hosting</span></span>](index.md)
