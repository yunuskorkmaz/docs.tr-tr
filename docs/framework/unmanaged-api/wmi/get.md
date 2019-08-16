---
title: GET işlevi (yönetilmeyen API Başvurusu)
description: GET işlevi belirtilen özellik değerini alır.
ms.date: 11/06/2017
api_name:
- Get
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Get
helpviewer_keywords:
- Get function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 265d3edbd3175eebcf6fd35be24f5b66144c960f
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69037947"
---
# <a name="get-function"></a><span data-ttu-id="8e21c-103">Get işlevi</span><span class="sxs-lookup"><span data-stu-id="8e21c-103">Get function</span></span>

<span data-ttu-id="8e21c-104">Varsa belirtilen özellik değerini alır.</span><span class="sxs-lookup"><span data-stu-id="8e21c-104">Retrieves the specified property value if it exists.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="8e21c-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8e21c-105">Syntax</span></span>

```cpp
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

## <a name="parameters"></a><span data-ttu-id="8e21c-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8e21c-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="8e21c-107">'ndaki Bu parametre kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="8e21c-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="8e21c-108">'ndaki [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneğine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="8e21c-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszName`\
<span data-ttu-id="8e21c-109">'ndaki Özelliğin adı.</span><span class="sxs-lookup"><span data-stu-id="8e21c-109">[in] The name of the property.</span></span>

`lFlags`\
<span data-ttu-id="8e21c-110">'ndaki Ayrılamadı.</span><span class="sxs-lookup"><span data-stu-id="8e21c-110">[in] Reserved.</span></span> <span data-ttu-id="8e21c-111">Bu parametre 0 olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8e21c-111">This parameter must be 0.</span></span>

`pVal`\
<span data-ttu-id="8e21c-112">dışı İşlev başarıyla döndürürse, `wszName` özelliğinin değerini içerir.</span><span class="sxs-lookup"><span data-stu-id="8e21c-112">[out] If the function returns successfully, contains the value of the `wszName` property.</span></span> <span data-ttu-id="8e21c-113">`pval` Bağımsız değişkenine, niteleyicisi için doğru tür ve değer atanır.</span><span class="sxs-lookup"><span data-stu-id="8e21c-113">The `pval` argument is assigned the correct type and value for the qualifier.</span></span>

`pvtType`\
<span data-ttu-id="8e21c-114">dışı İşlev başarıyla döndürürse, özellik türünü gösteren bir [CIM türü sabiti](/windows/win32/api/wbemcli/ne-wbemcli-cimtype_enumeration) içerir.</span><span class="sxs-lookup"><span data-stu-id="8e21c-114">[out] If the function returns successfully, contains a [CIM-type constant](/windows/win32/api/wbemcli/ne-wbemcli-cimtype_enumeration) that indicates the property type.</span></span> <span data-ttu-id="8e21c-115">Değeri de olabilir `null`.</span><span class="sxs-lookup"><span data-stu-id="8e21c-115">Its value can also be `null`.</span></span> 

`plFlavor`\
<span data-ttu-id="8e21c-116">dışı İşlev başarıyla döndürürse, özelliğin kaynağı hakkında bilgi alır.</span><span class="sxs-lookup"><span data-stu-id="8e21c-116">[out] If the function returns successfully, receives information about the origin of the property.</span></span> <span data-ttu-id="8e21c-117">Bunun değeri `null`, *wbemcli. h* üstbilgi dosyasında tanımlanan aşağıdaki WBEM_FLAVOR_TYPE sabitlerinden biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="8e21c-117">Its value can be `null`, or one of the following WBEM_FLAVOR_TYPE constants defined in the *WbemCli.h* header file:</span></span> 

