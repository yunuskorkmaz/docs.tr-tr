---
title: İşlev alın (Yönetilmeyen API Başvurusu)
description: Get işlevi belirtilen özellik değerini alır.
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
ms.openlocfilehash: 67fcfb301eebfcf4ed4fdcaa5c9ddf85c47a6073
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174985"
---
# <a name="get-function"></a><span data-ttu-id="e6a41-103">Get işlevi</span><span class="sxs-lookup"><span data-stu-id="e6a41-103">Get function</span></span>

<span data-ttu-id="e6a41-104">Varsa belirtilen özellik değerini alır.</span><span class="sxs-lookup"><span data-stu-id="e6a41-104">Retrieves the specified property value if it exists.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="e6a41-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e6a41-105">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="e6a41-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e6a41-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="e6a41-107">[içinde] Bu parametre kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="e6a41-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="e6a41-108">[içinde] [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneğine işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e6a41-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszName`\
<span data-ttu-id="e6a41-109">[içinde] Mülkün adı.</span><span class="sxs-lookup"><span data-stu-id="e6a41-109">[in] The name of the property.</span></span>

`lFlags`\
<span data-ttu-id="e6a41-110">[içinde] Saklı -dır.</span><span class="sxs-lookup"><span data-stu-id="e6a41-110">[in] Reserved.</span></span> <span data-ttu-id="e6a41-111">Bu parametre 0 olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e6a41-111">This parameter must be 0.</span></span>

`pVal`\
<span data-ttu-id="e6a41-112">[çıkış] İşlev başarılı bir şekilde dönerse, `wszName` özelliğin değerini içerir.</span><span class="sxs-lookup"><span data-stu-id="e6a41-112">[out] If the function returns successfully, contains the value of the `wszName` property.</span></span> <span data-ttu-id="e6a41-113">Bağımsız `pval` değişken, niteleyici için doğru tür ve değer atanır.</span><span class="sxs-lookup"><span data-stu-id="e6a41-113">The `pval` argument is assigned the correct type and value for the qualifier.</span></span>

`pvtType`\
<span data-ttu-id="e6a41-114">[çıkış] İşlev başarıyla dönerse, özellik türünü gösteren bir [CIM tipi sabit](/windows/win32/api/wbemcli/ne-wbemcli-cimtype_enumeration) içerir.</span><span class="sxs-lookup"><span data-stu-id="e6a41-114">[out] If the function returns successfully, contains a [CIM-type constant](/windows/win32/api/wbemcli/ne-wbemcli-cimtype_enumeration) that indicates the property type.</span></span> <span data-ttu-id="e6a41-115">Değeri de olabilir. `null`</span><span class="sxs-lookup"><span data-stu-id="e6a41-115">Its value can also be `null`.</span></span>

`plFlavor`\
<span data-ttu-id="e6a41-116">[çıkış] İşlev başarıyla dönerse, özelliğin kaynağı hakkında bilgi alır.</span><span class="sxs-lookup"><span data-stu-id="e6a41-116">[out] If the function returns successfully, receives information about the origin of the property.</span></span> <span data-ttu-id="e6a41-117">Değeri, `null` *WbemCli.h* üstbilgi dosyasında tanımlanan aşağıdaki WBEM_FLAVOR_TYPE sabitlerden biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="e6a41-117">Its value can be `null`, or one of the following WBEM_FLAVOR_TYPE constants defined in the *WbemCli.h* header file:</span></span>

|<span data-ttu-id="e6a41-118">Sabit</span><span class="sxs-lookup"><span data-stu-id="e6a41-118">Constant</span></span>  |<span data-ttu-id="e6a41-119">Değer</span><span class="sxs-lookup"><span data-stu-id="e6a41-119">Value</span></span>  |<span data-ttu-id="e6a41-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e6a41-120">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAVOR_ORIGIN_SYSTEM` | <span data-ttu-id="e6a41-121">0x40</span><span class="sxs-lookup"><span data-stu-id="e6a41-121">0x40</span></span> | <span data-ttu-id="e6a41-122">Özellik standart bir sistem özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="e6a41-122">The property is a standard system property.</span></span> |
| `WBEM_FLAVOR_ORIGIN_PROPAGATED` | <span data-ttu-id="e6a41-123">0x20</span><span class="sxs-lookup"><span data-stu-id="e6a41-123">0x20</span></span> | <span data-ttu-id="e6a41-124">Bir sınıf için: Özellik üst sınıftan devralır.</span><span class="sxs-lookup"><span data-stu-id="e6a41-124">For a class: The property is inherited from the parent class.</span></span> <br> <span data-ttu-id="e6a41-125">Örneğin: Özellik, üst sınıftan devralınmış olsa da, örnek tarafından değiştirilmedi.</span><span class="sxs-lookup"><span data-stu-id="e6a41-125">For an instance: The property, while inherited from the parent class, has not been modified by the instance.</span></span>  |
| `WBEM_FLAVOR_ORIGIN_LOCAL` | <span data-ttu-id="e6a41-126">0</span><span class="sxs-lookup"><span data-stu-id="e6a41-126">0</span></span> | <span data-ttu-id="e6a41-127">Bir sınıf için: Özellik türemiş sınıfa aittir.</span><span class="sxs-lookup"><span data-stu-id="e6a41-127">For a class: The property belongs to the derived class.</span></span> <br> <span data-ttu-id="e6a41-128">Örneğin: Özellik örnek tarafından değiştirilir; diğer bir şekilde, bir değer sağlandı veya bir niteleyici eklendi veya değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="e6a41-128">For an instance: The property is modified by the instance; that is, a value was supplied, or a qualifier was added or modified.</span></span> |

## <a name="return-value"></a><span data-ttu-id="e6a41-129">Döndürülen değer</span><span class="sxs-lookup"><span data-stu-id="e6a41-129">Return value</span></span>

<span data-ttu-id="e6a41-130">Bu işlev tarafından döndürülen aşağıdaki değerler *WbemCli.h* üstbilgi dosyasında tanımlanır veya bunları kodunuzdaki sabitler olarak tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e6a41-130">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="e6a41-131">Sabit</span><span class="sxs-lookup"><span data-stu-id="e6a41-131">Constant</span></span>  |<span data-ttu-id="e6a41-132">Değer</span><span class="sxs-lookup"><span data-stu-id="e6a41-132">Value</span></span>  |<span data-ttu-id="e6a41-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e6a41-133">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="e6a41-134">0x80041001</span><span class="sxs-lookup"><span data-stu-id="e6a41-134">0x80041001</span></span> | <span data-ttu-id="e6a41-135">Genel bir başarısızlık oldu.</span><span class="sxs-lookup"><span data-stu-id="e6a41-135">There has been a general failure.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="e6a41-136">0x80041008</span><span class="sxs-lookup"><span data-stu-id="e6a41-136">0x80041008</span></span> | <span data-ttu-id="e6a41-137">Bir veya daha fazla parametre geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="e6a41-137">One or more parameters are not valid.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="e6a41-138">0x80041002</span><span class="sxs-lookup"><span data-stu-id="e6a41-138">0x80041002</span></span> | <span data-ttu-id="e6a41-139">Belirtilen özellik bulunamadı.</span><span class="sxs-lookup"><span data-stu-id="e6a41-139">The specified property was not found.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="e6a41-140">0x80041006</span><span class="sxs-lookup"><span data-stu-id="e6a41-140">0x80041006</span></span> | <span data-ttu-id="e6a41-141">İşlemi tamamlamak için yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="e6a41-141">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="e6a41-142">0</span><span class="sxs-lookup"><span data-stu-id="e6a41-142">0</span></span> | <span data-ttu-id="e6a41-143">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="e6a41-143">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="e6a41-144">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e6a41-144">Remarks</span></span>

<span data-ttu-id="e6a41-145">Bu işlev [IWbemClassObject](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-get) bir çağrı sarar::Get yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e6a41-145">This function wraps a call to the [IWbemClassObject::Get](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-get) method.</span></span>

<span data-ttu-id="e6a41-146">İşlev `Get` sistem özelliklerini de döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="e6a41-146">The `Get` function can also return system properties.</span></span>

<span data-ttu-id="e6a41-147">Bağımsız `pVal` değişken, niteleyici ve COM [VariantInit](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-variantinit) işlevi için doğru tür ve değer atanır</span><span class="sxs-lookup"><span data-stu-id="e6a41-147">The `pVal` argument is assigned the correct type and value for the qualifier and the COM [VariantInit](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-variantinit) function</span></span>

## <a name="requirements"></a><span data-ttu-id="e6a41-148">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e6a41-148">Requirements</span></span>

 <span data-ttu-id="e6a41-149">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e6a41-149">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

 <span data-ttu-id="e6a41-150">**Üstbilgi:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="e6a41-150">**Header:** WMINet_Utils.idl</span></span>

 <span data-ttu-id="e6a41-151">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="e6a41-151">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="e6a41-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e6a41-152">See also</span></span>

- [<span data-ttu-id="e6a41-153">WMI ve Performans Sayaçları (Yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="e6a41-153">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
