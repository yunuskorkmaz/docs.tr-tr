---
description: ': ICLRMetaHost:: Enumerateloadedçalışma zamanları yöntemi hakkında daha fazla bilgi edinin'
title: ICLRMetaHost::EnumerateLoadedRuntimes Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.EnumerateLoadedRuntimes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::EnumerateLoadedRuntimes
helpviewer_keywords:
- EnumerateLoadedRuntimes method [.NET Framework hosting]
- ICLRMetaHost::EnumerateLoadedRuntimes method [.NET Framework hosting]
ms.assetid: 22fc0a3f-dce4-4766-9a3c-9fab15f4b4ca
topic_type:
- apiref
ms.openlocfilehash: 508c4daca7e34366e0da35591f4e7a780301e823
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789872"
---
# <a name="iclrmetahostenumerateloadedruntimes-method"></a><span data-ttu-id="8f9fc-103">ICLRMetaHost::EnumerateLoadedRuntimes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8f9fc-103">ICLRMetaHost::EnumerateLoadedRuntimes Method</span></span>

<span data-ttu-id="8f9fc-104">Belirli bir işlemde yüklenen ortak dil çalışma zamanının (CLR) her sürümü için geçerli bir [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) arabirimi işaretçisi içeren bir sabit listesi döndürür.</span><span class="sxs-lookup"><span data-stu-id="8f9fc-104">Returns an enumeration that includes a valid [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface pointer for each version of the common language runtime (CLR) that is loaded in a given process.</span></span> <span data-ttu-id="8f9fc-105">Bu yöntem [GetVersionFromProcess](getversionfromprocess-function.md) işlevinin yerini alır.</span><span class="sxs-lookup"><span data-stu-id="8f9fc-105">This method supersedes the [GetVersionFromProcess](getversionfromprocess-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f9fc-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8f9fc-106">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateLoadedRuntimes (  
    [in] HANDLE hndProcess,  
    [out, retval] IEnumUnknown **ppEnumerator  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8f9fc-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8f9fc-107">Parameters</span></span>  

 `hndProcess`  
 <span data-ttu-id="8f9fc-108">'ndaki Yüklenen çalışma zamanları için İnceleme işleminin tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="8f9fc-108">[in] The handle of the process to inspect for loaded runtimes.</span></span>  
  
 `ppEnumerator`  
 <span data-ttu-id="8f9fc-109">dışı <xref:Microsoft.VisualStudio.OLE.Interop.IEnumUnknown> İşlem tarafından yüklenen her clr 'ye karşılık gelen [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) arabirimlerinin numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="8f9fc-109">[out] An <xref:Microsoft.VisualStudio.OLE.Interop.IEnumUnknown> enumeration of [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interfaces corresponding to each CLR that is loaded by the process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8f9fc-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8f9fc-110">Return Value</span></span>  

 <span data-ttu-id="8f9fc-111">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="8f9fc-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="8f9fc-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8f9fc-112">HRESULT</span></span>|<span data-ttu-id="8f9fc-113">Description</span><span class="sxs-lookup"><span data-stu-id="8f9fc-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8f9fc-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="8f9fc-114">S_OK</span></span>|<span data-ttu-id="8f9fc-115">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="8f9fc-115">The method completed successfully.</span></span>|  
|<span data-ttu-id="8f9fc-116">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="8f9fc-116">E_POINTER</span></span>|<span data-ttu-id="8f9fc-117">`ppEnumerator` null.</span><span class="sxs-lookup"><span data-stu-id="8f9fc-117">`ppEnumerator` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8f9fc-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8f9fc-118">Remarks</span></span>  

 <span data-ttu-id="8f9fc-119">Bu yöntem, [CorBindToRuntime](corbindtoruntime-function.md)gibi kullanım dışı işlevlerle yüklenseler bile, tüm yüklenen çalışma zamanlarını listeler.</span><span class="sxs-lookup"><span data-stu-id="8f9fc-119">This method is lists all loaded runtimes, even if they were loaded with deprecated functions such as [CorBindToRuntime](corbindtoruntime-function.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f9fc-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8f9fc-120">Requirements</span></span>  

 <span data-ttu-id="8f9fc-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8f9fc-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f9fc-122">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="8f9fc-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="8f9fc-123">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="8f9fc-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8f9fc-124">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f9fc-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f9fc-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8f9fc-125">See also</span></span>

- [<span data-ttu-id="8f9fc-126">ICLRMetaHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8f9fc-126">ICLRMetaHost Interface</span></span>](iclrmetahost-interface.md)
- [<span data-ttu-id="8f9fc-127">Hosting</span><span class="sxs-lookup"><span data-stu-id="8f9fc-127">Hosting</span></span>](index.md)
