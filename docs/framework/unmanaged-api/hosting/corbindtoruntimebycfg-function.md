---
title: CorBindToRuntimeByCfg İşlevi
ms.date: 03/30/2017
api_name:
- CorBindToRuntimeByCfg
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- CorBindToRuntimeByCfg
helpviewer_keywords:
- CorBindToRuntimeByCfg function [.NET Framework hosting]
ms.assetid: ded1e492-a782-4185-9c66-709e421c1782
topic_type:
- apiref
ms.openlocfilehash: 4fbc6e7ea531f65a6b1cd0ec93f4847ab8e4fe83
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178240"
---
# <a name="corbindtoruntimebycfg-function"></a><span data-ttu-id="9eb47-102">CorBindToRuntimeByCfg İşlevi</span><span class="sxs-lookup"><span data-stu-id="9eb47-102">CorBindToRuntimeByCfg Function</span></span>
<span data-ttu-id="9eb47-103">XML dosyasından okunan sürüm bilgilerini kullanarak ortak dil çalışma süresini (CLR) işleme yükler.</span><span class="sxs-lookup"><span data-stu-id="9eb47-103">Loads the common language runtime (CLR) into a process by using version information that is read from an XML file.</span></span>  
  
 <span data-ttu-id="9eb47-104">Bu işlev .NET Framework 4'te amortismana hazırlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="9eb47-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9eb47-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9eb47-105">Syntax</span></span>  
  
```cpp  
HRESULT CorBindToRuntimeByCfg (  
    [in]  IStream     *pCfgStream,  
    [in]  DWORD        reserved,  
    [in]  DWORD        startupFlags,  
    [in]  REFCLSID     rclsid,  
    [in]  REFIID       riid,
    [out] LPVOID FAR*  ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9eb47-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9eb47-106">Parameters</span></span>  
 `pCfgStream`  
 <span data-ttu-id="9eb47-107">[içinde] XML dosyasını okuyan bir `IStream` nesneye işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9eb47-107">[in] A pointer to an `IStream` object that reads the XML file.</span></span>  
  
 `reserved`  
 <span data-ttu-id="9eb47-108">[içinde] İleride kullanım için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="9eb47-108">[in] Reserved for future use.</span></span> <span data-ttu-id="9eb47-109">Değer olarak 0 (sıfır) kullanın.</span><span class="sxs-lookup"><span data-stu-id="9eb47-109">Use 0 (zero) as value.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="9eb47-110">[içinde] CLR'nin başlangıç davranışını belirten [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) numaralandırmadeğeri.</span><span class="sxs-lookup"><span data-stu-id="9eb47-110">[in] A value of the [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) enumeration that specifies the startup behavior of the CLR.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="9eb47-111">[içinde] `CLSID` [ICorRuntimeHost veya ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) arabirimi [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) ya uygular coclass.</span><span class="sxs-lookup"><span data-stu-id="9eb47-111">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="9eb47-112">Desteklenen değerler CLSID_CorRuntimeHost veya CLSID_CLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="9eb47-112">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="9eb47-113">[içinde] Ya `IID` `ICorRuntimeHost` arayüz ya `ICLRRuntimeHost` da.</span><span class="sxs-lookup"><span data-stu-id="9eb47-113">[in] The `IID` of either the `ICorRuntimeHost` or the `ICLRRuntimeHost` interface.</span></span> <span data-ttu-id="9eb47-114">Desteklenen değerler IID_ICorRuntimeHost veya IID_ICLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="9eb47-114">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="9eb47-115">[çıkış] Döndürülen arabirimin adresine işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9eb47-115">[out] A pointer to the address of the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9eb47-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9eb47-116">Remarks</span></span>  
 <span data-ttu-id="9eb47-117">XML dosyasının biçimi standart uygulama yapılandırma dosyasından sonra modellenir.</span><span class="sxs-lookup"><span data-stu-id="9eb47-117">The format of the XML file is modeled after the standard application configuration file.</span></span> <span data-ttu-id="9eb47-118">XML dosyaları hakkında daha fazla bilgi için [Configuration File Schema'ya](../../../../docs/framework/configure-apps/file-schema/index.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="9eb47-118">For more information about XML files, see [Configuration File Schema](../../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9eb47-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9eb47-119">Requirements</span></span>  
 <span data-ttu-id="9eb47-120">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9eb47-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9eb47-121">**Üstbilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9eb47-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9eb47-122">**Kütüphane:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="9eb47-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9eb47-123">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9eb47-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9eb47-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9eb47-124">See also</span></span>

- [<span data-ttu-id="9eb47-125">CorBindToCurrentRuntime İşlevi</span><span class="sxs-lookup"><span data-stu-id="9eb47-125">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [<span data-ttu-id="9eb47-126">CorBindToRuntime İşlevi</span><span class="sxs-lookup"><span data-stu-id="9eb47-126">CorBindToRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)
- [<span data-ttu-id="9eb47-127">CorBindToRuntimeEx İşlevi</span><span class="sxs-lookup"><span data-stu-id="9eb47-127">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [<span data-ttu-id="9eb47-128">CorBindToRuntimeHost İşlevi</span><span class="sxs-lookup"><span data-stu-id="9eb47-128">CorBindToRuntimeHost Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)
- [<span data-ttu-id="9eb47-129">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9eb47-129">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [<span data-ttu-id="9eb47-130">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="9eb47-130">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
