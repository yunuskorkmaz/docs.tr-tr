---
title: ICLRMetaHost::GetVersionFromFile Metodu
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.GetVersionFromFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::GetVersionFromFile
helpviewer_keywords:
- ICLRMetaHost::GetVersionFromFile method [.NET Framework hosting]
- GetVersionFromFile method [.NET Framework hosting]
ms.assetid: 55bb3eb4-f665-42fc-973c-465567570e82
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e1c8f5ea20d00d692e0eea0cba93ec4e73038e8a
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57497450"
---
# <a name="iclrmetahostgetversionfromfile-method"></a><span data-ttu-id="d9555-102">ICLRMetaHost::GetVersionFromFile Metodu</span><span class="sxs-lookup"><span data-stu-id="d9555-102">ICLRMetaHost::GetVersionFromFile Method</span></span>
<span data-ttu-id="d9555-103">Verilen dosya yoluna (meta verilerinde depolanır), bir derlemenin özgün .NET Framework derleme sürümü alır.</span><span class="sxs-lookup"><span data-stu-id="d9555-103">Gets an assembly's original .NET Framework compilation version (stored in the metadata), given its file path.</span></span> <span data-ttu-id="d9555-104">Bu yöntem yerine geçer [GetFileVersion](../../../../docs/framework/unmanaged-api/hosting/getfileversion-function.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="d9555-104">This method supersedes the [GetFileVersion](../../../../docs/framework/unmanaged-api/hosting/getfileversion-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9555-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d9555-105">Syntax</span></span>  
  
```  
HRESULT GetVersionFromFile (  
    [in] LPCWSTR pwzFilePath,  
    [out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBuffer);  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d9555-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d9555-106">Parameters</span></span>  
 `pwzFilePath`  
 <span data-ttu-id="d9555-107">[in] Tam derleme dosya yolu.</span><span class="sxs-lookup"><span data-stu-id="d9555-107">[in] The complete assembly file path.</span></span>  
  
 `pwzbuffer`  
 <span data-ttu-id="d9555-108">[out] .NET Framework derleme sürümü biçiminde meta verilerde depolanan "v*A*. *B*[. *X*] ".</span><span class="sxs-lookup"><span data-stu-id="d9555-108">[out] The .NET Framework compilation version stored in the metadata, in the format "v*A*.*B*[.*X*]".</span></span> <span data-ttu-id="d9555-109">*A*, *B*, ve *X* ana sürüm, ikincil sürüm ve derleme numarasını karşılık gelen ondalık sayılardır.</span><span class="sxs-lookup"><span data-stu-id="d9555-109">*A*, *B*, and *X* are decimal numbers that correspond to the major version, the minor version, and the build number.</span></span> <span data-ttu-id="d9555-110">Bu dizenin uzunluğu için MAX_PATH sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="d9555-110">The length of this string is limited to MAX_PATH.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d9555-111">Bu çıkış C:\Windows\Microsoft.NET\Framework altında göründüğü gibi .NET Framework sürümü için dizin adı ile eşleşir.</span><span class="sxs-lookup"><span data-stu-id="d9555-111">This output matches the directory name for the .NET Framework version, as it appears under C:\Windows\Microsoft.NET\Framework.</span></span>  
  
 <span data-ttu-id="d9555-112">Örnek değerler şunlardır: "v1.0.3705", "v1.1.4322", "v2.0.50727" ve "v4.0. *X*"burada *X* yüklü derleme sayısına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="d9555-112">Example values are "v1.0.3705", "v1.1.4322", "v2.0.50727", and "v4.0.*X*", where *X* depends on the build number installed.</span></span> <span data-ttu-id="d9555-113">"V" ön eki gerekli olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="d9555-113">Note that the "v" prefix is required.</span></span>  
  
 `pcchBuffer`  
 <span data-ttu-id="d9555-114">[out içinde] Boyutu `pwzbuffer` arabellek taşması önlemek için.</span><span class="sxs-lookup"><span data-stu-id="d9555-114">[in, out] The size of `pwzbuffer` to avoid buffer overruns.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d9555-115">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d9555-115">Return Value</span></span>  
 <span data-ttu-id="d9555-116">Bu yöntem aşağıdaki özel HRESULT'ları yanı sıra HRESULT döndürür yöntemi hatayı gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="d9555-116">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="d9555-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d9555-117">HRESULT</span></span>|<span data-ttu-id="d9555-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d9555-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d9555-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="d9555-119">S_OK</span></span>|<span data-ttu-id="d9555-120">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="d9555-120">The method completed successfully.</span></span>|  
|<span data-ttu-id="d9555-121">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="d9555-121">E_POINTER</span></span>|<span data-ttu-id="d9555-122">`pwzbuffer` veya `pcchBuffer` null.</span><span class="sxs-lookup"><span data-stu-id="d9555-122">`pwzbuffer` or `pcchBuffer` is null.</span></span>|  
|<span data-ttu-id="d9555-123">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span><span class="sxs-lookup"><span data-stu-id="d9555-123">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span></span>|<span data-ttu-id="d9555-124">Arabellek çok küçük.</span><span class="sxs-lookup"><span data-stu-id="d9555-124">The buffer is too small.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d9555-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d9555-125">Requirements</span></span>  
 <span data-ttu-id="d9555-126">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d9555-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9555-127">**Üst bilgi:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="d9555-127">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="d9555-128">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="d9555-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d9555-129">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9555-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9555-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d9555-130">See also</span></span>
- [<span data-ttu-id="d9555-131">ICLRMetaHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d9555-131">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)
- [<span data-ttu-id="d9555-132">Barındırma</span><span class="sxs-lookup"><span data-stu-id="d9555-132">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
