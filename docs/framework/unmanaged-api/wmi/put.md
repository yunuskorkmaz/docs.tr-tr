---
title: Put işlevi (yönetilmeyen API Başvurusu)
description: Put işlevi, adlandırılmış bir özelliği için yeni bir değer atar.
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
ms.openlocfilehash: 1ec8fe889885b555cbf9a95cd34b7330efff27f2
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43460991"
---
# <a name="put-function"></a><span data-ttu-id="bc3b6-103">Put işlevi</span><span class="sxs-lookup"><span data-stu-id="bc3b6-103">Put function</span></span>
<span data-ttu-id="bc3b6-104">Adlandırılmış bir özelliği, yeni değere ayarlar.</span><span class="sxs-lookup"><span data-stu-id="bc3b6-104">Sets a named property to a new value.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="bc3b6-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bc3b6-105">Syntax</span></span>  
  
```  
HRESULT Put (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszName,
   [in] LONG              lFlags,
   [in] VARIANT*          pVal,
   [in] CIMTYPE           vtType
); 
```  

## <a name="parameters"></a><span data-ttu-id="bc3b6-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bc3b6-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="bc3b6-107">[in] Bu parametre kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="bc3b6-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="bc3b6-108">[in] Bir işaretçi bir [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneği.</span><span class="sxs-lookup"><span data-stu-id="bc3b6-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszName`  
<span data-ttu-id="bc3b6-109">[in] Özelliğin adı.</span><span class="sxs-lookup"><span data-stu-id="bc3b6-109">[in] The name of the property.</span></span> <span data-ttu-id="bc3b6-110">Bu parametre olamaz `null`.</span><span class="sxs-lookup"><span data-stu-id="bc3b6-110">This parameter cannot be `null`.</span></span>

`lFlags`  
<span data-ttu-id="bc3b6-111">[in] Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="bc3b6-111">[in] Reserved.</span></span> <span data-ttu-id="bc3b6-112">Bu parametre 0 olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bc3b6-112">This parameter must be 0.</span></span>

`pVal`   
<span data-ttu-id="bc3b6-113">[in] Geçerli bir işaretçi `VARIANT` , yeni özellik değeri olur.</span><span class="sxs-lookup"><span data-stu-id="bc3b6-113">[in] A pointer to a valid `VARIANT` that becomes the new property value.</span></span> <span data-ttu-id="bc3b6-114">Varsa `pVal` olan `null` veya işaret eden bir `VARIANT` türü `VT_NULL`, özelliği `null`.</span><span class="sxs-lookup"><span data-stu-id="bc3b6-114">If `pVal` is `null` or points to a `VARIANT` of type `VT_NULL`, the property is set to `null`.</span></span> 

