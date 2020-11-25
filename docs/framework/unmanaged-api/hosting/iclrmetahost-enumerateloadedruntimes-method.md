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
ms.openlocfilehash: 98184dd6ea16df066905039b028acd689ff3f290
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730441"
---
# <a name="iclrmetahostenumerateloadedruntimes-method"></a><span data-ttu-id="4bd5e-102">ICLRMetaHost::EnumerateLoadedRuntimes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4bd5e-102">ICLRMetaHost::EnumerateLoadedRuntimes Method</span></span>

<span data-ttu-id="4bd5e-103">Belirli bir işlemde yüklenen ortak dil çalışma zamanının (CLR) her sürümü için geçerli bir [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) arabirimi işaretçisi içeren bir sabit listesi döndürür.</span><span class="sxs-lookup"><span data-stu-id="4bd5e-103">Returns an enumeration that includes a valid [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface pointer for each version of the common language runtime (CLR) that is loaded in a given process.</span></span> <span data-ttu-id="4bd5e-104">Bu yöntem [GetVersionFromProcess](getversionfromprocess-function.md) işlevinin yerini alır.</span><span class="sxs-lookup"><span data-stu-id="4bd5e-104">This method supersedes the [GetVersionFromProcess](getversionfromprocess-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4bd5e-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="4bd5e-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateLoadedRuntimes (  
    [in] HANDLE hndProcess,  
    [out, retval] IEnumUnknown **ppEnumerator  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4bd5e-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4bd5e-106">Parameters</span></span>  

 `hndProcess`  
 <span data-ttu-id="4bd5e-107">'ndaki Yüklenen çalışma zamanları için İnceleme işleminin tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="4bd5e-107">[in] The handle of the process to inspect for loaded runtimes.</span></span>  
  
 `ppEnumerator`  
 <span data-ttu-id="4bd5e-108">dışı <xref:Microsoft.VisualStudio.OLE.Interop.IEnumUnknown> İşlem tarafından yüklenen her clr 'ye karşılık gelen [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) arabirimlerinin numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="4bd5e-108">[out] An <xref:Microsoft.VisualStudio.OLE.Interop.IEnumUnknown> enumeration of [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interfaces corresponding to each CLR that is loaded by the process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4bd5e-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="4bd5e-109">Return Value</span></span>  

 <span data-ttu-id="4bd5e-110">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="4bd5e-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="4bd5e-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4bd5e-111">HRESULT</span></span>|<span data-ttu-id="4bd5e-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4bd5e-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4bd5e-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="4bd5e-113">S_OK</span></span>|<span data-ttu-id="4bd5e-114">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="4bd5e-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="4bd5e-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="4bd5e-115">E_POINTER</span></span>|<span data-ttu-id="4bd5e-116">`ppEnumerator` null.</span><span class="sxs-lookup"><span data-stu-id="4bd5e-116">`ppEnumerator` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4bd5e-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4bd5e-117">Remarks</span></span>  

 <span data-ttu-id="4bd5e-118">Bu yöntem, [CorBindToRuntime](corbindtoruntime-function.md)gibi kullanım dışı işlevlerle yüklenseler bile, tüm yüklenen çalışma zamanlarını listeler.</span><span class="sxs-lookup"><span data-stu-id="4bd5e-118">This method is lists all loaded runtimes, even if they were loaded with deprecated functions such as [CorBindToRuntime](corbindtoruntime-function.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4bd5e-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4bd5e-119">Requirements</span></span>  

 <span data-ttu-id="4bd5e-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4bd5e-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4bd5e-121">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="4bd5e-121">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="4bd5e-122">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="4bd5e-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4bd5e-123">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4bd5e-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4bd5e-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4bd5e-124">See also</span></span>

- [<span data-ttu-id="4bd5e-125">ICLRMetaHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4bd5e-125">ICLRMetaHost Interface</span></span>](iclrmetahost-interface.md)
- [<span data-ttu-id="4bd5e-126">Hosting</span><span class="sxs-lookup"><span data-stu-id="4bd5e-126">Hosting</span></span>](index.md)
