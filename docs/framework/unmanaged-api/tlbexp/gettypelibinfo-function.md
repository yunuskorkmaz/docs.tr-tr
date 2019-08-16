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
ms.openlocfilehash: 7da0986269189ba5c2dfa0f10d509bf51deb446d
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040203"
---
# <a name="gettypelibinfo-function"></a><span data-ttu-id="26fcf-102">GetTypeLibInfo İşlevi</span><span class="sxs-lookup"><span data-stu-id="26fcf-102">GetTypeLibInfo Function</span></span>
<span data-ttu-id="26fcf-103">[Tlibattr](https://docs.microsoft.com/windows/win32/api/oaidl/ns-oaidl-tlibattr) yapısını inceleyerek belirtilen tür kitaplığıyla ilgili bilgileri döndürür.</span><span class="sxs-lookup"><span data-stu-id="26fcf-103">Returns information about the specified type library by examining its [TLIBATTR](https://docs.microsoft.com/windows/win32/api/oaidl/ns-oaidl-tlibattr) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26fcf-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="26fcf-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="26fcf-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="26fcf-105">Parameters</span></span>  
 `szFile`  
 <span data-ttu-id="26fcf-106">'ndaki Tür kitaplığının dosya adı.</span><span class="sxs-lookup"><span data-stu-id="26fcf-106">[in] The file name of the type library.</span></span>  
  
 `pTypeLibID`  
 <span data-ttu-id="26fcf-107">dışı Tür kitaplığının GUID 'SI.</span><span class="sxs-lookup"><span data-stu-id="26fcf-107">[out] The GUID of the type library.</span></span>  
  
 `pTypeLibLCID`  
 <span data-ttu-id="26fcf-108">dışı Tür kitaplığının yerelleştirme KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="26fcf-108">[out] The localization ID of the type library.</span></span>  
  
 `pTypeLibPlatform`  
 <span data-ttu-id="26fcf-109">dışı Tür kitaplığı için hedef işletim sistemini tanımlayan bir [Syskind](https://docs.microsoft.com/windows/win32/api/oaidl/ne-oaidl-syskind) bayrağı.</span><span class="sxs-lookup"><span data-stu-id="26fcf-109">[out] A [SYSKIND](https://docs.microsoft.com/windows/win32/api/oaidl/ne-oaidl-syskind) flag that identifies the target operating system for the type library.</span></span> <span data-ttu-id="26fcf-110">Ortak değerler SYS_WIN32 ve SYS_WIN64.</span><span class="sxs-lookup"><span data-stu-id="26fcf-110">Common values are SYS_WIN32 and SYS_WIN64.</span></span>  
  
 `pTypeLibMajorVer`  
 <span data-ttu-id="26fcf-111">dışı Tür kitaplığının ana sürüm numarası.</span><span class="sxs-lookup"><span data-stu-id="26fcf-111">[out] The major version number of the type library.</span></span> <span data-ttu-id="26fcf-112">Örneğin, *x. y*sürümü için ana sürüm numarası *x*olur.</span><span class="sxs-lookup"><span data-stu-id="26fcf-112">For example, for version *x.y*, the major version number is *x*.</span></span>  
  
 `pTypeLibMinorVer`  
 <span data-ttu-id="26fcf-113">dışı Tür kitaplığının ikincil sürüm numarası.</span><span class="sxs-lookup"><span data-stu-id="26fcf-113">[out] The minor version number of the type library.</span></span> <span data-ttu-id="26fcf-114">Örneğin, *x. y*sürümü için, ikincil sürüm numarası *y*' dir.</span><span class="sxs-lookup"><span data-stu-id="26fcf-114">For example, for version *x.y*, the minor version number is *y*.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="26fcf-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="26fcf-115">Remarks</span></span>  
 <span data-ttu-id="26fcf-116">İşlevi Tlbexp [. exe (tür kitaplığı verme programı)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md)tarafından çağrılır. `GetTypeLibInfo`</span><span class="sxs-lookup"><span data-stu-id="26fcf-116">The `GetTypeLibInfo` function is called by the [Tlbexp.exe (Type Library Exporter)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md).</span></span> <span data-ttu-id="26fcf-117">Bu araç, ortak dil çalışma zamanı (CLR) derlemesindeki türleri açıklayan bir tür kitaplığı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="26fcf-117">This tool generates a type library that describes the types in a common language runtime (CLR) assembly.</span></span>  
  
 <span data-ttu-id="26fcf-118">Herhangi bir parametre null ise, işlev ' ı döndürür `HRESULT`. `E_POINTER`</span><span class="sxs-lookup"><span data-stu-id="26fcf-118">If any parameter is null, the function returns an `HRESULT` of `E_POINTER`.</span></span> <span data-ttu-id="26fcf-119">Aksi takdirde, döndürür `S_OK`.</span><span class="sxs-lookup"><span data-stu-id="26fcf-119">Otherwise, it returns `S_OK`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="26fcf-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="26fcf-120">Requirements</span></span>  
 <span data-ttu-id="26fcf-121">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="26fcf-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26fcf-122">**Üst bilgi** TlbRef. h</span><span class="sxs-lookup"><span data-stu-id="26fcf-122">**Header:** TlbRef.h</span></span>  
  
 <span data-ttu-id="26fcf-123">**Kitaplığı** TlbRef. lib</span><span class="sxs-lookup"><span data-stu-id="26fcf-123">**Library:** TlbRef.lib</span></span>  
  
 <span data-ttu-id="26fcf-124">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="26fcf-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26fcf-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="26fcf-125">See also</span></span>

- [<span data-ttu-id="26fcf-126">Tlbexp Yardımcı İşlevleri</span><span class="sxs-lookup"><span data-stu-id="26fcf-126">Tlbexp Helper Functions</span></span>](../../../../docs/framework/unmanaged-api/tlbexp/index.md)
- [<span data-ttu-id="26fcf-127">LoadTypeLibEx Işlevi</span><span class="sxs-lookup"><span data-stu-id="26fcf-127">LoadTypeLibEx Function</span></span>](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
