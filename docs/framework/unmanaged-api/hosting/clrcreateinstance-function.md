---
description: 'Şu konuda daha fazla bilgi edinin: CLRCreateInstance Işlevi'
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
ms.openlocfilehash: ac81aeadce651a04e2cabc8a6740fe86825edcc3
ms.sourcegitcommit: 44af69720863bd09bd7a4509bf1ec119466ba6e8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2021
ms.locfileid: "106231355"
---
# <a name="clrcreateinstance-function"></a><span data-ttu-id="3a0d0-103">CLRCreateInstance İşlevi</span><span class="sxs-lookup"><span data-stu-id="3a0d0-103">CLRCreateInstance Function</span></span>

<span data-ttu-id="3a0d0-104">Üç arabirimden birini sunar: [ICLRMetaHost](iclrmetahost-interface.md), [ICLRMetaHostPolicy](iclrmetahostpolicy-interface.md)veya [ICLRDebugging](../debugging/iclrdebugging-interface.md).</span><span class="sxs-lookup"><span data-stu-id="3a0d0-104">Provides one of three interfaces: [ICLRMetaHost](iclrmetahost-interface.md), [ICLRMetaHostPolicy](iclrmetahostpolicy-interface.md), or [ICLRDebugging](../debugging/iclrdebugging-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a0d0-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3a0d0-105">Syntax</span></span>  
  
```cpp  
HRESULT CLRCreateInstance(  
    [in]  REFCLSID  clsid,  
    [in]  REFIID     riid,  
    [out] LPVOID  * ppInterface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3a0d0-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3a0d0-106">Parameters</span></span>  

 `clsid`  
 <span data-ttu-id="3a0d0-107">'ndaki Üç sınıf tanımlayıcılarından biri: CLSID_CLRMetaHost, CLSID_CLRMetaHostPolicy veya CLSID_CLRDebugging.</span><span class="sxs-lookup"><span data-stu-id="3a0d0-107">[in] One of three class identifiers: CLSID_CLRMetaHost, CLSID_CLRMetaHostPolicy, or CLSID_CLRDebugging.</span></span>  
  
 `riid`  
 <span data-ttu-id="3a0d0-108">'ndaki Üç arabirim tanımlayıcılarından biri (IIDS): IID_ICLRMetaHost, IID_ICLRMetaHostPolicy veya IID_ICLRDebugging.</span><span class="sxs-lookup"><span data-stu-id="3a0d0-108">[in] One of three interface identifiers (IIDs): IID_ICLRMetaHost, IID_ICLRMetaHostPolicy, or IID_ICLRDebugging.</span></span>  
  
 `ppInterface`  
 <span data-ttu-id="3a0d0-109">dışı Üç arabirimden biri: [ICLRMetaHost](iclrmetahost-interface.md), [ICLRMetaHostPolicy](iclrmetahostpolicy-interface.md)veya [ICLRDebugging](../debugging/iclrdebugging-interface.md).</span><span class="sxs-lookup"><span data-stu-id="3a0d0-109">[out] One of three interfaces: [ICLRMetaHost](iclrmetahost-interface.md), [ICLRMetaHostPolicy](iclrmetahostpolicy-interface.md), or [ICLRDebugging](../debugging/iclrdebugging-interface.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3a0d0-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3a0d0-110">Return Value</span></span>  

 <span data-ttu-id="3a0d0-111">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="3a0d0-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="3a0d0-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3a0d0-112">HRESULT</span></span>|<span data-ttu-id="3a0d0-113">Description</span><span class="sxs-lookup"><span data-stu-id="3a0d0-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3a0d0-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="3a0d0-114">S_OK</span></span>|<span data-ttu-id="3a0d0-115">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="3a0d0-115">The method completed successfully.</span></span>|  
|<span data-ttu-id="3a0d0-116">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="3a0d0-116">E_POINTER</span></span>|<span data-ttu-id="3a0d0-117">`ppInterface` null.</span><span class="sxs-lookup"><span data-stu-id="3a0d0-117">`ppInterface` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3a0d0-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3a0d0-118">Remarks</span></span>  

 <span data-ttu-id="3a0d0-119">Aşağıdaki tabloda ve için desteklenen birleşimler gösterilmektedir `clsid` `riid` .</span><span class="sxs-lookup"><span data-stu-id="3a0d0-119">The following table shows the supported combinations for `clsid` and `riid`.</span></span>  
  
|`clsid`|`riid`|  
|--------------|------------|  
|<span data-ttu-id="3a0d0-120">CLSID_CLRMetaHost</span><span class="sxs-lookup"><span data-stu-id="3a0d0-120">CLSID_CLRMetaHost</span></span>|<span data-ttu-id="3a0d0-121">IID_ICLRMetaHost</span><span class="sxs-lookup"><span data-stu-id="3a0d0-121">IID_ICLRMetaHost</span></span>|  
|<span data-ttu-id="3a0d0-122">CLSID_CLRMetaHostPolicy</span><span class="sxs-lookup"><span data-stu-id="3a0d0-122">CLSID_CLRMetaHostPolicy</span></span>|<span data-ttu-id="3a0d0-123">IID_ICLRMetaHostPolicy</span><span class="sxs-lookup"><span data-stu-id="3a0d0-123">IID_ICLRMetaHostPolicy</span></span>|  
|<span data-ttu-id="3a0d0-124">CLSID_CLRDebugging</span><span class="sxs-lookup"><span data-stu-id="3a0d0-124">CLSID_CLRDebugging</span></span>|<span data-ttu-id="3a0d0-125">IID_ICLRDebugging</span><span class="sxs-lookup"><span data-stu-id="3a0d0-125">IID_ICLRDebugging</span></span>|  
  
 <span data-ttu-id="3a0d0-126">Aşağıdaki kod, `CLRCreateInstance` üç arabirimi de almak için nasıl kullanılacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="3a0d0-126">The following code shows how to use `CLRCreateInstance` to get all three interfaces:</span></span>  
  
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

<span data-ttu-id="3a0d0-127">`CreateInterface`İşlevin diğer adı `CLRCreateInstance` .</span><span class="sxs-lookup"><span data-stu-id="3a0d0-127">The `CreateInterface` function is aliased to `CLRCreateInstance`.</span></span>  <span data-ttu-id="3a0d0-128">Hem hem de `CLRCreateInstance` `CreateInterface` işlevleri birbirinin yerine kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3a0d0-128">Both `CLRCreateInstance` and `CreateInterface` functions can be used interchangeably.</span></span> <span data-ttu-id="3a0d0-129">Örnek:</span><span class="sxs-lookup"><span data-stu-id="3a0d0-129">For example:</span></span>

```cpp
HMODULE hModule = LoadLibrary(L"mscoree.dll");
CreateInterfaceFnPtr createInterface = (CreateInterfaceFnPtr)GetProcAddress(hModule, "CreateInterface");
HRESULT hr;
hr = createInterface(CLSID_CLRMetaHost, IID_ICLRMetaHost, (LPVOID*)&pMetaHost);
hr = createInterface (CLSID_CLRMetaHostPolicy, IID_ICLRMetaHostPolicy,  (LPVOID*)&pMetaHostPolicy);  
hr = createInterface (CLSID_CLRDebugging, IID_ICLRDebugging,  (LPVOID*)&pCLRDebugging);
```
  
## <a name="requirements"></a><span data-ttu-id="3a0d0-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3a0d0-130">Requirements</span></span>  

 <span data-ttu-id="3a0d0-131">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3a0d0-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a0d0-132">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="3a0d0-132">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="3a0d0-133">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="3a0d0-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3a0d0-134">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a0d0-134">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a0d0-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3a0d0-135">See also</span></span>

- [<span data-ttu-id="3a0d0-136">Barındırma</span><span class="sxs-lookup"><span data-stu-id="3a0d0-136">Hosting</span></span>](index.md)
