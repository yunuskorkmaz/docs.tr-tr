---
title: "GetPropertyOrigin işlevi (Unmnaged API Başvurusu)"
description: "GetPropertyOrigin işlevi bir özellik bildirilmedi sınıfı belirler."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: GetPropertyOrigin
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: GetPropertyOrigin
helpviewer_keywords: GetPropertyOrigin function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 68df29e88b41cb12d002913d5bbd42050395d871
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/15/2017
---
# <a name="getpropertyorigin-function"></a><span data-ttu-id="6c145-103">GetPropertyOrigin işlevi</span><span class="sxs-lookup"><span data-stu-id="6c145-103">GetPropertyOrigin function</span></span>
<span data-ttu-id="6c145-104">Bir özellik bildirilmedi sınıfı belirler.</span><span class="sxs-lookup"><span data-stu-id="6c145-104">Determines the class in which a property is declared.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="6c145-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6c145-105">Syntax</span></span>  
  
```  
HRESULT GetPropertyOrigin (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LPCWSTR             wszMethodName,
   [out] BSTR*              pstrClassName
); 
```  

## <a name="parameters"></a><span data-ttu-id="6c145-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6c145-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="6c145-107">[in] Bu parametre kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="6c145-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="6c145-108">[in] Bir işaretçi bir [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) örneği.</span><span class="sxs-lookup"><span data-stu-id="6c145-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`wszMethodName`  
<span data-ttu-id="6c145-109">[in] Özellik adı, sahibi olan sınıf istenen nesne için.</span><span class="sxs-lookup"><span data-stu-id="6c145-109">[in] The name of the property for the object whose owning class is being requested.</span></span> 

`pstrClassName`  
<span data-ttu-id="6c145-110">[out] Özellik sahibi sınıfın adını alır.</span><span class="sxs-lookup"><span data-stu-id="6c145-110">[out] Receives the name of the class that owns the property.</span></span>

## <a name="return-value"></a><span data-ttu-id="6c145-111">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="6c145-111">Return value</span></span>

<span data-ttu-id="6c145-112">Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üstbilgi dosyası, veya tanımlayabilirsiniz bunları sabitleri kodunuzda:</span><span class="sxs-lookup"><span data-stu-id="6c145-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="6c145-113">Sabit</span><span class="sxs-lookup"><span data-stu-id="6c145-113">Constant</span></span>  |<span data-ttu-id="6c145-114">Değer</span><span class="sxs-lookup"><span data-stu-id="6c145-114">Value</span></span>  |<span data-ttu-id="6c145-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6c145-115">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="6c145-116">0x80041001</span><span class="sxs-lookup"><span data-stu-id="6c145-116">0x80041001</span></span> | <span data-ttu-id="6c145-117">Genel bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="6c145-117">There has been a general failure.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="6c145-118">0x80041002</span><span class="sxs-lookup"><span data-stu-id="6c145-118">0x80041002</span></span> | <span data-ttu-id="6c145-119">Belirtilen özellik bulunamadı.</span><span class="sxs-lookup"><span data-stu-id="6c145-119">The specified property was not found.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="6c145-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="6c145-120">0x80041008</span></span> | <span data-ttu-id="6c145-121">Parametre geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="6c145-121">A parameter is not valid.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="6c145-122">0x80041006</span><span class="sxs-lookup"><span data-stu-id="6c145-122">0x80041006</span></span> | <span data-ttu-id="6c145-123">İşlemi tamamlamak yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="6c145-123">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="6c145-124">0</span><span class="sxs-lookup"><span data-stu-id="6c145-124">0</span></span> | <span data-ttu-id="6c145-125">İşlev çağrısı başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="6c145-125">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="6c145-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6c145-126">Remarks</span></span>

<span data-ttu-id="6c145-127">Bu işlev çağrısı sarmalar [IWbemClassObject::GetPropertyOrigin](https://msdn.microsoft.com/library/aa391449(v=vs.85).aspx) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="6c145-127">This function wraps a call to the [IWbemClassObject::GetPropertyOrigin](https://msdn.microsoft.com/library/aa391449(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="6c145-128">Bir sınıf bir veya daha fazla temel sınıflardan özellikleri devrettiği için geliştiriciler genellikle belirli bir yöntemin tanımlandığı özellik belirlemek istersiniz.</span><span class="sxs-lookup"><span data-stu-id="6c145-128">Because a class can inherit properties from one or more base classes, developers often want to determine the property in which a given method is defined.</span></span>

<span data-ttu-id="6c145-129">`pstrClassName` Parametre gerekir göstermiyor geçerli bir `BSTR` bu olduğundan işlevi çağrılmadan önce bir `out` parametresi; bu işaretçisi değil serbest işlevi döndükten sonra.</span><span class="sxs-lookup"><span data-stu-id="6c145-129">The `pstrClassName` parameter must not point to a valid `BSTR` before the function is called because this is an `out` parameter; this pointer is not deallocated after the function returns.</span></span>

## <a name="requirements"></a><span data-ttu-id="6c145-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6c145-130">Requirements</span></span>  
<span data-ttu-id="6c145-131">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c145-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c145-132">**Başlık:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="6c145-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="6c145-133">**.NET framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="6c145-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c145-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6c145-134">See also</span></span>  
[<span data-ttu-id="6c145-135">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="6c145-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
