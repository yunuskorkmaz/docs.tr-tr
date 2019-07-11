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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2455c896ebdc12f2bb92a30d55745f7bd5bc308a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67765526"
---
# <a name="iclrruntimeinfogetruntimedirectory-method"></a><span data-ttu-id="aa899-102">ICLRRuntimeInfo::GetRuntimeDirectory Metodu</span><span class="sxs-lookup"><span data-stu-id="aa899-102">ICLRRuntimeInfo::GetRuntimeDirectory Method</span></span>
<span data-ttu-id="aa899-103">Bu arabirimi ile ilişkili ortak dil çalışma zamanı (CLR) yükleme dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="aa899-103">Gets the installation directory of the common language runtime (CLR) associated with this interface.</span></span>  
  
 <span data-ttu-id="aa899-104">Bu yöntem yerine geçer [GetCORSystemDirectory](../../../../docs/framework/unmanaged-api/hosting/getcorsystemdirectory-function.md) .NET Framework sürüm 2.0, 3.0 ve 3.5 içinde sağlanan işlev.</span><span class="sxs-lookup"><span data-stu-id="aa899-104">This method supersedes the [GetCORSystemDirectory](../../../../docs/framework/unmanaged-api/hosting/getcorsystemdirectory-function.md) function provided in the .NET Framework versions 2.0, 3.0, and 3.5.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa899-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="aa899-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRuntimeDirectory(  
[out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
[in, out]  DWORD *pcchBuffer);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aa899-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="aa899-106">Parameters</span></span>  
 `pwzBuffer`  
 <span data-ttu-id="aa899-107">[out] CLR yükleme dizinini döndürür.</span><span class="sxs-lookup"><span data-stu-id="aa899-107">[out] Returns the CLR installation directory.</span></span> <span data-ttu-id="aa899-108">Yükleme yolu tam olarak; Örneğin, "c:\windows\microsoft.net\framework\v1.0.3705\\".</span><span class="sxs-lookup"><span data-stu-id="aa899-108">The installation path is fully qualified; for example, "c:\windows\microsoft.net\framework\v1.0.3705\\".</span></span>  
  
 `pchBuffer`  
 <span data-ttu-id="aa899-109">[out içinde] Boyutunu belirtir `pwzBuffer` arabellek taşması önlemek için.</span><span class="sxs-lookup"><span data-stu-id="aa899-109">[in, out] Specifies the size of `pwzBuffer` to avoid buffer overruns.</span></span> <span data-ttu-id="aa899-110">Varsa `pwzBuffer` boş `pchBuffer` gerekli boyutunu döndürür `pwzBuffer`.</span><span class="sxs-lookup"><span data-stu-id="aa899-110">If `pwzBuffer` is null, `pchBuffer` returns the required size of `pwzBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="aa899-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="aa899-111">Return Value</span></span>  
 <span data-ttu-id="aa899-112">Bu yöntem aşağıdaki özel HRESULT'ları yanı sıra HRESULT döndürür yöntemi hatayı gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="aa899-112">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="aa899-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="aa899-113">HRESULT</span></span>|<span data-ttu-id="aa899-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aa899-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="aa899-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="aa899-115">S_OK</span></span>|<span data-ttu-id="aa899-116">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="aa899-116">The method completed successfully.</span></span>|  
|<span data-ttu-id="aa899-117">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="aa899-117">E_POINTER</span></span>|<span data-ttu-id="aa899-118">`pwzBuffer` veya `pchBuffer` null.</span><span class="sxs-lookup"><span data-stu-id="aa899-118">`pwzBuffer` or `pchBuffer` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aa899-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="aa899-119">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aa899-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="aa899-120">Requirements</span></span>  
 <span data-ttu-id="aa899-121">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aa899-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aa899-122">**Üst bilgi:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="aa899-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="aa899-123">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="aa899-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="aa899-124">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aa899-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa899-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aa899-125">See also</span></span>

- [<span data-ttu-id="aa899-126">ICLRRuntimeInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="aa899-126">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="aa899-127">Barındırma</span><span class="sxs-lookup"><span data-stu-id="aa899-127">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
