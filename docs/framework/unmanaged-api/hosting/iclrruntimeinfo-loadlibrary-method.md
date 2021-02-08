---
description: ': ICLRRuntimeInfo:: LoadLibrary yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 47557934868c7c1b68b23bf4eded0e90705d7252
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785061"
---
# <a name="iclrruntimeinfoloadlibrary-method"></a><span data-ttu-id="e6526-103">ICLRRuntimeInfo::LoadLibrary Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e6526-103">ICLRRuntimeInfo::LoadLibrary Method</span></span>

<span data-ttu-id="e6526-104">Bir [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) arabirimi tarafından temsil edilen ortak dil çalışma ZAMANıNDAN (CLR) bir .NET Framework kitaplığı yükler.</span><span class="sxs-lookup"><span data-stu-id="e6526-104">Loads a .NET Framework library from the common language runtime (CLR) represented by an [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface.</span></span>  
  
 <span data-ttu-id="e6526-105">Bu yöntem [LoadLibraryShim](loadlibraryshim-function.md) işlevinin yerini alır.</span><span class="sxs-lookup"><span data-stu-id="e6526-105">This method supersedes the [LoadLibraryShim](loadlibraryshim-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6526-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e6526-106">Syntax</span></span>  
  
```cpp  
HRESULT LoadLibrary(  
     [in]  LPCWSTR pwzDllName,  
     [out, retval] HMODULE *phndModule);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e6526-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e6526-107">Parameters</span></span>  

 `pwzDllName`  
 <span data-ttu-id="e6526-108">'ndaki Yüklenecek derlemenin adı.</span><span class="sxs-lookup"><span data-stu-id="e6526-108">[in] The name of the assembly to be loaded.</span></span>  
  
 `phndModule`  
 <span data-ttu-id="e6526-109">dışı Yüklenen derleme için bir tanıtıcı.</span><span class="sxs-lookup"><span data-stu-id="e6526-109">[out] A handle to the loaded assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e6526-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e6526-110">Return Value</span></span>  

 <span data-ttu-id="e6526-111">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="e6526-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="e6526-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e6526-112">HRESULT</span></span>|<span data-ttu-id="e6526-113">Description</span><span class="sxs-lookup"><span data-stu-id="e6526-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e6526-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="e6526-114">S_OK</span></span>|<span data-ttu-id="e6526-115">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="e6526-115">The method completed successfully.</span></span>|  
|<span data-ttu-id="e6526-116">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="e6526-116">E_POINTER</span></span>|<span data-ttu-id="e6526-117">`pwzDllName` ya da `phndModule` null.</span><span class="sxs-lookup"><span data-stu-id="e6526-117">`pwzDllName` or `phndModule` is null.</span></span>|  
|<span data-ttu-id="e6526-118">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="e6526-118">E_OUTOFMEMORY</span></span>|<span data-ttu-id="e6526-119">İsteği işlemek için yeterli kullanılabilir bellek yok.</span><span class="sxs-lookup"><span data-stu-id="e6526-119">Not enough memory is available to handle the request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e6526-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e6526-120">Remarks</span></span>  

 <span data-ttu-id="e6526-121">Bu yöntem yalnızca .NET Framework yeniden dağıtılabilir pakette bulunan dll 'Leri yükler.</span><span class="sxs-lookup"><span data-stu-id="e6526-121">This method only loads DLLs included in the .NET Framework redistributable package.</span></span> <span data-ttu-id="e6526-122">Kullanıcı tarafından oluşturulan derlemeler yükleyemez.</span><span class="sxs-lookup"><span data-stu-id="e6526-122">It can not load user-generated assemblies.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e6526-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e6526-123">Requirements</span></span>  

 <span data-ttu-id="e6526-124">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e6526-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6526-125">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="e6526-125">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="e6526-126">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="e6526-126">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e6526-127">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e6526-127">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6526-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e6526-128">See also</span></span>

- [<span data-ttu-id="e6526-129">ICLRRuntimeInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e6526-129">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="e6526-130">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e6526-130">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="e6526-131">Hosting</span><span class="sxs-lookup"><span data-stu-id="e6526-131">Hosting</span></span>](index.md)
