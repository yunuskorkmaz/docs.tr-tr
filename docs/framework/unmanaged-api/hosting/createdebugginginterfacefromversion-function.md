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
ms.openlocfilehash: 0e1395229b67c4054df62935375a4136edf63078
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616495"
---
# <a name="createdebugginginterfacefromversion-function"></a><span data-ttu-id="db3dc-102">CreateDebuggingInterfaceFromVersion İşlevi</span><span class="sxs-lookup"><span data-stu-id="db3dc-102">CreateDebuggingInterfaceFromVersion Function</span></span>
<span data-ttu-id="db3dc-103">Belirtilen sürüm bilgilerini temel alan bir [ICorDebug](../debugging/icordebug-interface.md) nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="db3dc-103">Creates an [ICorDebug](../debugging/icordebug-interface.md) object based on the specified version information.</span></span>  
  
 <span data-ttu-id="db3dc-104">Bu işlev .NET Framework 4 ' te kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="db3dc-104">This function is obsolete in the .NET Framework 4.</span></span> <span data-ttu-id="db3dc-105">Bunun yerine, ortak dil çalışma zamanı (CLR) 2,0 için bir arabirim almak üzere [ICLRRuntimeInfo:: GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) yöntemini kullanın ve sınıf tanımlayıcısını CLSID_CLRDebuggingLegacy ve arabirim tanımlayıcısını IID_ICorDebug belirtin.</span><span class="sxs-lookup"><span data-stu-id="db3dc-105">Instead, to get an interface for the common language runtime (CLR) 2.0, use the [ICLRRuntimeInfo::GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) method and specify the class identifier CLSID_CLRDebuggingLegacy and the interface identifier IID_ICorDebug.</span></span> <span data-ttu-id="db3dc-106">CLR 4 veya üzeri bir arabirim almak için, [CLRCreateInstance](clrcreateinstance-function.md) işlevini çağırın ve sınıf tanımlayıcısını CLSID_CLRDebugging ve arabirim tanımlayıcısı IID_ICLRDebugging belirtin.</span><span class="sxs-lookup"><span data-stu-id="db3dc-106">To get an interface for CLR 4 or later, call the [CLRCreateInstance](clrcreateinstance-function.md) function and specify the class identifier CLSID_CLRDebugging and the interface identifier IID_ICLRDebugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db3dc-107">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="db3dc-107">Syntax</span></span>  
  
```cpp  
HRESULT CreateDebuggingInterfaceFromVersion (  
    [in]  int      iDebuggerVersion,
    [in]  LPCWSTR  szDebuggeeVersion,
    [out] IUnknown **ppCordb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="db3dc-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="db3dc-108">Parameters</span></span>  
 `iDebuggerVersion`  
 <span data-ttu-id="db3dc-109">'ndaki `ICorDebug`Hata ayıklayıcı tarafından beklenen sürümü.</span><span class="sxs-lookup"><span data-stu-id="db3dc-109">[in] The version of `ICorDebug` that is expected by the debugger.</span></span> <span data-ttu-id="db3dc-110">Geçerli değerler için [CorDebugInterfaceVersion](../debugging/cordebuginterfaceversion-enumeration.md) numaralandırması bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="db3dc-110">See the [CorDebugInterfaceVersion](../debugging/cordebuginterfaceversion-enumeration.md) enumeration for valid values.</span></span>  
  
 `szDebuggeeVersion`  
 <span data-ttu-id="db3dc-111">'ndaki Hata Ayıklanacak uygulamayla veya işlemle ilişkili ortak dil çalışma zamanı sürümü.</span><span class="sxs-lookup"><span data-stu-id="db3dc-111">[in] The common language runtime version associated with the application or process to be debugged.</span></span> <span data-ttu-id="db3dc-112">Bu değeri alma hakkında bilgi için bkz. [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md) veya [GetRequestedRuntimeVersion](getrequestedruntimeversion-function.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="db3dc-112">See the [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md) or [GetRequestedRuntimeVersion](getrequestedruntimeversion-function.md) method for information on retrieving this value.</span></span>  
  
 `ppCordb`  
 <span data-ttu-id="db3dc-113">dışı Nesneye bir işaretçi alan konum `ICorDebug` .</span><span class="sxs-lookup"><span data-stu-id="db3dc-113">[out] The location that receives a pointer to the `ICorDebug` object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="db3dc-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="db3dc-114">Return Value</span></span>  
 <span data-ttu-id="db3dc-115">Bu yöntem, aşağıdaki değerlere ek olarak WinError. h dosyasında tanımlanan standart COM hata kodlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="db3dc-115">This method returns standard COM error codes as defined in the WinError.h file in addition to the following values.</span></span>  
  
|<span data-ttu-id="db3dc-116">Dönüş kodu</span><span class="sxs-lookup"><span data-stu-id="db3dc-116">Return code</span></span>|<span data-ttu-id="db3dc-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="db3dc-117">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="db3dc-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="db3dc-118">S_OK</span></span>|<span data-ttu-id="db3dc-119">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="db3dc-119">The method completed successfully.</span></span>|  
|<span data-ttu-id="db3dc-120">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="db3dc-120">E_INVALIDARG</span></span>|<span data-ttu-id="db3dc-121">`szDebuggeeVersion`ya `ppCordb` da null ya da sürüm dizesi yanlış.</span><span class="sxs-lookup"><span data-stu-id="db3dc-121">`szDebuggeeVersion` or `ppCordb` is null, or the version string is incorrect.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="db3dc-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="db3dc-122">Remarks</span></span>  
 <span data-ttu-id="db3dc-123">`szDebuggeeVersion`Parametresi, MSCorDbi. dll ' nin ilgili sürümüyle eşlenir.</span><span class="sxs-lookup"><span data-stu-id="db3dc-123">The `szDebuggeeVersion` parameter maps to the corresponding version of MSCorDbi.dll.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="db3dc-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="db3dc-124">Requirements</span></span>  
 <span data-ttu-id="db3dc-125">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="db3dc-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db3dc-126">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="db3dc-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="db3dc-127">**Kitaplık:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="db3dc-127">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="db3dc-128">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db3dc-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db3dc-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="db3dc-129">See also</span></span>

- [<span data-ttu-id="db3dc-130">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="db3dc-130">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
