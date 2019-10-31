---
title: CLRCreateInstance İşlevi
ms.date: 03/30/2017
api_name:
- CLRCreateInstance
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- COM
f1_keywords:
- CLRCreateInstance
helpviewer_keywords:
- CLRCreateInstance function [.NET Framework hosting]
ms.assetid: 5de13327-96c6-4697-a89e-b8bf40717855
topic_type:
- apiref
ms.openlocfilehash: c1d796c6ef5f707f865a60023899d3b451c2085b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131950"
---
# <a name="clrcreateinstance-function"></a><span data-ttu-id="3313b-102">CLRCreateInstance İşlevi</span><span class="sxs-lookup"><span data-stu-id="3313b-102">CLRCreateInstance Function</span></span>
<span data-ttu-id="3313b-103">Üç arabirimden birini sunar: [ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md), [ICLRMetaHostPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md)veya [ICLRDebugging](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-interface.md).</span><span class="sxs-lookup"><span data-stu-id="3313b-103">Provides one of three interfaces: [ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md), [ICLRMetaHostPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md), or [ICLRDebugging](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3313b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3313b-104">Syntax</span></span>  
  
```cpp  
HRESULT CLRCreateInstance(  
    [in]  REFCLSID  clsid,  
    [in]  REFIID     riid,  
    [out] LPVOID  * ppInterface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3313b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3313b-105">Parameters</span></span>  
 `clsid`  
 <span data-ttu-id="3313b-106">'ndaki Üç sınıf tanımlayıcılarından biri: CLSID_CLRMetaHost, CLSID_CLRMetaHostPolicy veya CLSID_CLRDebugging.</span><span class="sxs-lookup"><span data-stu-id="3313b-106">[in] One of three class identifiers: CLSID_CLRMetaHost, CLSID_CLRMetaHostPolicy, or CLSID_CLRDebugging.</span></span>  
  
 `riid`  
 <span data-ttu-id="3313b-107">'ndaki Üç arabirim tanımlayıcılarından biri (IIDS): IID_ICLRMetaHost, IID_ICLRMetaHostPolicy veya IID_ICLRDebugging.</span><span class="sxs-lookup"><span data-stu-id="3313b-107">[in] One of three interface identifiers (IIDs): IID_ICLRMetaHost, IID_ICLRMetaHostPolicy, or IID_ICLRDebugging.</span></span>  
  
 `ppInterface`  
 <span data-ttu-id="3313b-108">dışı Üç arabirimden biri: [ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md), [ICLRMetaHostPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md)veya [ICLRDebugging](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-interface.md).</span><span class="sxs-lookup"><span data-stu-id="3313b-108">[out] One of three interfaces: [ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md), [ICLRMetaHostPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md), or [ICLRDebugging](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-interface.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3313b-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3313b-109">Return Value</span></span>  
 <span data-ttu-id="3313b-110">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="3313b-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="3313b-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3313b-111">HRESULT</span></span>|<span data-ttu-id="3313b-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3313b-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3313b-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="3313b-113">S_OK</span></span>|<span data-ttu-id="3313b-114">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="3313b-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="3313b-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="3313b-115">E_POINTER</span></span>|<span data-ttu-id="3313b-116">`ppInterface` null.</span><span class="sxs-lookup"><span data-stu-id="3313b-116">`ppInterface` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3313b-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3313b-117">Remarks</span></span>  
 <span data-ttu-id="3313b-118">Aşağıdaki tabloda `clsid` ve `riid`için desteklenen birleşimler gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="3313b-118">The following table shows the supported combinations for `clsid` and `riid`.</span></span>  
  
|`clsid`|`riid`|  
|--------------|------------|  
|<span data-ttu-id="3313b-119">CLSID_CLRMetaHost</span><span class="sxs-lookup"><span data-stu-id="3313b-119">CLSID_CLRMetaHost</span></span>|<span data-ttu-id="3313b-120">IID_ICLRMetaHost</span><span class="sxs-lookup"><span data-stu-id="3313b-120">IID_ICLRMetaHost</span></span>|  
|<span data-ttu-id="3313b-121">CLSID_CLRMetaHostPolicy</span><span class="sxs-lookup"><span data-stu-id="3313b-121">CLSID_CLRMetaHostPolicy</span></span>|<span data-ttu-id="3313b-122">IID_ICLRMetaHostPolicy</span><span class="sxs-lookup"><span data-stu-id="3313b-122">IID_ICLRMetaHostPolicy</span></span>|  
|<span data-ttu-id="3313b-123">CLSID_CLRDebugging</span><span class="sxs-lookup"><span data-stu-id="3313b-123">CLSID_CLRDebugging</span></span>|<span data-ttu-id="3313b-124">IID_ICLRDebugging</span><span class="sxs-lookup"><span data-stu-id="3313b-124">IID_ICLRDebugging</span></span>|  
  
 <span data-ttu-id="3313b-125">Aşağıdaki kod, üç arabirimi de almak için `CLRCreateInstance` nasıl kullanacağınızı gösterir:</span><span class="sxs-lookup"><span data-stu-id="3313b-125">The following code shows how to use `CLRCreateInstance` to get all three interfaces:</span></span>  
  
```cpp  
#include <metahost.h>  
#pragma comment(lib, "mscoree.lib")  
  
ICLRMetaHost       *pMetaHost       = NULL;  
ICLRMetaHostPolicy *pMetaHostPolicy = NULL;  
ICLRDebugging      *pCLRDebugging   = NULL;  
HRESULT hr;  
hr = CLRCreateInstance(CLSID_CLRMetaHost, IID_ICLRMetaHost,  
                    (LPVOID*)&pMetaHost);  
hr = CLRCreateInstance (CLSID_CLRMetaHostPolicy, IID_ICLRMetaHostPolicy,  
                    (LPVOID*)&pMetaHostPolicy);  
hr = CLRCreateInstance (CLSID_CLRDebugging, IID_ICLRDebugging,  
                    (LPVOID*)&pCLRDebugging);  
```  
  
## <a name="requirements"></a><span data-ttu-id="3313b-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3313b-126">Requirements</span></span>  
 <span data-ttu-id="3313b-127">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3313b-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3313b-128">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="3313b-128">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="3313b-129">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="3313b-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3313b-130">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3313b-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3313b-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3313b-131">See also</span></span>

- [<span data-ttu-id="3313b-132">Barındırma</span><span class="sxs-lookup"><span data-stu-id="3313b-132">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
