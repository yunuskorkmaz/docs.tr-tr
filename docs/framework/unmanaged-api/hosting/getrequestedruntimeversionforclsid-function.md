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
ms.openlocfilehash: e8d3a7168ce0ee3484384ae0e2d10ca00367fc9c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33432865"
---
# <a name="getrequestedruntimeversionforclsid-function"></a><span data-ttu-id="1f290-102">GetRequestedRuntimeVersionForCLSID İşlevi</span><span class="sxs-lookup"><span data-stu-id="1f290-102">GetRequestedRuntimeVersionForCLSID Function</span></span>
<span data-ttu-id="1f290-103">Belirtilen sınıfı için uygun ortak dil çalışma zamanı (CLR) sürüm bilgilerini alır `CLSID`.</span><span class="sxs-lookup"><span data-stu-id="1f290-103">Gets the appropriate common language runtime (CLR) version information for the class with the specified `CLSID`.</span></span>  
  
 <span data-ttu-id="1f290-104">Bu işlev kaldırılmamıştır [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1f290-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f290-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1f290-105">Syntax</span></span>  
  
```  
HRESULT GetRequestedRuntimeVersionForCLSID (  
    [in]  REFCLSID   rclsid,   
    [out]  LPWSTR     pVersion,   
    [in]  DWORD      cchBuffer,   
    [out] DWORD*     dwLength,   
    [in]  CLSID_RESOLUTION_FLAGS dwResolutionFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1f290-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1f290-106">Parameters</span></span>  
 `rclsid`  
 <span data-ttu-id="1f290-107">[in]  `CLSID` Bileşeninin.</span><span class="sxs-lookup"><span data-stu-id="1f290-107">[in]  The `CLSID` of the component.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="1f290-108">[out]  Başarıyla tamamlandıktan sonra sürüm numarası dizesi içeren bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="1f290-108">[out]  A buffer that contains the version number string upon successful completion.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="1f290-109">[in]  Geniş karakterler boyutu, `pVersion` arabellek.</span><span class="sxs-lookup"><span data-stu-id="1f290-109">[in]  The size, in wide characters, of the `pVersion` buffer.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="1f290-110">[out] Bayt cinsinden döndürülen arabellek uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="1f290-110">[out] The length, in bytes, of the returned buffer.</span></span>  
  
 `dwResolutionFlags`  
 <span data-ttu-id="1f290-111">[in]  Clsıd_resolutıon_flags değerlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="1f290-111">[in]  One of the CLSID_RESOLUTION_FLAGS values.</span></span> <span data-ttu-id="1f290-112">Aşağıdaki değerleri desteklenir:</span><span class="sxs-lookup"><span data-stu-id="1f290-112">The following values are supported:</span></span>  
  
-   <span data-ttu-id="1f290-113">CLSID_RESOLUTION_DEFAULT: Bu varsayılan birlikte çalışma davranışı belirtir (0x0) olmalıdır kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1f290-113">CLSID_RESOLUTION_DEFAULT: (0x0) Specifies that default interop behavior should be used.</span></span>  
  
-   <span data-ttu-id="1f290-114">CLSID_RESOLUTION_REGISTERED: kayıt defteri aranıp aranmayacağını ve dolguya ilkesi belirtir (0x1) olmalıdır uygulanır.</span><span class="sxs-lookup"><span data-stu-id="1f290-114">CLSID_RESOLUTION_REGISTERED: (0x1) Specifies that the registry should be searched and shim policy should be applied.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1f290-115">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="1f290-115">Return Value</span></span>  
  
|<span data-ttu-id="1f290-116">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1f290-116">HRESULT</span></span>|<span data-ttu-id="1f290-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1f290-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1f290-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="1f290-118">S_OK</span></span>|<span data-ttu-id="1f290-119">İşlev başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="1f290-119">The function returned successfully.</span></span>|  
|<span data-ttu-id="1f290-120">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="1f290-120">E_INVALIDARG</span></span>|<span data-ttu-id="1f290-121">Parametrelerden biri geçersiz tür veya biçimi vardır.</span><span class="sxs-lookup"><span data-stu-id="1f290-121">One of the parameters has an invalid type or format.</span></span>|  
|<span data-ttu-id="1f290-122">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="1f290-122">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="1f290-123">`pVersion` Arabelleği tüm sürüm dizesi tutmak için yeterince büyük değil.</span><span class="sxs-lookup"><span data-stu-id="1f290-123">The `pVersion` buffer is not large enough to hold the entire version string.</span></span>|  
|<span data-ttu-id="1f290-124">REGDB_E_CLASSNOTREG</span><span class="sxs-lookup"><span data-stu-id="1f290-124">REGDB_E_CLASSNOTREG</span></span>|<span data-ttu-id="1f290-125">Belirtilen ile kayıtlı bir sınıf yok `CLSID`.</span><span class="sxs-lookup"><span data-stu-id="1f290-125">There is no class registered with the specified `CLSID`.</span></span>|  
|<span data-ttu-id="1f290-126">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="1f290-126">E_POINTER</span></span>|<span data-ttu-id="1f290-127">`dwLength` null, veya `cchBuffer` sürüm dizesi tutmak için yeterince büyük olduğundan, ancak `pVersion` null.</span><span class="sxs-lookup"><span data-stu-id="1f290-127">`dwLength` is null, or `cchBuffer` is large enough to hold the version string, but `pVersion` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1f290-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1f290-128">Requirements</span></span>  
 <span data-ttu-id="1f290-129">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1f290-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f290-130">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1f290-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1f290-131">**.NET framework sürümleri:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f290-131">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f290-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1f290-132">See Also</span></span>  
 [<span data-ttu-id="1f290-133">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="1f290-133">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
