---
title: Put işlevi (yönetilmeyen API Başvurusu)
description: Put işlevi, adlandırılmış bir özelliğe yeni bir değer atar.
ms.date: 11/06/2017
api_name:
- Put
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Put
helpviewer_keywords:
- Put function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5aa629c2d07fb25db035cd80aba3c74413070e6e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798405"
---
# <a name="put-function"></a><span data-ttu-id="3ace9-103">Put işlevi</span><span class="sxs-lookup"><span data-stu-id="3ace9-103">Put function</span></span>

<span data-ttu-id="3ace9-104">Adlandırılmış bir özelliği yeni bir değere ayarlar.</span><span class="sxs-lookup"><span data-stu-id="3ace9-104">Sets a named property to a new value.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="3ace9-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3ace9-105">Syntax</span></span>

```cpp
HRESULT Put (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LPCWSTR           wszName,
   [in] LONG              lFlags,
   [in] VARIANT*          pVal,
   [in] CIMTYPE           vtType
);
```

## <a name="parameters"></a><span data-ttu-id="3ace9-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3ace9-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="3ace9-107">'ndaki Bu parametre kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="3ace9-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="3ace9-108">'ndaki [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneğine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3ace9-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszName`\
<span data-ttu-id="3ace9-109">'ndaki Özelliğin adı.</span><span class="sxs-lookup"><span data-stu-id="3ace9-109">[in] The name of the property.</span></span> <span data-ttu-id="3ace9-110">Bu parametre `null`olamaz.</span><span class="sxs-lookup"><span data-stu-id="3ace9-110">This parameter cannot be `null`.</span></span>

`lFlags`\
<span data-ttu-id="3ace9-111">'ndaki Ayrılamadı.</span><span class="sxs-lookup"><span data-stu-id="3ace9-111">[in] Reserved.</span></span> <span data-ttu-id="3ace9-112">Bu parametre 0 olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3ace9-112">This parameter must be 0.</span></span>

`pVal`\
<span data-ttu-id="3ace9-113">'ndaki Yeni özellik değeri haline gelen `VARIANT` geçerli bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="3ace9-113">[in] A pointer to a valid `VARIANT` that becomes the new property value.</span></span> <span data-ttu-id="3ace9-114">`pVal` , `null`Veya türünden bir`VARIANT`işaret ediyorsa, özelliği olarak ayarlanır. `VT_NULL` `null`</span><span class="sxs-lookup"><span data-stu-id="3ace9-114">If `pVal` is `null` or points to a `VARIANT` of type `VT_NULL`, the property is set to `null`.</span></span>

`vtType`\
<span data-ttu-id="3ace9-115">'ndaki `VARIANT` Tarafından`pVal`işaret edilen türü.</span><span class="sxs-lookup"><span data-stu-id="3ace9-115">[in] The type of `VARIANT` pointed to by `pVal`.</span></span> <span data-ttu-id="3ace9-116">Daha fazla bilgi için [açıklamalar](#remarks) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="3ace9-116">See the [Remarks](#remarks) section for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="3ace9-117">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="3ace9-117">Return value</span></span>

