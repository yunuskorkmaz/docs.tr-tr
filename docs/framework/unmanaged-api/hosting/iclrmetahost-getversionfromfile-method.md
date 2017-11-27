---
title: ICLRMetaHost::GetVersionFromFile Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRMetaHost.GetVersionFromFile
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRMetaHost::GetVersionFromFile
helpviewer_keywords:
- ICLRMetaHost::GetVersionFromFile method [.NET Framework hosting]
- GetVersionFromFile method [.NET Framework hosting]
ms.assetid: 55bb3eb4-f665-42fc-973c-465567570e82
topic_type: apiref
caps.latest.revision: "20"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 90fcf5ca8306c4e91ff6b96bac36ad2639d81d5d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrmetahostgetversionfromfile-method"></a><span data-ttu-id="aab51-102">ICLRMetaHost::GetVersionFromFile Metodu</span><span class="sxs-lookup"><span data-stu-id="aab51-102">ICLRMetaHost::GetVersionFromFile Method</span></span>
<span data-ttu-id="aab51-103">Dosya yoluna verilen (meta verilerde depolanan), bir derlemenin özgün .NET Framework derleme sürümünü alır.</span><span class="sxs-lookup"><span data-stu-id="aab51-103">Gets an assembly's original .NET Framework compilation version (stored in the metadata), given its file path.</span></span> <span data-ttu-id="aab51-104">Bu yöntem yerini [GetFileVersion](../../../../docs/framework/unmanaged-api/hosting/getfileversion-function.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="aab51-104">This method supersedes the [GetFileVersion](../../../../docs/framework/unmanaged-api/hosting/getfileversion-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aab51-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="aab51-105">Syntax</span></span>  
  
```  
HRESULT GetVersionFromFile (  
    [in] LPCWSTR pwzFilePath,  
    [out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBuffer);  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="aab51-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="aab51-106">Parameters</span></span>  
 `pwzFilePath`  
 <span data-ttu-id="aab51-107">[in] Tam derleme dosya yolu.</span><span class="sxs-lookup"><span data-stu-id="aab51-107">[in] The complete assembly file path.</span></span>  
  
 `pwzbuffer`  
 <span data-ttu-id="aab51-108">[out] .NET Framework derleme sürüm biçimde meta verilerde depolanan "v*A*. *B*[. *X*] ".</span><span class="sxs-lookup"><span data-stu-id="aab51-108">[out] The .NET Framework compilation version stored in the metadata, in the format "v*A*.*B*[.*X*]".</span></span> <span data-ttu-id="aab51-109">*A*, *B*, ve *X* ana sürüm, alt sürüm ve yapı numarası karşılık gelen ondalık sayılar.</span><span class="sxs-lookup"><span data-stu-id="aab51-109">*A*, *B*, and *X* are decimal numbers that correspond to the major version, the minor version, and the build number.</span></span> <span data-ttu-id="aab51-110">Bu dize uzunluğu için MAX_PATH sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="aab51-110">The length of this string is limited to MAX_PATH.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="aab51-111">Bu çıktı C:\Windows\Microsoft.NET\Framework altında göründüğü gibi .NET Framework sürümü için dizin adı eşleşir.</span><span class="sxs-lookup"><span data-stu-id="aab51-111">This output matches the directory name for the .NET Framework version, as it appears under C:\Windows\Microsoft.NET\Framework.</span></span>  
  
 <span data-ttu-id="aab51-112">Örnek değerler şunlardır: "v1.0.3705", "v1.1.4322", "v2.0.50727" ve "v4.0. *X*", burada *X* yüklü yapı sayısına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="aab51-112">Example values are "v1.0.3705", "v1.1.4322", "v2.0.50727", and "v4.0.*X*", where *X* depends on the build number installed.</span></span> <span data-ttu-id="aab51-113">"V" öneki gerekli olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="aab51-113">Note that the "v" prefix is required.</span></span>  
  
 `pcchBuffer`  
 <span data-ttu-id="aab51-114">[içinde out] Boyutunu `pwzbuffer` arabellek taşmaları önlemek için.</span><span class="sxs-lookup"><span data-stu-id="aab51-114">[in, out] The size of `pwzbuffer` to avoid buffer overruns.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="aab51-115">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="aab51-115">Return Value</span></span>  
 <span data-ttu-id="aab51-116">Bu yöntem aşağıdaki belirli HRESULTs yanı sıra HRESULT yöntem hatası olduğunu gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="aab51-116">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="aab51-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="aab51-117">HRESULT</span></span>|<span data-ttu-id="aab51-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aab51-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="aab51-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="aab51-119">S_OK</span></span>|<span data-ttu-id="aab51-120">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="aab51-120">The method completed successfully.</span></span>|  
|<span data-ttu-id="aab51-121">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="aab51-121">E_POINTER</span></span>|<span data-ttu-id="aab51-122">`pwzbuffer`veya `pcchBuffer` null.</span><span class="sxs-lookup"><span data-stu-id="aab51-122">`pwzbuffer` or `pcchBuffer` is null.</span></span>|  
|<span data-ttu-id="aab51-123">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span><span class="sxs-lookup"><span data-stu-id="aab51-123">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span></span>|<span data-ttu-id="aab51-124">Arabellek çok küçük.</span><span class="sxs-lookup"><span data-stu-id="aab51-124">The buffer is too small.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="aab51-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="aab51-125">Requirements</span></span>  
 <span data-ttu-id="aab51-126">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aab51-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aab51-127">**Başlık:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="aab51-127">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="aab51-128">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="aab51-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="aab51-129">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aab51-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aab51-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="aab51-130">See Also</span></span>  
 [<span data-ttu-id="aab51-131">Iclrmetahost arabirimi</span><span class="sxs-lookup"><span data-stu-id="aab51-131">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)  
 [<span data-ttu-id="aab51-132">Barındırma</span><span class="sxs-lookup"><span data-stu-id="aab51-132">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
