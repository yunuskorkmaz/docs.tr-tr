---
title: ICLRRuntimeInfo::LoadLibrary Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.LoadLibrary
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::LoadLibrary
helpviewer_keywords:
- ICLRRuntimeInfo::LoadLibrary method [.NET Framework hosting]
- LoadLibrary method [.NET Framework hosting]
ms.assetid: 4517ada3-4417-4ac5-a150-73da7a87c686
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3fe1f93c621fd567471b9a49e4aa75cb90e6e0e7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59161167"
---
# <a name="iclrruntimeinfoloadlibrary-method"></a><span data-ttu-id="4c521-102">ICLRRuntimeInfo::LoadLibrary Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4c521-102">ICLRRuntimeInfo::LoadLibrary Method</span></span>
<span data-ttu-id="4c521-103">.NET Framework kitaplığı tarafından temsil edilen ortak dil çalışma zamanı (CLR) yükleyen bir [Iclrruntimeınfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="4c521-103">Loads a .NET Framework library from the common language runtime (CLR) represented by an [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface.</span></span>  
  
 <span data-ttu-id="4c521-104">Bu yöntem yerine geçer [LoadLibraryShim](../../../../docs/framework/unmanaged-api/hosting/loadlibraryshim-function.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="4c521-104">This method supersedes the [LoadLibraryShim](../../../../docs/framework/unmanaged-api/hosting/loadlibraryshim-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c521-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4c521-105">Syntax</span></span>  
  
```  
HRESULT LoadLibrary(  
     [in]  LPCWSTR pwzDllName,  
     [out, retval] HMODULE *phndModule);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4c521-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4c521-106">Parameters</span></span>  
 `pwzDllName`  
 <span data-ttu-id="4c521-107">[in] Yüklenecek derlemenin adı.</span><span class="sxs-lookup"><span data-stu-id="4c521-107">[in] The name of the assembly to be loaded.</span></span>  
  
 `phndModule`  
 <span data-ttu-id="4c521-108">[out] Yüklenen derleme için bir tanıtıcı.</span><span class="sxs-lookup"><span data-stu-id="4c521-108">[out] A handle to the loaded assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4c521-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="4c521-109">Return Value</span></span>  
 <span data-ttu-id="4c521-110">Bu yöntem aşağıdaki özel HRESULT'ları yanı sıra HRESULT döndürür yöntemi hatayı gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="4c521-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="4c521-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4c521-111">HRESULT</span></span>|<span data-ttu-id="4c521-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4c521-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4c521-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="4c521-113">S_OK</span></span>|<span data-ttu-id="4c521-114">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="4c521-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="4c521-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="4c521-115">E_POINTER</span></span>|`pwzDllName` <span data-ttu-id="4c521-116">veya `phndModule` null.</span><span class="sxs-lookup"><span data-stu-id="4c521-116">or `phndModule` is null.</span></span>|  
|<span data-ttu-id="4c521-117">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="4c521-117">E_OUTOFMEMORY</span></span>|<span data-ttu-id="4c521-118">İsteği işlemek yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="4c521-118">Not enough memory is available to handle the request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4c521-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4c521-119">Remarks</span></span>  
 <span data-ttu-id="4c521-120">Bu yöntem, yalnızca .NET Framework yeniden dağıtılabilir paket içerisine dâhil DLL'leri yükler.</span><span class="sxs-lookup"><span data-stu-id="4c521-120">This method only loads DLLs included in the .NET Framework redistributable package.</span></span> <span data-ttu-id="4c521-121">Kullanıcı tarafından oluşturulan bütünleştirilmiş kodları yüklenemiyor.</span><span class="sxs-lookup"><span data-stu-id="4c521-121">It can not load user-generated assemblies.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4c521-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4c521-122">Requirements</span></span>  
 <span data-ttu-id="4c521-123">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4c521-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c521-124">**Üst bilgi:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="4c521-124">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="4c521-125">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="4c521-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="4c521-126">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="4c521-126">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="4c521-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4c521-127">See also</span></span>

- [<span data-ttu-id="4c521-128">ICLRRuntimeInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4c521-128">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="4c521-129">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="4c521-129">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="4c521-130">Barındırma</span><span class="sxs-lookup"><span data-stu-id="4c521-130">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
