---
title: ICLRRuntimeInfo::GetRuntimeDirectory Metodu
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.GetRuntimeDirectory
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::GetRuntimeDirectory
helpviewer_keywords:
- GetRuntimeDirectory method [.NET Framework hosting]
- ICLRRuntimeInfo::GetRuntimeDirectory method [.NET Framework hosting]
ms.assetid: 4401546e-4d48-453f-a1fb-b2ebda54df5c
topic_type:
- apiref
ms.openlocfilehash: 24679118e4255282f7da3ff8be2ce9c08250e181
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732053"
---
# <a name="iclrruntimeinfogetruntimedirectory-method"></a><span data-ttu-id="2865a-102">ICLRRuntimeInfo::GetRuntimeDirectory Metodu</span><span class="sxs-lookup"><span data-stu-id="2865a-102">ICLRRuntimeInfo::GetRuntimeDirectory Method</span></span>

<span data-ttu-id="2865a-103">Bu arabirimle ilişkili ortak dil çalışma zamanının (CLR) yükleme dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="2865a-103">Gets the installation directory of the common language runtime (CLR) associated with this interface.</span></span>  
  
 <span data-ttu-id="2865a-104">Bu yöntem 2,0, 3,0 ve 3,5 .NET Framework sürümlerinde sunulan [GetCORSystemDirectory](getcorsystemdirectory-function.md) işlevinin yerini alır.</span><span class="sxs-lookup"><span data-stu-id="2865a-104">This method supersedes the [GetCORSystemDirectory](getcorsystemdirectory-function.md) function provided in the .NET Framework versions 2.0, 3.0, and 3.5.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2865a-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="2865a-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRuntimeDirectory(  
[out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
[in, out]  DWORD *pcchBuffer);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2865a-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2865a-106">Parameters</span></span>  

 `pwzBuffer`  
 <span data-ttu-id="2865a-107">dışı CLR yükleme dizinini döndürür.</span><span class="sxs-lookup"><span data-stu-id="2865a-107">[out] Returns the CLR installation directory.</span></span> <span data-ttu-id="2865a-108">Yükleme yolu tam olarak nitelenir; Örneğin, "c:\Windows\Microsoft.NET\Framework\v1.0.3705 \\ ".</span><span class="sxs-lookup"><span data-stu-id="2865a-108">The installation path is fully qualified; for example, "c:\windows\microsoft.net\framework\v1.0.3705\\".</span></span>  
  
 `pchBuffer`  
 <span data-ttu-id="2865a-109">[in, out] `pwzBuffer` Arabellek taşmalarını önlemek için boyutunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="2865a-109">[in, out] Specifies the size of `pwzBuffer` to avoid buffer overruns.</span></span> <span data-ttu-id="2865a-110">`pwzBuffer`Null ise, `pchBuffer` gereken boyutunu döndürür `pwzBuffer` .</span><span class="sxs-lookup"><span data-stu-id="2865a-110">If `pwzBuffer` is null, `pchBuffer` returns the required size of `pwzBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2865a-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="2865a-111">Return Value</span></span>  

 <span data-ttu-id="2865a-112">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="2865a-112">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="2865a-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2865a-113">HRESULT</span></span>|<span data-ttu-id="2865a-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2865a-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2865a-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="2865a-115">S_OK</span></span>|<span data-ttu-id="2865a-116">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="2865a-116">The method completed successfully.</span></span>|  
|<span data-ttu-id="2865a-117">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="2865a-117">E_POINTER</span></span>|<span data-ttu-id="2865a-118">`pwzBuffer` ya da `pchBuffer` null.</span><span class="sxs-lookup"><span data-stu-id="2865a-118">`pwzBuffer` or `pchBuffer` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2865a-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2865a-119">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2865a-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2865a-120">Requirements</span></span>  

 <span data-ttu-id="2865a-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2865a-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2865a-122">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="2865a-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="2865a-123">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="2865a-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2865a-124">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2865a-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2865a-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2865a-125">See also</span></span>

- [<span data-ttu-id="2865a-126">ICLRRuntimeInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2865a-126">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="2865a-127">Hosting</span><span class="sxs-lookup"><span data-stu-id="2865a-127">Hosting</span></span>](index.md)
