---
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 63e6ec271634a52abe7c640bbbabdaedebd2a31d
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57471907"
---
# <a name="getrequestedruntimeversionforclsid-function"></a><span data-ttu-id="baabb-102">GetRequestedRuntimeVersionForCLSID İşlevi</span><span class="sxs-lookup"><span data-stu-id="baabb-102">GetRequestedRuntimeVersionForCLSID Function</span></span>
<span data-ttu-id="baabb-103">Belirtilen sınıf için uygun ortak dil çalışma zamanı (CLR) sürümü bilgisini alır `CLSID`.</span><span class="sxs-lookup"><span data-stu-id="baabb-103">Gets the appropriate common language runtime (CLR) version information for the class with the specified `CLSID`.</span></span>  
  
 <span data-ttu-id="baabb-104">Bu işlev içinde kullanımdan kalkmış [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="baabb-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="baabb-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="baabb-105">Syntax</span></span>  
  
```  
HRESULT GetRequestedRuntimeVersionForCLSID (  
    [in]  REFCLSID   rclsid,   
    [out]  LPWSTR     pVersion,   
    [in]  DWORD      cchBuffer,   
    [out] DWORD*     dwLength,   
    [in]  CLSID_RESOLUTION_FLAGS dwResolutionFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="baabb-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="baabb-106">Parameters</span></span>  
 `rclsid`  
 <span data-ttu-id="baabb-107">[in]  `CLSID` Bileşen.</span><span class="sxs-lookup"><span data-stu-id="baabb-107">[in]  The `CLSID` of the component.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="baabb-108">[out]  Başarıyla tamamlandıktan sonra sürüm numarası dizesi içeren bir arabelleği.</span><span class="sxs-lookup"><span data-stu-id="baabb-108">[out]  A buffer that contains the version number string upon successful completion.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="baabb-109">[in]  Geniş karakter cinsinden boyutu, `pVersion` arabellek.</span><span class="sxs-lookup"><span data-stu-id="baabb-109">[in]  The size, in wide characters, of the `pVersion` buffer.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="baabb-110">[out] Bayt cinsinden döndürülen arabellek uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="baabb-110">[out] The length, in bytes, of the returned buffer.</span></span>  
  
 `dwResolutionFlags`  
 <span data-ttu-id="baabb-111">[in]  Clsıd_resolutıon_flags değerlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="baabb-111">[in]  One of the CLSID_RESOLUTION_FLAGS values.</span></span> <span data-ttu-id="baabb-112">Aşağıdaki değerleri desteklenir:</span><span class="sxs-lookup"><span data-stu-id="baabb-112">The following values are supported:</span></span>  
  
-   <span data-ttu-id="baabb-113">CLSID_RESOLUTION_DEFAULT: (0x0) birlikte çalışma davranışı kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="baabb-113">CLSID_RESOLUTION_DEFAULT: (0x0) Specifies that default interop behavior should be used.</span></span>  
  
-   <span data-ttu-id="baabb-114">CLSID_RESOLUTION_REGISTERED: (0x1) dolgu ilke uygulanabilir ve kayıt defteri aranıp aranmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="baabb-114">CLSID_RESOLUTION_REGISTERED: (0x1) Specifies that the registry should be searched and shim policy should be applied.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="baabb-115">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="baabb-115">Return Value</span></span>  
  
|<span data-ttu-id="baabb-116">HRESULT</span><span class="sxs-lookup"><span data-stu-id="baabb-116">HRESULT</span></span>|<span data-ttu-id="baabb-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="baabb-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="baabb-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="baabb-118">S_OK</span></span>|<span data-ttu-id="baabb-119">İşlev başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="baabb-119">The function returned successfully.</span></span>|  
|<span data-ttu-id="baabb-120">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="baabb-120">E_INVALIDARG</span></span>|<span data-ttu-id="baabb-121">Parametrelerden biri, bir türü geçersiz veya biçim vardır.</span><span class="sxs-lookup"><span data-stu-id="baabb-121">One of the parameters has an invalid type or format.</span></span>|  
|<span data-ttu-id="baabb-122">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="baabb-122">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="baabb-123">`pVersion` Arabelleği tüm sürüm dizesini tutabilecek kadar büyük değil.</span><span class="sxs-lookup"><span data-stu-id="baabb-123">The `pVersion` buffer is not large enough to hold the entire version string.</span></span>|  
|<span data-ttu-id="baabb-124">REGDB_E_CLASSNOTREG</span><span class="sxs-lookup"><span data-stu-id="baabb-124">REGDB_E_CLASSNOTREG</span></span>|<span data-ttu-id="baabb-125">Belirtilen ile kayıtlı bir sınıf yok `CLSID`.</span><span class="sxs-lookup"><span data-stu-id="baabb-125">There is no class registered with the specified `CLSID`.</span></span>|  
|<span data-ttu-id="baabb-126">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="baabb-126">E_POINTER</span></span>|<span data-ttu-id="baabb-127">`dwLength` null ise veya `cchBuffer` sürüm dizesi tutabilecek kadar büyük olduğunu ancak `pVersion` null.</span><span class="sxs-lookup"><span data-stu-id="baabb-127">`dwLength` is null, or `cchBuffer` is large enough to hold the version string, but `pVersion` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="baabb-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="baabb-128">Requirements</span></span>  
 <span data-ttu-id="baabb-129">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="baabb-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="baabb-130">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="baabb-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="baabb-131">**.NET framework sürümleri:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="baabb-131">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="baabb-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="baabb-132">See also</span></span>
- [<span data-ttu-id="baabb-133">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="baabb-133">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
