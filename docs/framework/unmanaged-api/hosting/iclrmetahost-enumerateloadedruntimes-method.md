---
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
ms.openlocfilehash: f89307ad7ed41f872ad66a99be03663ac1f30f13
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140977"
---
# <a name="iclrmetahostenumerateloadedruntimes-method"></a><span data-ttu-id="53179-102">ICLRMetaHost::EnumerateLoadedRuntimes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="53179-102">ICLRMetaHost::EnumerateLoadedRuntimes Method</span></span>
<span data-ttu-id="53179-103">Belirli bir işlemde yüklenen ortak dil çalışma zamanının (CLR) her sürümü için geçerli bir [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) arabirimi işaretçisi içeren bir sabit listesi döndürür.</span><span class="sxs-lookup"><span data-stu-id="53179-103">Returns an enumeration that includes a valid [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface pointer for each version of the common language runtime (CLR) that is loaded in a given process.</span></span> <span data-ttu-id="53179-104">Bu yöntem [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md) işlevinin yerini alır.</span><span class="sxs-lookup"><span data-stu-id="53179-104">This method supersedes the [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53179-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="53179-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateLoadedRuntimes (  
    [in] HANDLE hndProcess,  
    [out, retval] IEnumUnknown **ppEnumerator  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="53179-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="53179-106">Parameters</span></span>  
 `hndProcess`  
 <span data-ttu-id="53179-107">'ndaki Yüklenen çalışma zamanları için İnceleme işleminin tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="53179-107">[in] The handle of the process to inspect for loaded runtimes.</span></span>  
  
 `ppEnumerator`  
 <span data-ttu-id="53179-108">dışı İşlem tarafından yüklenen her CLR 'ye karşılık gelen [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) arabirimlerinin <xref:Microsoft.VisualStudio.OLE.Interop.IEnumUnknown> numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="53179-108">[out] An <xref:Microsoft.VisualStudio.OLE.Interop.IEnumUnknown> enumeration of [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interfaces corresponding to each CLR that is loaded by the process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="53179-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="53179-109">Return Value</span></span>  
 <span data-ttu-id="53179-110">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="53179-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="53179-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="53179-111">HRESULT</span></span>|<span data-ttu-id="53179-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="53179-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="53179-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="53179-113">S_OK</span></span>|<span data-ttu-id="53179-114">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="53179-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="53179-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="53179-115">E_POINTER</span></span>|<span data-ttu-id="53179-116">`ppEnumerator` null.</span><span class="sxs-lookup"><span data-stu-id="53179-116">`ppEnumerator` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="53179-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="53179-117">Remarks</span></span>  
 <span data-ttu-id="53179-118">Bu yöntem, [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)gibi kullanım dışı işlevlerle yüklenseler bile, tüm yüklenen çalışma zamanlarını listeler.</span><span class="sxs-lookup"><span data-stu-id="53179-118">This method is lists all loaded runtimes, even if they were loaded with deprecated functions such as [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="53179-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="53179-119">Requirements</span></span>  
 <span data-ttu-id="53179-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="53179-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53179-121">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="53179-121">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="53179-122">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="53179-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="53179-123">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53179-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53179-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="53179-124">See also</span></span>

- [<span data-ttu-id="53179-125">ICLRMetaHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="53179-125">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)
- [<span data-ttu-id="53179-126">Barındırma</span><span class="sxs-lookup"><span data-stu-id="53179-126">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