`vtType`  
<span data-ttu-id="bc3b6-115">[in] Türünü `VARIANT` işaret ettiği `pVal`.</span><span class="sxs-lookup"><span data-stu-id="bc3b6-115">[in] The type of `VARIANT` pointed to by `pVal`.</span></span> <span data-ttu-id="bc3b6-116">Bkz: [açıklamalar](#remarks) bölümünde daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="bc3b6-116">See the [Remarks](#remarks) section for more information.</span></span>
 

## <a name="return-value"></a><span data-ttu-id="bc3b6-117">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="bc3b6-117">Return value</span></span>

<span data-ttu-id="bc3b6-118">Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üst bilgi dosyası veya tanımlayabilirsiniz bunları sabitleri kodunuzda:</span><span class="sxs-lookup"><span data-stu-id="bc3b6-118">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="bc3b6-119">Sabit</span><span class="sxs-lookup"><span data-stu-id="bc3b6-119">Constant</span></span>  |<span data-ttu-id="bc3b6-120">Değer</span><span class="sxs-lookup"><span data-stu-id="bc3b6-120">Value</span></span>  |<span data-ttu-id="bc3b6-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bc3b6-121">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="bc3b6-122">0x80041001</span><span class="sxs-lookup"><span data-stu-id="bc3b6-122">0x80041001</span></span> | <span data-ttu-id="bc3b6-123">Genel bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="bc3b6-123">There has been a general failure.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="bc3b6-124">0x80041008</span><span class="sxs-lookup"><span data-stu-id="bc3b6-124">0x80041008</span></span> | <span data-ttu-id="bc3b6-125">Bir veya daha fazla parametre geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="bc3b6-125">One or more parameters are not valid.</span></span> |
|`WBEM_E_INVALID_PROPERTY_TYPE` | <span data-ttu-id="bc3b6-126">0x8004102a</span><span class="sxs-lookup"><span data-stu-id="bc3b6-126">0x8004102a</span></span> | <span data-ttu-id="bc3b6-127">Özellik türü tanınmıyor.</span><span class="sxs-lookup"><span data-stu-id="bc3b6-127">The property type is not recognized.</span></span> <span data-ttu-id="bc3b6-128">Bu değer, sınıf zaten varsa, sınıf örnekleri oluşturulurken döndürülür.</span><span class="sxs-lookup"><span data-stu-id="bc3b6-128">This value is returned when creating class instances if the class already exists.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="bc3b6-129">0x80041006</span><span class="sxs-lookup"><span data-stu-id="bc3b6-129">0x80041006</span></span> | <span data-ttu-id="bc3b6-130">İşlemi tamamlamak yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="bc3b6-130">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_TYPE_MISMATCH` | <span data-ttu-id="bc3b6-131">0x80041005</span><span class="sxs-lookup"><span data-stu-id="bc3b6-131">0x80041005</span></span> | <span data-ttu-id="bc3b6-132">İçin örnek: gösterir `pVal` işaret eden bir `VARIANT` özelliği için yanlış türde.</span><span class="sxs-lookup"><span data-stu-id="bc3b6-132">For instances: Indicates that `pVal` points to a `VARIANT` of an incorrect type for the property.</span></span> <br/> <span data-ttu-id="bc3b6-133">Sınıf tanımları için: özellik üst sınıfta zaten mevcut ve yeni bir COM tür eski bir COM türünden farklıdır.</span><span class="sxs-lookup"><span data-stu-id="bc3b6-133">For class definitions: The property already exists in the parent class, and the new COM type is different from the old COM type.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="bc3b6-134">0</span><span class="sxs-lookup"><span data-stu-id="bc3b6-134">0</span></span> | <span data-ttu-id="bc3b6-135">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="bc3b6-135">The function call was successful.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="bc3b6-136">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bc3b6-136">Remarks</span></span>

<span data-ttu-id="bc3b6-137">Bu işlev bir çağrı sarılır [IWbemClassObject::Put](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-put) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="bc3b6-137">This function wraps a call to the [IWbemClassObject::Put](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-put) method.</span></span>

<span data-ttu-id="bc3b6-138">Bu işlev her zaman geçerli özellik değeri ile yeni bir üzerine yazar.</span><span class="sxs-lookup"><span data-stu-id="bc3b6-138">This function always overwrites the current property value with a new one.</span></span> <span data-ttu-id="bc3b6-139">Varsa [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) işaret eden bir sınıf tanımı için `Put` oluşturur veya özellik değerini güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="bc3b6-139">If the [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) points to a class definition, `Put` creates or updates the property value.</span></span> <span data-ttu-id="bc3b6-140">Zaman [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) işaret eden bir CIM örneğine `Put` özellik değeri yalnızca; güncelleştirir `Put` bir özellik değeri oluşturulamıyor.</span><span class="sxs-lookup"><span data-stu-id="bc3b6-140">When [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) points to a CIM instance, `Put` updates the property value only; `Put` cannot create a property value.</span></span>

<span data-ttu-id="bc3b6-141">`__CLASS` Sistem özelliği olduğunda yalnızca yazılabilir sınıfı oluşturma sırasında boş bırakılamaz.</span><span class="sxs-lookup"><span data-stu-id="bc3b6-141">The `__CLASS` system property is only writable during class creation, when it may not be left blank.</span></span> <span data-ttu-id="bc3b6-142">Diğer tüm sistem özellikleri salt okunurdur.</span><span class="sxs-lookup"><span data-stu-id="bc3b6-142">All other system properties are read-only.</span></span>

<span data-ttu-id="bc3b6-143">Kullanıcı özellikleri ile başlayamaz veya bitemez bir alt çizgi ("_") adları oluşturulamıyor.</span><span class="sxs-lookup"><span data-stu-id="bc3b6-143">A user cannot create properties with names that begin or end with an underscore ("_").</span></span> <span data-ttu-id="bc3b6-144">Bu, sistem sınıfları ve özellikleri için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="bc3b6-144">This is reserved for system classes and properties.</span></span>

<span data-ttu-id="bc3b6-145">Özelliği ayarlarsanız `Put` üst sınıfta exists işlevi, özelliğinin varsayılan değeri üst sınıfı türü Özellik türüyle eşleşmiyor sürece değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="bc3b6-145">If the property set by the `Put` function exists in the parent class, the default value of the property is changed unless the property type does not match the parent class type.</span></span> <span data-ttu-id="bc3b6-146">Özelliği yok ve tür uyuşmazlığı değil, ceated özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="bc3b6-146">If the property does not exist and it is not a type mismatch, the property is ceated.</span></span>

<span data-ttu-id="bc3b6-147">Kullanım `vtType` yalnızca bir CIM sınıf tanımına yeni özellikler oluştururken, parametre ve `pVal` olduğu `null` veya işaret bir `VARIANT` türü `VT_NULL`.</span><span class="sxs-lookup"><span data-stu-id="bc3b6-147">Use the `vtType` parameter only when creating new properties in a CIM class definition and `pVal` is `null` or points to a `VARIANT` of type `VT_NULL`.</span></span> <span data-ttu-id="bc3b6-148">Bu durumda, `vType` parametresi, özelliğin CIM türü belirtir.</span><span class="sxs-lookup"><span data-stu-id="bc3b6-148">In this case, the `vType` parameter specifies the CIM type of the property.</span></span> <span data-ttu-id="bc3b6-149">Diğer her durumda `vtType` 0 olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bc3b6-149">In every other case, `vtType` must be 0.</span></span> <span data-ttu-id="bc3b6-150">`vtType` temel alınan nesne örneği ise 0 olmalıdır (bile `Val` olan `null`) özelliğinin türü sabittir ve değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="bc3b6-150">`vtType` must also be 0 if the underlying object is an instance (even if `Val` is `null`) because the type of the property is fixed and cannot be changed.</span></span>   

## <a name="example"></a><span data-ttu-id="bc3b6-151">Örnek</span><span class="sxs-lookup"><span data-stu-id="bc3b6-151">Example</span></span>

<span data-ttu-id="bc3b6-152">Bir örnek için bkz. [IWbemClassObject::Put](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-put) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="bc3b6-152">For an example, see the [IWbemClassObject::Put](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-put) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="bc3b6-153">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bc3b6-153">Requirements</span></span>  
 <span data-ttu-id="bc3b6-154">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bc3b6-154">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc3b6-155">**Başlık:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="bc3b6-155">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="bc3b6-156">**.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="bc3b6-156">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc3b6-157">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bc3b6-157">See also</span></span>  
[<span data-ttu-id="bc3b6-158">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="bc3b6-158">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
