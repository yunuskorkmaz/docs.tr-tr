---
title: Next işlevi (yönetilmeyen API Başvurusu)
description: Next işlevi bir Numaralandırmadaki sonraki özelliği alır.
ms.date: 11/06/2017
api_name:
- Next
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Next
helpviewer_keywords:
- Next function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: c2a7fae32e82caae40a95bfdad10fa78082988ef
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726797"
---
# <a name="next-function"></a><span data-ttu-id="91496-103">Next işlevi</span><span class="sxs-lookup"><span data-stu-id="91496-103">Next function</span></span>

<span data-ttu-id="91496-104">Bir [beginenumeration](beginenumeration.md)çağrısıyla başlayan bir Numaralandırmadaki bir sonraki özelliği alır.</span><span class="sxs-lookup"><span data-stu-id="91496-104">Retrieves the next property in an enumeration that begins with a call to [BeginEnumeration](beginenumeration.md).</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="91496-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="91496-105">Syntax</span></span>

```cpp
HRESULT Next (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LONG              lFlags,
   [out] BSTR*            pstrName,
   [out] VARIANT*         pVal,
   [out] CIMTYPE*         pvtType,
   [out] LONG*            plFlavor
);
```

## <a name="parameters"></a><span data-ttu-id="91496-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="91496-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="91496-107">'ndaki Bu parametre kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="91496-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="91496-108">'ndaki [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneğine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="91496-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lFlags`\
<span data-ttu-id="91496-109">'ndaki Ayrılamadı.</span><span class="sxs-lookup"><span data-stu-id="91496-109">[in] Reserved.</span></span> <span data-ttu-id="91496-110">Bu parametre 0 olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="91496-110">This parameter must be 0.</span></span>

`pstrName`\
<span data-ttu-id="91496-111">dışı `BSTR` Özellik adını içeren yeni bir.</span><span class="sxs-lookup"><span data-stu-id="91496-111">[out] A new `BSTR` that contains the property name.</span></span> <span data-ttu-id="91496-112">Ad gerekmiyorsa, bu parametreyi olarak ayarlayabilirsiniz `null` .</span><span class="sxs-lookup"><span data-stu-id="91496-112">You can set this parameter to `null` if the name is not required.</span></span>

`pVal`\
<span data-ttu-id="91496-113">dışı , `VARIANT` Özelliğinin değeri ile doldurulmuştur.</span><span class="sxs-lookup"><span data-stu-id="91496-113">[out] A `VARIANT` filled with the value of the property.</span></span> <span data-ttu-id="91496-114">Değer gerekmiyorsa, bu parametreyi olarak ayarlayabilirsiniz `null` .</span><span class="sxs-lookup"><span data-stu-id="91496-114">You can set this parameter to `null` if the value is not required.</span></span> <span data-ttu-id="91496-115">İşlev bir hata kodu döndürürse, `VARIANT` geçilen öğesine `pVal` değiştirilmemiş olarak kalır.</span><span class="sxs-lookup"><span data-stu-id="91496-115">If the function returns an error code, the `VARIANT` passed to `pVal` is left unmodified.</span></span>

`pvtType`\
<span data-ttu-id="91496-116">dışı Bir `CIMTYPE` değişken işaretçisi ( `LONG` özelliğin türünün yerleştirildiği bir).</span><span class="sxs-lookup"><span data-stu-id="91496-116">[out] A pointer to a `CIMTYPE` variable (a `LONG` into which the type of the property is placed).</span></span> <span data-ttu-id="91496-117">Bu özelliğin değeri bir olabilir `VT_NULL_VARIANT` , bu durumda özelliğin gerçek türünü belirlenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="91496-117">The value of this property can be a `VT_NULL_VARIANT`, in which case it is necessary to determine the actual type of the property.</span></span> <span data-ttu-id="91496-118">Bu parametre de olabilir `null` .</span><span class="sxs-lookup"><span data-stu-id="91496-118">This parameter can also be `null`.</span></span>

