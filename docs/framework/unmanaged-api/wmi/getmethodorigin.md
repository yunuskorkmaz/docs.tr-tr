---
title: "GetMethodOrigin işlevi (yönetilmeyen API Başvurusu)"
description: "GetMethodOrigin işlevi bir yöntem olarak bildirilen sınıfı belirler."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: GetMethodOrigin
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: GetMethodOrigin
helpviewer_keywords: GetMethodOrigin function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7982ef2f272173e89434b64a4c296a2ce963594e
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/15/2017
---
# <a name="getmethodorigin-function"></a><span data-ttu-id="e5a72-103">GetMethodOrigin işlevi</span><span class="sxs-lookup"><span data-stu-id="e5a72-103">GetMethodOrigin function</span></span>
<span data-ttu-id="e5a72-104">Bir yöntem olarak bildirilen sınıfı belirler.</span><span class="sxs-lookup"><span data-stu-id="e5a72-104">Determines the class in which a method is declared.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="e5a72-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e5a72-105">Syntax</span></span>  
  
```  
HRESULT GetMethodOrigin (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LPCWSTR             wszMethodName,
   [out] BSTR*              pstrClassName
); 
```  

## <a name="parameters"></a><span data-ttu-id="e5a72-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e5a72-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="e5a72-107">[in] Bu parametre kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="e5a72-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="e5a72-108">[in] Bir işaretçi bir [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) örneği.</span><span class="sxs-lookup"><span data-stu-id="e5a72-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`wszMethodName`  
<span data-ttu-id="e5a72-109">[in] Sahibi olan sınıf istenen nesne için yöntemin adı.</span><span class="sxs-lookup"><span data-stu-id="e5a72-109">[in] The name of the method for the object whose owning class is being requested.</span></span> 

`pstrClassName`  
<span data-ttu-id="e5a72-110">[out] Yöntem sahip olduğu sınıfın adını alır.</span><span class="sxs-lookup"><span data-stu-id="e5a72-110">[out] Receives the name of the class that owns the method.</span></span>

## <a name="return-value"></a><span data-ttu-id="e5a72-111">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="e5a72-111">Return value</span></span>

<span data-ttu-id="e5a72-112">Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üstbilgi dosyası, veya tanımlayabilirsiniz bunları sabitleri kodunuzda:</span><span class="sxs-lookup"><span data-stu-id="e5a72-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="e5a72-113">Sabit</span><span class="sxs-lookup"><span data-stu-id="e5a72-113">Constant</span></span>  |<span data-ttu-id="e5a72-114">Değer</span><span class="sxs-lookup"><span data-stu-id="e5a72-114">Value</span></span>  |<span data-ttu-id="e5a72-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e5a72-115">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="e5a72-116">0x80041002</span><span class="sxs-lookup"><span data-stu-id="e5a72-116">0x80041002</span></span> | <span data-ttu-id="e5a72-117">Belirtilen yöntem bulunamadı.</span><span class="sxs-lookup"><span data-stu-id="e5a72-117">The specified method was not found.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="e5a72-118">0x80041008</span><span class="sxs-lookup"><span data-stu-id="e5a72-118">0x80041008</span></span> | <span data-ttu-id="e5a72-119">Bir veya daha fazla parametre geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="e5a72-119">One or more parameters are not valid.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="e5a72-120">0</span><span class="sxs-lookup"><span data-stu-id="e5a72-120">0</span></span> | <span data-ttu-id="e5a72-121">İşlev çağrısı başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="e5a72-121">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="e5a72-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e5a72-122">Remarks</span></span>

<span data-ttu-id="e5a72-123">Bu işlev çağrısı sarmalar [IWbemClassObject::GetMethodOrigin](https://msdn.microsoft.com/library/aa391443(v=vs.85).aspx) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e5a72-123">This function wraps a call to the [IWbemClassObject::GetMethodOrigin](https://msdn.microsoft.com/library/aa391443(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="e5a72-124">Bir sınıf bir veya daha fazla temel sınıflardan yöntemleri devrettiği için geliştiriciler genellikle belirli bir yöntemin tanımlandığı sınıfı belirlemek istiyorsanız.</span><span class="sxs-lookup"><span data-stu-id="e5a72-124">Because a class can inherit methods from one or more base classes, developers often want to determine the class in which a given method is defined.</span></span>

<span data-ttu-id="e5a72-125">`pstrClassName` Parametre gerekir göstermiyor geçerli bir `BSTR` bu olduğundan işlevi çağrılmadan önce bir `out` parametresi; bu işaretçisi değil serbest işlevi döndükten sonra.</span><span class="sxs-lookup"><span data-stu-id="e5a72-125">The `pstrClassName` parameter must not point to a valid `BSTR` before the function is called because this is an `out` parameter; this pointer is not deallocated after the function returns.</span></span>

## <a name="requirements"></a><span data-ttu-id="e5a72-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e5a72-126">Requirements</span></span>  
<span data-ttu-id="e5a72-127">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e5a72-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5a72-128">**Başlık:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="e5a72-128">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="e5a72-129">**.NET framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="e5a72-129">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5a72-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e5a72-130">See also</span></span>  
[<span data-ttu-id="e5a72-131">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="e5a72-131">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
