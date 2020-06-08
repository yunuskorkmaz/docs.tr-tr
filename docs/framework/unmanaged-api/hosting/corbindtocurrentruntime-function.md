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
ms.openlocfilehash: 4c015d77deb4e6ed3d43074f2903e26b687de84f
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84493571"
---
# <a name="corbindtocurrentruntime-function"></a><span data-ttu-id="72e83-102">CorBindToCurrentRuntime İşlevi</span><span class="sxs-lookup"><span data-stu-id="72e83-102">CorBindToCurrentRuntime Function</span></span>
<span data-ttu-id="72e83-103">Bir XML dosyasında depolanan sürüm bilgilerini kullanarak ortak dil çalışma zamanını (CLR) bir işleme yükler.</span><span class="sxs-lookup"><span data-stu-id="72e83-103">Loads the common language runtime (CLR) into a process by using version information stored in an XML file.</span></span> <span data-ttu-id="72e83-104">XML dosyasının biçimi, standart uygulama yapılandırma dosyasından sonra modellenir.</span><span class="sxs-lookup"><span data-stu-id="72e83-104">The format of the XML file is modeled after the standard application configuration file.</span></span> <span data-ttu-id="72e83-105">Yapılandırma dosyaları hakkında daha fazla bilgi için bkz. [yapılandırma dosyası şeması](../../configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="72e83-105">For more information about configuration files, see [Configuration File Schema](../../configure-apps/file-schema/index.md).</span></span>  
  
 <span data-ttu-id="72e83-106">Bu işlev .NET Framework 4 ' te kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="72e83-106">This function has been deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="72e83-107">Bkz. [ortak dil çalışma zamanını bir Işleme yükleme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/01918c6x(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="72e83-107">See [Loading the Common Language Runtime into a Process](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/01918c6x(v=vs.100)).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72e83-108">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="72e83-108">Syntax</span></span>  
  
```cpp  
HRESULT CorBindToCurrentRuntime (  
    [in]  LPCWSTR   pwszFileName,  
    [in]  REFCLSID  rclsid,  
    [in]  REFIID    riid,  
    [out] LPVOID    *ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="72e83-109">Parametreler</span><span class="sxs-lookup"><span data-stu-id="72e83-109">Parameters</span></span>  
 `pwszFileName`  
 <span data-ttu-id="72e83-110">'ndaki Yüklenecek CLR sürümünü belirten bir uygulama yapılandırma dosyasının adı.</span><span class="sxs-lookup"><span data-stu-id="72e83-110">[in] The name of an application configuration file that specifies the version of the CLR to load.</span></span> <span data-ttu-id="72e83-111">Dosya adı tam nitelikli değilse, çağrıyı yapan yürütülebilirle aynı dizinde olduğu varsayılır.</span><span class="sxs-lookup"><span data-stu-id="72e83-111">If the file name is not fully qualified, it is assumed to be in the same directory as the executable making the call.</span></span>  
  
 <span data-ttu-id="72e83-112">Yüklenecek çalışma zamanının sürümü, [\<requiredRuntime>](../../configure-apps/file-schema/startup/requiredruntime-element.md) yapılandırma dosyasının öğesindeki sürüm özniteliğiyle açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="72e83-112">The version of the runtime to be loaded is described by the version attribute in the [\<requiredRuntime>](../../configure-apps/file-schema/startup/requiredruntime-element.md) element of the configuration file.</span></span>  
  
 <span data-ttu-id="72e83-113">Sürüm belirtilmemişse veya `<requiredRuntime>` öğe bulunamazsa, makinede yüklü olan CLR 'nin en son sürümü yüklenir.</span><span class="sxs-lookup"><span data-stu-id="72e83-113">If no version is specified, or if the `<requiredRuntime>` element cannot be found, the latest version of the CLR that is installed on the machine is loaded.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="72e83-114">'ndaki `CLSID` [ICorRuntimeHost](icorruntimehost-interface.md) veya [ICLRRuntimeHost](iclrruntimehost-interface.md) arabirimini uygulayan coclass.</span><span class="sxs-lookup"><span data-stu-id="72e83-114">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](icorruntimehost-interface.md) or the [ICLRRuntimeHost](iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="72e83-115">Desteklenen değerler CLSID_CorRuntimeHost veya CLSID_CLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="72e83-115">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="72e83-116">'ndaki `IID`İstediğiniz arabirim.</span><span class="sxs-lookup"><span data-stu-id="72e83-116">[in] The `IID` of the interface you are requesting.</span></span> <span data-ttu-id="72e83-117">Desteklenen değerler IID_ICorRuntimeHost veya IID_ICLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="72e83-117">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="72e83-118">dışı Döndürülen arabirim işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="72e83-118">[out] The returned interface pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72e83-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="72e83-119">Requirements</span></span>  
 <span data-ttu-id="72e83-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="72e83-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72e83-121">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="72e83-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="72e83-122">**Kitaplık:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="72e83-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="72e83-123">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72e83-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72e83-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="72e83-124">See also</span></span>

- [<span data-ttu-id="72e83-125">CorBindToRuntime İşlevi</span><span class="sxs-lookup"><span data-stu-id="72e83-125">CorBindToRuntime Function</span></span>](corbindtoruntime-function.md)
- [<span data-ttu-id="72e83-126">CorBindToRuntimeByCfg İşlevi</span><span class="sxs-lookup"><span data-stu-id="72e83-126">CorBindToRuntimeByCfg Function</span></span>](corbindtoruntimebycfg-function.md)
- [<span data-ttu-id="72e83-127">CorBindToRuntimeEx İşlevi</span><span class="sxs-lookup"><span data-stu-id="72e83-127">CorBindToRuntimeEx Function</span></span>](corbindtoruntimeex-function.md)
- [<span data-ttu-id="72e83-128">CorBindToRuntimeHost İşlevi</span><span class="sxs-lookup"><span data-stu-id="72e83-128">CorBindToRuntimeHost Function</span></span>](corbindtoruntimehost-function.md)
- [<span data-ttu-id="72e83-129">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="72e83-129">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
- [<span data-ttu-id="72e83-130">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="72e83-130">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
