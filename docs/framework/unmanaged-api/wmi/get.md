---
title: Get işlevi (yönetilmeyen API Başvurusu)
description: Get işlevi, belirtilen özellik değerini alır.
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
ms.openlocfilehash: cb7475623961fe2ee5fc821c5f237f0a2acfae1a
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43507668"
---
# <a name="get-function"></a><span data-ttu-id="4b381-103">Get işlevi</span><span class="sxs-lookup"><span data-stu-id="4b381-103">Get function</span></span>
<span data-ttu-id="4b381-104">Varsa belirtilen özelliğin değerini alır.</span><span class="sxs-lookup"><span data-stu-id="4b381-104">Retrieves the specified property value if it exists.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="4b381-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4b381-105">Syntax</span></span>  
  
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

## <a name="parameters"></a><span data-ttu-id="4b381-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4b381-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="4b381-107">[in] Bu parametre kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="4b381-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="4b381-108">[in] Bir işaretçi bir [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneği.</span><span class="sxs-lookup"><span data-stu-id="4b381-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszName`  
<span data-ttu-id="4b381-109">[in] Özelliğin adı.</span><span class="sxs-lookup"><span data-stu-id="4b381-109">[in] The name of the property.</span></span>

<span data-ttu-id="4b381-110">`lFlags` [in] Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="4b381-110">`lFlags` [in] Reserved.</span></span> <span data-ttu-id="4b381-111">Bu parametre 0 olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4b381-111">This parameter must be 0.</span></span>

<span data-ttu-id="4b381-112">`pVal` [out] İşlev başarıyla döndürürse, değerini içeren `wszName` özelliği.</span><span class="sxs-lookup"><span data-stu-id="4b381-112">`pVal` [out] If the function returns successfully, contains the value of the `wszName` property.</span></span> <span data-ttu-id="4b381-113">`pval` Bağımsız değişkeni doğru tür ve niteleyici değeri atanır.</span><span class="sxs-lookup"><span data-stu-id="4b381-113">The `pval` argument is assigned the correct type and value for the qualifier.</span></span>

<span data-ttu-id="4b381-114">`pvtType` [out] İşlev başarıyla döndürürse, içeren bir [CIM türü sabiti](/windows/desktop/api/wbemcli/ne-wbemcli-tag_cimtype_enumeration) özellik türü gösterir.</span><span class="sxs-lookup"><span data-stu-id="4b381-114">`pvtType` [out] If the function returns successfully, contains a [CIM-type constant](/windows/desktop/api/wbemcli/ne-wbemcli-tag_cimtype_enumeration) that indicates the property type.</span></span> <span data-ttu-id="4b381-115">Değeri de olabilir `null`.</span><span class="sxs-lookup"><span data-stu-id="4b381-115">Its value can also be `null`.</span></span> 

<span data-ttu-id="4b381-116">`plFlavor` [out] İşlev başarıyla döndürürse, özellik kaynağı hakkındaki bilgileri alır.</span><span class="sxs-lookup"><span data-stu-id="4b381-116">`plFlavor` [out] If the function returns successfully, receives information about the origin of the property.</span></span> <span data-ttu-id="4b381-117">Değeri olabilir `null`, veya tanımlanan WBEM_FLAVOR_TYPE sabitlerden biri *WbemCli.h* üst bilgi dosyası:</span><span class="sxs-lookup"><span data-stu-id="4b381-117">Its value can be `null`, or one of the following WBEM_FLAVOR_TYPE constants defined in the *WbemCli.h* header file:</span></span> 

