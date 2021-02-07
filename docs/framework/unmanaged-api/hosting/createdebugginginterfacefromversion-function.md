---
description: 'Daha fazla bilgi edinin: CreateDebuggingInterfaceFromVersion Işlevi'
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
ms.openlocfilehash: 163ada49f028071b48c93ee3c565152a773782ac
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760639"
---
# <a name="createdebugginginterfacefromversion-function"></a><span data-ttu-id="2bb4a-103">CreateDebuggingInterfaceFromVersion İşlevi</span><span class="sxs-lookup"><span data-stu-id="2bb4a-103">CreateDebuggingInterfaceFromVersion Function</span></span>

<span data-ttu-id="2bb4a-104">Belirtilen sürüm bilgilerini temel alan bir [ICorDebug](../debugging/icordebug-interface.md) nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2bb4a-104">Creates an [ICorDebug](../debugging/icordebug-interface.md) object based on the specified version information.</span></span>  
  
 <span data-ttu-id="2bb4a-105">Bu işlev .NET Framework 4 ' te kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="2bb4a-105">This function is obsolete in the .NET Framework 4.</span></span> <span data-ttu-id="2bb4a-106">Bunun yerine, ortak dil çalışma zamanı (CLR) 2,0 için bir arabirim almak üzere [ICLRRuntimeInfo:: GetInterface](iclrruntimeinfo-getinterface-method.md) yöntemini kullanın ve sınıf tanımlayıcısını CLSID_CLRDebuggingLegacy ve arabirim tanımlayıcısını IID_ICorDebug belirtin.</span><span class="sxs-lookup"><span data-stu-id="2bb4a-106">Instead, to get an interface for the common language runtime (CLR) 2.0, use the [ICLRRuntimeInfo::GetInterface](iclrruntimeinfo-getinterface-method.md) method and specify the class identifier CLSID_CLRDebuggingLegacy and the interface identifier IID_ICorDebug.</span></span> <span data-ttu-id="2bb4a-107">CLR 4 veya üzeri bir arabirim almak için, [CLRCreateInstance](clrcreateinstance-function.md) işlevini çağırın ve sınıf tanımlayıcısını CLSID_CLRDebugging ve arabirim tanımlayıcısı IID_ICLRDebugging belirtin.</span><span class="sxs-lookup"><span data-stu-id="2bb4a-107">To get an interface for CLR 4 or later, call the [CLRCreateInstance](clrcreateinstance-function.md) function and specify the class identifier CLSID_CLRDebugging and the interface identifier IID_ICLRDebugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2bb4a-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2bb4a-108">Syntax</span></span>  
  
```cpp  
HRESULT CreateDebuggingInterfaceFromVersion (  
    [in]  int      iDebuggerVersion,
    [in]  LPCWSTR  szDebuggeeVersion,
    [out] IUnknown **ppCordb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2bb4a-109">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2bb4a-109">Parameters</span></span>  

 `iDebuggerVersion`  
 <span data-ttu-id="2bb4a-110">'ndaki `ICorDebug` Hata ayıklayıcı tarafından beklenen sürümü.</span><span class="sxs-lookup"><span data-stu-id="2bb4a-110">[in] The version of `ICorDebug` that is expected by the debugger.</span></span> <span data-ttu-id="2bb4a-111">Geçerli değerler için [CorDebugInterfaceVersion](../debugging/cordebuginterfaceversion-enumeration.md) numaralandırması bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="2bb4a-111">See the [CorDebugInterfaceVersion](../debugging/cordebuginterfaceversion-enumeration.md) enumeration for valid values.</span></span>  
  
 `szDebuggeeVersion`  
 <span data-ttu-id="2bb4a-112">'ndaki Hata Ayıklanacak uygulamayla veya işlemle ilişkili ortak dil çalışma zamanı sürümü.</span><span class="sxs-lookup"><span data-stu-id="2bb4a-112">[in] The common language runtime version associated with the application or process to be debugged.</span></span> <span data-ttu-id="2bb4a-113">Bu değeri alma hakkında bilgi için bkz. [GetVersionFromProcess](getversionfromprocess-function.md) veya [GetRequestedRuntimeVersion](getrequestedruntimeversion-function.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="2bb4a-113">See the [GetVersionFromProcess](getversionfromprocess-function.md) or [GetRequestedRuntimeVersion](getrequestedruntimeversion-function.md) method for information on retrieving this value.</span></span>  
  
 `ppCordb`  
 <span data-ttu-id="2bb4a-114">dışı Nesneye bir işaretçi alan konum `ICorDebug` .</span><span class="sxs-lookup"><span data-stu-id="2bb4a-114">[out] The location that receives a pointer to the `ICorDebug` object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2bb4a-115">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="2bb4a-115">Return Value</span></span>  

 <span data-ttu-id="2bb4a-116">Bu yöntem, aşağıdaki değerlere ek olarak WinError. h dosyasında tanımlanan standart COM hata kodlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="2bb4a-116">This method returns standard COM error codes as defined in the WinError.h file in addition to the following values.</span></span>  
  
|<span data-ttu-id="2bb4a-117">Dönüş kodu</span><span class="sxs-lookup"><span data-stu-id="2bb4a-117">Return code</span></span>|<span data-ttu-id="2bb4a-118">Description</span><span class="sxs-lookup"><span data-stu-id="2bb4a-118">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="2bb4a-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="2bb4a-119">S_OK</span></span>|<span data-ttu-id="2bb4a-120">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="2bb4a-120">The method completed successfully.</span></span>|  
|<span data-ttu-id="2bb4a-121">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="2bb4a-121">E_INVALIDARG</span></span>|<span data-ttu-id="2bb4a-122">`szDebuggeeVersion` ya `ppCordb` da null ya da sürüm dizesi yanlış.</span><span class="sxs-lookup"><span data-stu-id="2bb4a-122">`szDebuggeeVersion` or `ppCordb` is null, or the version string is incorrect.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2bb4a-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2bb4a-123">Remarks</span></span>  

 <span data-ttu-id="2bb4a-124">`szDebuggeeVersion`Parametresi karşılık gelen MSCorDbi.dll sürümüne eşlenir.</span><span class="sxs-lookup"><span data-stu-id="2bb4a-124">The `szDebuggeeVersion` parameter maps to the corresponding version of MSCorDbi.dll.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2bb4a-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2bb4a-125">Requirements</span></span>  

 <span data-ttu-id="2bb4a-126">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2bb4a-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2bb4a-127">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="2bb4a-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2bb4a-128">**Kitaplık:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2bb4a-128">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2bb4a-129">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2bb4a-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2bb4a-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2bb4a-130">See also</span></span>

- [<span data-ttu-id="2bb4a-131">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="2bb4a-131">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
