---
title: "Get işlevi (yönetilmeyen API Başvurusu)"
description: "Get işlevi, belirtilen özellik değerini alır."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: Get
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: Get
helpviewer_keywords: Get function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 75329ee4ee925f4eb74d96d8ce7ef3145eb4a966
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/15/2017
---
# <a name="get-function"></a><span data-ttu-id="1e855-103">Get işlevi</span><span class="sxs-lookup"><span data-stu-id="1e855-103">Get function</span></span>
<span data-ttu-id="1e855-104">Varsa belirtilen özellik değerini alır.</span><span class="sxs-lookup"><span data-stu-id="1e855-104">Retrieves the specified property value if it exists.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="1e855-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1e855-105">Syntax</span></span>  
  
```  
HRESULT Get (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszName,
   [in] LONG              lFlags,
   [out] VARIANT*         pVal,
   [out] CIMTYPE*         pvtType,
   [out] LONG*            plFlavor
); 
```  

## <a name="parameters"></a><span data-ttu-id="1e855-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1e855-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="1e855-107">[in] Bu parametre kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="1e855-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="1e855-108">[in] Bir işaretçi bir [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) örneği.</span><span class="sxs-lookup"><span data-stu-id="1e855-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`wszName`  
<span data-ttu-id="1e855-109">[in] Özelliğin adı.</span><span class="sxs-lookup"><span data-stu-id="1e855-109">[in] The name of the property.</span></span>

<span data-ttu-id="1e855-110">`lFlags`[in] Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="1e855-110">`lFlags` [in] Reserved.</span></span> <span data-ttu-id="1e855-111">Bu parametre 0 olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1e855-111">This parameter must be 0.</span></span>

<span data-ttu-id="1e855-112">`pVal`[out] İşlev başarıyla döndürürse, değerini içeren `wszName` özelliği.</span><span class="sxs-lookup"><span data-stu-id="1e855-112">`pVal` [out] If the function returns successfully, contains the value of the `wszName` property.</span></span> <span data-ttu-id="1e855-113">`pval` Bağımsız değişkeni doğru türü ve değerine Niteleyici için atanır.</span><span class="sxs-lookup"><span data-stu-id="1e855-113">The `pval` argument is assigned the correct type and value for the qualifier.</span></span>

