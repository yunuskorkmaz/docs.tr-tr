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
ms.openlocfilehash: 65ac05a524297029ca50970bdd231c6a9112e35c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67748390"
---
# <a name="iclrruntimeinfoloadlibrary-method"></a><span data-ttu-id="7045e-102">ICLRRuntimeInfo::LoadLibrary Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7045e-102">ICLRRuntimeInfo::LoadLibrary Method</span></span>
<span data-ttu-id="7045e-103">.NET Framework kitaplığı tarafından temsil edilen ortak dil çalışma zamanı (CLR) yükleyen bir [Iclrruntimeınfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="7045e-103">Loads a .NET Framework library from the common language runtime (CLR) represented by an [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface.</span></span>  
  
 <span data-ttu-id="7045e-104">Bu yöntem yerine geçer [LoadLibraryShim](../../../../docs/framework/unmanaged-api/hosting/loadlibraryshim-function.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="7045e-104">This method supersedes the [LoadLibraryShim](../../../../docs/framework/unmanaged-api/hosting/loadlibraryshim-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7045e-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7045e-105">Syntax</span></span>  
  
```cpp  
HRESULT LoadLibrary(  
     [in]  LPCWSTR pwzDllName,  
     [out, retval] HMODULE *phndModule);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7045e-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7045e-106">Parameters</span></span>  
 `pwzDllName`  
 <span data-ttu-id="7045e-107">[in] Yüklenecek derlemenin adı.</span><span class="sxs-lookup"><span data-stu-id="7045e-107">[in] The name of the assembly to be loaded.</span></span>  
  
 `phndModule`  
 <span data-ttu-id="7045e-108">[out] Yüklenen derleme için bir tanıtıcı.</span><span class="sxs-lookup"><span data-stu-id="7045e-108">[out] A handle to the loaded assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7045e-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="7045e-109">Return Value</span></span>  
 <span data-ttu-id="7045e-110">Bu yöntem aşağıdaki özel HRESULT'ları yanı sıra HRESULT döndürür yöntemi hatayı gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="7045e-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="7045e-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7045e-111">HRESULT</span></span>|<span data-ttu-id="7045e-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7045e-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7045e-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="7045e-113">S_OK</span></span>|<span data-ttu-id="7045e-114">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="7045e-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="7045e-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="7045e-115">E_POINTER</span></span>|<span data-ttu-id="7045e-116">`pwzDllName` veya `phndModule` null.</span><span class="sxs-lookup"><span data-stu-id="7045e-116">`pwzDllName` or `phndModule` is null.</span></span>|  
|<span data-ttu-id="7045e-117">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="7045e-117">E_OUTOFMEMORY</span></span>|<span data-ttu-id="7045e-118">İsteği işlemek yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="7045e-118">Not enough memory is available to handle the request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7045e-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7045e-119">Remarks</span></span>  
 <span data-ttu-id="7045e-120">Bu yöntem, yalnızca .NET Framework yeniden dağıtılabilir paket içerisine dâhil DLL'leri yükler.</span><span class="sxs-lookup"><span data-stu-id="7045e-120">This method only loads DLLs included in the .NET Framework redistributable package.</span></span> <span data-ttu-id="7045e-121">Kullanıcı tarafından oluşturulan bütünleştirilmiş kodları yüklenemiyor.</span><span class="sxs-lookup"><span data-stu-id="7045e-121">It can not load user-generated assemblies.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7045e-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7045e-122">Requirements</span></span>  
 <span data-ttu-id="7045e-123">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7045e-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7045e-124">**Üst bilgi:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="7045e-124">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="7045e-125">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="7045e-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7045e-126">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7045e-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7045e-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7045e-127">See also</span></span>

- [<span data-ttu-id="7045e-128">ICLRRuntimeInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7045e-128">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="7045e-129">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="7045e-129">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="7045e-130">Barındırma</span><span class="sxs-lookup"><span data-stu-id="7045e-130">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
