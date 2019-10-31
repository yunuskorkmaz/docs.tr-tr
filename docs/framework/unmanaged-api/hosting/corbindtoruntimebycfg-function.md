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
ms.openlocfilehash: 3802354bf52cd2aab2a4149d565993b9965e8312
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138295"
---
# <a name="corbindtoruntimebycfg-function"></a><span data-ttu-id="21522-102">CorBindToRuntimeByCfg İşlevi</span><span class="sxs-lookup"><span data-stu-id="21522-102">CorBindToRuntimeByCfg Function</span></span>
<span data-ttu-id="21522-103">Bir XML dosyasından okunan sürüm bilgilerini kullanarak ortak dil çalışma zamanını (CLR) bir işleme yükler.</span><span class="sxs-lookup"><span data-stu-id="21522-103">Loads the common language runtime (CLR) into a process by using version information that is read from an XML file.</span></span>  
  
 <span data-ttu-id="21522-104">Bu işlev .NET Framework 4 ' te kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="21522-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21522-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="21522-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="21522-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="21522-106">Parameters</span></span>  
 `pCfgStream`  
 <span data-ttu-id="21522-107">'ndaki XML dosyasını okuyan `IStream` nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="21522-107">[in] A pointer to an `IStream` object that reads the XML file.</span></span>  
  
 `reserved`  
 <span data-ttu-id="21522-108">'ndaki Gelecekte kullanılmak üzere ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="21522-108">[in] Reserved for future use.</span></span> <span data-ttu-id="21522-109">Değer olarak 0 (sıfır) kullanın.</span><span class="sxs-lookup"><span data-stu-id="21522-109">Use 0 (zero) as value.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="21522-110">'ndaki CLR 'nin başlangıç davranışını belirten [startup_flags](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) numaralandırması değeri.</span><span class="sxs-lookup"><span data-stu-id="21522-110">[in] A value of the [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) enumeration that specifies the startup behavior of the CLR.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="21522-111">'ndaki [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) veya [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) arabirimini uygulayan coclass 'ın `CLSID`.</span><span class="sxs-lookup"><span data-stu-id="21522-111">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="21522-112">Desteklenen değerler CLSID_CorRuntimeHost veya CLSID_CLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="21522-112">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="21522-113">'ndaki `ICorRuntimeHost` ya da `ICLRRuntimeHost` arabiriminin `IID`.</span><span class="sxs-lookup"><span data-stu-id="21522-113">[in] The `IID` of either the `ICorRuntimeHost` or the `ICLRRuntimeHost` interface.</span></span> <span data-ttu-id="21522-114">Desteklenen değerler IID_ICorRuntimeHost veya IID_ICLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="21522-114">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="21522-115">dışı Döndürülen arabirimin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="21522-115">[out] A pointer to the address of the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="21522-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="21522-116">Remarks</span></span>  
 <span data-ttu-id="21522-117">XML dosyasının biçimi, standart uygulama yapılandırma dosyasından sonra modellenir.</span><span class="sxs-lookup"><span data-stu-id="21522-117">The format of the XML file is modeled after the standard application configuration file.</span></span> <span data-ttu-id="21522-118">XML dosyaları hakkında daha fazla bilgi için bkz. [yapılandırma dosya şeması](../../../../docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="21522-118">For more information about XML files, see [Configuration File Schema](../../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21522-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="21522-119">Requirements</span></span>  
 <span data-ttu-id="21522-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21522-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21522-121">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="21522-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="21522-122">**Kitaplık:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="21522-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="21522-123">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21522-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21522-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="21522-124">See also</span></span>

- [<span data-ttu-id="21522-125">CorBindToCurrentRuntime İşlevi</span><span class="sxs-lookup"><span data-stu-id="21522-125">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [<span data-ttu-id="21522-126">CorBindToRuntime İşlevi</span><span class="sxs-lookup"><span data-stu-id="21522-126">CorBindToRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)
- [<span data-ttu-id="21522-127">CorBindToRuntimeEx İşlevi</span><span class="sxs-lookup"><span data-stu-id="21522-127">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [<span data-ttu-id="21522-128">CorBindToRuntimeHost İşlevi</span><span class="sxs-lookup"><span data-stu-id="21522-128">CorBindToRuntimeHost Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)
- [<span data-ttu-id="21522-129">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="21522-129">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [<span data-ttu-id="21522-130">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="21522-130">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
