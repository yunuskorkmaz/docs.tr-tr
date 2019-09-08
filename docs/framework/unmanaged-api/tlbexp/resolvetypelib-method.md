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
ms.openlocfilehash: ce0f11547d4b16516b7c78d1b1947f5c4bc831a3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798804"
---
# <a name="resolvetypelib-method"></a><span data-ttu-id="1fdd8-102">ResolveTypeLib Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1fdd8-102">ResolveTypeLib Method</span></span>
<span data-ttu-id="1fdd8-103">Tam nitelikli yolunu döndürerek bir tür kitaplığının basit adını çözer.</span><span class="sxs-lookup"><span data-stu-id="1fdd8-103">Resolves the simple name of a type library by returning its fully qualified path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1fdd8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1fdd8-104">Syntax</span></span>  
  
```cpp  
HRESULT ResolveTypeLib(  
    [in]  BSTR      bstrSimpleName,  
    [in]  GUID      tlbid,  
    [in]  LCID      lcid,  
    [in]  USHORT    wMajorVersion,  
    [in]  USHORT    wMinorVersion,  
    [in]  SYSKIND   syskind,  
    [out] BSTR     *pbstrResolvedTlbName);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1fdd8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1fdd8-105">Parameters</span></span>  
 `bstrSimpleName`  
 <span data-ttu-id="1fdd8-106">'ndaki Tür kitaplığının basit adını içeren bir [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) .</span><span class="sxs-lookup"><span data-stu-id="1fdd8-106">[in] A [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) that contains the simple name of the type library.</span></span>  
  
 `tlbid`  
 <span data-ttu-id="1fdd8-107">'ndaki Kayıt defterindeki tür kitaplığına atanan GUID.</span><span class="sxs-lookup"><span data-stu-id="1fdd8-107">[in] The GUID assigned to the type library in the registry.</span></span>  
  
 `lcid`  
 <span data-ttu-id="1fdd8-108">'ndaki Tür kitaplığının yerelleştirme KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="1fdd8-108">[in] The localization ID of the type library.</span></span>  
  
 `wMajorVersion`  
 <span data-ttu-id="1fdd8-109">'ndaki Tür kitaplığının ana sürüm numarası.</span><span class="sxs-lookup"><span data-stu-id="1fdd8-109">[in] The major version number of the type library.</span></span> <span data-ttu-id="1fdd8-110">Örneğin, *x. y*sürümü için ana sürüm numarası *x*olur.</span><span class="sxs-lookup"><span data-stu-id="1fdd8-110">For example, for version *x.y*, the major version number is *x*.</span></span>  
  
 `wMinorVersion`  
 <span data-ttu-id="1fdd8-111">'ndaki Tür kitaplığının ikincil sürüm numarası.</span><span class="sxs-lookup"><span data-stu-id="1fdd8-111">[in] The minor version number of the type library.</span></span> <span data-ttu-id="1fdd8-112">Örneğin, *x. y*sürümü için, ikincil sürüm numarası *y*' dir.</span><span class="sxs-lookup"><span data-stu-id="1fdd8-112">For example, for version *x.y*, the minor version number is *y*.</span></span>  
  
 `syskind`  
 <span data-ttu-id="1fdd8-113">'ndaki İşletim ortamını tanımlayan bir [Syskind](https://docs.microsoft.com/windows/win32/api/oaidl/ne-oaidl-syskind) bayrağı.</span><span class="sxs-lookup"><span data-stu-id="1fdd8-113">[in] A [SYSKIND](https://docs.microsoft.com/windows/win32/api/oaidl/ne-oaidl-syskind) flag that identifies the operating environment.</span></span> <span data-ttu-id="1fdd8-114">Ortak değerler SYS_WIN32 ve SYS_WIN64.</span><span class="sxs-lookup"><span data-stu-id="1fdd8-114">Common values are SYS_WIN32 and SYS_WIN64.</span></span>  
  
 `pbstrResolvedTlbName`  
 <span data-ttu-id="1fdd8-115">dışı `bstrSimpleName` Parametresinde adlı tür kitaplığının tam yolunu içeren bir [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1fdd8-115">[out] A pointer to a [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) that contains the full path of the type library named in the `bstrSimpleName` parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1fdd8-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1fdd8-116">Remarks</span></span>  
 <span data-ttu-id="1fdd8-117">Yöntemi, [Tlbexp. exe (tür kitaplığı verme programı)](../../tools/tlbexp-exe-type-library-exporter.md) işleme sırasında [LoadTypeLibWithResolver işlevi](loadtypelibwithresolver-function.md) tarafından çağrılır. `ResolveTypeLib`</span><span class="sxs-lookup"><span data-stu-id="1fdd8-117">The `ResolveTypeLib` method is called by the [LoadTypeLibWithResolver function](loadtypelibwithresolver-function.md) during [Tlbexp.exe (Type Library Exporter)](../../tools/tlbexp-exe-type-library-exporter.md) processing.</span></span>  
  
 <span data-ttu-id="1fdd8-118">Bu arabirimin özel uygulamaları, `bstrSimpleName` parametresinde adlı tür kitaplığının tam yolunu içeren bir [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="1fdd8-118">Custom implementations of this interface must return a [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) that contains the full path of the type library named in the `bstrSimpleName` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1fdd8-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1fdd8-119">Requirements</span></span>  
 <span data-ttu-id="1fdd8-120">**Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1fdd8-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1fdd8-121">**Üst bilgi** TlbRef. IDL, TlbRef. h</span><span class="sxs-lookup"><span data-stu-id="1fdd8-121">**Header:** TlbRef.idl, TlbRef.h</span></span>  
  
 <span data-ttu-id="1fdd8-122">**Kitaplığı** TlbRef. lib</span><span class="sxs-lookup"><span data-stu-id="1fdd8-122">**Library:** TlbRef.lib</span></span>  
  
 <span data-ttu-id="1fdd8-123">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1fdd8-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1fdd8-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1fdd8-124">See also</span></span>

- [<span data-ttu-id="1fdd8-125">Tlbexp Yardımcı İşlevleri</span><span class="sxs-lookup"><span data-stu-id="1fdd8-125">Tlbexp Helper Functions</span></span>](index.md)
- [<span data-ttu-id="1fdd8-126">LoadTypeLibEx</span><span class="sxs-lookup"><span data-stu-id="1fdd8-126">LoadTypeLibEx</span></span>](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
