---
title: CorBindToCurrentRuntime İşlevi
ms.date: 03/30/2017
api_name:
- CorBindToCurrentRuntime
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- HeaderDef
f1_keywords:
- CorBindToCurrentRuntime
helpviewer_keywords:
- CorBindToCurrentRuntime function [.NET Framework hosting]
ms.assetid: 6105c13e-d9cd-44d2-a95a-924e042830c7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d0acb322fa3348f0bb2d819529a370110580343c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59178067"
---
# <a name="corbindtocurrentruntime-function"></a><span data-ttu-id="c7ba7-102">CorBindToCurrentRuntime İşlevi</span><span class="sxs-lookup"><span data-stu-id="c7ba7-102">CorBindToCurrentRuntime Function</span></span>
<span data-ttu-id="c7ba7-103">Ortak dil çalışma zamanı (CLR), bir XML dosyasında depolanan sürüm bilgilerini kullanarak bir işlem içine yükler.</span><span class="sxs-lookup"><span data-stu-id="c7ba7-103">Loads the common language runtime (CLR) into a process by using version information stored in an XML file.</span></span> <span data-ttu-id="c7ba7-104">XML dosyasının biçimi sonra standart uygulama yapılandırma dosyasına modellenir.</span><span class="sxs-lookup"><span data-stu-id="c7ba7-104">The format of the XML file is modeled after the standard application configuration file.</span></span> <span data-ttu-id="c7ba7-105">Yapılandırma dosyaları hakkında daha fazla bilgi için bkz. [yapılandırma dosyası şeması](../../../../docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="c7ba7-105">For more information about configuration files, see [Configuration File Schema](../../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
 <span data-ttu-id="c7ba7-106">Bu işlev içinde kullanımdan kalkmış [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c7ba7-106">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="c7ba7-107">Bkz: [ortak dil çalışma zamanını bir işleme yükleme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/01918c6x(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="c7ba7-107">See [Loading the Common Language Runtime into a Process](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/01918c6x(v=vs.100)).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7ba7-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c7ba7-108">Syntax</span></span>  
  
```  
HRESULT CorBindToCurrentRuntime (  
    [in]  LPCWSTR   pwszFileName,  
    [in]  REFCLSID  rclsid,  
    [in]  REFIID    riid,  
    [out] LPVOID    *ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c7ba7-109">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c7ba7-109">Parameters</span></span>  
 `pwszFileName`  
 <span data-ttu-id="c7ba7-110">[in] Yüklenecek CLR sürümünü belirten bir uygulama yapılandırma dosyası adı.</span><span class="sxs-lookup"><span data-stu-id="c7ba7-110">[in] The name of an application configuration file that specifies the version of the CLR to load.</span></span> <span data-ttu-id="c7ba7-111">Dosya adı tam nitelenmiş değil, çağrıyı yapan yürütülebilir dosya ile aynı dizinde olduğu varsayılır.</span><span class="sxs-lookup"><span data-stu-id="c7ba7-111">If the file name is not fully qualified, it is assumed to be in the same directory as the executable making the call.</span></span>  
  
 <span data-ttu-id="c7ba7-112">Yüklenecek çalışma zamanı sürümü içindeki version özniteliği tarafından tanımlanan [ \<requiredRuntime >](../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md) yapılandırma dosyasının öğesi.</span><span class="sxs-lookup"><span data-stu-id="c7ba7-112">The version of the runtime to be loaded is described by the version attribute in the [\<requiredRuntime>](../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md) element of the configuration file.</span></span>  
  
 <span data-ttu-id="c7ba7-113">Hiçbir sürüm belirtilmezse veya `<requiredRuntime>` öğesi bulunamıyor, makinede yüklü CLR en son sürümü yüklendi.</span><span class="sxs-lookup"><span data-stu-id="c7ba7-113">If no version is specified, or if the `<requiredRuntime>` element cannot be found, the latest version of the CLR that is installed on the machine is loaded.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="c7ba7-114">[in] `CLSID` Ya da uygulayan yardımcı sınıf, [Icorruntimehost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) veya [Iclrruntimehost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="c7ba7-114">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="c7ba7-115">Desteklenen değerler: clsıd_corruntimehost veya clsıd_clrruntimehost şunlardır.</span><span class="sxs-lookup"><span data-stu-id="c7ba7-115">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="c7ba7-116">[in] `IID` Arabirimin istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="c7ba7-116">[in] The `IID` of the interface you are requesting.</span></span> <span data-ttu-id="c7ba7-117">Desteklenen değerler: ııd_ıcorruntimehost veya ııd_ıclrruntimehost şunlardır.</span><span class="sxs-lookup"><span data-stu-id="c7ba7-117">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="c7ba7-118">[out] Döndürülen arabirim işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="c7ba7-118">[out] The returned interface pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7ba7-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c7ba7-119">Requirements</span></span>  
 <span data-ttu-id="c7ba7-120">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c7ba7-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7ba7-121">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c7ba7-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c7ba7-122">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c7ba7-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c7ba7-123">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7ba7-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7ba7-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c7ba7-124">See also</span></span>

- [<span data-ttu-id="c7ba7-125">CorBindToRuntime İşlevi</span><span class="sxs-lookup"><span data-stu-id="c7ba7-125">CorBindToRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)
- [<span data-ttu-id="c7ba7-126">CorBindToRuntimeByCfg İşlevi</span><span class="sxs-lookup"><span data-stu-id="c7ba7-126">CorBindToRuntimeByCfg Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)
- [<span data-ttu-id="c7ba7-127">CorBindToRuntimeEx İşlevi</span><span class="sxs-lookup"><span data-stu-id="c7ba7-127">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [<span data-ttu-id="c7ba7-128">CorBindToRuntimeHost İşlevi</span><span class="sxs-lookup"><span data-stu-id="c7ba7-128">CorBindToRuntimeHost Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)
- [<span data-ttu-id="c7ba7-129">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c7ba7-129">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [<span data-ttu-id="c7ba7-130">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="c7ba7-130">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
