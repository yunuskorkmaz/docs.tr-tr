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
ms.openlocfilehash: 4c630f5f7e3dc66ce44f10cd69fcd108226b0250
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554338"
---
# <a name="gettypelibinfo-function"></a><span data-ttu-id="81410-102">GetTypeLibInfo İşlevi</span><span class="sxs-lookup"><span data-stu-id="81410-102">GetTypeLibInfo Function</span></span>
<span data-ttu-id="81410-103">[Tlibattr](/windows/win32/api/oaidl/ns-oaidl-tlibattr) yapısını inceleyerek belirtilen tür kitaplığıyla ilgili bilgileri döndürür.</span><span class="sxs-lookup"><span data-stu-id="81410-103">Returns information about the specified type library by examining its [TLIBATTR](/windows/win32/api/oaidl/ns-oaidl-tlibattr) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81410-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="81410-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="81410-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="81410-105">Parameters</span></span>  
 `szFile`  
 <span data-ttu-id="81410-106">'ndaki Tür kitaplığının dosya adı.</span><span class="sxs-lookup"><span data-stu-id="81410-106">[in] The file name of the type library.</span></span>  
  
 `pTypeLibID`  
 <span data-ttu-id="81410-107">dışı Tür kitaplığının GUID 'SI.</span><span class="sxs-lookup"><span data-stu-id="81410-107">[out] The GUID of the type library.</span></span>  
  
 `pTypeLibLCID`  
 <span data-ttu-id="81410-108">dışı Tür kitaplığının yerelleştirme KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="81410-108">[out] The localization ID of the type library.</span></span>  
  
 `pTypeLibPlatform`  
 <span data-ttu-id="81410-109">dışı Tür kitaplığı için hedef işletim sistemini tanımlayan bir [Syskind](/windows/win32/api/oaidl/ne-oaidl-syskind) bayrağı.</span><span class="sxs-lookup"><span data-stu-id="81410-109">[out] A [SYSKIND](/windows/win32/api/oaidl/ne-oaidl-syskind) flag that identifies the target operating system for the type library.</span></span> <span data-ttu-id="81410-110">Ortak değerler SYS_WIN32 ve SYS_WIN64.</span><span class="sxs-lookup"><span data-stu-id="81410-110">Common values are SYS_WIN32 and SYS_WIN64.</span></span>  
  
 `pTypeLibMajorVer`  
 <span data-ttu-id="81410-111">dışı Tür kitaplığının ana sürüm numarası.</span><span class="sxs-lookup"><span data-stu-id="81410-111">[out] The major version number of the type library.</span></span> <span data-ttu-id="81410-112">Örneğin, *x. y*sürümü için ana sürüm numarası *x*olur.</span><span class="sxs-lookup"><span data-stu-id="81410-112">For example, for version *x.y*, the major version number is *x*.</span></span>  
  
 `pTypeLibMinorVer`  
 <span data-ttu-id="81410-113">dışı Tür kitaplığının ikincil sürüm numarası.</span><span class="sxs-lookup"><span data-stu-id="81410-113">[out] The minor version number of the type library.</span></span> <span data-ttu-id="81410-114">Örneğin, *x. y*sürümü için, ikincil sürüm numarası *y*' dir.</span><span class="sxs-lookup"><span data-stu-id="81410-114">For example, for version *x.y*, the minor version number is *y*.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="81410-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="81410-115">Remarks</span></span>  
 <span data-ttu-id="81410-116">`GetTypeLibInfo`İşlev, [Tlbexp.exe (tür kitaplığı verme programı)](../../tools/tlbexp-exe-type-library-exporter.md)tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="81410-116">The `GetTypeLibInfo` function is called by the [Tlbexp.exe (Type Library Exporter)](../../tools/tlbexp-exe-type-library-exporter.md).</span></span> <span data-ttu-id="81410-117">Bu araç, ortak dil çalışma zamanı (CLR) derlemesindeki türleri açıklayan bir tür kitaplığı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="81410-117">This tool generates a type library that describes the types in a common language runtime (CLR) assembly.</span></span>  
  
 <span data-ttu-id="81410-118">Herhangi bir parametre null ise, işlev ' ı döndürür `HRESULT` `E_POINTER` .</span><span class="sxs-lookup"><span data-stu-id="81410-118">If any parameter is null, the function returns an `HRESULT` of `E_POINTER`.</span></span> <span data-ttu-id="81410-119">Aksi takdirde, döndürür `S_OK` .</span><span class="sxs-lookup"><span data-stu-id="81410-119">Otherwise, it returns `S_OK`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81410-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="81410-120">Requirements</span></span>  
 <span data-ttu-id="81410-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="81410-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81410-122">**Üst bilgi:** TlbRef. h</span><span class="sxs-lookup"><span data-stu-id="81410-122">**Header:** TlbRef.h</span></span>  
  
 <span data-ttu-id="81410-123">**Kitaplık:** TlbRef. lib</span><span class="sxs-lookup"><span data-stu-id="81410-123">**Library:** TlbRef.lib</span></span>  
  
 <span data-ttu-id="81410-124">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81410-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81410-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="81410-125">See also</span></span>

- [<span data-ttu-id="81410-126">Tlbexp Yardımcı İşlevleri</span><span class="sxs-lookup"><span data-stu-id="81410-126">Tlbexp Helper Functions</span></span>](index.md)
- [<span data-ttu-id="81410-127">LoadTypeLibEx Işlevi</span><span class="sxs-lookup"><span data-stu-id="81410-127">LoadTypeLibEx Function</span></span>](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