|<span data-ttu-id="4b381-118">Sabit</span><span class="sxs-lookup"><span data-stu-id="4b381-118">Constant</span></span>  |<span data-ttu-id="4b381-119">Değer</span><span class="sxs-lookup"><span data-stu-id="4b381-119">Value</span></span>  |<span data-ttu-id="4b381-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4b381-120">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAVOR_ORIGIN_SYSTEM` | <span data-ttu-id="4b381-121">0x40</span><span class="sxs-lookup"><span data-stu-id="4b381-121">0x40</span></span> | <span data-ttu-id="4b381-122">Standart sistem özelliği özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="4b381-122">The property is a standard system property.</span></span> |
| `WBEM_FLAVOR_ORIGIN_PROPAGATED` | <span data-ttu-id="4b381-123">0x20</span><span class="sxs-lookup"><span data-stu-id="4b381-123">0x20</span></span> | <span data-ttu-id="4b381-124">Bir sınıf için: özellik üst sınıftan devralınır.</span><span class="sxs-lookup"><span data-stu-id="4b381-124">For a class: The property is inherited from the parent class.</span></span> </br> <span data-ttu-id="4b381-125">Bir örneği için: özellik üst sınıftan devralındı sırada örneği tarafından değiştirilmedi.</span><span class="sxs-lookup"><span data-stu-id="4b381-125">For an instance: The property, while inherited from the parent class, has not been modified by the instance.</span></span>  |
| `WBEM_FLAVOR_ORIGIN_LOCAL` | <span data-ttu-id="4b381-126">0</span><span class="sxs-lookup"><span data-stu-id="4b381-126">0</span></span> | <span data-ttu-id="4b381-127">Bir sınıf için: özelliği türetilmiş bir sınıfa aittir.</span><span class="sxs-lookup"><span data-stu-id="4b381-127">For a class: The property belongs to the derived class.</span></span> </br> <span data-ttu-id="4b381-128">Bir örneği için: özelliğin bir örneği tarafından; değiştirilir diğer bir deyişle, bir değer sağlanmamış veya niteleyicisi eklenemez veya değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="4b381-128">For an instance: The property is modified by the instance; that is, a value was supplied, or a qualifier was added or modified.</span></span> |

## <a name="return-value"></a><span data-ttu-id="4b381-129">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="4b381-129">Return value</span></span>

<span data-ttu-id="4b381-130">Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üst bilgi dosyası veya tanımlayabilirsiniz bunları sabitleri kodunuzda:</span><span class="sxs-lookup"><span data-stu-id="4b381-130">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="4b381-131">Sabit</span><span class="sxs-lookup"><span data-stu-id="4b381-131">Constant</span></span>  |<span data-ttu-id="4b381-132">Değer</span><span class="sxs-lookup"><span data-stu-id="4b381-132">Value</span></span>  |<span data-ttu-id="4b381-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4b381-133">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="4b381-134">0x80041001</span><span class="sxs-lookup"><span data-stu-id="4b381-134">0x80041001</span></span> | <span data-ttu-id="4b381-135">Genel bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="4b381-135">There has been a general failure.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="4b381-136">0x80041008</span><span class="sxs-lookup"><span data-stu-id="4b381-136">0x80041008</span></span> | <span data-ttu-id="4b381-137">Bir veya daha fazla parametre geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="4b381-137">One or more parameters are not valid.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="4b381-138">0x80041002</span><span class="sxs-lookup"><span data-stu-id="4b381-138">0x80041002</span></span> | <span data-ttu-id="4b381-139">Belirtilen özellik bulunamadı.</span><span class="sxs-lookup"><span data-stu-id="4b381-139">The specified property was not found.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="4b381-140">0x80041006</span><span class="sxs-lookup"><span data-stu-id="4b381-140">0x80041006</span></span> | <span data-ttu-id="4b381-141">İşlemi tamamlamak yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="4b381-141">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="4b381-142">0</span><span class="sxs-lookup"><span data-stu-id="4b381-142">0</span></span> | <span data-ttu-id="4b381-143">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="4b381-143">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="4b381-144">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4b381-144">Remarks</span></span>

<span data-ttu-id="4b381-145">Bu işlev bir çağrı sarılır [IWbemClassObject::Get](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-get) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="4b381-145">This function wraps a call to the [IWbemClassObject::Get](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-get) method.</span></span>

<span data-ttu-id="4b381-146">`Get` İşlev Ayrıca Sistem özellikleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="4b381-146">The `Get` function can also return system properties.</span></span>

<span data-ttu-id="4b381-147">`pVal` Bağımsız değişkeni doğru tür ve değer niteleyicisi ve COM atandığı [VariantInit](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-variantinit) işlevi</span><span class="sxs-lookup"><span data-stu-id="4b381-147">The `pVal` argument is assigned the correct type and value for the qualifier and the COM [VariantInit](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-variantinit) function</span></span>

## <a name="requirements"></a><span data-ttu-id="4b381-148">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4b381-148">Requirements</span></span>  
 <span data-ttu-id="4b381-149">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4b381-149">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b381-150">**Başlık:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="4b381-150">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="4b381-151">**.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="4b381-151">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b381-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4b381-152">See also</span></span>  
[<span data-ttu-id="4b381-153">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="4b381-153">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
