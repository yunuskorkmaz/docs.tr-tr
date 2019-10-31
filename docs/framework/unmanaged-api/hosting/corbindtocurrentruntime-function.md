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
ms.openlocfilehash: 77a0a8f58c11673a1958d837b4c3a21a05754c94
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138326"
---
# <a name="corbindtocurrentruntime-function"></a><span data-ttu-id="e2c98-102">CorBindToCurrentRuntime İşlevi</span><span class="sxs-lookup"><span data-stu-id="e2c98-102">CorBindToCurrentRuntime Function</span></span>
<span data-ttu-id="e2c98-103">Bir XML dosyasında depolanan sürüm bilgilerini kullanarak ortak dil çalışma zamanını (CLR) bir işleme yükler.</span><span class="sxs-lookup"><span data-stu-id="e2c98-103">Loads the common language runtime (CLR) into a process by using version information stored in an XML file.</span></span> <span data-ttu-id="e2c98-104">XML dosyasının biçimi, standart uygulama yapılandırma dosyasından sonra modellenir.</span><span class="sxs-lookup"><span data-stu-id="e2c98-104">The format of the XML file is modeled after the standard application configuration file.</span></span> <span data-ttu-id="e2c98-105">Yapılandırma dosyaları hakkında daha fazla bilgi için bkz. [yapılandırma dosyası şeması](../../../../docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="e2c98-105">For more information about configuration files, see [Configuration File Schema](../../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
 <span data-ttu-id="e2c98-106">Bu işlev .NET Framework 4 ' te kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="e2c98-106">This function has been deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="e2c98-107">Bkz. [ortak dil çalışma zamanını bir Işleme yükleme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/01918c6x(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="e2c98-107">See [Loading the Common Language Runtime into a Process](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/01918c6x(v=vs.100)).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2c98-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e2c98-108">Syntax</span></span>  
  
```cpp  
HRESULT CorBindToCurrentRuntime (  
    [in]  LPCWSTR   pwszFileName,  
    [in]  REFCLSID  rclsid,  
    [in]  REFIID    riid,  
    [out] LPVOID    *ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e2c98-109">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e2c98-109">Parameters</span></span>  
 `pwszFileName`  
 <span data-ttu-id="e2c98-110">'ndaki Yüklenecek CLR sürümünü belirten bir uygulama yapılandırma dosyasının adı.</span><span class="sxs-lookup"><span data-stu-id="e2c98-110">[in] The name of an application configuration file that specifies the version of the CLR to load.</span></span> <span data-ttu-id="e2c98-111">Dosya adı tam nitelikli değilse, çağrıyı yapan yürütülebilirle aynı dizinde olduğu varsayılır.</span><span class="sxs-lookup"><span data-stu-id="e2c98-111">If the file name is not fully qualified, it is assumed to be in the same directory as the executable making the call.</span></span>  
  
 <span data-ttu-id="e2c98-112">Yüklenecek çalışma zamanının sürümü, yapılandırma dosyasının [\<requiredRuntime >](../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md) öğesindeki sürüm özniteliğiyle açıklanır.</span><span class="sxs-lookup"><span data-stu-id="e2c98-112">The version of the runtime to be loaded is described by the version attribute in the [\<requiredRuntime>](../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md) element of the configuration file.</span></span>  
  
 <span data-ttu-id="e2c98-113">Sürüm belirtilmemişse veya `<requiredRuntime>` öğesi bulunamazsa, makinede yüklü olan CLR 'nin en son sürümü yüklenir.</span><span class="sxs-lookup"><span data-stu-id="e2c98-113">If no version is specified, or if the `<requiredRuntime>` element cannot be found, the latest version of the CLR that is installed on the machine is loaded.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="e2c98-114">'ndaki [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) veya [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) arabirimini uygulayan coclass 'ın `CLSID`.</span><span class="sxs-lookup"><span data-stu-id="e2c98-114">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="e2c98-115">Desteklenen değerler CLSID_CorRuntimeHost veya CLSID_CLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="e2c98-115">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="e2c98-116">'ndaki İstediğiniz arabirimin `IID`.</span><span class="sxs-lookup"><span data-stu-id="e2c98-116">[in] The `IID` of the interface you are requesting.</span></span> <span data-ttu-id="e2c98-117">Desteklenen değerler IID_ICorRuntimeHost veya IID_ICLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="e2c98-117">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="e2c98-118">dışı Döndürülen arabirim işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="e2c98-118">[out] The returned interface pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e2c98-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e2c98-119">Requirements</span></span>  
 <span data-ttu-id="e2c98-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e2c98-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e2c98-121">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e2c98-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e2c98-122">**Kitaplık:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e2c98-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e2c98-123">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e2c98-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2c98-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e2c98-124">See also</span></span>

- [<span data-ttu-id="e2c98-125">CorBindToRuntime İşlevi</span><span class="sxs-lookup"><span data-stu-id="e2c98-125">CorBindToRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)
- [<span data-ttu-id="e2c98-126">CorBindToRuntimeByCfg İşlevi</span><span class="sxs-lookup"><span data-stu-id="e2c98-126">CorBindToRuntimeByCfg Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)
- [<span data-ttu-id="e2c98-127">CorBindToRuntimeEx İşlevi</span><span class="sxs-lookup"><span data-stu-id="e2c98-127">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [<span data-ttu-id="e2c98-128">CorBindToRuntimeHost İşlevi</span><span class="sxs-lookup"><span data-stu-id="e2c98-128">CorBindToRuntimeHost Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)
- [<span data-ttu-id="e2c98-129">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e2c98-129">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [<span data-ttu-id="e2c98-130">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="e2c98-130">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
