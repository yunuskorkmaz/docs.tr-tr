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
ms.workload: dotnet
ms.openlocfilehash: 0a79bfc62ad776cb2bfab2c143d19761d64358bf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="getpropertyorigin-function"></a><span data-ttu-id="f67a8-103">GetPropertyOrigin işlevi</span><span class="sxs-lookup"><span data-stu-id="f67a8-103">GetPropertyOrigin function</span></span>
<span data-ttu-id="f67a8-104">Bir özellik bildirilmedi sınıfı belirler.</span><span class="sxs-lookup"><span data-stu-id="f67a8-104">Determines the class in which a property is declared.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="f67a8-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f67a8-105">Syntax</span></span>  
  
```  
HRESULT GetPropertyOrigin (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LPCWSTR             wszMethodName,
   [out] BSTR*              pstrClassName
); 
```  

## <a name="parameters"></a><span data-ttu-id="f67a8-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f67a8-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="f67a8-107">[in] Bu parametre kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="f67a8-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="f67a8-108">[in] Bir işaretçi bir [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) örneği.</span><span class="sxs-lookup"><span data-stu-id="f67a8-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`wszMethodName`  
<span data-ttu-id="f67a8-109">[in] Özellik adı, sahibi olan sınıf istenen nesne için.</span><span class="sxs-lookup"><span data-stu-id="f67a8-109">[in] The name of the property for the object whose owning class is being requested.</span></span> 

`pstrClassName`  
<span data-ttu-id="f67a8-110">[out] Özellik sahibi sınıfın adını alır.</span><span class="sxs-lookup"><span data-stu-id="f67a8-110">[out] Receives the name of the class that owns the property.</span></span>

## <a name="return-value"></a><span data-ttu-id="f67a8-111">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="f67a8-111">Return value</span></span>

<span data-ttu-id="f67a8-112">Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üstbilgi dosyası, veya tanımlayabilirsiniz bunları sabitleri kodunuzda:</span><span class="sxs-lookup"><span data-stu-id="f67a8-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="f67a8-113">Sabit</span><span class="sxs-lookup"><span data-stu-id="f67a8-113">Constant</span></span>  |<span data-ttu-id="f67a8-114">Değer</span><span class="sxs-lookup"><span data-stu-id="f67a8-114">Value</span></span>  |<span data-ttu-id="f67a8-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f67a8-115">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="f67a8-116">0x80041001</span><span class="sxs-lookup"><span data-stu-id="f67a8-116">0x80041001</span></span> | <span data-ttu-id="f67a8-117">Genel bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="f67a8-117">There has been a general failure.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="f67a8-118">0x80041002</span><span class="sxs-lookup"><span data-stu-id="f67a8-118">0x80041002</span></span> | <span data-ttu-id="f67a8-119">Belirtilen özellik bulunamadı.</span><span class="sxs-lookup"><span data-stu-id="f67a8-119">The specified property was not found.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="f67a8-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="f67a8-120">0x80041008</span></span> | <span data-ttu-id="f67a8-121">Parametre geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="f67a8-121">A parameter is not valid.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="f67a8-122">0x80041006</span><span class="sxs-lookup"><span data-stu-id="f67a8-122">0x80041006</span></span> | <span data-ttu-id="f67a8-123">İşlemi tamamlamak yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="f67a8-123">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="f67a8-124">0</span><span class="sxs-lookup"><span data-stu-id="f67a8-124">0</span></span> | <span data-ttu-id="f67a8-125">İşlev çağrısı başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="f67a8-125">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="f67a8-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f67a8-126">Remarks</span></span>

<span data-ttu-id="f67a8-127">Bu işlev çağrısı sarmalar [IWbemClassObject::GetPropertyOrigin](https://msdn.microsoft.com/library/aa391449(v=vs.85).aspx) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f67a8-127">This function wraps a call to the [IWbemClassObject::GetPropertyOrigin](https://msdn.microsoft.com/library/aa391449(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="f67a8-128">Bir sınıf bir veya daha fazla temel sınıflardan özellikleri devrettiği için geliştiriciler genellikle belirli bir yöntemin tanımlandığı özellik belirlemek istersiniz.</span><span class="sxs-lookup"><span data-stu-id="f67a8-128">Because a class can inherit properties from one or more base classes, developers often want to determine the property in which a given method is defined.</span></span>

<span data-ttu-id="f67a8-129">`pstrClassName` Parametre gerekir göstermiyor geçerli bir `BSTR` bu olduğundan işlevi çağrılmadan önce bir `out` parametresi; bu işaretçisi değil serbest işlevi döndükten sonra.</span><span class="sxs-lookup"><span data-stu-id="f67a8-129">The `pstrClassName` parameter must not point to a valid `BSTR` before the function is called because this is an `out` parameter; this pointer is not deallocated after the function returns.</span></span>

## <a name="requirements"></a><span data-ttu-id="f67a8-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f67a8-130">Requirements</span></span>  
<span data-ttu-id="f67a8-131">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f67a8-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f67a8-132">**Başlık:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="f67a8-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="f67a8-133">**.NET framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="f67a8-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f67a8-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f67a8-134">See also</span></span>  
[<span data-ttu-id="f67a8-135">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="f67a8-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
