---
description: ': Gettypeliınfo Işlevi hakkında daha fazla bilgi'
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
ms.openlocfilehash: 61a830f3ce81345634da377f6fc815a307700e9e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794474"
---
# <a name="gettypelibinfo-function"></a><span data-ttu-id="4394c-103">GetTypeLibInfo İşlevi</span><span class="sxs-lookup"><span data-stu-id="4394c-103">GetTypeLibInfo Function</span></span>

<span data-ttu-id="4394c-104">[Tlibattr](/windows/win32/api/oaidl/ns-oaidl-tlibattr) yapısını inceleyerek belirtilen tür kitaplığıyla ilgili bilgileri döndürür.</span><span class="sxs-lookup"><span data-stu-id="4394c-104">Returns information about the specified type library by examining its [TLIBATTR](/windows/win32/api/oaidl/ns-oaidl-tlibattr) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4394c-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4394c-105">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeLibInfo(  
    [in]   LPWSTR     szFile,  
    [out]  GUID      *pTypeLibID,  
    [out]  LCID      *pTypeLibLCID,  
    [out]  SYSKIND   *pTypeLibPlatform,  
    [out]  USHORT    *pTypeLibMajorVer,  
    [out]  USHORT    *pTypeLibMinorVer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4394c-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4394c-106">Parameters</span></span>  

 `szFile`  
 <span data-ttu-id="4394c-107">'ndaki Tür kitaplığının dosya adı.</span><span class="sxs-lookup"><span data-stu-id="4394c-107">[in] The file name of the type library.</span></span>  
  
 `pTypeLibID`  
 <span data-ttu-id="4394c-108">dışı Tür kitaplığının GUID 'SI.</span><span class="sxs-lookup"><span data-stu-id="4394c-108">[out] The GUID of the type library.</span></span>  
  
 `pTypeLibLCID`  
 <span data-ttu-id="4394c-109">dışı Tür kitaplığının yerelleştirme KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="4394c-109">[out] The localization ID of the type library.</span></span>  
  
 `pTypeLibPlatform`  
 <span data-ttu-id="4394c-110">dışı Tür kitaplığı için hedef işletim sistemini tanımlayan bir [Syskind](/windows/win32/api/oaidl/ne-oaidl-syskind) bayrağı.</span><span class="sxs-lookup"><span data-stu-id="4394c-110">[out] A [SYSKIND](/windows/win32/api/oaidl/ne-oaidl-syskind) flag that identifies the target operating system for the type library.</span></span> <span data-ttu-id="4394c-111">Ortak değerler SYS_WIN32 ve SYS_WIN64.</span><span class="sxs-lookup"><span data-stu-id="4394c-111">Common values are SYS_WIN32 and SYS_WIN64.</span></span>  
  
 `pTypeLibMajorVer`  
 <span data-ttu-id="4394c-112">dışı Tür kitaplığının ana sürüm numarası.</span><span class="sxs-lookup"><span data-stu-id="4394c-112">[out] The major version number of the type library.</span></span> <span data-ttu-id="4394c-113">Örneğin, *x. y* sürümü için ana sürüm numarası *x* olur.</span><span class="sxs-lookup"><span data-stu-id="4394c-113">For example, for version *x.y*, the major version number is *x*.</span></span>  
  
 `pTypeLibMinorVer`  
 <span data-ttu-id="4394c-114">dışı Tür kitaplığının ikincil sürüm numarası.</span><span class="sxs-lookup"><span data-stu-id="4394c-114">[out] The minor version number of the type library.</span></span> <span data-ttu-id="4394c-115">Örneğin, *x. y* sürümü için, ikincil sürüm numarası *y*' dir.</span><span class="sxs-lookup"><span data-stu-id="4394c-115">For example, for version *x.y*, the minor version number is *y*.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4394c-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4394c-116">Remarks</span></span>  

 <span data-ttu-id="4394c-117">`GetTypeLibInfo`İşlev, [Tlbexp.exe (tür kitaplığı verme programı)](../../tools/tlbexp-exe-type-library-exporter.md)tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="4394c-117">The `GetTypeLibInfo` function is called by the [Tlbexp.exe (Type Library Exporter)](../../tools/tlbexp-exe-type-library-exporter.md).</span></span> <span data-ttu-id="4394c-118">Bu araç, ortak dil çalışma zamanı (CLR) derlemesindeki türleri açıklayan bir tür kitaplığı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4394c-118">This tool generates a type library that describes the types in a common language runtime (CLR) assembly.</span></span>  
  
 <span data-ttu-id="4394c-119">Herhangi bir parametre null ise, işlev ' ı döndürür `HRESULT` `E_POINTER` .</span><span class="sxs-lookup"><span data-stu-id="4394c-119">If any parameter is null, the function returns an `HRESULT` of `E_POINTER`.</span></span> <span data-ttu-id="4394c-120">Aksi takdirde, döndürür `S_OK` .</span><span class="sxs-lookup"><span data-stu-id="4394c-120">Otherwise, it returns `S_OK`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4394c-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4394c-121">Requirements</span></span>  

 <span data-ttu-id="4394c-122">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4394c-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4394c-123">**Üst bilgi:** TlbRef. h</span><span class="sxs-lookup"><span data-stu-id="4394c-123">**Header:** TlbRef.h</span></span>  
  
 <span data-ttu-id="4394c-124">**Kitaplık:** TlbRef. lib</span><span class="sxs-lookup"><span data-stu-id="4394c-124">**Library:** TlbRef.lib</span></span>  
  
 <span data-ttu-id="4394c-125">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4394c-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4394c-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4394c-126">See also</span></span>

- [<span data-ttu-id="4394c-127">Tlbexp Yardımcı İşlevleri</span><span class="sxs-lookup"><span data-stu-id="4394c-127">Tlbexp Helper Functions</span></span>](index.md)
- [<span data-ttu-id="4394c-128">LoadTypeLibEx Işlevi</span><span class="sxs-lookup"><span data-stu-id="4394c-128">LoadTypeLibEx Function</span></span>](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
