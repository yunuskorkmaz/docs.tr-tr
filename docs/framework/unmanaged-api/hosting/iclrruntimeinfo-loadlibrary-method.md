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
ms.openlocfilehash: 8c72f58bb65bd862b0625bfa0398b26bad0197e9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73192082"
---
# <a name="iclrruntimeinfoloadlibrary-method"></a><span data-ttu-id="ecd10-102">ICLRRuntimeInfo::LoadLibrary Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ecd10-102">ICLRRuntimeInfo::LoadLibrary Method</span></span>
<span data-ttu-id="ecd10-103">Bir [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) arabirimi tarafından temsil edilen ortak dil çalışma ZAMANıNDAN (CLR) bir .NET Framework kitaplığı yükler.</span><span class="sxs-lookup"><span data-stu-id="ecd10-103">Loads a .NET Framework library from the common language runtime (CLR) represented by an [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface.</span></span>  
  
 <span data-ttu-id="ecd10-104">Bu yöntem [LoadLibraryShim](../../../../docs/framework/unmanaged-api/hosting/loadlibraryshim-function.md) işlevinin yerini alır.</span><span class="sxs-lookup"><span data-stu-id="ecd10-104">This method supersedes the [LoadLibraryShim](../../../../docs/framework/unmanaged-api/hosting/loadlibraryshim-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ecd10-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ecd10-105">Syntax</span></span>  
  
```cpp  
HRESULT LoadLibrary(  
     [in]  LPCWSTR pwzDllName,  
     [out, retval] HMODULE *phndModule);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ecd10-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ecd10-106">Parameters</span></span>  
 `pwzDllName`  
 <span data-ttu-id="ecd10-107">'ndaki Yüklenecek derlemenin adı.</span><span class="sxs-lookup"><span data-stu-id="ecd10-107">[in] The name of the assembly to be loaded.</span></span>  
  
 `phndModule`  
 <span data-ttu-id="ecd10-108">dışı Yüklenen derleme için bir tanıtıcı.</span><span class="sxs-lookup"><span data-stu-id="ecd10-108">[out] A handle to the loaded assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ecd10-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ecd10-109">Return Value</span></span>  
 <span data-ttu-id="ecd10-110">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="ecd10-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="ecd10-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ecd10-111">HRESULT</span></span>|<span data-ttu-id="ecd10-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ecd10-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ecd10-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="ecd10-113">S_OK</span></span>|<span data-ttu-id="ecd10-114">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="ecd10-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="ecd10-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="ecd10-115">E_POINTER</span></span>|<span data-ttu-id="ecd10-116">`pwzDllName` veya `phndModule` null.</span><span class="sxs-lookup"><span data-stu-id="ecd10-116">`pwzDllName` or `phndModule` is null.</span></span>|  
|<span data-ttu-id="ecd10-117">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="ecd10-117">E_OUTOFMEMORY</span></span>|<span data-ttu-id="ecd10-118">İsteği işlemek için yeterli kullanılabilir bellek yok.</span><span class="sxs-lookup"><span data-stu-id="ecd10-118">Not enough memory is available to handle the request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ecd10-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ecd10-119">Remarks</span></span>  
 <span data-ttu-id="ecd10-120">Bu yöntem yalnızca .NET Framework yeniden dağıtılabilir pakette bulunan dll 'Leri yükler.</span><span class="sxs-lookup"><span data-stu-id="ecd10-120">This method only loads DLLs included in the .NET Framework redistributable package.</span></span> <span data-ttu-id="ecd10-121">Kullanıcı tarafından oluşturulan derlemeler yükleyemez.</span><span class="sxs-lookup"><span data-stu-id="ecd10-121">It can not load user-generated assemblies.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ecd10-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ecd10-122">Requirements</span></span>  
 <span data-ttu-id="ecd10-123">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ecd10-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ecd10-124">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="ecd10-124">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="ecd10-125">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="ecd10-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ecd10-126">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ecd10-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecd10-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ecd10-127">See also</span></span>

- [<span data-ttu-id="ecd10-128">ICLRRuntimeInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ecd10-128">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="ecd10-129">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ecd10-129">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="ecd10-130">Barındırma</span><span class="sxs-lookup"><span data-stu-id="ecd10-130">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