<span data-ttu-id="3ace9-118">Bu işlev tarafından döndürülen aşağıdaki değerler, *Wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="3ace9-118">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="3ace9-119">Sabit</span><span class="sxs-lookup"><span data-stu-id="3ace9-119">Constant</span></span>  |<span data-ttu-id="3ace9-120">Değer</span><span class="sxs-lookup"><span data-stu-id="3ace9-120">Value</span></span>  |<span data-ttu-id="3ace9-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3ace9-121">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="3ace9-122">0x80041001</span><span class="sxs-lookup"><span data-stu-id="3ace9-122">0x80041001</span></span> | <span data-ttu-id="3ace9-123">Genel bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="3ace9-123">There has been a general failure.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="3ace9-124">0x80041008</span><span class="sxs-lookup"><span data-stu-id="3ace9-124">0x80041008</span></span> | <span data-ttu-id="3ace9-125">Bir veya daha fazla parametre geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="3ace9-125">One or more parameters are not valid.</span></span> |
|`WBEM_E_INVALID_PROPERTY_TYPE` | <span data-ttu-id="3ace9-126">0x8004102a</span><span class="sxs-lookup"><span data-stu-id="3ace9-126">0x8004102a</span></span> | <span data-ttu-id="3ace9-127">Özellik türü tanınmıyor.</span><span class="sxs-lookup"><span data-stu-id="3ace9-127">The property type is not recognized.</span></span> <span data-ttu-id="3ace9-128">Sınıf örnekleri oluşturulurken Bu değer döndürülür.</span><span class="sxs-lookup"><span data-stu-id="3ace9-128">This value is returned when creating class instances if the class already exists.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="3ace9-129">0x80041006</span><span class="sxs-lookup"><span data-stu-id="3ace9-129">0x80041006</span></span> | <span data-ttu-id="3ace9-130">İşlemi gerçekleştirmek için yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="3ace9-130">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_TYPE_MISMATCH` | <span data-ttu-id="3ace9-131">0x80041005</span><span class="sxs-lookup"><span data-stu-id="3ace9-131">0x80041005</span></span> | <span data-ttu-id="3ace9-132">Örnekler için: Özelliği için `pVal` yanlış türde bir `VARIANT` işaret olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="3ace9-132">For instances: Indicates that `pVal` points to a `VARIANT` of an incorrect type for the property.</span></span> <br/> <span data-ttu-id="3ace9-133">Sınıf tanımları için: Özellik üst sınıfta zaten var ve yeni COM türü eski COM türünden farklı.</span><span class="sxs-lookup"><span data-stu-id="3ace9-133">For class definitions: The property already exists in the parent class, and the new COM type is different from the old COM type.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="3ace9-134">0</span><span class="sxs-lookup"><span data-stu-id="3ace9-134">0</span></span> | <span data-ttu-id="3ace9-135">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="3ace9-135">The function call was successful.</span></span> |

## <a name="remarks"></a><span data-ttu-id="3ace9-136">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3ace9-136">Remarks</span></span>

<span data-ttu-id="3ace9-137">Bu işlev, [IWbemClassObject::P UT](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-put) yöntemine bir çağrı kaydırır.</span><span class="sxs-lookup"><span data-stu-id="3ace9-137">This function wraps a call to the [IWbemClassObject::Put](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-put) method.</span></span>

<span data-ttu-id="3ace9-138">Bu işlev her zaman geçerli özellik değerinin üzerine yeni bir değer yazar.</span><span class="sxs-lookup"><span data-stu-id="3ace9-138">This function always overwrites the current property value with a new one.</span></span> <span data-ttu-id="3ace9-139">[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) bir sınıf tanımına işaret ediyorsa, `Put` özellik değerini oluşturur veya güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="3ace9-139">If the [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) points to a class definition, `Put` creates or updates the property value.</span></span> <span data-ttu-id="3ace9-140">[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) bir CIM örneğine işaret ediyorsa, `Put` yalnızca özellik değerini güncelleştirir; `Put` Özellik değeri oluşturulamıyor.</span><span class="sxs-lookup"><span data-stu-id="3ace9-140">When [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) points to a CIM instance, `Put` updates the property value only; `Put` cannot create a property value.</span></span>

<span data-ttu-id="3ace9-141">`__CLASS` System özelliği, yalnızca sınıf oluşturma sırasında yazılabilir, boş bırakılmayabilir.</span><span class="sxs-lookup"><span data-stu-id="3ace9-141">The `__CLASS` system property is only writable during class creation, when it may not be left blank.</span></span> <span data-ttu-id="3ace9-142">Diğer tüm sistem özellikleri salt okunurdur.</span><span class="sxs-lookup"><span data-stu-id="3ace9-142">All other system properties are read-only.</span></span>

<span data-ttu-id="3ace9-143">Bir Kullanıcı, alt çizgi ("_") ile başlayan veya biten adlara sahip özellikler oluşturamaz.</span><span class="sxs-lookup"><span data-stu-id="3ace9-143">A user cannot create properties with names that begin or end with an underscore ("_").</span></span> <span data-ttu-id="3ace9-144">Bu sistem sınıfları ve özellikleri için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="3ace9-144">This is reserved for system classes and properties.</span></span>

<span data-ttu-id="3ace9-145">`Put` İşlev tarafından ayarlanan özellik üst sınıfta varsa, özellik türü üst sınıf türüyle eşleşmediğinden özelliğin varsayılan değeri değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="3ace9-145">If the property set by the `Put` function exists in the parent class, the default value of the property is changed unless the property type does not match the parent class type.</span></span> <span data-ttu-id="3ace9-146">Özellik yoksa ve bir tür uyumsuzluğu değilse, özellik oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="3ace9-146">If the property does not exist and it is not a type mismatch, the property is created.</span></span>

<span data-ttu-id="3ace9-147">`null` `pVal` `VT_NULL` `VARIANT` Parametresini yalnızca bir CIM sınıf tanımında yeni özellikler oluştururken kullanın ve veya türünü işaret eder. `vtType`</span><span class="sxs-lookup"><span data-stu-id="3ace9-147">Use the `vtType` parameter only when creating new properties in a CIM class definition and `pVal` is `null` or points to a `VARIANT` of type `VT_NULL`.</span></span> <span data-ttu-id="3ace9-148">Bu durumda, `vType` parametresi özelliğinin CIM türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="3ace9-148">In this case, the `vType` parameter specifies the CIM type of the property.</span></span> <span data-ttu-id="3ace9-149">Her iki durumda da `vtType` 0 olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3ace9-149">In every other case, `vtType` must be 0.</span></span> <span data-ttu-id="3ace9-150">`vtType`Ayrıca, özelliğin türü düzeltildiği ve değiştirilemediğinden, temeldeki nesne bir örnek `Val` ise `null`(olsa bile) 0 olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3ace9-150">`vtType` must also be 0 if the underlying object is an instance (even if `Val` is `null`) because the type of the property is fixed and cannot be changed.</span></span>

## <a name="example"></a><span data-ttu-id="3ace9-151">Örnek</span><span class="sxs-lookup"><span data-stu-id="3ace9-151">Example</span></span>

<span data-ttu-id="3ace9-152">Bir örnek için, bkz. [IWbemClassObject::P UT](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-put) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="3ace9-152">For an example, see the [IWbemClassObject::Put](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-put) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="3ace9-153">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3ace9-153">Requirements</span></span>

<span data-ttu-id="3ace9-154">**Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3ace9-154">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="3ace9-155">**Üst bilgi** WMINet_Utils. IDL</span><span class="sxs-lookup"><span data-stu-id="3ace9-155">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="3ace9-156">**.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="3ace9-156">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="3ace9-157">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3ace9-157">See also</span></span>

- [<span data-ttu-id="3ace9-158">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="3ace9-158">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
