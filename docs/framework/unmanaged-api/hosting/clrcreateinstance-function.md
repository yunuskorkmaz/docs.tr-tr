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
ms.openlocfilehash: 5d25ca8ea33aacf88a3359335b2b4bbfb91c06eb
ms.sourcegitcommit: 80f38cb67bd02f51d5722fa13d0ea207e3b14a8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/26/2021
ms.locfileid: "105610882"
---
# <a name="clrcreateinstance-function"></a><span data-ttu-id="75aa4-103">CLRCreateInstance İşlevi</span><span class="sxs-lookup"><span data-stu-id="75aa4-103">CLRCreateInstance Function</span></span>

<span data-ttu-id="75aa4-104">Üç arabirimden birini sunar: [ICLRMetaHost](iclrmetahost-interface.md), [ICLRMetaHostPolicy](iclrmetahostpolicy-interface.md)veya [ICLRDebugging](../debugging/iclrdebugging-interface.md).</span><span class="sxs-lookup"><span data-stu-id="75aa4-104">Provides one of three interfaces: [ICLRMetaHost](iclrmetahost-interface.md), [ICLRMetaHostPolicy](iclrmetahostpolicy-interface.md), or [ICLRDebugging](../debugging/iclrdebugging-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75aa4-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="75aa4-105">Syntax</span></span>  
  
```cpp  
HRESULT CLRCreateInstance(  
    [in]  REFCLSID  clsid,  
    [in]  REFIID     riid,  
    [out] LPVOID  * ppInterface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="75aa4-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="75aa4-106">Parameters</span></span>  

 `clsid`  
 <span data-ttu-id="75aa4-107">'ndaki Üç sınıf tanımlayıcılarından biri: CLSID_CLRMetaHost, CLSID_CLRMetaHostPolicy veya CLSID_CLRDebugging.</span><span class="sxs-lookup"><span data-stu-id="75aa4-107">[in] One of three class identifiers: CLSID_CLRMetaHost, CLSID_CLRMetaHostPolicy, or CLSID_CLRDebugging.</span></span>  
  
 `riid`  
 <span data-ttu-id="75aa4-108">'ndaki Üç arabirim tanımlayıcılarından biri (IIDS): IID_ICLRMetaHost, IID_ICLRMetaHostPolicy veya IID_ICLRDebugging.</span><span class="sxs-lookup"><span data-stu-id="75aa4-108">[in] One of three interface identifiers (IIDs): IID_ICLRMetaHost, IID_ICLRMetaHostPolicy, or IID_ICLRDebugging.</span></span>  
  
 `ppInterface`  
 <span data-ttu-id="75aa4-109">dışı Üç arabirimden biri: [ICLRMetaHost](iclrmetahost-interface.md), [ICLRMetaHostPolicy](iclrmetahostpolicy-interface.md)veya [ICLRDebugging](../debugging/iclrdebugging-interface.md).</span><span class="sxs-lookup"><span data-stu-id="75aa4-109">[out] One of three interfaces: [ICLRMetaHost](iclrmetahost-interface.md), [ICLRMetaHostPolicy](iclrmetahostpolicy-interface.md), or [ICLRDebugging](../debugging/iclrdebugging-interface.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="75aa4-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="75aa4-110">Return Value</span></span>  

 <span data-ttu-id="75aa4-111">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="75aa4-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="75aa4-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="75aa4-112">HRESULT</span></span>|<span data-ttu-id="75aa4-113">Description</span><span class="sxs-lookup"><span data-stu-id="75aa4-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="75aa4-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="75aa4-114">S_OK</span></span>|<span data-ttu-id="75aa4-115">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="75aa4-115">The method completed successfully.</span></span>|  
|<span data-ttu-id="75aa4-116">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="75aa4-116">E_POINTER</span></span>|<span data-ttu-id="75aa4-117">`ppInterface` null.</span><span class="sxs-lookup"><span data-stu-id="75aa4-117">`ppInterface` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="75aa4-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="75aa4-118">Remarks</span></span>  

 <span data-ttu-id="75aa4-119">Aşağıdaki tabloda ve için desteklenen birleşimler gösterilmektedir `clsid` `riid` .</span><span class="sxs-lookup"><span data-stu-id="75aa4-119">The following table shows the supported combinations for `clsid` and `riid`.</span></span>  
  
|`clsid`|`riid`|  
|--------------|------------|  
|<span data-ttu-id="75aa4-120">CLSID_CLRMetaHost</span><span class="sxs-lookup"><span data-stu-id="75aa4-120">CLSID_CLRMetaHost</span></span>|<span data-ttu-id="75aa4-121">IID_ICLRMetaHost</span><span class="sxs-lookup"><span data-stu-id="75aa4-121">IID_ICLRMetaHost</span></span>|  
|<span data-ttu-id="75aa4-122">CLSID_CLRMetaHostPolicy</span><span class="sxs-lookup"><span data-stu-id="75aa4-122">CLSID_CLRMetaHostPolicy</span></span>|<span data-ttu-id="75aa4-123">IID_ICLRMetaHostPolicy</span><span class="sxs-lookup"><span data-stu-id="75aa4-123">IID_ICLRMetaHostPolicy</span></span>|  
|<span data-ttu-id="75aa4-124">CLSID_CLRDebugging</span><span class="sxs-lookup"><span data-stu-id="75aa4-124">CLSID_CLRDebugging</span></span>|<span data-ttu-id="75aa4-125">IID_ICLRDebugging</span><span class="sxs-lookup"><span data-stu-id="75aa4-125">IID_ICLRDebugging</span></span>|  
  
 <span data-ttu-id="75aa4-126">Aşağıdaki kod, `CLRCreateInstance` üç arabirimi de almak için nasıl kullanılacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="75aa4-126">The following code shows how to use `CLRCreateInstance` to get all three interfaces:</span></span>  
  
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

<span data-ttu-id="75aa4-127">`CreateInterface`İşlevin diğer adı `CLRCreateInstance` .</span><span class="sxs-lookup"><span data-stu-id="75aa4-127">The `CreateInterface` function is aliased to `CLRCreateInstance`.</span></span>  <span data-ttu-id="75aa4-128">Hem hem de `CLRCreateInstance` `CreateInterface` işlevleri birbirinin yerine kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="75aa4-128">Both `CLRCreateInstance` and `CreateInterface` functions can be used interchangeably.</span></span> <span data-ttu-id="75aa4-129">Örnek:</span><span class="sxs-lookup"><span data-stu-id="75aa4-129">For example:</span></span>

```cpp
HMODULE hModule = LoadLibrary(L"mscoree.dll");
CreateInterfaceFnPtr createInterface = (CreateInterfaceFnPtr)GetProcAddress(hModule, "CreateInterface");
HRESULT hr;
hr = createInterface(CLSID_CLRMetaHost, IID_ICLRMetaHost, (LPVOID*)&pMetaHost);
hr = createInterface (CLSID_CLRMetaHostPolicy, IID_ICLRMetaHostPolicy,  (LPVOID*)&pMetaHostPolicy);  
hr = createInterface (CLSID_CLRDebugging, IID_ICLRDebugging,  (LPVOID*)&pCLRDebugging); 
```
  
## <a name="requirements"></a><span data-ttu-id="75aa4-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="75aa4-130">Requirements</span></span>  

 <span data-ttu-id="75aa4-131">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="75aa4-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75aa4-132">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="75aa4-132">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="75aa4-133">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="75aa4-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="75aa4-134">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="75aa4-134">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75aa4-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="75aa4-135">See also</span></span>

- [<span data-ttu-id="75aa4-136">Barındırma</span><span class="sxs-lookup"><span data-stu-id="75aa4-136">Hosting</span></span>](index.md)
