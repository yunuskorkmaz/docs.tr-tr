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
ms.openlocfilehash: adc8ea16f0ab2bf383f8a63c49ba7d61c6bac113
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176454"
---
# <a name="createdebugginginterfacefromversion-function"></a><span data-ttu-id="e2564-102">CreateDebuggingInterfaceFromVersion İşlevi</span><span class="sxs-lookup"><span data-stu-id="e2564-102">CreateDebuggingInterfaceFromVersion Function</span></span>
<span data-ttu-id="e2564-103">Belirtilen sürüm bilgilerini temel alan bir [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e2564-103">Creates an [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) object based on the specified version information.</span></span>  
  
 <span data-ttu-id="e2564-104">Bu işlev .NET Framework 4'te geçersizdir.</span><span class="sxs-lookup"><span data-stu-id="e2564-104">This function is obsolete in the .NET Framework 4.</span></span> <span data-ttu-id="e2564-105">Bunun yerine, ortak dil çalışma süresi (CLR) 2.0 için bir arayüz elde etmek [için, ICLRRuntimeInfo kullanın::GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) yöntemi ve sınıf tanımlayıcıCLSID_CLRDebuggingLegacy ve arayüz tanımlayıcıIID_ICorDebug belirtin.</span><span class="sxs-lookup"><span data-stu-id="e2564-105">Instead, to get an interface for the common language runtime (CLR) 2.0, use the [ICLRRuntimeInfo::GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) method and specify the class identifier CLSID_CLRDebuggingLegacy and the interface identifier IID_ICorDebug.</span></span> <span data-ttu-id="e2564-106">CLR 4 veya sonraki bir arabirim almak için [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) işlevini arayın ve sınıf tanımlayıcısını CLSID_CLRDebugging ve arayüz tanımlayıcısını IID_ICLRDebugging belirtin.</span><span class="sxs-lookup"><span data-stu-id="e2564-106">To get an interface for CLR 4 or later, call the [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) function and specify the class identifier CLSID_CLRDebugging and the interface identifier IID_ICLRDebugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2564-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e2564-107">Syntax</span></span>  
  
```cpp  
HRESULT CreateDebuggingInterfaceFromVersion (  
    [in]  int      iDebuggerVersion,
    [in]  LPCWSTR  szDebuggeeVersion,
    [out] IUnknown **ppCordb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e2564-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e2564-108">Parameters</span></span>  
 `iDebuggerVersion`  
 <span data-ttu-id="e2564-109">[içinde] Bunun sürümü `ICorDebug` hata ayıklayıcı tarafından bekleniyor.</span><span class="sxs-lookup"><span data-stu-id="e2564-109">[in] The version of `ICorDebug` that is expected by the debugger.</span></span> <span data-ttu-id="e2564-110">Geçerli değerler için [CorDebugInterfaceVersion](../../../../docs/framework/unmanaged-api/debugging/cordebuginterfaceversion-enumeration.md) numaralandırmabölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="e2564-110">See the [CorDebugInterfaceVersion](../../../../docs/framework/unmanaged-api/debugging/cordebuginterfaceversion-enumeration.md) enumeration for valid values.</span></span>  
  
 `szDebuggeeVersion`  
 <span data-ttu-id="e2564-111">[içinde] Hata ayıklanacak uygulama veya işlemle ilişkili ortak dil çalışma zamanı sürümü.</span><span class="sxs-lookup"><span data-stu-id="e2564-111">[in] The common language runtime version associated with the application or process to be debugged.</span></span> <span data-ttu-id="e2564-112">Bu değeri alma hakkında bilgi almak için [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md) veya [GetRequestedRuntimeVersion](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md) yöntemine bakın.</span><span class="sxs-lookup"><span data-stu-id="e2564-112">See the [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md) or [GetRequestedRuntimeVersion](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md) method for information on retrieving this value.</span></span>  
  
 `ppCordb`  
 <span data-ttu-id="e2564-113">[çıkış] `ICorDebug` Nesneye işaretçi alan konum.</span><span class="sxs-lookup"><span data-stu-id="e2564-113">[out] The location that receives a pointer to the `ICorDebug` object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e2564-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e2564-114">Return Value</span></span>  
 <span data-ttu-id="e2564-115">Bu yöntem, aşağıdaki değerlere ek olarak WinError.h dosyasında tanımlandığı gibi standart COM hata kodlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="e2564-115">This method returns standard COM error codes as defined in the WinError.h file in addition to the following values.</span></span>  
  
|<span data-ttu-id="e2564-116">Dönüş kodu</span><span class="sxs-lookup"><span data-stu-id="e2564-116">Return code</span></span>|<span data-ttu-id="e2564-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e2564-117">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="e2564-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="e2564-118">S_OK</span></span>|<span data-ttu-id="e2564-119">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="e2564-119">The method completed successfully.</span></span>|  
|<span data-ttu-id="e2564-120">E_ınvalıdarg</span><span class="sxs-lookup"><span data-stu-id="e2564-120">E_INVALIDARG</span></span>|<span data-ttu-id="e2564-121">`szDebuggeeVersion`veya `ppCordb` null veya sürüm dizesi yanlıştır.</span><span class="sxs-lookup"><span data-stu-id="e2564-121">`szDebuggeeVersion` or `ppCordb` is null, or the version string is incorrect.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e2564-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e2564-122">Remarks</span></span>  
 <span data-ttu-id="e2564-123">`szDebuggeeVersion` Parametre, MSCorDbi.dll'nin ilgili sürümüyle eşler.</span><span class="sxs-lookup"><span data-stu-id="e2564-123">The `szDebuggeeVersion` parameter maps to the corresponding version of MSCorDbi.dll.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e2564-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e2564-124">Requirements</span></span>  
 <span data-ttu-id="e2564-125">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e2564-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e2564-126">**Üstbilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e2564-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e2564-127">**Kütüphane:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="e2564-127">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e2564-128">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e2564-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2564-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e2564-129">See also</span></span>

- [<span data-ttu-id="e2564-130">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="e2564-130">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
