---
title: "GetTypeLibInfo İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetTypeLibInfo
api_location: TlbRef.dll
api_type: DLLExport
f1_keywords: GetTypeLibInfo
helpviewer_keywords: GetTypeLibInfo function [.NET Framework]
ms.assetid: a1c4d165-9bdc-4ca8-940e-292d4ffcc338
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a5dc55a9538798b81dce9db02583c271b9f2ed54
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="gettypelibinfo-function"></a><span data-ttu-id="c032f-102">GetTypeLibInfo İşlevi</span><span class="sxs-lookup"><span data-stu-id="c032f-102">GetTypeLibInfo Function</span></span>
<span data-ttu-id="c032f-103">Belirtilen tür kitaplığı hakkında bilgi inceleyerek döndürür, [TLIBATTR](https://msdn.microsoft.com/library/ms221376\(v=vs.85\).aspx) yapısı.</span><span class="sxs-lookup"><span data-stu-id="c032f-103">Returns information about the specified type library by examining its [TLIBATTR](https://msdn.microsoft.com/library/ms221376\(v=vs.85\).aspx) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c032f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c032f-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="c032f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c032f-105">Parameters</span></span>  
 `szFile`  
 <span data-ttu-id="c032f-106">[in] Tür kitaplığı dosya adı.</span><span class="sxs-lookup"><span data-stu-id="c032f-106">[in] The file name of the type library.</span></span>  
  
 `pTypeLibID`  
 <span data-ttu-id="c032f-107">[out] Tür kitaplığı GUID.</span><span class="sxs-lookup"><span data-stu-id="c032f-107">[out] The GUID of the type library.</span></span>  
  
 `pTypeLibLCID`  
 <span data-ttu-id="c032f-108">[out] Tür kitaplığı yerelleştirme kimliği.</span><span class="sxs-lookup"><span data-stu-id="c032f-108">[out] The localization ID of the type library.</span></span>  
  
 `pTypeLibPlatform`  
 <span data-ttu-id="c032f-109">[out] A [SYSKIND](https://msdn.microsoft.com/library/ms221272\(v=vs.85\).aspx) tür kitaplığı için hedef işletim sistemini tanımlayan bayrağı.</span><span class="sxs-lookup"><span data-stu-id="c032f-109">[out] A [SYSKIND](https://msdn.microsoft.com/library/ms221272\(v=vs.85\).aspx) flag that identifies the target operating system for the type library.</span></span> <span data-ttu-id="c032f-110">SYS_WIN32 ve SYS_WIN64 bunun ortak değerlerdir.</span><span class="sxs-lookup"><span data-stu-id="c032f-110">Common values are SYS_WIN32 and SYS_WIN64.</span></span>  
  
 `pTypeLibMajorVer`  
 <span data-ttu-id="c032f-111">[out] Tür kitaplığı ana sürüm numarası.</span><span class="sxs-lookup"><span data-stu-id="c032f-111">[out] The major version number of the type library.</span></span> <span data-ttu-id="c032f-112">Örneğin, sürüm *x.y*, ana sürüm numarası *x*.</span><span class="sxs-lookup"><span data-stu-id="c032f-112">For example, for version *x.y*, the major version number is *x*.</span></span>  
  
 `pTypeLibMinorVer`  
 <span data-ttu-id="c032f-113">[out] Tür kitaplığı ikincil sürüm numarası.</span><span class="sxs-lookup"><span data-stu-id="c032f-113">[out] The minor version number of the type library.</span></span> <span data-ttu-id="c032f-114">Örneğin, sürüm *x.y*, ikincil sürüm numarası *y*.</span><span class="sxs-lookup"><span data-stu-id="c032f-114">For example, for version *x.y*, the minor version number is *y*.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c032f-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c032f-115">Remarks</span></span>  
 <span data-ttu-id="c032f-116">`GetTypeLibInfo` İşlevi çağrıldığında [Tlbexp.exe (tür kitaplığı dışarı Aktarıcı)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md).</span><span class="sxs-lookup"><span data-stu-id="c032f-116">The `GetTypeLibInfo` function is called by the [Tlbexp.exe (Type Library Exporter)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md).</span></span> <span data-ttu-id="c032f-117">Bu araç, bir ortak dil çalışma zamanı (CLR) derlemesindeki türler açıklayan bir tür kitaplığı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c032f-117">This tool generates a type library that describes the types in a common language runtime (CLR) assembly.</span></span>  
  
 <span data-ttu-id="c032f-118">Herhangi bir parametre null ise işlev verir bir `HRESULT` , `E_POINTER`.</span><span class="sxs-lookup"><span data-stu-id="c032f-118">If any parameter is null, the function returns an `HRESULT` of `E_POINTER`.</span></span> <span data-ttu-id="c032f-119">Aksi takdirde, döndürür `S_OK`.</span><span class="sxs-lookup"><span data-stu-id="c032f-119">Otherwise, it returns `S_OK`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c032f-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c032f-120">Requirements</span></span>  
 <span data-ttu-id="c032f-121">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c032f-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c032f-122">**Başlık:** TlbRef.h</span><span class="sxs-lookup"><span data-stu-id="c032f-122">**Header:** TlbRef.h</span></span>  
  
 <span data-ttu-id="c032f-123">**Kitaplığı:** TlbRef.lib</span><span class="sxs-lookup"><span data-stu-id="c032f-123">**Library:** TlbRef.lib</span></span>  
  
 <span data-ttu-id="c032f-124">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c032f-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c032f-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c032f-125">See Also</span></span>  
 [<span data-ttu-id="c032f-126">Tlbexp yardımcı işlevleri</span><span class="sxs-lookup"><span data-stu-id="c032f-126">Tlbexp Helper Functions</span></span>](../../../../docs/framework/unmanaged-api/tlbexp/index.md)  
 <span data-ttu-id="c032f-127">[LoadTypeLibEx işlevi](https://msdn.microsoft.com/library/ms221249\(v=vs.85\).aspx)</span><span class="sxs-lookup"><span data-stu-id="c032f-127">[LoadTypeLibEx Function](https://msdn.microsoft.com/library/ms221249\(v=vs.85\).aspx)</span></span>