<span data-ttu-id="1e855-114">`pvtType`[out] İşlev başarıyla döndürürse, içeren bir [CIM türü sabiti](https://msdn.microsoft.com/library/aa386309(v=vs.85).aspx) özellik türü gösterir.</span><span class="sxs-lookup"><span data-stu-id="1e855-114">`pvtType` [out] If the function returns successfully, contains a [CIM-type constant](https://msdn.microsoft.com/library/aa386309(v=vs.85).aspx) that indicates the property type.</span></span> <span data-ttu-id="1e855-115">Değerini de olabilir `null`.</span><span class="sxs-lookup"><span data-stu-id="1e855-115">Its value can also be `null`.</span></span> 

<span data-ttu-id="1e855-116">`plFlavor`[out] İşlev başarıyla döndürürse, özelliğin kaynak hakkında bilgi alır.</span><span class="sxs-lookup"><span data-stu-id="1e855-116">`plFlavor` [out] If the function returns successfully, receives information about the origin of the property.</span></span> <span data-ttu-id="1e855-117">Değerini olabilir `null`, veya tanımlanan WBEM_FLAVOR_TYPE sabitlerden biri *WbemCli.h* üstbilgi dosyası:</span><span class="sxs-lookup"><span data-stu-id="1e855-117">Its value can be `null`, or one of the following WBEM_FLAVOR_TYPE constants defined in the *WbemCli.h* header file:</span></span> 

|<span data-ttu-id="1e855-118">Sabit</span><span class="sxs-lookup"><span data-stu-id="1e855-118">Constant</span></span>  |<span data-ttu-id="1e855-119">Değer</span><span class="sxs-lookup"><span data-stu-id="1e855-119">Value</span></span>  |<span data-ttu-id="1e855-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1e855-120">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAVOR_ORIGIN_SYSTEM` | <span data-ttu-id="1e855-121">0x40</span><span class="sxs-lookup"><span data-stu-id="1e855-121">0x40</span></span> | <span data-ttu-id="1e855-122">Özelliği bir standart sistemi özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="1e855-122">The property is a standard system property.</span></span> |
| `WBEM_FLAVOR_ORIGIN_PROPAGATED` | <span data-ttu-id="1e855-123">0x20</span><span class="sxs-lookup"><span data-stu-id="1e855-123">0x20</span></span> | <span data-ttu-id="1e855-124">Bir sınıf için: özellik üst sınıftan devralındı.</span><span class="sxs-lookup"><span data-stu-id="1e855-124">For a class: The property is inherited from the parent class.</span></span> </br> <span data-ttu-id="1e855-125">Bir örneği için: özellik üst sınıftan devralındı ederken örneği tarafından değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="1e855-125">For an instance: The property, while inherited from the parent class, has not been modified by the instance.</span></span>  |
| `WBEM_FLAVOR_ORIGIN_LOCAL` | <span data-ttu-id="1e855-126">0</span><span class="sxs-lookup"><span data-stu-id="1e855-126">0</span></span> | <span data-ttu-id="1e855-127">Bir sınıf için: türetilmiş sınıf özellik ait.</span><span class="sxs-lookup"><span data-stu-id="1e855-127">For a class: The property belongs to the derived class.</span></span> </br> <span data-ttu-id="1e855-128">Bir örneği için: özelliğini örneği tarafından; değiştirdi diğer bir deyişle, bir değer sağlandı veya bir niteleyicisi eklenemez veya değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="1e855-128">For an instance: The property is modified by the instance; that is, a value was supplied, or a qualifier was added or modified.</span></span> |

## <a name="return-value"></a><span data-ttu-id="1e855-129">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="1e855-129">Return value</span></span>

<span data-ttu-id="1e855-130">Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üstbilgi dosyası, veya tanımlayabilirsiniz bunları sabitleri kodunuzda:</span><span class="sxs-lookup"><span data-stu-id="1e855-130">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="1e855-131">Sabit</span><span class="sxs-lookup"><span data-stu-id="1e855-131">Constant</span></span>  |<span data-ttu-id="1e855-132">Değer</span><span class="sxs-lookup"><span data-stu-id="1e855-132">Value</span></span>  |<span data-ttu-id="1e855-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1e855-133">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="1e855-134">0x80041001</span><span class="sxs-lookup"><span data-stu-id="1e855-134">0x80041001</span></span> | <span data-ttu-id="1e855-135">Genel bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="1e855-135">There has been a general failure.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="1e855-136">0x80041008</span><span class="sxs-lookup"><span data-stu-id="1e855-136">0x80041008</span></span> | <span data-ttu-id="1e855-137">Bir veya daha fazla parametre geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="1e855-137">One or more parameters are not valid.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="1e855-138">0x80041002</span><span class="sxs-lookup"><span data-stu-id="1e855-138">0x80041002</span></span> | <span data-ttu-id="1e855-139">Belirtilen özellik bulunamadı.</span><span class="sxs-lookup"><span data-stu-id="1e855-139">The specified property was not found.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="1e855-140">0x80041006</span><span class="sxs-lookup"><span data-stu-id="1e855-140">0x80041006</span></span> | <span data-ttu-id="1e855-141">İşlemi tamamlamak yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="1e855-141">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="1e855-142">0</span><span class="sxs-lookup"><span data-stu-id="1e855-142">0</span></span> | <span data-ttu-id="1e855-143">İşlev çağrısı başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="1e855-143">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="1e855-144">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1e855-144">Remarks</span></span>

<span data-ttu-id="1e855-145">Bu işlev çağrısı sarmalar [IWbemClassObject::Get](https://msdn.microsoft.com/library/aa391442(v=vs.85).aspx) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="1e855-145">This function wraps a call to the [IWbemClassObject::Get](https://msdn.microsoft.com/library/aa391442(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="1e855-146">`Get` İşlevi ayrıca sistem özellikleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="1e855-146">The `Get` function can also return system properties.</span></span>

<span data-ttu-id="1e855-147">`pVal` Bağımsız değişkeni doğru türü ve değerine niteleyici ve COM için atanan [VariantInit](https://msdn.microsoft.com/library/ms221402(v=vs.85).aspx) işlevi</span><span class="sxs-lookup"><span data-stu-id="1e855-147">The `pVal` argument is assigned the correct type and value for the qualifier and the COM [VariantInit](https://msdn.microsoft.com/library/ms221402(v=vs.85).aspx) function</span></span>

## <a name="requirements"></a><span data-ttu-id="1e855-148">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1e855-148">Requirements</span></span>  
 <span data-ttu-id="1e855-149">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1e855-149">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1e855-150">**Başlık:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="1e855-150">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="1e855-151">**.NET framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="1e855-151">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e855-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1e855-152">See also</span></span>  
[<span data-ttu-id="1e855-153">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="1e855-153">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
