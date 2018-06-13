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
ms.openlocfilehash: 56a9b97f37240e385dbd1788bafea62578d687a7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33457874"
---
# <a name="gettypelibinfo-function"></a><span data-ttu-id="fc996-102">GetTypeLibInfo İşlevi</span><span class="sxs-lookup"><span data-stu-id="fc996-102">GetTypeLibInfo Function</span></span>
<span data-ttu-id="fc996-103">Belirtilen tür kitaplığı hakkında bilgi inceleyerek döndürür, [TLIBATTR](https://msdn.microsoft.com/library/ms221376\(v=vs.85\).aspx) yapısı.</span><span class="sxs-lookup"><span data-stu-id="fc996-103">Returns information about the specified type library by examining its [TLIBATTR](https://msdn.microsoft.com/library/ms221376\(v=vs.85\).aspx) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc996-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fc996-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="fc996-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fc996-105">Parameters</span></span>  
 `szFile`  
 <span data-ttu-id="fc996-106">[in] Tür kitaplığı dosya adı.</span><span class="sxs-lookup"><span data-stu-id="fc996-106">[in] The file name of the type library.</span></span>  
  
 `pTypeLibID`  
 <span data-ttu-id="fc996-107">[out] Tür kitaplığı GUID.</span><span class="sxs-lookup"><span data-stu-id="fc996-107">[out] The GUID of the type library.</span></span>  
  
 `pTypeLibLCID`  
 <span data-ttu-id="fc996-108">[out] Tür kitaplığı yerelleştirme kimliği.</span><span class="sxs-lookup"><span data-stu-id="fc996-108">[out] The localization ID of the type library.</span></span>  
  
 `pTypeLibPlatform`  
 <span data-ttu-id="fc996-109">[out] A [SYSKIND](https://msdn.microsoft.com/library/ms221272\(v=vs.85\).aspx) tür kitaplığı için hedef işletim sistemini tanımlayan bayrağı.</span><span class="sxs-lookup"><span data-stu-id="fc996-109">[out] A [SYSKIND](https://msdn.microsoft.com/library/ms221272\(v=vs.85\).aspx) flag that identifies the target operating system for the type library.</span></span> <span data-ttu-id="fc996-110">SYS_WIN32 ve SYS_WIN64 bunun ortak değerlerdir.</span><span class="sxs-lookup"><span data-stu-id="fc996-110">Common values are SYS_WIN32 and SYS_WIN64.</span></span>  
  
 `pTypeLibMajorVer`  
 <span data-ttu-id="fc996-111">[out] Tür kitaplığı ana sürüm numarası.</span><span class="sxs-lookup"><span data-stu-id="fc996-111">[out] The major version number of the type library.</span></span> <span data-ttu-id="fc996-112">Örneğin, sürüm *x.y*, ana sürüm numarası *x*.</span><span class="sxs-lookup"><span data-stu-id="fc996-112">For example, for version *x.y*, the major version number is *x*.</span></span>  
  
 `pTypeLibMinorVer`  
 <span data-ttu-id="fc996-113">[out] Tür kitaplığı ikincil sürüm numarası.</span><span class="sxs-lookup"><span data-stu-id="fc996-113">[out] The minor version number of the type library.</span></span> <span data-ttu-id="fc996-114">Örneğin, sürüm *x.y*, ikincil sürüm numarası *y*.</span><span class="sxs-lookup"><span data-stu-id="fc996-114">For example, for version *x.y*, the minor version number is *y*.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fc996-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fc996-115">Remarks</span></span>  
 <span data-ttu-id="fc996-116">`GetTypeLibInfo` İşlevi çağrıldığında [Tlbexp.exe (tür kitaplığı dışarı Aktarıcı)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md).</span><span class="sxs-lookup"><span data-stu-id="fc996-116">The `GetTypeLibInfo` function is called by the [Tlbexp.exe (Type Library Exporter)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md).</span></span> <span data-ttu-id="fc996-117">Bu araç, bir ortak dil çalışma zamanı (CLR) derlemesindeki türler açıklayan bir tür kitaplığı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="fc996-117">This tool generates a type library that describes the types in a common language runtime (CLR) assembly.</span></span>  
  
 <span data-ttu-id="fc996-118">Herhangi bir parametre null ise işlev verir bir `HRESULT` , `E_POINTER`.</span><span class="sxs-lookup"><span data-stu-id="fc996-118">If any parameter is null, the function returns an `HRESULT` of `E_POINTER`.</span></span> <span data-ttu-id="fc996-119">Aksi takdirde, döndürür `S_OK`.</span><span class="sxs-lookup"><span data-stu-id="fc996-119">Otherwise, it returns `S_OK`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc996-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fc996-120">Requirements</span></span>  
 <span data-ttu-id="fc996-121">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc996-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc996-122">**Başlık:** TlbRef.h</span><span class="sxs-lookup"><span data-stu-id="fc996-122">**Header:** TlbRef.h</span></span>  
  
 <span data-ttu-id="fc996-123">**Kitaplığı:** TlbRef.lib</span><span class="sxs-lookup"><span data-stu-id="fc996-123">**Library:** TlbRef.lib</span></span>  
  
 <span data-ttu-id="fc996-124">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc996-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc996-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fc996-125">See Also</span></span>  
 [<span data-ttu-id="fc996-126">Tlbexp Yardımcı İşlevleri</span><span class="sxs-lookup"><span data-stu-id="fc996-126">Tlbexp Helper Functions</span></span>](../../../../docs/framework/unmanaged-api/tlbexp/index.md)  
 <span data-ttu-id="fc996-127">[LoadTypeLibEx işlevi](https://msdn.microsoft.com/library/ms221249\(v=vs.85\).aspx)</span><span class="sxs-lookup"><span data-stu-id="fc996-127">[LoadTypeLibEx Function](https://msdn.microsoft.com/library/ms221249\(v=vs.85\).aspx)</span></span>
