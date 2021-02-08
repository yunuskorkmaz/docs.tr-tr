---
description: 'Daha fazla bilgi edinin: CorBindToRuntimeByCfg Işlevi'
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
ms.openlocfilehash: c1acf6a8f1d8637bc2d6cd180016ff51cf500107
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790080"
---
# <a name="corbindtoruntimebycfg-function"></a><span data-ttu-id="70b71-103">CorBindToRuntimeByCfg İşlevi</span><span class="sxs-lookup"><span data-stu-id="70b71-103">CorBindToRuntimeByCfg Function</span></span>

<span data-ttu-id="70b71-104">Bir XML dosyasından okunan sürüm bilgilerini kullanarak ortak dil çalışma zamanını (CLR) bir işleme yükler.</span><span class="sxs-lookup"><span data-stu-id="70b71-104">Loads the common language runtime (CLR) into a process by using version information that is read from an XML file.</span></span>  
  
 <span data-ttu-id="70b71-105">Bu işlev .NET Framework 4 ' te kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="70b71-105">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70b71-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="70b71-106">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="70b71-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="70b71-107">Parameters</span></span>  

 `pCfgStream`  
 <span data-ttu-id="70b71-108">'ndaki `IStream` XML dosyasını okuyan bir nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="70b71-108">[in] A pointer to an `IStream` object that reads the XML file.</span></span>  
  
 `reserved`  
 <span data-ttu-id="70b71-109">'ndaki Gelecekte kullanılmak üzere ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="70b71-109">[in] Reserved for future use.</span></span> <span data-ttu-id="70b71-110">Değer olarak 0 (sıfır) kullanın.</span><span class="sxs-lookup"><span data-stu-id="70b71-110">Use 0 (zero) as value.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="70b71-111">'ndaki CLR 'nin başlangıç davranışını belirten [startup_flags](startup-flags-enumeration.md) numaralandırması değeri.</span><span class="sxs-lookup"><span data-stu-id="70b71-111">[in] A value of the [STARTUP_FLAGS](startup-flags-enumeration.md) enumeration that specifies the startup behavior of the CLR.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="70b71-112">'ndaki `CLSID` [ICorRuntimeHost](icorruntimehost-interface.md) veya [ICLRRuntimeHost](iclrruntimehost-interface.md) arabirimini uygulayan coclass.</span><span class="sxs-lookup"><span data-stu-id="70b71-112">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](icorruntimehost-interface.md) or the [ICLRRuntimeHost](iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="70b71-113">Desteklenen değerler CLSID_CorRuntimeHost veya CLSID_CLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="70b71-113">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="70b71-114">'ndaki `IID` `ICorRuntimeHost` Ya da `ICLRRuntimeHost` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="70b71-114">[in] The `IID` of either the `ICorRuntimeHost` or the `ICLRRuntimeHost` interface.</span></span> <span data-ttu-id="70b71-115">Desteklenen değerler IID_ICorRuntimeHost veya IID_ICLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="70b71-115">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="70b71-116">dışı Döndürülen arabirimin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="70b71-116">[out] A pointer to the address of the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="70b71-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="70b71-117">Remarks</span></span>  

 <span data-ttu-id="70b71-118">XML dosyasının biçimi, standart uygulama yapılandırma dosyasından sonra modellenir.</span><span class="sxs-lookup"><span data-stu-id="70b71-118">The format of the XML file is modeled after the standard application configuration file.</span></span> <span data-ttu-id="70b71-119">XML dosyaları hakkında daha fazla bilgi için bkz. [yapılandırma dosya şeması](../../configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="70b71-119">For more information about XML files, see [Configuration File Schema](../../configure-apps/file-schema/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="70b71-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="70b71-120">Requirements</span></span>  

 <span data-ttu-id="70b71-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="70b71-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70b71-122">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="70b71-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="70b71-123">**Kitaplık:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="70b71-123">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="70b71-124">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="70b71-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70b71-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="70b71-125">See also</span></span>

- [<span data-ttu-id="70b71-126">CorBindToCurrentRuntime İşlevi</span><span class="sxs-lookup"><span data-stu-id="70b71-126">CorBindToCurrentRuntime Function</span></span>](corbindtocurrentruntime-function.md)
- [<span data-ttu-id="70b71-127">CorBindToRuntime İşlevi</span><span class="sxs-lookup"><span data-stu-id="70b71-127">CorBindToRuntime Function</span></span>](corbindtoruntime-function.md)
- [<span data-ttu-id="70b71-128">CorBindToRuntimeEx İşlevi</span><span class="sxs-lookup"><span data-stu-id="70b71-128">CorBindToRuntimeEx Function</span></span>](corbindtoruntimeex-function.md)
- [<span data-ttu-id="70b71-129">CorBindToRuntimeHost İşlevi</span><span class="sxs-lookup"><span data-stu-id="70b71-129">CorBindToRuntimeHost Function</span></span>](corbindtoruntimehost-function.md)
- [<span data-ttu-id="70b71-130">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="70b71-130">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
- [<span data-ttu-id="70b71-131">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="70b71-131">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
