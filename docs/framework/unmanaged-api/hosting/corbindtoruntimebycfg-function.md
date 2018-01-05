---
title: "CorBindToRuntimeByCfg İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorBindToRuntimeByCfg
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: CorBindToRuntimeByCfg
helpviewer_keywords: CorBindToRuntimeByCfg function [.NET Framework hosting]
ms.assetid: ded1e492-a782-4185-9c66-709e421c1782
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2dccd777ef20f68d091cfdd7939c57a1f8d42ad5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="corbindtoruntimebycfg-function"></a><span data-ttu-id="a6cf7-102">CorBindToRuntimeByCfg İşlevi</span><span class="sxs-lookup"><span data-stu-id="a6cf7-102">CorBindToRuntimeByCfg Function</span></span>
<span data-ttu-id="a6cf7-103">Ortak dil çalışma zamanı (CLR), bir XML dosyasından okuma sürüm bilgilerini kullanarak bir sürecine yükler.</span><span class="sxs-lookup"><span data-stu-id="a6cf7-103">Loads the common language runtime (CLR) into a process by using version information that is read from an XML file.</span></span>  
  
 <span data-ttu-id="a6cf7-104">Bu işlev kaldırılmamıştır [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a6cf7-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6cf7-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a6cf7-105">Syntax</span></span>  
  
```  
HRESULT CorBindToRuntimeByCfg (  
    [in]  IStream     *pCfgStream,  
    [in]  DWORD        reserved,  
    [in]  DWORD        startupFlags,  
    [in]  REFCLSID     rclsid,  
    [in]  REFIID       riid,   
    [out] LPVOID FAR*  ppv  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a6cf7-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a6cf7-106">Parameters</span></span>  
 `pCfgStream`  
 <span data-ttu-id="a6cf7-107">[in] Bir işaretçi bir `IStream` XML dosyasını okur nesnesi.</span><span class="sxs-lookup"><span data-stu-id="a6cf7-107">[in] A pointer to an `IStream` object that reads the XML file.</span></span>  
  
 `reserved`  
 <span data-ttu-id="a6cf7-108">[in] Gelecekte kullanılmak üzere ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="a6cf7-108">[in] Reserved for future use.</span></span> <span data-ttu-id="a6cf7-109">0 (sıfır) değeri olarak kullanın.</span><span class="sxs-lookup"><span data-stu-id="a6cf7-109">Use 0 (zero) as value.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="a6cf7-110">[in] Değerini [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) CLR başlatma davranışını belirtir numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="a6cf7-110">[in] A value of the [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) enumeration that specifies the startup behavior of the CLR.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="a6cf7-111">[in] `CLSID` Ya da uygulayan coclass'ı, [Icorruntimehost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) veya [Iclrruntimehost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="a6cf7-111">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="a6cf7-112">Değerleri CLSID_CorRuntimeHost veya CLSID_CLRRuntimeHost desteklenir.</span><span class="sxs-lookup"><span data-stu-id="a6cf7-112">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="a6cf7-113">[in] `IID` Herhangi birinin `ICorRuntimeHost` veya `ICLRRuntimeHost` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="a6cf7-113">[in] The `IID` of either the `ICorRuntimeHost` or the `ICLRRuntimeHost` interface.</span></span> <span data-ttu-id="a6cf7-114">Değerleri IID_ICorRuntimeHost veya IID_ICLRRuntimeHost desteklenir.</span><span class="sxs-lookup"><span data-stu-id="a6cf7-114">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="a6cf7-115">[out] Döndürülen arabiriminin adresini gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a6cf7-115">[out] A pointer to the address of the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a6cf7-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a6cf7-116">Remarks</span></span>  
 <span data-ttu-id="a6cf7-117">XML dosyasının formatı sonra standart uygulama yapılandırma dosyası modellenir.</span><span class="sxs-lookup"><span data-stu-id="a6cf7-117">The format of the XML file is modeled after the standard application configuration file.</span></span> <span data-ttu-id="a6cf7-118">XML dosyaları hakkında daha fazla bilgi için bkz: [yapılandırma dosyası şeması](../../../../docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="a6cf7-118">For more information about XML files, see [Configuration File Schema](../../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a6cf7-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a6cf7-119">Requirements</span></span>  
 <span data-ttu-id="a6cf7-120">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a6cf7-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6cf7-121">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a6cf7-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a6cf7-122">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a6cf7-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a6cf7-123">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a6cf7-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6cf7-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a6cf7-124">See Also</span></span>  
 [<span data-ttu-id="a6cf7-125">CorBindToCurrentRuntime İşlevi</span><span class="sxs-lookup"><span data-stu-id="a6cf7-125">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)  
 [<span data-ttu-id="a6cf7-126">CorBindToRuntime İşlevi</span><span class="sxs-lookup"><span data-stu-id="a6cf7-126">CorBindToRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)  
 [<span data-ttu-id="a6cf7-127">CorBindToRuntimeEx İşlevi</span><span class="sxs-lookup"><span data-stu-id="a6cf7-127">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)  
 [<span data-ttu-id="a6cf7-128">CorBindToRuntimeHost İşlevi</span><span class="sxs-lookup"><span data-stu-id="a6cf7-128">CorBindToRuntimeHost Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)  
 [<span data-ttu-id="a6cf7-129">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a6cf7-129">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)  
 [<span data-ttu-id="a6cf7-130">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="a6cf7-130">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
