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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bbba208296dd2099c9da58c81ff66fddc78fdc86
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59093826"
---
# <a name="corbindtoruntimebycfg-function"></a><span data-ttu-id="3ad98-102">CorBindToRuntimeByCfg İşlevi</span><span class="sxs-lookup"><span data-stu-id="3ad98-102">CorBindToRuntimeByCfg Function</span></span>
<span data-ttu-id="3ad98-103">Ortak dil çalışma zamanı (CLR), bir XML dosyasından okunan sürüm bilgilerini kullanarak bir işlem içine yükler.</span><span class="sxs-lookup"><span data-stu-id="3ad98-103">Loads the common language runtime (CLR) into a process by using version information that is read from an XML file.</span></span>  
  
 <span data-ttu-id="3ad98-104">Bu işlev içinde kullanımdan kalkmış [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3ad98-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ad98-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3ad98-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="3ad98-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3ad98-106">Parameters</span></span>  
 `pCfgStream`  
 <span data-ttu-id="3ad98-107">[in] Bir işaretçi bir `IStream` XML dosyasını okuyan bir nesne.</span><span class="sxs-lookup"><span data-stu-id="3ad98-107">[in] A pointer to an `IStream` object that reads the XML file.</span></span>  
  
 `reserved`  
 <span data-ttu-id="3ad98-108">[in] Gelecekte kullanılmak üzere ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="3ad98-108">[in] Reserved for future use.</span></span> <span data-ttu-id="3ad98-109">Değeri olarak 0 (sıfır) kullanın.</span><span class="sxs-lookup"><span data-stu-id="3ad98-109">Use 0 (zero) as value.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="3ad98-110">[in] Değerini [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) CLR başlangıç davranışını belirten sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="3ad98-110">[in] A value of the [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) enumeration that specifies the startup behavior of the CLR.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="3ad98-111">[in] `CLSID` Ya da uygulayan yardımcı sınıf, [Icorruntimehost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) veya [Iclrruntimehost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="3ad98-111">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="3ad98-112">Desteklenen değerler: clsıd_corruntimehost veya clsıd_clrruntimehost şunlardır.</span><span class="sxs-lookup"><span data-stu-id="3ad98-112">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="3ad98-113">[in] `IID` Herhangi birinin `ICorRuntimeHost` veya `ICLRRuntimeHost` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="3ad98-113">[in] The `IID` of either the `ICorRuntimeHost` or the `ICLRRuntimeHost` interface.</span></span> <span data-ttu-id="3ad98-114">Desteklenen değerler: ııd_ıcorruntimehost veya ııd_ıclrruntimehost şunlardır.</span><span class="sxs-lookup"><span data-stu-id="3ad98-114">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="3ad98-115">[out] Döndürülen arabirim adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3ad98-115">[out] A pointer to the address of the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3ad98-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3ad98-116">Remarks</span></span>  
 <span data-ttu-id="3ad98-117">XML dosyasının biçimi sonra standart uygulama yapılandırma dosyasına modellenir.</span><span class="sxs-lookup"><span data-stu-id="3ad98-117">The format of the XML file is modeled after the standard application configuration file.</span></span> <span data-ttu-id="3ad98-118">XML dosyaları hakkında daha fazla bilgi için bkz. [yapılandırma dosyası şeması](../../../../docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="3ad98-118">For more information about XML files, see [Configuration File Schema](../../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3ad98-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3ad98-119">Requirements</span></span>  
 <span data-ttu-id="3ad98-120">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3ad98-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3ad98-121">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3ad98-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3ad98-122">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3ad98-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3ad98-123">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3ad98-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ad98-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3ad98-124">See also</span></span>

- [<span data-ttu-id="3ad98-125">CorBindToCurrentRuntime İşlevi</span><span class="sxs-lookup"><span data-stu-id="3ad98-125">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [<span data-ttu-id="3ad98-126">CorBindToRuntime İşlevi</span><span class="sxs-lookup"><span data-stu-id="3ad98-126">CorBindToRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)
- [<span data-ttu-id="3ad98-127">CorBindToRuntimeEx İşlevi</span><span class="sxs-lookup"><span data-stu-id="3ad98-127">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [<span data-ttu-id="3ad98-128">CorBindToRuntimeHost İşlevi</span><span class="sxs-lookup"><span data-stu-id="3ad98-128">CorBindToRuntimeHost Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)
- [<span data-ttu-id="3ad98-129">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3ad98-129">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [<span data-ttu-id="3ad98-130">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="3ad98-130">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
