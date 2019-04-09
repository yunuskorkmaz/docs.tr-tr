---
title: GetTypeLibInfo İşlevi
ms.date: 03/30/2017
api_name:
- GetTypeLibInfo
api_location:
- TlbRef.dll
api_type:
- DLLExport
f1_keywords:
- GetTypeLibInfo
helpviewer_keywords:
- GetTypeLibInfo function [.NET Framework]
ms.assetid: a1c4d165-9bdc-4ca8-940e-292d4ffcc338
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d12cbb66464baba4ee706ccb076764fbf025fc5f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59148544"
---
# <a name="gettypelibinfo-function"></a><span data-ttu-id="07d69-102">GetTypeLibInfo İşlevi</span><span class="sxs-lookup"><span data-stu-id="07d69-102">GetTypeLibInfo Function</span></span>
<span data-ttu-id="07d69-103">Belirtilen tür kitaplığı hakkında bilgi inceleyerek döndürür, [TLIBATTR](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/ns-oaidl-tagtlibattr) yapısı.</span><span class="sxs-lookup"><span data-stu-id="07d69-103">Returns information about the specified type library by examining its [TLIBATTR](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/ns-oaidl-tagtlibattr) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07d69-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="07d69-104">Syntax</span></span>  
  
```  
HRESULT GetTypeLibInfo(  
    [in]   LPWSTR     szFile,  
    [out]  GUID      *pTypeLibID,  
    [out]  LCID      *pTypeLibLCID,  
    [out]  SYSKIND   *pTypeLibPlatform,  
    [out]  USHORT    *pTypeLibMajorVer,  
    [out]  USHORT    *pTypeLibMinorVer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="07d69-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="07d69-105">Parameters</span></span>  
 `szFile`  
 <span data-ttu-id="07d69-106">[in] Tür kitaplığı dosyasının adı.</span><span class="sxs-lookup"><span data-stu-id="07d69-106">[in] The file name of the type library.</span></span>  
  
 `pTypeLibID`  
 <span data-ttu-id="07d69-107">[out] Tür kitaplığının GUID.</span><span class="sxs-lookup"><span data-stu-id="07d69-107">[out] The GUID of the type library.</span></span>  
  
 `pTypeLibLCID`  
 <span data-ttu-id="07d69-108">[out] Tür kitaplığının yerelleştirme kimliği.</span><span class="sxs-lookup"><span data-stu-id="07d69-108">[out] The localization ID of the type library.</span></span>  
  
 `pTypeLibPlatform`  
 <span data-ttu-id="07d69-109">[out] A [SYSKIND](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/ne-oaidl-tagsyskind) tür kitaplığı için hedef işletim sistemini tanımlayan bir bayrak.</span><span class="sxs-lookup"><span data-stu-id="07d69-109">[out] A [SYSKIND](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/ne-oaidl-tagsyskind) flag that identifies the target operating system for the type library.</span></span> <span data-ttu-id="07d69-110">Genel değerler şunlardır: SYS_WIN32 ve SYS_WIN64.</span><span class="sxs-lookup"><span data-stu-id="07d69-110">Common values are SYS_WIN32 and SYS_WIN64.</span></span>  
  
 `pTypeLibMajorVer`  
 <span data-ttu-id="07d69-111">[out] Tür kitaplığı sürüm sayısı.</span><span class="sxs-lookup"><span data-stu-id="07d69-111">[out] The major version number of the type library.</span></span> <span data-ttu-id="07d69-112">Örneğin, sürüm için *x.y*, ana sürüm numarası *x*.</span><span class="sxs-lookup"><span data-stu-id="07d69-112">For example, for version *x.y*, the major version number is *x*.</span></span>  
  
 `pTypeLibMinorVer`  
 <span data-ttu-id="07d69-113">[out] Tür kitaplığının ikincil sürüm numarası.</span><span class="sxs-lookup"><span data-stu-id="07d69-113">[out] The minor version number of the type library.</span></span> <span data-ttu-id="07d69-114">Örneğin, sürüm için *x.y*, ikincil sürüm numarası *y*.</span><span class="sxs-lookup"><span data-stu-id="07d69-114">For example, for version *x.y*, the minor version number is *y*.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="07d69-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="07d69-115">Remarks</span></span>  
 <span data-ttu-id="07d69-116">`GetTypeLibInfo` İşlevi çağrıldığında [Tlbexp.exe (tür kitaplığı dışarı Aktarıcı)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md).</span><span class="sxs-lookup"><span data-stu-id="07d69-116">The `GetTypeLibInfo` function is called by the [Tlbexp.exe (Type Library Exporter)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md).</span></span> <span data-ttu-id="07d69-117">Bu araç, bir ortak dil çalışma zamanı (CLR) derlemedeki türleri açıklayan bir tür kitaplığı üretir.</span><span class="sxs-lookup"><span data-stu-id="07d69-117">This tool generates a type library that describes the types in a common language runtime (CLR) assembly.</span></span>  
  
 <span data-ttu-id="07d69-118">Herhangi bir parametre null ise, işlev döndürür bir `HRESULT` , `E_POINTER`.</span><span class="sxs-lookup"><span data-stu-id="07d69-118">If any parameter is null, the function returns an `HRESULT` of `E_POINTER`.</span></span> <span data-ttu-id="07d69-119">Aksi halde `S_OK`.</span><span class="sxs-lookup"><span data-stu-id="07d69-119">Otherwise, it returns `S_OK`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="07d69-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="07d69-120">Requirements</span></span>  
 <span data-ttu-id="07d69-121">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="07d69-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="07d69-122">**Üst bilgi:** TlbRef.h</span><span class="sxs-lookup"><span data-stu-id="07d69-122">**Header:** TlbRef.h</span></span>  
  
 <span data-ttu-id="07d69-123">**Kitaplığı:** TlbRef.lib</span><span class="sxs-lookup"><span data-stu-id="07d69-123">**Library:** TlbRef.lib</span></span>  
  
 **<span data-ttu-id="07d69-124">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="07d69-124">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="07d69-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="07d69-125">See also</span></span>

- [<span data-ttu-id="07d69-126">Tlbexp Yardımcı İşlevleri</span><span class="sxs-lookup"><span data-stu-id="07d69-126">Tlbexp Helper Functions</span></span>](../../../../docs/framework/unmanaged-api/tlbexp/index.md)
- [<span data-ttu-id="07d69-127">LoadTypeLibEx işlevi</span><span class="sxs-lookup"><span data-stu-id="07d69-127">LoadTypeLibEx Function</span></span>](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
