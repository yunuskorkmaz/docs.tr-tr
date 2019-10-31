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
ms.openlocfilehash: b0a2e5f259fe1ee566f9cc25152b2d2a1f740bea
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120333"
---
# <a name="iclrruntimeinfogetruntimedirectory-method"></a><span data-ttu-id="016cd-102">ICLRRuntimeInfo::GetRuntimeDirectory Metodu</span><span class="sxs-lookup"><span data-stu-id="016cd-102">ICLRRuntimeInfo::GetRuntimeDirectory Method</span></span>
<span data-ttu-id="016cd-103">Bu arabirimle ilişkili ortak dil çalışma zamanının (CLR) yükleme dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="016cd-103">Gets the installation directory of the common language runtime (CLR) associated with this interface.</span></span>  
  
 <span data-ttu-id="016cd-104">Bu yöntem 2,0, 3,0 ve 3,5 .NET Framework sürümlerinde sunulan [GetCORSystemDirectory](../../../../docs/framework/unmanaged-api/hosting/getcorsystemdirectory-function.md) işlevinin yerini alır.</span><span class="sxs-lookup"><span data-stu-id="016cd-104">This method supersedes the [GetCORSystemDirectory](../../../../docs/framework/unmanaged-api/hosting/getcorsystemdirectory-function.md) function provided in the .NET Framework versions 2.0, 3.0, and 3.5.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="016cd-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="016cd-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRuntimeDirectory(  
[out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
[in, out]  DWORD *pcchBuffer);  
```  
  
## <a name="parameters"></a><span data-ttu-id="016cd-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="016cd-106">Parameters</span></span>  
 `pwzBuffer`  
 <span data-ttu-id="016cd-107">dışı CLR yükleme dizinini döndürür.</span><span class="sxs-lookup"><span data-stu-id="016cd-107">[out] Returns the CLR installation directory.</span></span> <span data-ttu-id="016cd-108">Yükleme yolu tam olarak nitelenir; Örneğin, "c:\Windows\Microsoft.NET\Framework\v1.0.3705\\".</span><span class="sxs-lookup"><span data-stu-id="016cd-108">The installation path is fully qualified; for example, "c:\windows\microsoft.net\framework\v1.0.3705\\".</span></span>  
  
 `pchBuffer`  
 <span data-ttu-id="016cd-109">[in, out] Arabellek taşmalarını önlemek için `pwzBuffer` boyutunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="016cd-109">[in, out] Specifies the size of `pwzBuffer` to avoid buffer overruns.</span></span> <span data-ttu-id="016cd-110">`pwzBuffer` null ise, `pchBuffer` `pwzBuffer`gereken boyutunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="016cd-110">If `pwzBuffer` is null, `pchBuffer` returns the required size of `pwzBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="016cd-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="016cd-111">Return Value</span></span>  
 <span data-ttu-id="016cd-112">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="016cd-112">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="016cd-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="016cd-113">HRESULT</span></span>|<span data-ttu-id="016cd-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="016cd-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="016cd-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="016cd-115">S_OK</span></span>|<span data-ttu-id="016cd-116">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="016cd-116">The method completed successfully.</span></span>|  
|<span data-ttu-id="016cd-117">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="016cd-117">E_POINTER</span></span>|<span data-ttu-id="016cd-118">`pwzBuffer` veya `pchBuffer` null.</span><span class="sxs-lookup"><span data-stu-id="016cd-118">`pwzBuffer` or `pchBuffer` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="016cd-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="016cd-119">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="016cd-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="016cd-120">Requirements</span></span>  
 <span data-ttu-id="016cd-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="016cd-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="016cd-122">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="016cd-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="016cd-123">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="016cd-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="016cd-124">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="016cd-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="016cd-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="016cd-125">See also</span></span>

- [<span data-ttu-id="016cd-126">ICLRRuntimeInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="016cd-126">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="016cd-127">Barındırma</span><span class="sxs-lookup"><span data-stu-id="016cd-127">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
