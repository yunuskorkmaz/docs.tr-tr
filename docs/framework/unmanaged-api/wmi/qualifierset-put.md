---
title: QualifierSet_Put işlevi (yönetilmeyen API Başvurusu)
description: QualifierSet_Put işlevi adlandırılmış niteleyici ve değerini yazar.
ms.date: 11/06/2017
api_name:
- QualifierSet_Put
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_Put
helpviewer_keywords:
- QualifierSet_Put function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7ccb0aef0e998ffccd7526f9f0554bceb892001b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33462195"
---
# <a name="qualifiersetput-function"></a><span data-ttu-id="1c2bb-103">QualifierSet_Put işlevi</span><span class="sxs-lookup"><span data-stu-id="1c2bb-103">QualifierSet_Put function</span></span>
<span data-ttu-id="1c2bb-104">Değeri ve adlandırılmış niteleyicisi yazar.</span><span class="sxs-lookup"><span data-stu-id="1c2bb-104">Writes the named qualifier and value.</span></span> <span data-ttu-id="1c2bb-105">Yeni niteleyici aynı ada sahip önceki değerin üzerine yazar.</span><span class="sxs-lookup"><span data-stu-id="1c2bb-105">The new qualifier overwrites the previous value of the same name.</span></span> <span data-ttu-id="1c2bb-106">Niteleyici mevcut değilse oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="1c2bb-106">If the qualifier does not exist, it is created.</span></span> 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="1c2bb-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1c2bb-107">Syntax</span></span>  
  
```  
HRESULT QualifierSet_Put (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LPCWSTR              wszName,
   [in] VARIANT*             pVal,
   [in] LONG                 lFlavor
); 
```  

## <a name="parameters"></a><span data-ttu-id="1c2bb-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1c2bb-108">Parameters</span></span>

`vFunc`   
<span data-ttu-id="1c2bb-109">[in] Bu parametre kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="1c2bb-109">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="1c2bb-110">[in] Bir işaretçi bir [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) örneği.</span><span class="sxs-lookup"><span data-stu-id="1c2bb-110">[in] A pointer to an [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) instance.</span></span>

`wszName`   
<span data-ttu-id="1c2bb-111">[in] Yazılacak Niteleyici adı.</span><span class="sxs-lookup"><span data-stu-id="1c2bb-111">[in] The name of the qualifier to write.</span></span>

<span data-ttu-id="1c2bb-112">`pVal` [in] Geçerli bir işaretçi `VARIANT` niteleyicisi yazmak için içerir.</span><span class="sxs-lookup"><span data-stu-id="1c2bb-112">`pVal` [in] A pointer to a valid `VARIANT` that contains the qualifier to write.</span></span> <span data-ttu-id="1c2bb-113">Bu parametre olamaz `null`.</span><span class="sxs-lookup"><span data-stu-id="1c2bb-113">This parameter cannot be `null`.</span></span>

<span data-ttu-id="1c2bb-114">`lFlavor` [in] Bu Niteleyici için istenen niteleyici özellikleri tanımlar sabitlerden biri.</span><span class="sxs-lookup"><span data-stu-id="1c2bb-114">`lFlavor` [in] One of the following constants that defines the desired qualifier flavors for this qualifier.</span></span> <span data-ttu-id="1c2bb-115">Varsayılan değer `WBEM_FLAVOR_OVERRIDABLE` (0).</span><span class="sxs-lookup"><span data-stu-id="1c2bb-115">The default value is `WBEM_FLAVOR_OVERRIDABLE` (0).</span></span>

