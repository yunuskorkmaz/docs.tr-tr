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
ms.openlocfilehash: 2e22b8a2d0213b3bd766d80218d6f396721a90e1
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703759"
---
# <a name="iclrmetahostenumerateloadedruntimes-method"></a><span data-ttu-id="3ab1a-102">ICLRMetaHost::EnumerateLoadedRuntimes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3ab1a-102">ICLRMetaHost::EnumerateLoadedRuntimes Method</span></span>
<span data-ttu-id="3ab1a-103">Belirli bir işlemde yüklenen ortak dil çalışma zamanının (CLR) her sürümü için geçerli bir [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) arabirimi işaretçisi içeren bir sabit listesi döndürür.</span><span class="sxs-lookup"><span data-stu-id="3ab1a-103">Returns an enumeration that includes a valid [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface pointer for each version of the common language runtime (CLR) that is loaded in a given process.</span></span> <span data-ttu-id="3ab1a-104">Bu yöntem [GetVersionFromProcess](getversionfromprocess-function.md) işlevinin yerini alır.</span><span class="sxs-lookup"><span data-stu-id="3ab1a-104">This method supersedes the [GetVersionFromProcess](getversionfromprocess-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ab1a-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="3ab1a-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateLoadedRuntimes (  
    [in] HANDLE hndProcess,  
    [out, retval] IEnumUnknown **ppEnumerator  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3ab1a-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3ab1a-106">Parameters</span></span>  
 `hndProcess`  
 <span data-ttu-id="3ab1a-107">'ndaki Yüklenen çalışma zamanları için İnceleme işleminin tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="3ab1a-107">[in] The handle of the process to inspect for loaded runtimes.</span></span>  
  
 `ppEnumerator`  
 <span data-ttu-id="3ab1a-108">dışı <xref:Microsoft.VisualStudio.OLE.Interop.IEnumUnknown>İşlem tarafından yüklenen her clr 'ye karşılık gelen [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) arabirimlerinin numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="3ab1a-108">[out] An <xref:Microsoft.VisualStudio.OLE.Interop.IEnumUnknown> enumeration of [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interfaces corresponding to each CLR that is loaded by the process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3ab1a-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3ab1a-109">Return Value</span></span>  
 <span data-ttu-id="3ab1a-110">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="3ab1a-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="3ab1a-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3ab1a-111">HRESULT</span></span>|<span data-ttu-id="3ab1a-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3ab1a-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3ab1a-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="3ab1a-113">S_OK</span></span>|<span data-ttu-id="3ab1a-114">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="3ab1a-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="3ab1a-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="3ab1a-115">E_POINTER</span></span>|<span data-ttu-id="3ab1a-116">`ppEnumerator`null.</span><span class="sxs-lookup"><span data-stu-id="3ab1a-116">`ppEnumerator` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3ab1a-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3ab1a-117">Remarks</span></span>  
 <span data-ttu-id="3ab1a-118">Bu yöntem, [CorBindToRuntime](corbindtoruntime-function.md)gibi kullanım dışı işlevlerle yüklenseler bile, tüm yüklenen çalışma zamanlarını listeler.</span><span class="sxs-lookup"><span data-stu-id="3ab1a-118">This method is lists all loaded runtimes, even if they were loaded with deprecated functions such as [CorBindToRuntime](corbindtoruntime-function.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3ab1a-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3ab1a-119">Requirements</span></span>  
 <span data-ttu-id="3ab1a-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3ab1a-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3ab1a-121">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="3ab1a-121">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="3ab1a-122">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="3ab1a-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3ab1a-123">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3ab1a-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ab1a-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3ab1a-124">See also</span></span>

- [<span data-ttu-id="3ab1a-125">ICLRMetaHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3ab1a-125">ICLRMetaHost Interface</span></span>](iclrmetahost-interface.md)
- [<span data-ttu-id="3ab1a-126">Barındırma</span><span class="sxs-lookup"><span data-stu-id="3ab1a-126">Hosting</span></span>](index.md)
