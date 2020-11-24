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
ms.openlocfilehash: f5e0ead41ebd13c259c24fa0c02bcc9a3b33e0fb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95689452"
---
# <a name="iclrmetahostgetversionfromfile-method"></a><span data-ttu-id="523cf-102">ICLRMetaHost::GetVersionFromFile Metodu</span><span class="sxs-lookup"><span data-stu-id="523cf-102">ICLRMetaHost::GetVersionFromFile Method</span></span>

<span data-ttu-id="523cf-103">Bir derlemenin özgün .NET Framework derleme sürümünü (meta verilerde depolanır), dosya yolu olarak alır.</span><span class="sxs-lookup"><span data-stu-id="523cf-103">Gets an assembly's original .NET Framework compilation version (stored in the metadata), given its file path.</span></span> <span data-ttu-id="523cf-104">Bu yöntem, [GetFileVersion](getfileversion-function.md) işlevinin yerini alır.</span><span class="sxs-lookup"><span data-stu-id="523cf-104">This method supersedes the [GetFileVersion](getfileversion-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="523cf-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="523cf-105">Syntax</span></span>  
  
```cpp  
HRESULT GetVersionFromFile (  
    [in] LPCWSTR pwzFilePath,  
    [out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBuffer);  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="523cf-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="523cf-106">Parameters</span></span>  

 `pwzFilePath`  
 <span data-ttu-id="523cf-107">'ndaki Tüm derleme dosyası yolu.</span><span class="sxs-lookup"><span data-stu-id="523cf-107">[in] The complete assembly file path.</span></span>  
  
 `pwzbuffer`  
 <span data-ttu-id="523cf-108">dışı Meta verilerde depolanan .NET Framework derleme sürümü, "v *A*" biçimindedir. *B*[.*X*] ".</span><span class="sxs-lookup"><span data-stu-id="523cf-108">[out] The .NET Framework compilation version stored in the metadata, in the format "v *A*.*B*[.*X*]".</span></span> <span data-ttu-id="523cf-109">*A*, *B* ve *X* , ana sürüme, ikincil sürüme ve yapı numarasına karşılık gelen ondalık sayılardır.</span><span class="sxs-lookup"><span data-stu-id="523cf-109">*A*, *B*, and *X* are decimal numbers that correspond to the major version, the minor version, and the build number.</span></span> <span data-ttu-id="523cf-110">Bu dizenin uzunluğu MAX_PATH sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="523cf-110">The length of this string is limited to MAX_PATH.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="523cf-111">Bu çıktı, C:\Windows\Microsoft.NET\Framework. altında göründüğü gibi .NET Framework sürümünün dizin adıyla eşleşir.</span><span class="sxs-lookup"><span data-stu-id="523cf-111">This output matches the directory name for the .NET Framework version, as it appears under C:\Windows\Microsoft.NET\Framework.</span></span>  
  
 <span data-ttu-id="523cf-112">Örnek değerler şunlardır "v 1.0.3705", "v 1.1.4322", "v 2.0.50727" ve "v 4.0. *X*", burada *x* , yüklü yapı numarasına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="523cf-112">Example values are "v1.0.3705", "v1.1.4322", "v2.0.50727", and "v4.0.*X*", where *X* depends on the build number installed.</span></span> <span data-ttu-id="523cf-113">"V" ön ekinin gerekli olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="523cf-113">Note that the "v" prefix is required.</span></span>  
  
 `pcchBuffer`  
 <span data-ttu-id="523cf-114">[in, out] `pwzbuffer` Arabellek taşmalarını önlemek için boyutu.</span><span class="sxs-lookup"><span data-stu-id="523cf-114">[in, out] The size of `pwzbuffer` to avoid buffer overruns.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="523cf-115">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="523cf-115">Return Value</span></span>  

 <span data-ttu-id="523cf-116">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="523cf-116">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="523cf-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="523cf-117">HRESULT</span></span>|<span data-ttu-id="523cf-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="523cf-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="523cf-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="523cf-119">S_OK</span></span>|<span data-ttu-id="523cf-120">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="523cf-120">The method completed successfully.</span></span>|  
|<span data-ttu-id="523cf-121">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="523cf-121">E_POINTER</span></span>|<span data-ttu-id="523cf-122">`pwzbuffer` ya da `pcchBuffer` null.</span><span class="sxs-lookup"><span data-stu-id="523cf-122">`pwzbuffer` or `pcchBuffer` is null.</span></span>|  
|<span data-ttu-id="523cf-123">HRESULT_FROM_WIN32 (ERROR_INSUFFICIENT_BUFFER)</span><span class="sxs-lookup"><span data-stu-id="523cf-123">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span></span>|<span data-ttu-id="523cf-124">Arabellek çok küçük.</span><span class="sxs-lookup"><span data-stu-id="523cf-124">The buffer is too small.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="523cf-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="523cf-125">Requirements</span></span>  

 <span data-ttu-id="523cf-126">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="523cf-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="523cf-127">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="523cf-127">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="523cf-128">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="523cf-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="523cf-129">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="523cf-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="523cf-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="523cf-130">See also</span></span>

- [<span data-ttu-id="523cf-131">ICLRMetaHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="523cf-131">ICLRMetaHost Interface</span></span>](iclrmetahost-interface.md)
- [<span data-ttu-id="523cf-132">Hosting</span><span class="sxs-lookup"><span data-stu-id="523cf-132">Hosting</span></span>](index.md)
