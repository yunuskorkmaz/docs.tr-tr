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
ms.openlocfilehash: 09c80c3a56d86943ebe00e5222bb5452ab44e150
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762181"
---
# <a name="iclrruntimeinfoloadlibrary-method"></a><span data-ttu-id="ed6bf-102">ICLRRuntimeInfo::LoadLibrary Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ed6bf-102">ICLRRuntimeInfo::LoadLibrary Method</span></span>
<span data-ttu-id="ed6bf-103">Bir [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) arabirimi tarafından temsil edilen ortak dil çalışma ZAMANıNDAN (CLR) bir .NET Framework kitaplığı yükler.</span><span class="sxs-lookup"><span data-stu-id="ed6bf-103">Loads a .NET Framework library from the common language runtime (CLR) represented by an [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface.</span></span>  
  
 <span data-ttu-id="ed6bf-104">Bu yöntem [LoadLibraryShim](loadlibraryshim-function.md) işlevinin yerini alır.</span><span class="sxs-lookup"><span data-stu-id="ed6bf-104">This method supersedes the [LoadLibraryShim](loadlibraryshim-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed6bf-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="ed6bf-105">Syntax</span></span>  
  
```cpp  
HRESULT LoadLibrary(  
     [in]  LPCWSTR pwzDllName,  
     [out, retval] HMODULE *phndModule);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ed6bf-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ed6bf-106">Parameters</span></span>  
 `pwzDllName`  
 <span data-ttu-id="ed6bf-107">'ndaki Yüklenecek derlemenin adı.</span><span class="sxs-lookup"><span data-stu-id="ed6bf-107">[in] The name of the assembly to be loaded.</span></span>  
  
 `phndModule`  
 <span data-ttu-id="ed6bf-108">dışı Yüklenen derleme için bir tanıtıcı.</span><span class="sxs-lookup"><span data-stu-id="ed6bf-108">[out] A handle to the loaded assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ed6bf-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ed6bf-109">Return Value</span></span>  
 <span data-ttu-id="ed6bf-110">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="ed6bf-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="ed6bf-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ed6bf-111">HRESULT</span></span>|<span data-ttu-id="ed6bf-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ed6bf-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ed6bf-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="ed6bf-113">S_OK</span></span>|<span data-ttu-id="ed6bf-114">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="ed6bf-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="ed6bf-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="ed6bf-115">E_POINTER</span></span>|<span data-ttu-id="ed6bf-116">`pwzDllName`ya da `phndModule` null.</span><span class="sxs-lookup"><span data-stu-id="ed6bf-116">`pwzDllName` or `phndModule` is null.</span></span>|  
|<span data-ttu-id="ed6bf-117">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="ed6bf-117">E_OUTOFMEMORY</span></span>|<span data-ttu-id="ed6bf-118">İsteği işlemek için yeterli kullanılabilir bellek yok.</span><span class="sxs-lookup"><span data-stu-id="ed6bf-118">Not enough memory is available to handle the request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ed6bf-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ed6bf-119">Remarks</span></span>  
 <span data-ttu-id="ed6bf-120">Bu yöntem yalnızca .NET Framework yeniden dağıtılabilir pakette bulunan dll 'Leri yükler.</span><span class="sxs-lookup"><span data-stu-id="ed6bf-120">This method only loads DLLs included in the .NET Framework redistributable package.</span></span> <span data-ttu-id="ed6bf-121">Kullanıcı tarafından oluşturulan derlemeler yükleyemez.</span><span class="sxs-lookup"><span data-stu-id="ed6bf-121">It can not load user-generated assemblies.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ed6bf-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ed6bf-122">Requirements</span></span>  
 <span data-ttu-id="ed6bf-123">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ed6bf-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ed6bf-124">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="ed6bf-124">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="ed6bf-125">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="ed6bf-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ed6bf-126">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ed6bf-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed6bf-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ed6bf-127">See also</span></span>

- [<span data-ttu-id="ed6bf-128">ICLRRuntimeInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ed6bf-128">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="ed6bf-129">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ed6bf-129">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="ed6bf-130">Barındırma</span><span class="sxs-lookup"><span data-stu-id="ed6bf-130">Hosting</span></span>](index.md)
