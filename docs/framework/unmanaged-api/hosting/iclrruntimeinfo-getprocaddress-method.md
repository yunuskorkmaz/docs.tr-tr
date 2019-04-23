---
title: ICLRRuntimeInfo::GetProcAddress Metodu
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.GetProcAddress
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::GetProcAddress
helpviewer_keywords:
- GetProcAddress method [.NET Framework hosting]
- ICLRRuntimeInfo::GetProcAddress method [.NET Framework hosting]
ms.assetid: a7732bfc-689a-4926-88fd-4f81e6f9ed78
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a95b6b7e20bbcd86dedf187c932f2cf74d37cdab
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59199186"
---
# <a name="iclrruntimeinfogetprocaddress-method"></a><span data-ttu-id="7d7fc-102">ICLRRuntimeInfo::GetProcAddress Metodu</span><span class="sxs-lookup"><span data-stu-id="7d7fc-102">ICLRRuntimeInfo::GetProcAddress Method</span></span>
<span data-ttu-id="7d7fc-103">Bu arabirim ile ilişkili ortak dil çalışma zamanı (CLR) dışarı aktarılan belirtilen işlevin adresini alır.</span><span class="sxs-lookup"><span data-stu-id="7d7fc-103">Gets the address of a specified function that was exported from the common language runtime (CLR) associated with this interface.</span></span>  
  
 <span data-ttu-id="7d7fc-104">Bu yöntem yerine geçer [GetRealProcAddress](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="7d7fc-104">This method supersedes the [GetRealProcAddress](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d7fc-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7d7fc-105">Syntax</span></span>  
  
```  
HRESULT GetProcAddress(  
     [in]  LPCSTR pszProcName,  
     [out, retval] LPVOID *ppProc);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7d7fc-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7d7fc-106">Parameters</span></span>  
 `pszProcName`  
 <span data-ttu-id="7d7fc-107">[in] Dışarı aktarılan işlevin adı.</span><span class="sxs-lookup"><span data-stu-id="7d7fc-107">[in] The name of the exported function.</span></span>  
  
 `ppProc`  
 <span data-ttu-id="7d7fc-108">[out] Dışarı aktarılan işlevin adresi.</span><span class="sxs-lookup"><span data-stu-id="7d7fc-108">[out] The address of the exported function.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7d7fc-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="7d7fc-109">Return Value</span></span>  
 <span data-ttu-id="7d7fc-110">Bu yöntem aşağıdaki özel HRESULT'ları yanı sıra HRESULT döndürür yöntemi hatayı gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="7d7fc-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="7d7fc-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7d7fc-111">HRESULT</span></span>|<span data-ttu-id="7d7fc-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7d7fc-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7d7fc-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="7d7fc-113">S_OK</span></span>|<span data-ttu-id="7d7fc-114">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="7d7fc-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="7d7fc-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="7d7fc-115">E_POINTER</span></span>|<span data-ttu-id="7d7fc-116">`pszProcName` veya `ppProc` null.</span><span class="sxs-lookup"><span data-stu-id="7d7fc-116">`pszProcName` or `ppProc` is null.</span></span>|  
|<span data-ttu-id="7d7fc-117">CLR_E_SHIM_RUNTIMEEXPORT</span><span class="sxs-lookup"><span data-stu-id="7d7fc-117">CLR_E_SHIM_RUNTIMEEXPORT</span></span>|<span data-ttu-id="7d7fc-118">Belirtilen işlevi dışa aktarılan bir işlevin değil.</span><span class="sxs-lookup"><span data-stu-id="7d7fc-118">The specified function is not an exported function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7d7fc-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7d7fc-119">Remarks</span></span>  
 <span data-ttu-id="7d7fc-120">Bu yöntem CLR'nin yüklendi ancak başlatılmadı neden olur.</span><span class="sxs-lookup"><span data-stu-id="7d7fc-120">This method causes the CLR to be loaded but not initialized.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d7fc-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7d7fc-121">Requirements</span></span>  
 <span data-ttu-id="7d7fc-122">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7d7fc-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d7fc-123">**Üst bilgi:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="7d7fc-123">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="7d7fc-124">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="7d7fc-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7d7fc-125">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d7fc-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d7fc-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7d7fc-126">See also</span></span>

- [<span data-ttu-id="7d7fc-127">ICLRRuntimeInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7d7fc-127">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="7d7fc-128">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="7d7fc-128">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="7d7fc-129">Barındırma</span><span class="sxs-lookup"><span data-stu-id="7d7fc-129">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