`plFlavor`\
<span data-ttu-id="91496-119">[out] `null` veya özelliğin kaynağına bilgi alan bir değer.</span><span class="sxs-lookup"><span data-stu-id="91496-119">[out] `null`, or a value that receives information on the origin of the property.</span></span> <span data-ttu-id="91496-120">Olası değerler için [açıklamalar] bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="91496-120">See the [Remarks] section for possible values.</span></span>

## <a name="return-value"></a><span data-ttu-id="91496-121">Döndürülen değer</span><span class="sxs-lookup"><span data-stu-id="91496-121">Return value</span></span>

<span data-ttu-id="91496-122">Bu işlev tarafından döndürülen aşağıdaki değerler, *Wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="91496-122">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="91496-123">Sabit</span><span class="sxs-lookup"><span data-stu-id="91496-123">Constant</span></span>  |<span data-ttu-id="91496-124">Değer</span><span class="sxs-lookup"><span data-stu-id="91496-124">Value</span></span>  |<span data-ttu-id="91496-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="91496-125">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="91496-126">0x80041001</span><span class="sxs-lookup"><span data-stu-id="91496-126">0x80041001</span></span> | <span data-ttu-id="91496-127">Genel bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="91496-127">There has been a general failure.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="91496-128">0x80041008</span><span class="sxs-lookup"><span data-stu-id="91496-128">0x80041008</span></span> | <span data-ttu-id="91496-129">Bir parametre geçersiz.</span><span class="sxs-lookup"><span data-stu-id="91496-129">A parameter is invalid.</span></span> |
| `WBEM_E_UNEXPECTED` | <span data-ttu-id="91496-130">0x8004101D</span><span class="sxs-lookup"><span data-stu-id="91496-130">0x8004101d</span></span> | <span data-ttu-id="91496-131">İşleve bir çağrı yoktu [`BeginEnumeration`](beginenumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="91496-131">There was no call to the [`BeginEnumeration`](beginenumeration.md) function.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="91496-132">0x80041006</span><span class="sxs-lookup"><span data-stu-id="91496-132">0x80041006</span></span> | <span data-ttu-id="91496-133">Yeni bir sabit listesi başlatmak için yeterli kullanılabilir bellek yok.</span><span class="sxs-lookup"><span data-stu-id="91496-133">Not enough memory is available to begin a new enumeration.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="91496-134">0x80041015</span><span class="sxs-lookup"><span data-stu-id="91496-134">0x80041015</span></span> | <span data-ttu-id="91496-135">Geçerli işlem ile Windows Yönetimi arasındaki uzak yordam çağrısı başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="91496-135">The remote procedure call between the current process and Windows Management failed.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="91496-136">0</span><span class="sxs-lookup"><span data-stu-id="91496-136">0</span></span> | <span data-ttu-id="91496-137">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="91496-137">The function call was successful.</span></span>  |
| `WBEM_S_NO_MORE_DATA` | <span data-ttu-id="91496-138">0x40005</span><span class="sxs-lookup"><span data-stu-id="91496-138">0x40005</span></span> | <span data-ttu-id="91496-139">Numaralandırmada daha fazla özellik yok.</span><span class="sxs-lookup"><span data-stu-id="91496-139">There are no more properties in the enumeration.</span></span> |

## <a name="remarks"></a><span data-ttu-id="91496-140">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="91496-140">Remarks</span></span>

<span data-ttu-id="91496-141">Bu işlev [IWbemClassObject:: Next](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-next) yöntemine bir çağrı kaydırır.</span><span class="sxs-lookup"><span data-stu-id="91496-141">This function wraps a call to the [IWbemClassObject::Next](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-next) method.</span></span>

<span data-ttu-id="91496-142">Bu yöntem ayrıca sistem özelliklerini de döndürür.</span><span class="sxs-lookup"><span data-stu-id="91496-142">This method also returns system properties.</span></span>

<span data-ttu-id="91496-143">Özelliğin temeldeki türü bir nesne yolu, bir tarih veya saat ya da başka bir özel tür ise, döndürülen tür yeterli bilgi içermez.</span><span class="sxs-lookup"><span data-stu-id="91496-143">If the underlying type of the property is an object path, a date or time, or another special type, then the returned type does not contain enough information.</span></span> <span data-ttu-id="91496-144">Çağıran, `CIMTYPE` özelliğin bir nesne başvurusu, bir tarih veya saat ya da başka bir özel tür olduğunu belirleyebilmek için belirtilen özelliği için öğesini incelemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="91496-144">The caller must examine the `CIMTYPE` for the specified property to determine if the property is an object reference, a date or time, or another special type.</span></span>

<span data-ttu-id="91496-145">`plFlavor`Değilse `null` , `LONG` değeri özelliğin kaynağı hakkında aşağıdaki gibi bilgileri alır:</span><span class="sxs-lookup"><span data-stu-id="91496-145">If `plFlavor` is not `null`, the `LONG` value receives information about the origin of the property, as follows:</span></span>

|<span data-ttu-id="91496-146">Sabit</span><span class="sxs-lookup"><span data-stu-id="91496-146">Constant</span></span>  |<span data-ttu-id="91496-147">Değer</span><span class="sxs-lookup"><span data-stu-id="91496-147">Value</span></span>  |<span data-ttu-id="91496-148">Açıklama</span><span class="sxs-lookup"><span data-stu-id="91496-148">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAVOR_ORIGIN_SYSTEM` | <span data-ttu-id="91496-149">0x40</span><span class="sxs-lookup"><span data-stu-id="91496-149">0x40</span></span> | <span data-ttu-id="91496-150">Özelliği, standart bir sistem özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="91496-150">The property is a standard system property.</span></span> |
| `WBEM_FLAVOR_ORIGIN_PROPAGATED` | <span data-ttu-id="91496-151">0x20</span><span class="sxs-lookup"><span data-stu-id="91496-151">0x20</span></span> | <span data-ttu-id="91496-152">Bir sınıf için: özellik üst sınıftan devralınır.</span><span class="sxs-lookup"><span data-stu-id="91496-152">For a class: The property is inherited from the parent class.</span></span> <br> <span data-ttu-id="91496-153">Bir örnek için: üst sınıftan Devralındığı sürece özelliği, örnek tarafından değiştirilmez.</span><span class="sxs-lookup"><span data-stu-id="91496-153">For an instance: The property, while inherited from the parent class, has not been modified by the instance.</span></span>  |
| `WBEM_FLAVOR_ORIGIN_LOCAL` | <span data-ttu-id="91496-154">0</span><span class="sxs-lookup"><span data-stu-id="91496-154">0</span></span> | <span data-ttu-id="91496-155">Bir sınıf için: özellik türetilmiş sınıfa aittir.</span><span class="sxs-lookup"><span data-stu-id="91496-155">For a class: The property belongs to the derived class.</span></span> <br> <span data-ttu-id="91496-156">Bir örnek için: özelliği örnek tarafından değiştirilir; diğer bir deyişle, bir değer sağlanmış veya bir niteleyici eklenmiş ya da değiştirilmiş.</span><span class="sxs-lookup"><span data-stu-id="91496-156">For an instance: The property is modified by the instance; that is, a value was supplied, or a qualifier was added or modified.</span></span> |

## <a name="requirements"></a><span data-ttu-id="91496-157">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="91496-157">Requirements</span></span>

<span data-ttu-id="91496-158">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="91496-158">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="91496-159">**Üst bilgi:** WMINet_Utils. IDL</span><span class="sxs-lookup"><span data-stu-id="91496-159">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="91496-160">**.NET Framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="91496-160">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="91496-161">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="91496-161">See also</span></span>

- [<span data-ttu-id="91496-162">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="91496-162">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
