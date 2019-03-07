---
title: ResolveTypeLib Yöntemi
ms.date: 03/30/2017
api_name:
- ResolveTypeLib
api_location:
- tlbref.dll
f1_keywords:
- ResolveTypeLib
helpviewer_keywords:
- ITypeLibResolver::ResolveTypeLib method [.NET Framework]
- ResolveTypeLib method [.NET Framework]
ms.assetid: 95d2aa0d-8eeb-4a9f-a216-5249f7e2c167
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5b87460b9e525f2cf91b8f177c06286b5bbb3c52
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57486127"
---
# <a name="resolvetypelib-method"></a><span data-ttu-id="76ab4-102">ResolveTypeLib Yöntemi</span><span class="sxs-lookup"><span data-stu-id="76ab4-102">ResolveTypeLib Method</span></span>
<span data-ttu-id="76ab4-103">Basit bir tür kitaplığı adı, tam nitelenmiş bir yol döndürerek çözümler.</span><span class="sxs-lookup"><span data-stu-id="76ab4-103">Resolves the simple name of a type library by returning its fully qualified path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76ab4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="76ab4-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="76ab4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="76ab4-105">Parameters</span></span>  
 `bstrSimpleName`  
 <span data-ttu-id="76ab4-106">[in] A [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) içeren basit tür kitaplığı adı.</span><span class="sxs-lookup"><span data-stu-id="76ab4-106">[in] A [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) that contains the simple name of the type library.</span></span>  
  
 `tlbid`  
 <span data-ttu-id="76ab4-107">[in] Kayıt defterinde tür kitaplığına atanan GUID.</span><span class="sxs-lookup"><span data-stu-id="76ab4-107">[in] The GUID assigned to the type library in the registry.</span></span>  
  
 `lcid`  
 <span data-ttu-id="76ab4-108">[in] Tür kitaplığının yerelleştirme kimliği.</span><span class="sxs-lookup"><span data-stu-id="76ab4-108">[in] The localization ID of the type library.</span></span>  
  
 `wMajorVersion`  
 <span data-ttu-id="76ab4-109">[in] Tür kitaplığı sürüm sayısı.</span><span class="sxs-lookup"><span data-stu-id="76ab4-109">[in] The major version number of the type library.</span></span> <span data-ttu-id="76ab4-110">Örneğin, sürüm için *x.y*, ana sürüm numarası *x*.</span><span class="sxs-lookup"><span data-stu-id="76ab4-110">For example, for version *x.y*, the major version number is *x*.</span></span>  
  
 `wMinorVersion`  
 <span data-ttu-id="76ab4-111">[in] Tür kitaplığının ikincil sürüm numarası.</span><span class="sxs-lookup"><span data-stu-id="76ab4-111">[in] The minor version number of the type library.</span></span> <span data-ttu-id="76ab4-112">Örneğin, sürüm için *x.y*, ikincil sürüm numarası *y*.</span><span class="sxs-lookup"><span data-stu-id="76ab4-112">For example, for version *x.y*, the minor version number is *y*.</span></span>  
  
 `syskind`  
 <span data-ttu-id="76ab4-113">[in] A [SYSKIND](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/ne-oaidl-tagsyskind) işletim ortamını belirten bayrak.</span><span class="sxs-lookup"><span data-stu-id="76ab4-113">[in] A [SYSKIND](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/ne-oaidl-tagsyskind) flag that identifies the operating environment.</span></span> <span data-ttu-id="76ab4-114">Genel değerler şunlardır: SYS_WIN32 ve SYS_WIN64.</span><span class="sxs-lookup"><span data-stu-id="76ab4-114">Common values are SYS_WIN32 and SYS_WIN64.</span></span>  
  
 `pbstrResolvedTlbName`  
 <span data-ttu-id="76ab4-115">[out] Bir işaretçi bir [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) adlı tür kitaplığının tam yolu içeren `bstrSimpleName` parametresi.</span><span class="sxs-lookup"><span data-stu-id="76ab4-115">[out] A pointer to a [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) that contains the full path of the type library named in the `bstrSimpleName` parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="76ab4-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="76ab4-116">Remarks</span></span>  
 <span data-ttu-id="76ab4-117">`ResolveTypeLib` Yöntemi tarafından çağrılır [LoadTypeLibWithResolver işlevi](../../../../docs/framework/unmanaged-api/tlbexp/loadtypelibwithresolver-function.md) sırasında [Tlbexp.exe (tür kitaplığı dışarı Aktarıcı)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) işleniyor.</span><span class="sxs-lookup"><span data-stu-id="76ab4-117">The `ResolveTypeLib` method is called by the [LoadTypeLibWithResolver function](../../../../docs/framework/unmanaged-api/tlbexp/loadtypelibwithresolver-function.md) during [Tlbexp.exe (Type Library Exporter)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) processing.</span></span>  
  
 <span data-ttu-id="76ab4-118">Bu arabirim özel uygulamaları döndürmelidir bir [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) adlı tür kitaplığının tam yolu içeren `bstrSimpleName` parametresi.</span><span class="sxs-lookup"><span data-stu-id="76ab4-118">Custom implementations of this interface must return a [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) that contains the full path of the type library named in the `bstrSimpleName` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="76ab4-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="76ab4-119">Requirements</span></span>  
 <span data-ttu-id="76ab4-120">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="76ab4-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="76ab4-121">**Üst bilgi:** TlbRef.idl, TlbRef.h</span><span class="sxs-lookup"><span data-stu-id="76ab4-121">**Header:** TlbRef.idl, TlbRef.h</span></span>  
  
 <span data-ttu-id="76ab4-122">**Kitaplığı:** TlbRef.lib</span><span class="sxs-lookup"><span data-stu-id="76ab4-122">**Library:** TlbRef.lib</span></span>  
  
 <span data-ttu-id="76ab4-123">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="76ab4-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76ab4-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="76ab4-124">See also</span></span>
- [<span data-ttu-id="76ab4-125">Tlbexp Yardımcı İşlevleri</span><span class="sxs-lookup"><span data-stu-id="76ab4-125">Tlbexp Helper Functions</span></span>](../../../../docs/framework/unmanaged-api/tlbexp/index.md)
- [<span data-ttu-id="76ab4-126">LoadTypeLibEx</span><span class="sxs-lookup"><span data-stu-id="76ab4-126">LoadTypeLibEx</span></span>](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
