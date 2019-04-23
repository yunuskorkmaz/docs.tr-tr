---
title: CreateDebuggingInterfaceFromVersion İşlevi
ms.date: 03/30/2017
api_name:
- CreateDebuggingInterfaceFromVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- CreateDebuggingInterfaceFromVersion
helpviewer_keywords:
- CreateDebuggingInterfaceFromVersion function [.NET Framework hosting]
ms.assetid: a746a849-463c-44f5-a2f0-9e812ed8bcc3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 60d1c49e8762d00e3e154c598c2542c4a76b9b28
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59107503"
---
# <a name="createdebugginginterfacefromversion-function"></a><span data-ttu-id="7a88c-102">CreateDebuggingInterfaceFromVersion İşlevi</span><span class="sxs-lookup"><span data-stu-id="7a88c-102">CreateDebuggingInterfaceFromVersion Function</span></span>
<span data-ttu-id="7a88c-103">Oluşturur bir [Icordebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) nesne belirtilen sürüm bilgisi esas alarak.</span><span class="sxs-lookup"><span data-stu-id="7a88c-103">Creates an [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) object based on the specified version information.</span></span>  
  
 <span data-ttu-id="7a88c-104">Bu işlev kullanılmıyor [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7a88c-104">This function is obsolete in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="7a88c-105">Bunun yerine, Ortak Dil Çalışma Zamanı Modülü (CLR) 2.0 bir arabirimi almak için kullanın [Iclrruntimeınfo::getınterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) yöntemi CLSID_CLRDebuggingLegacy sınıf tanımlayıcısı ve arabirim tanımlayıcısı IID_ICorDebug belirtin.</span><span class="sxs-lookup"><span data-stu-id="7a88c-105">Instead, to get an interface for the common language runtime (CLR) 2.0, use the [ICLRRuntimeInfo::GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) method and specify the class identifier CLSID_CLRDebuggingLegacy and the interface identifier IID_ICorDebug.</span></span> <span data-ttu-id="7a88c-106">Bir arabirim için CLR 4 veya sonraki sürümlerde, çağrı [Clrcreateınstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) işlev ve sınıf tanımlayıcısı CLSID_CLRDebugging ve IID_ICLRDebugging arabirimi tanımlayıcısını belirtin.</span><span class="sxs-lookup"><span data-stu-id="7a88c-106">To get an interface for CLR 4 or later, call the [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) function and specify the class identifier CLSID_CLRDebugging and the interface identifier IID_ICLRDebugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a88c-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7a88c-107">Syntax</span></span>  
  
```  
HRESULT CreateDebuggingInterfaceFromVersion (  
    [in]  int      iDebuggerVersion,   
    [in]  LPCWSTR  szDebuggeeVersion,   
    [out] IUnknown **ppCordb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7a88c-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7a88c-108">Parameters</span></span>  
 `iDebuggerVersion`  
 <span data-ttu-id="7a88c-109">[in] Sürümü `ICorDebug` hata ayıklayıcı tarafından bekleniyor.</span><span class="sxs-lookup"><span data-stu-id="7a88c-109">[in] The version of `ICorDebug` that is expected by the debugger.</span></span> <span data-ttu-id="7a88c-110">Bkz: [Cordebugınterfaceversion](../../../../docs/framework/unmanaged-api/debugging/cordebuginterfaceversion-enumeration.md) numaralandırma değerleri için.</span><span class="sxs-lookup"><span data-stu-id="7a88c-110">See the [CorDebugInterfaceVersion](../../../../docs/framework/unmanaged-api/debugging/cordebuginterfaceversion-enumeration.md) enumeration for valid values.</span></span>  
  
 `szDebuggeeVersion`  
 <span data-ttu-id="7a88c-111">[in] Ayıklanacak uygulamayı veya işlemi ile ilişkili ortak dil çalışma zamanı sürümü.</span><span class="sxs-lookup"><span data-stu-id="7a88c-111">[in] The common language runtime version associated with the application or process to be debugged.</span></span> <span data-ttu-id="7a88c-112">Bkz: [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md) veya [GetRequestedRuntimeVersion](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md) bu değer alma hakkında bilgi için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="7a88c-112">See the [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md) or [GetRequestedRuntimeVersion](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md) method for information on retrieving this value.</span></span>  
  
 `ppCordb`  
 <span data-ttu-id="7a88c-113">[out] Bir işaretçiye alan konumu `ICorDebug` nesne.</span><span class="sxs-lookup"><span data-stu-id="7a88c-113">[out] The location that receives a pointer to the `ICorDebug` object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7a88c-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="7a88c-114">Return Value</span></span>  
 <span data-ttu-id="7a88c-115">Bu yöntem, aşağıdaki değerlere ek olarak Wınerror dosyasında tanımlanan standart COM hata kodlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="7a88c-115">This method returns standard COM error codes as defined in the WinError.h file in addition to the following values.</span></span>  
  
|<span data-ttu-id="7a88c-116">Dönüş kodu</span><span class="sxs-lookup"><span data-stu-id="7a88c-116">Return code</span></span>|<span data-ttu-id="7a88c-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7a88c-117">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="7a88c-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="7a88c-118">S_OK</span></span>|<span data-ttu-id="7a88c-119">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="7a88c-119">The method completed successfully.</span></span>|  
|<span data-ttu-id="7a88c-120">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="7a88c-120">E_INVALIDARG</span></span>|<span data-ttu-id="7a88c-121">`szDebuggeeVersion` veya `ppCordb` null ya da sürüm dizesi yanlış.</span><span class="sxs-lookup"><span data-stu-id="7a88c-121">`szDebuggeeVersion` or `ppCordb` is null, or the version string is incorrect.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7a88c-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7a88c-122">Remarks</span></span>  
 <span data-ttu-id="7a88c-123">`szDebuggeeVersion` Parametre MSCorDbi.dll ilgili sürümü için eşler.</span><span class="sxs-lookup"><span data-stu-id="7a88c-123">The `szDebuggeeVersion` parameter maps to the corresponding version of MSCorDbi.dll.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a88c-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7a88c-124">Requirements</span></span>  
 <span data-ttu-id="7a88c-125">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7a88c-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a88c-126">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7a88c-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7a88c-127">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7a88c-127">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7a88c-128">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7a88c-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a88c-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7a88c-129">See also</span></span>

- [<span data-ttu-id="7a88c-130">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="7a88c-130">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
