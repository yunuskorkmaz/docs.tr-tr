---
description: ': GetRequestedRuntimeVersionForCLSID Işlevi hakkında daha fazla bilgi'
title: GetRequestedRuntimeVersionForCLSID İşlevi
ms.date: 03/30/2017
api_name:
- GetRequestedRuntimeVersionForCLSID
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetRequestedRuntimeVersionForCLSID
helpviewer_keywords:
- GetRequestedRuntimeVersionForCLSID function [.NET Framework hosting]
ms.assetid: 5bb12f9a-0612-434b-b4ed-2db636a20bec
topic_type:
- apiref
ms.openlocfilehash: 10fdc947181d3f1fa12b33f11cf31b68fc4285cd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785269"
---
# <a name="getrequestedruntimeversionforclsid-function"></a><span data-ttu-id="0a522-103">GetRequestedRuntimeVersionForCLSID İşlevi</span><span class="sxs-lookup"><span data-stu-id="0a522-103">GetRequestedRuntimeVersionForCLSID Function</span></span>

<span data-ttu-id="0a522-104">Belirtilen sınıf için uygun ortak dil çalışma zamanı (CLR) sürüm bilgilerini alır `CLSID` .</span><span class="sxs-lookup"><span data-stu-id="0a522-104">Gets the appropriate common language runtime (CLR) version information for the class with the specified `CLSID`.</span></span>  
  
 <span data-ttu-id="0a522-105">Bu işlev .NET Framework 4 ' te kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="0a522-105">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a522-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0a522-106">Syntax</span></span>  
  
```cpp  
HRESULT GetRequestedRuntimeVersionForCLSID (  
    [in]  REFCLSID   rclsid,
    [out]  LPWSTR     pVersion,
    [in]  DWORD      cchBuffer,
    [out] DWORD*     dwLength,
    [in]  CLSID_RESOLUTION_FLAGS dwResolutionFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0a522-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0a522-107">Parameters</span></span>  

 `rclsid`  
 <span data-ttu-id="0a522-108">'ndaki  `CLSID` Bileşen.</span><span class="sxs-lookup"><span data-stu-id="0a522-108">[in]  The `CLSID` of the component.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="0a522-109">dışı  Başarılı bir şekilde tamamlandıktan sonra sürüm numarası dizesini içeren bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="0a522-109">[out]  A buffer that contains the version number string upon successful completion.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="0a522-110">'ndaki  Arabelleğin geniş karakterdeki boyutu `pVersion` .</span><span class="sxs-lookup"><span data-stu-id="0a522-110">[in]  The size, in wide characters, of the `pVersion` buffer.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="0a522-111">dışı Döndürülen arabelleğin bayt cinsinden uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="0a522-111">[out] The length, in bytes, of the returned buffer.</span></span>  
  
 `dwResolutionFlags`  
 <span data-ttu-id="0a522-112">'ndaki  CLSID_RESOLUTION_FLAGS değerlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="0a522-112">[in]  One of the CLSID_RESOLUTION_FLAGS values.</span></span> <span data-ttu-id="0a522-113">Aşağıdaki değerler desteklenir:</span><span class="sxs-lookup"><span data-stu-id="0a522-113">The following values are supported:</span></span>  
  
- <span data-ttu-id="0a522-114">CLSID_RESOLUTION_DEFAULT: (0x0) varsayılan birlikte çalışma davranışının kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="0a522-114">CLSID_RESOLUTION_DEFAULT: (0x0) Specifies that default interop behavior should be used.</span></span>  
  
- <span data-ttu-id="0a522-115">CLSID_RESOLUTION_REGISTERED: (0x1) kayıt defterinin aranması gerektiğini ve dolgu ilkesinin uygulanacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="0a522-115">CLSID_RESOLUTION_REGISTERED: (0x1) Specifies that the registry should be searched and shim policy should be applied.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0a522-116">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="0a522-116">Return Value</span></span>  
  
|<span data-ttu-id="0a522-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0a522-117">HRESULT</span></span>|<span data-ttu-id="0a522-118">Description</span><span class="sxs-lookup"><span data-stu-id="0a522-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0a522-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="0a522-119">S_OK</span></span>|<span data-ttu-id="0a522-120">İşlev başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="0a522-120">The function returned successfully.</span></span>|  
|<span data-ttu-id="0a522-121">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="0a522-121">E_INVALIDARG</span></span>|<span data-ttu-id="0a522-122">Parametrelerden birinde geçersiz bir tür veya biçim vardır.</span><span class="sxs-lookup"><span data-stu-id="0a522-122">One of the parameters has an invalid type or format.</span></span>|  
|<span data-ttu-id="0a522-123">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="0a522-123">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="0a522-124">`pVersion`Arabellek, tüm sürüm dizesini tutabilecek kadar büyük değil.</span><span class="sxs-lookup"><span data-stu-id="0a522-124">The `pVersion` buffer is not large enough to hold the entire version string.</span></span>|  
|<span data-ttu-id="0a522-125">REGDB_E_CLASSNOTREG</span><span class="sxs-lookup"><span data-stu-id="0a522-125">REGDB_E_CLASSNOTREG</span></span>|<span data-ttu-id="0a522-126">Belirtilen ile kayıtlı bir sınıf yok `CLSID` .</span><span class="sxs-lookup"><span data-stu-id="0a522-126">There is no class registered with the specified `CLSID`.</span></span>|  
|<span data-ttu-id="0a522-127">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="0a522-127">E_POINTER</span></span>|<span data-ttu-id="0a522-128">`dwLength` null veya `cchBuffer` Sürüm dizesini tutabilecek kadar büyük, ancak `pVersion` null.</span><span class="sxs-lookup"><span data-stu-id="0a522-128">`dwLength` is null, or `cchBuffer` is large enough to hold the version string, but `pVersion` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0a522-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0a522-129">Requirements</span></span>  

 <span data-ttu-id="0a522-130">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0a522-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a522-131">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0a522-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0a522-132">**.NET Framework sürümleri:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0a522-132">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a522-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0a522-133">See also</span></span>

- [<span data-ttu-id="0a522-134">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="0a522-134">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
