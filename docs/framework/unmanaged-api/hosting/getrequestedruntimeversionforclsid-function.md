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
ms.openlocfilehash: 6132e94544b30486b70ecfec49c1ddd5e3c0f50b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178111"
---
# <a name="getrequestedruntimeversionforclsid-function"></a><span data-ttu-id="9b0fd-102">GetRequestedRuntimeVersionForCLSID İşlevi</span><span class="sxs-lookup"><span data-stu-id="9b0fd-102">GetRequestedRuntimeVersionForCLSID Function</span></span>
<span data-ttu-id="9b0fd-103">Belirtilen `CLSID`sınıf için uygun ortak dil çalışma zamanı (CLR) sürüm bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="9b0fd-103">Gets the appropriate common language runtime (CLR) version information for the class with the specified `CLSID`.</span></span>  
  
 <span data-ttu-id="9b0fd-104">Bu işlev .NET Framework 4'te amortismana hazırlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="9b0fd-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b0fd-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9b0fd-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRequestedRuntimeVersionForCLSID (  
    [in]  REFCLSID   rclsid,
    [out]  LPWSTR     pVersion,
    [in]  DWORD      cchBuffer,
    [out] DWORD*     dwLength,
    [in]  CLSID_RESOLUTION_FLAGS dwResolutionFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9b0fd-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9b0fd-106">Parameters</span></span>  
 `rclsid`  
 <span data-ttu-id="9b0fd-107">[içinde]  Bileşenin. `CLSID`</span><span class="sxs-lookup"><span data-stu-id="9b0fd-107">[in]  The `CLSID` of the component.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="9b0fd-108">[çıkış]  Başarılı bir şekilde tamamlandıktan sonra sürüm numarası dizesini içeren bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="9b0fd-108">[out]  A buffer that contains the version number string upon successful completion.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="9b0fd-109">[içinde]  Geniş karakterlerdeki arabelleğin `pVersion` boyutu.</span><span class="sxs-lookup"><span data-stu-id="9b0fd-109">[in]  The size, in wide characters, of the `pVersion` buffer.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="9b0fd-110">[çıkış] Döndürülen arabelleğe baytlar halindeki uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="9b0fd-110">[out] The length, in bytes, of the returned buffer.</span></span>  
  
 `dwResolutionFlags`  
 <span data-ttu-id="9b0fd-111">[içinde]  CLSID_RESOLUTION_FLAGS değerlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="9b0fd-111">[in]  One of the CLSID_RESOLUTION_FLAGS values.</span></span> <span data-ttu-id="9b0fd-112">Aşağıdaki değerler desteklenir:</span><span class="sxs-lookup"><span data-stu-id="9b0fd-112">The following values are supported:</span></span>  
  
- <span data-ttu-id="9b0fd-113">CLSID_RESOLUTION_DEFAULT: (0x0) Varsayılan interop davranışının kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="9b0fd-113">CLSID_RESOLUTION_DEFAULT: (0x0) Specifies that default interop behavior should be used.</span></span>  
  
- <span data-ttu-id="9b0fd-114">CLSID_RESOLUTION_REGISTERED: (0x1) Kayıt defterinin aranması ve şim ilkesinin uygulanması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="9b0fd-114">CLSID_RESOLUTION_REGISTERED: (0x1) Specifies that the registry should be searched and shim policy should be applied.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9b0fd-115">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="9b0fd-115">Return Value</span></span>  
  
|<span data-ttu-id="9b0fd-116">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9b0fd-116">HRESULT</span></span>|<span data-ttu-id="9b0fd-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9b0fd-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9b0fd-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="9b0fd-118">S_OK</span></span>|<span data-ttu-id="9b0fd-119">İşlev başarıyla döndü.</span><span class="sxs-lookup"><span data-stu-id="9b0fd-119">The function returned successfully.</span></span>|  
|<span data-ttu-id="9b0fd-120">E_ınvalıdarg</span><span class="sxs-lookup"><span data-stu-id="9b0fd-120">E_INVALIDARG</span></span>|<span data-ttu-id="9b0fd-121">Parametrelerden birinin geçersiz türü veya biçimi vardır.</span><span class="sxs-lookup"><span data-stu-id="9b0fd-121">One of the parameters has an invalid type or format.</span></span>|  
|<span data-ttu-id="9b0fd-122">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="9b0fd-122">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="9b0fd-123">Arabellek `pVersion` tüm sürüm dizesini tutacak kadar büyük değil.</span><span class="sxs-lookup"><span data-stu-id="9b0fd-123">The `pVersion` buffer is not large enough to hold the entire version string.</span></span>|  
|<span data-ttu-id="9b0fd-124">REGDB_E_CLASSNOTREG</span><span class="sxs-lookup"><span data-stu-id="9b0fd-124">REGDB_E_CLASSNOTREG</span></span>|<span data-ttu-id="9b0fd-125">Belirtilen `CLSID`sınıfa kayıtlı bir sınıf yok.</span><span class="sxs-lookup"><span data-stu-id="9b0fd-125">There is no class registered with the specified `CLSID`.</span></span>|  
|<span data-ttu-id="9b0fd-126">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="9b0fd-126">E_POINTER</span></span>|<span data-ttu-id="9b0fd-127">`dwLength`null veya `cchBuffer` sürüm dizesini tutmak için `pVersion` yeterince büyük, ancak null.</span><span class="sxs-lookup"><span data-stu-id="9b0fd-127">`dwLength` is null, or `cchBuffer` is large enough to hold the version string, but `pVersion` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9b0fd-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9b0fd-128">Requirements</span></span>  
 <span data-ttu-id="9b0fd-129">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9b0fd-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b0fd-130">**Üstbilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9b0fd-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9b0fd-131">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b0fd-131">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b0fd-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9b0fd-132">See also</span></span>

- [<span data-ttu-id="9b0fd-133">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="9b0fd-133">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
