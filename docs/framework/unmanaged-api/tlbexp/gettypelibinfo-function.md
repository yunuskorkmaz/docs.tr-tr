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
ms.openlocfilehash: 4f05eb2e6ef31cf1993a623c38bb177f7e3c297e
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75935646"
---
# <a name="gettypelibinfo-function"></a><span data-ttu-id="43dda-102">GetTypeLibInfo İşlevi</span><span class="sxs-lookup"><span data-stu-id="43dda-102">GetTypeLibInfo Function</span></span>
<span data-ttu-id="43dda-103">[Tlibattr](/windows/win32/api/oaidl/ns-oaidl-tlibattr) yapısını inceleyerek belirtilen tür kitaplığıyla ilgili bilgileri döndürür.</span><span class="sxs-lookup"><span data-stu-id="43dda-103">Returns information about the specified type library by examining its [TLIBATTR](/windows/win32/api/oaidl/ns-oaidl-tlibattr) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43dda-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="43dda-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="43dda-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="43dda-105">Parameters</span></span>  
 `szFile`  
 <span data-ttu-id="43dda-106">'ndaki Tür kitaplığının dosya adı.</span><span class="sxs-lookup"><span data-stu-id="43dda-106">[in] The file name of the type library.</span></span>  
  
 `pTypeLibID`  
 <span data-ttu-id="43dda-107">dışı Tür kitaplığının GUID 'SI.</span><span class="sxs-lookup"><span data-stu-id="43dda-107">[out] The GUID of the type library.</span></span>  
  
 `pTypeLibLCID`  
 <span data-ttu-id="43dda-108">dışı Tür kitaplığının yerelleştirme KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="43dda-108">[out] The localization ID of the type library.</span></span>  
  
 `pTypeLibPlatform`  
 <span data-ttu-id="43dda-109">dışı Tür kitaplığı için hedef işletim sistemini tanımlayan bir [Syskind](/windows/win32/api/oaidl/ne-oaidl-syskind) bayrağı.</span><span class="sxs-lookup"><span data-stu-id="43dda-109">[out] A [SYSKIND](/windows/win32/api/oaidl/ne-oaidl-syskind) flag that identifies the target operating system for the type library.</span></span> <span data-ttu-id="43dda-110">Ortak değerler SYS_WIN32 ve SYS_WIN64.</span><span class="sxs-lookup"><span data-stu-id="43dda-110">Common values are SYS_WIN32 and SYS_WIN64.</span></span>  
  
 `pTypeLibMajorVer`  
 <span data-ttu-id="43dda-111">dışı Tür kitaplığının ana sürüm numarası.</span><span class="sxs-lookup"><span data-stu-id="43dda-111">[out] The major version number of the type library.</span></span> <span data-ttu-id="43dda-112">Örneğin, *x. y*sürümü için ana sürüm numarası *x*olur.</span><span class="sxs-lookup"><span data-stu-id="43dda-112">For example, for version *x.y*, the major version number is *x*.</span></span>  
  
 `pTypeLibMinorVer`  
 <span data-ttu-id="43dda-113">dışı Tür kitaplığının ikincil sürüm numarası.</span><span class="sxs-lookup"><span data-stu-id="43dda-113">[out] The minor version number of the type library.</span></span> <span data-ttu-id="43dda-114">Örneğin, *x. y*sürümü için, ikincil sürüm numarası *y*' dir.</span><span class="sxs-lookup"><span data-stu-id="43dda-114">For example, for version *x.y*, the minor version number is *y*.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="43dda-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="43dda-115">Remarks</span></span>  
 <span data-ttu-id="43dda-116">`GetTypeLibInfo` işlevi [Tlbexp. exe (tür kitaplığı verme programı)](../../tools/tlbexp-exe-type-library-exporter.md)tarafından çağırılır.</span><span class="sxs-lookup"><span data-stu-id="43dda-116">The `GetTypeLibInfo` function is called by the [Tlbexp.exe (Type Library Exporter)](../../tools/tlbexp-exe-type-library-exporter.md).</span></span> <span data-ttu-id="43dda-117">Bu araç, ortak dil çalışma zamanı (CLR) derlemesindeki türleri açıklayan bir tür kitaplığı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="43dda-117">This tool generates a type library that describes the types in a common language runtime (CLR) assembly.</span></span>  
  
 <span data-ttu-id="43dda-118">Herhangi bir parametre null ise, işlev `E_POINTER``HRESULT` döndürür.</span><span class="sxs-lookup"><span data-stu-id="43dda-118">If any parameter is null, the function returns an `HRESULT` of `E_POINTER`.</span></span> <span data-ttu-id="43dda-119">Aksi takdirde, `S_OK`döndürür.</span><span class="sxs-lookup"><span data-stu-id="43dda-119">Otherwise, it returns `S_OK`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="43dda-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="43dda-120">Requirements</span></span>  
 <span data-ttu-id="43dda-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="43dda-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="43dda-122">**Üst bilgi:** TlbRef. h</span><span class="sxs-lookup"><span data-stu-id="43dda-122">**Header:** TlbRef.h</span></span>  
  
 <span data-ttu-id="43dda-123">**Kitaplık:** TlbRef. lib</span><span class="sxs-lookup"><span data-stu-id="43dda-123">**Library:** TlbRef.lib</span></span>  
  
 <span data-ttu-id="43dda-124">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="43dda-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43dda-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="43dda-125">See also</span></span>

- [<span data-ttu-id="43dda-126">Tlbexp Yardımcı İşlevleri</span><span class="sxs-lookup"><span data-stu-id="43dda-126">Tlbexp Helper Functions</span></span>](index.md)
- [<span data-ttu-id="43dda-127">LoadTypeLibEx Işlevi</span><span class="sxs-lookup"><span data-stu-id="43dda-127">LoadTypeLibEx Function</span></span>](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
