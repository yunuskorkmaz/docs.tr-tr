---
description: Daha fazla bilgi için bkz. Resolvettypeınfo LIB yöntemi
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
ms.openlocfilehash: ca7f94f630479d30bb9129497b38bcf04e759e5d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99646289"
---
# <a name="resolvetypelib-method"></a><span data-ttu-id="86a1f-103">ResolveTypeLib Yöntemi</span><span class="sxs-lookup"><span data-stu-id="86a1f-103">ResolveTypeLib Method</span></span>

<span data-ttu-id="86a1f-104">Tam nitelikli yolunu döndürerek bir tür kitaplığının basit adını çözer.</span><span class="sxs-lookup"><span data-stu-id="86a1f-104">Resolves the simple name of a type library by returning its fully qualified path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86a1f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="86a1f-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="86a1f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="86a1f-106">Parameters</span></span>  

 `bstrSimpleName`  
 <span data-ttu-id="86a1f-107">'ndaki Tür kitaplığının basit adını içeren bir [BSTR](/previous-versions/windows/desktop/automat/bstr) .</span><span class="sxs-lookup"><span data-stu-id="86a1f-107">[in] A [BSTR](/previous-versions/windows/desktop/automat/bstr) that contains the simple name of the type library.</span></span>  
  
 `tlbid`  
 <span data-ttu-id="86a1f-108">'ndaki Kayıt defterindeki tür kitaplığına atanan GUID.</span><span class="sxs-lookup"><span data-stu-id="86a1f-108">[in] The GUID assigned to the type library in the registry.</span></span>  
  
 `lcid`  
 <span data-ttu-id="86a1f-109">'ndaki Tür kitaplığının yerelleştirme KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="86a1f-109">[in] The localization ID of the type library.</span></span>  
  
 `wMajorVersion`  
 <span data-ttu-id="86a1f-110">'ndaki Tür kitaplığının ana sürüm numarası.</span><span class="sxs-lookup"><span data-stu-id="86a1f-110">[in] The major version number of the type library.</span></span> <span data-ttu-id="86a1f-111">Örneğin, *x. y* sürümü için ana sürüm numarası *x* olur.</span><span class="sxs-lookup"><span data-stu-id="86a1f-111">For example, for version *x.y*, the major version number is *x*.</span></span>  
  
 `wMinorVersion`  
 <span data-ttu-id="86a1f-112">'ndaki Tür kitaplığının ikincil sürüm numarası.</span><span class="sxs-lookup"><span data-stu-id="86a1f-112">[in] The minor version number of the type library.</span></span> <span data-ttu-id="86a1f-113">Örneğin, *x. y* sürümü için, ikincil sürüm numarası *y*' dir.</span><span class="sxs-lookup"><span data-stu-id="86a1f-113">For example, for version *x.y*, the minor version number is *y*.</span></span>  
  
 `syskind`  
 <span data-ttu-id="86a1f-114">'ndaki İşletim ortamını tanımlayan bir [Syskind](/windows/win32/api/oaidl/ne-oaidl-syskind) bayrağı.</span><span class="sxs-lookup"><span data-stu-id="86a1f-114">[in] A [SYSKIND](/windows/win32/api/oaidl/ne-oaidl-syskind) flag that identifies the operating environment.</span></span> <span data-ttu-id="86a1f-115">Ortak değerler SYS_WIN32 ve SYS_WIN64.</span><span class="sxs-lookup"><span data-stu-id="86a1f-115">Common values are SYS_WIN32 and SYS_WIN64.</span></span>  
  
 `pbstrResolvedTlbName`  
 <span data-ttu-id="86a1f-116">dışı Parametresinde adlı tür kitaplığının tam yolunu içeren bir [BSTR](/previous-versions/windows/desktop/automat/bstr) için bir işaretçi `bstrSimpleName` .</span><span class="sxs-lookup"><span data-stu-id="86a1f-116">[out] A pointer to a [BSTR](/previous-versions/windows/desktop/automat/bstr) that contains the full path of the type library named in the `bstrSimpleName` parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="86a1f-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="86a1f-117">Remarks</span></span>  

 <span data-ttu-id="86a1f-118">`ResolveTypeLib`Yöntemi, [Tlbexp.exe (tür kitaplığı verme programı)](../../tools/tlbexp-exe-type-library-exporter.md) Işlemi sırasında [LoadTypeLibWithResolver işlevi](loadtypelibwithresolver-function.md) tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="86a1f-118">The `ResolveTypeLib` method is called by the [LoadTypeLibWithResolver function](loadtypelibwithresolver-function.md) during [Tlbexp.exe (Type Library Exporter)](../../tools/tlbexp-exe-type-library-exporter.md) processing.</span></span>  
  
 <span data-ttu-id="86a1f-119">Bu arabirimin özel uygulamaları, parametresinde adlı tür kitaplığının tam yolunu içeren bir [BSTR](/previous-versions/windows/desktop/automat/bstr) döndürmelidir `bstrSimpleName` .</span><span class="sxs-lookup"><span data-stu-id="86a1f-119">Custom implementations of this interface must return a [BSTR](/previous-versions/windows/desktop/automat/bstr) that contains the full path of the type library named in the `bstrSimpleName` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86a1f-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="86a1f-120">Requirements</span></span>  

 <span data-ttu-id="86a1f-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="86a1f-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86a1f-122">**Üst bilgi:** TlbRef. IDL, TlbRef. h</span><span class="sxs-lookup"><span data-stu-id="86a1f-122">**Header:** TlbRef.idl, TlbRef.h</span></span>  
  
 <span data-ttu-id="86a1f-123">**Kitaplık:** TlbRef. lib</span><span class="sxs-lookup"><span data-stu-id="86a1f-123">**Library:** TlbRef.lib</span></span>  
  
 <span data-ttu-id="86a1f-124">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86a1f-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86a1f-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="86a1f-125">See also</span></span>

- [<span data-ttu-id="86a1f-126">Tlbexp Yardımcı İşlevleri</span><span class="sxs-lookup"><span data-stu-id="86a1f-126">Tlbexp Helper Functions</span></span>](index.md)
- [<span data-ttu-id="86a1f-127">LoadTypeLibEx</span><span class="sxs-lookup"><span data-stu-id="86a1f-127">LoadTypeLibEx</span></span>](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
