---
title: "ResolveTypeLib Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ResolveTypeLib
api_location: tlbref.dll
f1_keywords: ResolveTypeLib
helpviewer_keywords:
- ITypeLibResolver::ResolveTypeLib method [.NET Framework]
- ResolveTypeLib method [.NET Framework]
ms.assetid: 95d2aa0d-8eeb-4a9f-a216-5249f7e2c167
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b668610f50c32373790130def17928b8b3b3d8b2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="resolvetypelib-method"></a><span data-ttu-id="5da65-102">ResolveTypeLib Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5da65-102">ResolveTypeLib Method</span></span>
<span data-ttu-id="5da65-103">Basit bir tür kitaplığı adı, tam yolunu döndürerek çözümler.</span><span class="sxs-lookup"><span data-stu-id="5da65-103">Resolves the simple name of a type library by returning its fully qualified path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5da65-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5da65-104">Syntax</span></span>  
  
```  
HRESULT ResolveTypeLib(  
    [in]  BSTR      bstrSimpleName,  
    [in]  GUID      tlbid,  
    [in]  LCID      lcid,  
    [in]  USHORT    wMajorVersion,  
    [in]  USHORT    wMinorVersion,  
    [in]  SYSKIND   syskind,  
    [out] BSTR     *pbstrResolvedTlbName);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5da65-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5da65-105">Parameters</span></span>  
 `bstrSimpleName`  
 <span data-ttu-id="5da65-106">[in] A [BSTR](http://msdn.microsoft.com/en-us/1b2d7d2c-47af-4389-a6b6-b01b7e915228) basit tür kitaplığı adını içerir.</span><span class="sxs-lookup"><span data-stu-id="5da65-106">[in] A [BSTR](http://msdn.microsoft.com/en-us/1b2d7d2c-47af-4389-a6b6-b01b7e915228) that contains the simple name of the type library.</span></span>  
  
 `tlbid`  
 <span data-ttu-id="5da65-107">[in] Tür kitaplığı kayıt defterinde atanan GUID.</span><span class="sxs-lookup"><span data-stu-id="5da65-107">[in] The GUID assigned to the type library in the registry.</span></span>  
  
 `lcid`  
 <span data-ttu-id="5da65-108">[in] Tür kitaplığı yerelleştirme kimliği.</span><span class="sxs-lookup"><span data-stu-id="5da65-108">[in] The localization ID of the type library.</span></span>  
  
 `wMajorVersion`  
 <span data-ttu-id="5da65-109">[in] Tür kitaplığı ana sürüm numarası.</span><span class="sxs-lookup"><span data-stu-id="5da65-109">[in] The major version number of the type library.</span></span> <span data-ttu-id="5da65-110">Örneğin, sürüm *x.y*, ana sürüm numarası *x*.</span><span class="sxs-lookup"><span data-stu-id="5da65-110">For example, for version *x.y*, the major version number is *x*.</span></span>  
  
 `wMinorVersion`  
 <span data-ttu-id="5da65-111">[in] Tür kitaplığı ikincil sürüm numarası.</span><span class="sxs-lookup"><span data-stu-id="5da65-111">[in] The minor version number of the type library.</span></span> <span data-ttu-id="5da65-112">Örneğin, sürüm *x.y*, ikincil sürüm numarası *y*.</span><span class="sxs-lookup"><span data-stu-id="5da65-112">For example, for version *x.y*, the minor version number is *y*.</span></span>  
  
 `syskind`  
 <span data-ttu-id="5da65-113">[in] A [SYSKIND](http://msdn.microsoft.com/en-us/662048b2-59a8-48ca-9e4f-2f9a5306faa1) işletim sistemi ortamında belirleyen bayrak.</span><span class="sxs-lookup"><span data-stu-id="5da65-113">[in] A [SYSKIND](http://msdn.microsoft.com/en-us/662048b2-59a8-48ca-9e4f-2f9a5306faa1) flag that identifies the operating environment.</span></span> <span data-ttu-id="5da65-114">SYS_WIN32 ve SYS_WIN64 bunun ortak değerlerdir.</span><span class="sxs-lookup"><span data-stu-id="5da65-114">Common values are SYS_WIN32 and SYS_WIN64.</span></span>  
  
 `pbstrResolvedTlbName`  
 <span data-ttu-id="5da65-115">[out] Bir işaretçi bir [BSTR](http://msdn.microsoft.com/en-us/1b2d7d2c-47af-4389-a6b6-b01b7e915228) adlı tür kitaplığı tam yolunu içeren `bstrSimpleName` parametresi.</span><span class="sxs-lookup"><span data-stu-id="5da65-115">[out] A pointer to a [BSTR](http://msdn.microsoft.com/en-us/1b2d7d2c-47af-4389-a6b6-b01b7e915228) that contains the full path of the type library named in the `bstrSimpleName` parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5da65-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5da65-116">Remarks</span></span>  
 <span data-ttu-id="5da65-117">`ResolveTypeLib` Yöntemi çağrılır [LoadTypeLibWithResolver işlevi](../../../../docs/framework/unmanaged-api/tlbexp/loadtypelibwithresolver-function.md) sırasında [Tlbexp.exe (tür kitaplığı dışarı Aktarıcı)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) işleme.</span><span class="sxs-lookup"><span data-stu-id="5da65-117">The `ResolveTypeLib` method is called by the [LoadTypeLibWithResolver function](../../../../docs/framework/unmanaged-api/tlbexp/loadtypelibwithresolver-function.md) during [Tlbexp.exe (Type Library Exporter)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) processing.</span></span>  
  
 <span data-ttu-id="5da65-118">Bu arabirim özel uygulamaları döndürmelidir bir [BSTR](http://msdn.microsoft.com/en-us/1b2d7d2c-47af-4389-a6b6-b01b7e915228) adlı tür kitaplığı tam yolunu içeren `bstrSimpleName` parametresi.</span><span class="sxs-lookup"><span data-stu-id="5da65-118">Custom implementations of this interface must return a [BSTR](http://msdn.microsoft.com/en-us/1b2d7d2c-47af-4389-a6b6-b01b7e915228) that contains the full path of the type library named in the `bstrSimpleName` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5da65-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5da65-119">Requirements</span></span>  
 <span data-ttu-id="5da65-120">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5da65-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5da65-121">**Başlık:** TlbRef.idl, TlbRef.h</span><span class="sxs-lookup"><span data-stu-id="5da65-121">**Header:** TlbRef.idl, TlbRef.h</span></span>  
  
 <span data-ttu-id="5da65-122">**Kitaplığı:** TlbRef.lib</span><span class="sxs-lookup"><span data-stu-id="5da65-122">**Library:** TlbRef.lib</span></span>  
  
 <span data-ttu-id="5da65-123">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5da65-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5da65-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5da65-124">See Also</span></span>  
 [<span data-ttu-id="5da65-125">Tlbexp Yardımcı İşlevleri</span><span class="sxs-lookup"><span data-stu-id="5da65-125">Tlbexp Helper Functions</span></span>](../../../../docs/framework/unmanaged-api/tlbexp/index.md)  
 [<span data-ttu-id="5da65-126">LoadTypeLibEx</span><span class="sxs-lookup"><span data-stu-id="5da65-126">LoadTypeLibEx</span></span>](http://msdn.microsoft.com/en-us/56a7f9e1-810b-4a42-aa4d-691f4304f5ef)
