---
title: "CreateDebuggingInterfaceFromVersion İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CreateDebuggingInterfaceFromVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type: DLLExport
f1_keywords: CreateDebuggingInterfaceFromVersion
helpviewer_keywords: CreateDebuggingInterfaceFromVersion function [.NET Framework hosting]
ms.assetid: a746a849-463c-44f5-a2f0-9e812ed8bcc3
topic_type: apiref
caps.latest.revision: "20"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b3f269f5b1758481995d6064e7137e62bff4a868
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="createdebugginginterfacefromversion-function"></a><span data-ttu-id="97e8a-102">CreateDebuggingInterfaceFromVersion İşlevi</span><span class="sxs-lookup"><span data-stu-id="97e8a-102">CreateDebuggingInterfaceFromVersion Function</span></span>
<span data-ttu-id="97e8a-103">Oluşturur bir [Icordebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) nesne tabanlı belirtilen sürüm bilgileri.</span><span class="sxs-lookup"><span data-stu-id="97e8a-103">Creates an [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) object based on the specified version information.</span></span>  
  
 <span data-ttu-id="97e8a-104">Bu işlev kullanılmıyor [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="97e8a-104">This function is obsolete in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="97e8a-105">Bunun yerine, Ortak Dil Çalışma Zamanı Modülü (CLR) 2.0 arabirim almak için kullanın [Iclrruntimeınfo::getınterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) yöntemi ve sınıf tanımlayıcısı CLSID_CLRDebuggingLegacy ve IID_ICorDebug arabirim tanımlayıcısını belirtin.</span><span class="sxs-lookup"><span data-stu-id="97e8a-105">Instead, to get an interface for the common language runtime (CLR) 2.0, use the [ICLRRuntimeInfo::GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) method and specify the class identifier CLSID_CLRDebuggingLegacy and the interface identifier IID_ICorDebug.</span></span> <span data-ttu-id="97e8a-106">Bir arabirim için CLR 4 elde etmek veya daha sonra arama için [Clrcreateınstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) işlev ve sınıf tanımlayıcısı CLSID_CLRDebugging ve IID_ICLRDebugging arabirim tanımlayıcısını belirtin.</span><span class="sxs-lookup"><span data-stu-id="97e8a-106">To get an interface for CLR 4 or later, call the [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) function and specify the class identifier CLSID_CLRDebugging and the interface identifier IID_ICLRDebugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97e8a-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="97e8a-107">Syntax</span></span>  
  
```  
HRESULT CreateDebuggingInterfaceFromVersion (  
    [in]  int      iDebuggerVersion,   
    [in]  LPCWSTR  szDebuggeeVersion,   
    [out] IUnknown **ppCordb  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="97e8a-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="97e8a-108">Parameters</span></span>  
 `iDebuggerVersion`  
 <span data-ttu-id="97e8a-109">[in] Sürümü `ICorDebug` hata ayıklayıcı tarafından beklenmektedir.</span><span class="sxs-lookup"><span data-stu-id="97e8a-109">[in] The version of `ICorDebug` that is expected by the debugger.</span></span> <span data-ttu-id="97e8a-110">Bkz: [Cordebugınterfaceversion](../../../../docs/framework/unmanaged-api/debugging/cordebuginterfaceversion-enumeration.md) numaralandırma için geçerli değerler.</span><span class="sxs-lookup"><span data-stu-id="97e8a-110">See the [CorDebugInterfaceVersion](../../../../docs/framework/unmanaged-api/debugging/cordebuginterfaceversion-enumeration.md) enumeration for valid values.</span></span>  
  
 `szDebuggeeVersion`  
 <span data-ttu-id="97e8a-111">[in] Ayıklanacak uygulamanın veya işlemin ilişkili ortak dil çalışma zamanı sürümü.</span><span class="sxs-lookup"><span data-stu-id="97e8a-111">[in] The common language runtime version associated with the application or process to be debugged.</span></span> <span data-ttu-id="97e8a-112">Bkz: [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md) veya [GetRequestedRuntimeVersion](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md) yöntemi bu değer alma hakkında bilgi için.</span><span class="sxs-lookup"><span data-stu-id="97e8a-112">See the [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md) or [GetRequestedRuntimeVersion](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md) method for information on retrieving this value.</span></span>  
  
 `ppCordb`  
 <span data-ttu-id="97e8a-113">[out] Bir işaretçi aldığı konumu `ICorDebug` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="97e8a-113">[out] The location that receives a pointer to the `ICorDebug` object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="97e8a-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="97e8a-114">Return Value</span></span>  
 <span data-ttu-id="97e8a-115">Bu yöntem, aşağıdaki değerleri yanı sıra Winerror.h'de dosyasında tanımlanan standart COM hata kodlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="97e8a-115">This method returns standard COM error codes as defined in the WinError.h file in addition to the following values.</span></span>  
  
|<span data-ttu-id="97e8a-116">Dönüş kodu</span><span class="sxs-lookup"><span data-stu-id="97e8a-116">Return code</span></span>|<span data-ttu-id="97e8a-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="97e8a-117">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="97e8a-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="97e8a-118">S_OK</span></span>|<span data-ttu-id="97e8a-119">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="97e8a-119">The method completed successfully.</span></span>|  
|<span data-ttu-id="97e8a-120">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="97e8a-120">E_INVALIDARG</span></span>|<span data-ttu-id="97e8a-121">`szDebuggeeVersion`veya `ppCordb` null ya da sürüm dizesi yanlış.</span><span class="sxs-lookup"><span data-stu-id="97e8a-121">`szDebuggeeVersion` or `ppCordb` is null, or the version string is incorrect.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="97e8a-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="97e8a-122">Remarks</span></span>  
 <span data-ttu-id="97e8a-123">`szDebuggeeVersion` Parametresi MSCorDbi.dll karşılık gelen sürüme eşler.</span><span class="sxs-lookup"><span data-stu-id="97e8a-123">The `szDebuggeeVersion` parameter maps to the corresponding version of MSCorDbi.dll.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="97e8a-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="97e8a-124">Requirements</span></span>  
 <span data-ttu-id="97e8a-125">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="97e8a-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="97e8a-126">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="97e8a-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="97e8a-127">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="97e8a-127">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="97e8a-128">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="97e8a-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97e8a-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="97e8a-129">See Also</span></span>  
 [<span data-ttu-id="97e8a-130">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="97e8a-130">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