|<span data-ttu-id="1c2bb-116">Sabit</span><span class="sxs-lookup"><span data-stu-id="1c2bb-116">Constant</span></span>  |<span data-ttu-id="1c2bb-117">Değer</span><span class="sxs-lookup"><span data-stu-id="1c2bb-117">Value</span></span>  |<span data-ttu-id="1c2bb-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1c2bb-118">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAVOR_OVERRIDABLE` | <span data-ttu-id="1c2bb-119">0</span><span class="sxs-lookup"><span data-stu-id="1c2bb-119">0</span></span> | <span data-ttu-id="1c2bb-120">Bir türetilmiş sınıf veya örnek niteleyici geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="1c2bb-120">The qualifier can be overridden in a derived class or instance.</span></span> <span data-ttu-id="1c2bb-121">**Varsayılan değer budur.**</span><span class="sxs-lookup"><span data-stu-id="1c2bb-121">**This is the default value.**</span></span> |
| `WBEM_FLAVOR_FLAG_PROPAGATE_TO_INSTANCE` | <span data-ttu-id="1c2bb-122">1.</span><span class="sxs-lookup"><span data-stu-id="1c2bb-122">1</span></span> | <span data-ttu-id="1c2bb-123">Niteleyici örneklerine yayılır.</span><span class="sxs-lookup"><span data-stu-id="1c2bb-123">The qualifier is propagated to instances.</span></span> |
| `WBEM_FLAVOR_GLAG_PROPAGATE_TO_DERIVED_CLASS` | <span data-ttu-id="1c2bb-124">2</span><span class="sxs-lookup"><span data-stu-id="1c2bb-124">2</span></span> | <span data-ttu-id="1c2bb-125">Niteleyici için türetilen sınıflar yayılır.</span><span class="sxs-lookup"><span data-stu-id="1c2bb-125">The qualifier is propagated to derived classes.</span></span> |
| <span data-ttu-id="1c2bb-126">' WBEM_FLAVOR_NOT_OVERRIDABLE</span><span class="sxs-lookup"><span data-stu-id="1c2bb-126">\`WBEM_FLAVOR_NOT_OVERRIDABLE</span></span> | <span data-ttu-id="1c2bb-127">0x10</span><span class="sxs-lookup"><span data-stu-id="1c2bb-127">0x10</span></span> | <span data-ttu-id="1c2bb-128">Niteleyici bir türetilmiş sınıf veya örnek değiştirilemiyor.</span><span class="sxs-lookup"><span data-stu-id="1c2bb-128">The qualifier cannot be overridden in a derived class or instance.</span></span> |
| <span data-ttu-id="1c2bb-129">' WBEM_FLAVOR_AMENDED</span><span class="sxs-lookup"><span data-stu-id="1c2bb-129">\`WBEM_FLAVOR_AMENDED</span></span> | <span data-ttu-id="1c2bb-130">0x80</span><span class="sxs-lookup"><span data-stu-id="1c2bb-130">0x80</span></span> | <span data-ttu-id="1c2bb-131">Niteleyici yerelleştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="1c2bb-131">The qualifier is localized.</span></span> |

## <a name="return-value"></a><span data-ttu-id="1c2bb-132">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="1c2bb-132">Return value</span></span>

<span data-ttu-id="1c2bb-133">Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üstbilgi dosyası, veya tanımlayabilirsiniz bunları sabitleri kodunuzda:</span><span class="sxs-lookup"><span data-stu-id="1c2bb-133">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="1c2bb-134">Sabit</span><span class="sxs-lookup"><span data-stu-id="1c2bb-134">Constant</span></span>  |<span data-ttu-id="1c2bb-135">Değer</span><span class="sxs-lookup"><span data-stu-id="1c2bb-135">Value</span></span>  |<span data-ttu-id="1c2bb-136">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1c2bb-136">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_CANNOT_BE_KEY` | <span data-ttu-id="1c2bb-137">0x8004101f</span><span class="sxs-lookup"><span data-stu-id="1c2bb-137">0x8004101f</span></span> | <span data-ttu-id="1c2bb-138">Belirtmek için geçersiz bir deneme vardı **anahtar** niteleyici bir özellikte bir anahtar olamaz.</span><span class="sxs-lookup"><span data-stu-id="1c2bb-138">There was an illegal attempt to specify the **Key** qualifier on a property that cannot be a key.</span></span> <span data-ttu-id="1c2bb-139">Anahtarları belirtilen om c; bir nesne için ass tanımı ve örnek bazında değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="1c2bb-139">The keys are specified om tje c;ass definition for an object and cannot be altered on a per-instance basis.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="1c2bb-140">0x80041008</span><span class="sxs-lookup"><span data-stu-id="1c2bb-140">0x80041008</span></span> | <span data-ttu-id="1c2bb-141">Parametre geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="1c2bb-141">A parameter is not valid.</span></span> |
| `WBEM_E_INVALID_QUALIFIER_TYPE` | <span data-ttu-id="1c2bb-142">0x80041029</span><span class="sxs-lookup"><span data-stu-id="1c2bb-142">0x80041029</span></span> | <span data-ttu-id="1c2bb-143">`pVal` Parametresi geçerli niteleyici türü değil.</span><span class="sxs-lookup"><span data-stu-id="1c2bb-143">The `pVal` parameter is not of a legal qualifier type.</span></span> |
| `WBEM_E_OVERRIDE_NOT_ALLOWED` | <span data-ttu-id="1c2bb-144">0x8004101a</span><span class="sxs-lookup"><span data-stu-id="1c2bb-144">0x8004101a</span></span> | <span data-ttu-id="1c2bb-145">Çağrı mümkün değildir `QualifierSet_Put` sahip olan nesne izin vermiyor çünkü niteleyici yöntemini geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="1c2bb-145">It is not possible to call the `QualifierSet_Put` method on the qualifier because the owning object does not permit overrides.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="1c2bb-146">0</span><span class="sxs-lookup"><span data-stu-id="1c2bb-146">0</span></span> | <span data-ttu-id="1c2bb-147">İşlev çağrısı başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="1c2bb-147">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="1c2bb-148">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1c2bb-148">Remarks</span></span>

<span data-ttu-id="1c2bb-149">Bu işlev çağrısı sarmalar [IWbemQualifierSet::Put](https://msdn.microsoft.com/library/aa391871(v=vs.85).aspx) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="1c2bb-149">This function wraps a call to the [IWbemQualifierSet::Put](https://msdn.microsoft.com/library/aa391871(v=vs.85).aspx) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="1c2bb-150">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1c2bb-150">Requirements</span></span>  
 <span data-ttu-id="1c2bb-151">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1c2bb-151">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c2bb-152">**Başlık:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="1c2bb-152">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="1c2bb-153">**.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="1c2bb-153">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c2bb-154">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1c2bb-154">See also</span></span>  
[<span data-ttu-id="1c2bb-155">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="1c2bb-155">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