|<span data-ttu-id="8e21c-118">Sabit</span><span class="sxs-lookup"><span data-stu-id="8e21c-118">Constant</span></span>  |<span data-ttu-id="8e21c-119">Değer</span><span class="sxs-lookup"><span data-stu-id="8e21c-119">Value</span></span>  |<span data-ttu-id="8e21c-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8e21c-120">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAVOR_ORIGIN_SYSTEM` | <span data-ttu-id="8e21c-121">0x40</span><span class="sxs-lookup"><span data-stu-id="8e21c-121">0x40</span></span> | <span data-ttu-id="8e21c-122">Özelliği, standart bir sistem özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="8e21c-122">The property is a standard system property.</span></span> |
| `WBEM_FLAVOR_ORIGIN_PROPAGATED` | <span data-ttu-id="8e21c-123">0x20</span><span class="sxs-lookup"><span data-stu-id="8e21c-123">0x20</span></span> | <span data-ttu-id="8e21c-124">Bir sınıf için: Özelliği üst sınıftan devralınır.</span><span class="sxs-lookup"><span data-stu-id="8e21c-124">For a class: The property is inherited from the parent class.</span></span> <br> <span data-ttu-id="8e21c-125">Bir örnek için: Üst sınıftan Devralındığı sürece özelliği, örnek tarafından değiştirilmez.</span><span class="sxs-lookup"><span data-stu-id="8e21c-125">For an instance: The property, while inherited from the parent class, has not been modified by the instance.</span></span>  |
| `WBEM_FLAVOR_ORIGIN_LOCAL` | <span data-ttu-id="8e21c-126">0</span><span class="sxs-lookup"><span data-stu-id="8e21c-126">0</span></span> | <span data-ttu-id="8e21c-127">Bir sınıf için: Özelliği türetilmiş sınıfa aittir.</span><span class="sxs-lookup"><span data-stu-id="8e21c-127">For a class: The property belongs to the derived class.</span></span> <br> <span data-ttu-id="8e21c-128">Bir örnek için: Özelliği örnek tarafından değiştirilir; diğer bir deyişle, bir değer sağlanmış veya bir niteleyici eklenmiş ya da değiştirilmiş.</span><span class="sxs-lookup"><span data-stu-id="8e21c-128">For an instance: The property is modified by the instance; that is, a value was supplied, or a qualifier was added or modified.</span></span> |

## <a name="return-value"></a><span data-ttu-id="8e21c-129">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="8e21c-129">Return value</span></span>

<span data-ttu-id="8e21c-130">Bu işlev tarafından döndürülen aşağıdaki değerler, *Wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8e21c-130">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="8e21c-131">Sabit</span><span class="sxs-lookup"><span data-stu-id="8e21c-131">Constant</span></span>  |<span data-ttu-id="8e21c-132">Değer</span><span class="sxs-lookup"><span data-stu-id="8e21c-132">Value</span></span>  |<span data-ttu-id="8e21c-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8e21c-133">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="8e21c-134">0x80041001</span><span class="sxs-lookup"><span data-stu-id="8e21c-134">0x80041001</span></span> | <span data-ttu-id="8e21c-135">Genel bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="8e21c-135">There has been a general failure.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="8e21c-136">0x80041008</span><span class="sxs-lookup"><span data-stu-id="8e21c-136">0x80041008</span></span> | <span data-ttu-id="8e21c-137">Bir veya daha fazla parametre geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="8e21c-137">One or more parameters are not valid.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="8e21c-138">0x80041002</span><span class="sxs-lookup"><span data-stu-id="8e21c-138">0x80041002</span></span> | <span data-ttu-id="8e21c-139">Belirtilen özellik bulunamadı.</span><span class="sxs-lookup"><span data-stu-id="8e21c-139">The specified property was not found.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="8e21c-140">0x80041006</span><span class="sxs-lookup"><span data-stu-id="8e21c-140">0x80041006</span></span> | <span data-ttu-id="8e21c-141">İşlemi gerçekleştirmek için yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="8e21c-141">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="8e21c-142">0</span><span class="sxs-lookup"><span data-stu-id="8e21c-142">0</span></span> | <span data-ttu-id="8e21c-143">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="8e21c-143">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="8e21c-144">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8e21c-144">Remarks</span></span>

<span data-ttu-id="8e21c-145">Bu işlev, [IWbemClassObject:: Get](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-get) yöntemine bir çağrı kaydırır.</span><span class="sxs-lookup"><span data-stu-id="8e21c-145">This function wraps a call to the [IWbemClassObject::Get](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-get) method.</span></span>

<span data-ttu-id="8e21c-146">`Get` İşlev sistem özelliklerini de döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="8e21c-146">The `Get` function can also return system properties.</span></span>

<span data-ttu-id="8e21c-147">Bağımsız değişkenine, niteleyicinin ve com [variantinit](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-variantinit) işlevinin doğru türü ve değeri atanır `pVal`</span><span class="sxs-lookup"><span data-stu-id="8e21c-147">The `pVal` argument is assigned the correct type and value for the qualifier and the COM [VariantInit](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-variantinit) function</span></span>

## <a name="requirements"></a><span data-ttu-id="8e21c-148">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8e21c-148">Requirements</span></span>

 <span data-ttu-id="8e21c-149">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8e21c-149">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

 <span data-ttu-id="8e21c-150">**Üst bilgi** WMINet_Utils. IDL</span><span class="sxs-lookup"><span data-stu-id="8e21c-150">**Header:** WMINet_Utils.idl</span></span>

 <span data-ttu-id="8e21c-151">**.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="8e21c-151">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="8e21c-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8e21c-152">See also</span></span>

- [<span data-ttu-id="8e21c-153">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="8e21c-153">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
