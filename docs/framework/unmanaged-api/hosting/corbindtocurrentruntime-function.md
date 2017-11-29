---
title: "CorBindToCurrentRuntime İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorBindToCurrentRuntime
api_location:
- mscoree.dll
- mscoreei.dll
api_type: HeaderDef
f1_keywords: CorBindToCurrentRuntime
helpviewer_keywords: CorBindToCurrentRuntime function [.NET Framework hosting]
ms.assetid: 6105c13e-d9cd-44d2-a95a-924e042830c7
topic_type: apiref
caps.latest.revision: "22"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 630dab4fec8c37bd776b68870a53ab20e4050e06
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="corbindtocurrentruntime-function"></a><span data-ttu-id="21ee5-102">CorBindToCurrentRuntime İşlevi</span><span class="sxs-lookup"><span data-stu-id="21ee5-102">CorBindToCurrentRuntime Function</span></span>
<span data-ttu-id="21ee5-103">Ortak dil çalışma zamanı (CLR), bir XML dosyasında depolanan sürüm bilgileri kullanarak bir sürecine yükler.</span><span class="sxs-lookup"><span data-stu-id="21ee5-103">Loads the common language runtime (CLR) into a process by using version information stored in an XML file.</span></span> <span data-ttu-id="21ee5-104">XML dosyasının formatı sonra standart uygulama yapılandırma dosyası modellenir.</span><span class="sxs-lookup"><span data-stu-id="21ee5-104">The format of the XML file is modeled after the standard application configuration file.</span></span> <span data-ttu-id="21ee5-105">Yapılandırma dosyaları hakkında daha fazla bilgi için bkz: [yapılandırma dosyası şeması](../../../../docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="21ee5-105">For more information about configuration files, see [Configuration File Schema](../../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
 <span data-ttu-id="21ee5-106">Bu işlev kaldırılmamıştır [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="21ee5-106">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="21ee5-107">Bkz: [ortak dil çalışma zamanı yükleme işlemi](http://msdn.microsoft.com/en-us/1e2d6dc1-6aab-43e2-bbc0-aae40756d24f).</span><span class="sxs-lookup"><span data-stu-id="21ee5-107">See [Loading the Common Language Runtime into a Process](http://msdn.microsoft.com/en-us/1e2d6dc1-6aab-43e2-bbc0-aae40756d24f).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21ee5-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="21ee5-108">Syntax</span></span>  
  
```  
HRESULT CorBindToCurrentRuntime (  
    [in]  LPCWSTR   pwszFileName,  
    [in]  REFCLSID  rclsid,  
    [in]  REFIID    riid,  
    [out] LPVOID    *ppv  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="21ee5-109">Parametreler</span><span class="sxs-lookup"><span data-stu-id="21ee5-109">Parameters</span></span>  
 `pwszFileName`  
 <span data-ttu-id="21ee5-110">[in] Yüklemek için CLR sürümünü belirten bir uygulama yapılandırma dosyasının adı.</span><span class="sxs-lookup"><span data-stu-id="21ee5-110">[in] The name of an application configuration file that specifies the version of the CLR to load.</span></span> <span data-ttu-id="21ee5-111">Dosya adı tam olarak nitelenmiş değil, çağrıyı yapan yürütülebilir dosya ile aynı dizinde olduğu varsayılır.</span><span class="sxs-lookup"><span data-stu-id="21ee5-111">If the file name is not fully qualified, it is assumed to be in the same directory as the executable making the call.</span></span>  
  
 <span data-ttu-id="21ee5-112">Yüklenecek çalışma zamanı sürümü sürüm özniteliğinde tarafından açıklanan [ \<requiredRuntime >](../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md) yapılandırma dosyası öğesi.</span><span class="sxs-lookup"><span data-stu-id="21ee5-112">The version of the runtime to be loaded is described by the version attribute in the [\<requiredRuntime>](../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md) element of the configuration file.</span></span>  
  
 <span data-ttu-id="21ee5-113">Hiçbir sürüm belirtilmezse veya `<requiredRuntime>` öğesi bulunamadı, makinede yüklü CLR en son sürümü yüklendi.</span><span class="sxs-lookup"><span data-stu-id="21ee5-113">If no version is specified, or if the `<requiredRuntime>` element cannot be found, the latest version of the CLR that is installed on the machine is loaded.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="21ee5-114">[in] `CLSID` Ya da uygulayan coclass'ı, [Icorruntimehost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) veya [Iclrruntimehost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="21ee5-114">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="21ee5-115">Değerleri CLSID_CorRuntimeHost veya CLSID_CLRRuntimeHost desteklenir.</span><span class="sxs-lookup"><span data-stu-id="21ee5-115">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="21ee5-116">[in] `IID` İsteyen arabirimi.</span><span class="sxs-lookup"><span data-stu-id="21ee5-116">[in] The `IID` of the interface you are requesting.</span></span> <span data-ttu-id="21ee5-117">Değerleri IID_ICorRuntimeHost veya IID_ICLRRuntimeHost desteklenir.</span><span class="sxs-lookup"><span data-stu-id="21ee5-117">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="21ee5-118">[out] Döndürülen arabirim işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="21ee5-118">[out] The returned interface pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21ee5-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="21ee5-119">Requirements</span></span>  
 <span data-ttu-id="21ee5-120">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21ee5-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21ee5-121">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="21ee5-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="21ee5-122">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="21ee5-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="21ee5-123">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21ee5-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21ee5-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="21ee5-124">See Also</span></span>  
 [<span data-ttu-id="21ee5-125">CorBindToRuntime işlevi</span><span class="sxs-lookup"><span data-stu-id="21ee5-125">CorBindToRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)  
 [<span data-ttu-id="21ee5-126">CorBindToRuntimeByCfg işlevi</span><span class="sxs-lookup"><span data-stu-id="21ee5-126">CorBindToRuntimeByCfg Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)  
 [<span data-ttu-id="21ee5-127">CorBindToRuntimeEx işlevi</span><span class="sxs-lookup"><span data-stu-id="21ee5-127">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)  
 [<span data-ttu-id="21ee5-128">CorBindToRuntimeHost işlevi</span><span class="sxs-lookup"><span data-stu-id="21ee5-128">CorBindToRuntimeHost Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)  
 [<span data-ttu-id="21ee5-129">Icorruntimehost arabirimi</span><span class="sxs-lookup"><span data-stu-id="21ee5-129">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)  
 [<span data-ttu-id="21ee5-130">Kullanım dışı CLR barındırma işlevleri</span><span class="sxs-lookup"><span data-stu-id="21ee5-130">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
