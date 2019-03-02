---
title: QualifierSet_Put işlevi (yönetilmeyen API Başvurusu)
description: Adlandırılmış niteleyicisi ve değerini QualifierSet_Put işlevi yazar.
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
ms.openlocfilehash: bf3d422bbcec2754601f6dd07d7b45bab2a716e3
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57201189"
---
# <a name="qualifiersetput-function"></a><span data-ttu-id="2562f-103">QualifierSet_Put işlevi</span><span class="sxs-lookup"><span data-stu-id="2562f-103">QualifierSet_Put function</span></span>
<span data-ttu-id="2562f-104">Değer ve adlandırılmış niteleyicisi yazar.</span><span class="sxs-lookup"><span data-stu-id="2562f-104">Writes the named qualifier and value.</span></span> <span data-ttu-id="2562f-105">Yeni niteleyici aynı adlı önceki değerin üzerine yazar.</span><span class="sxs-lookup"><span data-stu-id="2562f-105">The new qualifier overwrites the previous value of the same name.</span></span> <span data-ttu-id="2562f-106">Niteleyici mevcut değilse oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="2562f-106">If the qualifier does not exist, it is created.</span></span> 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="2562f-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2562f-107">Syntax</span></span>  
  
```  
HRESULT QualifierSet_Put (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LPCWSTR              wszName,
   [in] VARIANT*             pVal,
   [in] LONG                 lFlavor
); 
```  

## <a name="parameters"></a><span data-ttu-id="2562f-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2562f-108">Parameters</span></span>

`vFunc`   
<span data-ttu-id="2562f-109">[in] Bu parametre kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="2562f-109">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="2562f-110">[in] Bir işaretçi bir [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) örneği.</span><span class="sxs-lookup"><span data-stu-id="2562f-110">[in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

`wszName`   
<span data-ttu-id="2562f-111">[in] Yazılacak niteleyicisi adı.</span><span class="sxs-lookup"><span data-stu-id="2562f-111">[in] The name of the qualifier to write.</span></span>

<span data-ttu-id="2562f-112">`pVal` [in] Geçerli bir işaretçi `VARIANT` yazılacak niteleyicisi içeriyor.</span><span class="sxs-lookup"><span data-stu-id="2562f-112">`pVal` [in] A pointer to a valid `VARIANT` that contains the qualifier to write.</span></span> <span data-ttu-id="2562f-113">Bu parametre olamaz `null`.</span><span class="sxs-lookup"><span data-stu-id="2562f-113">This parameter cannot be `null`.</span></span>

<span data-ttu-id="2562f-114">`lFlavor` [in] Bu niteleyici için'istenen niteleyici özelliği tanımlayan sabitlerden biri.</span><span class="sxs-lookup"><span data-stu-id="2562f-114">`lFlavor` [in] One of the following constants that defines the desired qualifier flavors for this qualifier.</span></span> <span data-ttu-id="2562f-115">Varsayılan değer `WBEM_FLAVOR_OVERRIDABLE` (0).</span><span class="sxs-lookup"><span data-stu-id="2562f-115">The default value is `WBEM_FLAVOR_OVERRIDABLE` (0).</span></span>

|<span data-ttu-id="2562f-116">Sabit</span><span class="sxs-lookup"><span data-stu-id="2562f-116">Constant</span></span>  |<span data-ttu-id="2562f-117">Değer</span><span class="sxs-lookup"><span data-stu-id="2562f-117">Value</span></span>  |<span data-ttu-id="2562f-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2562f-118">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAVOR_OVERRIDABLE` | <span data-ttu-id="2562f-119">0</span><span class="sxs-lookup"><span data-stu-id="2562f-119">0</span></span> | <span data-ttu-id="2562f-120">Niteleyici bir türetilmiş sınıf veya örnek geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="2562f-120">The qualifier can be overridden in a derived class or instance.</span></span> <span data-ttu-id="2562f-121">**Varsayılan değer budur.**</span><span class="sxs-lookup"><span data-stu-id="2562f-121">**This is the default value.**</span></span> |
| `WBEM_FLAVOR_FLAG_PROPAGATE_TO_INSTANCE` | <span data-ttu-id="2562f-122">1.</span><span class="sxs-lookup"><span data-stu-id="2562f-122">1</span></span> | <span data-ttu-id="2562f-123">Niteleyici örneklere yayılır.</span><span class="sxs-lookup"><span data-stu-id="2562f-123">The qualifier is propagated to instances.</span></span> |
| `WBEM_FLAVOR_GLAG_PROPAGATE_TO_DERIVED_CLASS` | <span data-ttu-id="2562f-124">2</span><span class="sxs-lookup"><span data-stu-id="2562f-124">2</span></span> | <span data-ttu-id="2562f-125">Türetilmiş sınıflara niteleyici yayılır.</span><span class="sxs-lookup"><span data-stu-id="2562f-125">The qualifier is propagated to derived classes.</span></span> |
| `WBEM_FLAVOR_NOT_OVERRIDABLE` | <span data-ttu-id="2562f-126">0x10</span><span class="sxs-lookup"><span data-stu-id="2562f-126">0x10</span></span> | <span data-ttu-id="2562f-127">Niteleyici bir türetilmiş sınıf veya örnek geçersiz kılınamaz.</span><span class="sxs-lookup"><span data-stu-id="2562f-127">The qualifier cannot be overridden in a derived class or instance.</span></span> |
| `WBEM_FLAVOR_AMENDED` | <span data-ttu-id="2562f-128">0x80</span><span class="sxs-lookup"><span data-stu-id="2562f-128">0x80</span></span> | <span data-ttu-id="2562f-129">Niteleyici yerelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="2562f-129">The qualifier is localized.</span></span> |

## <a name="return-value"></a><span data-ttu-id="2562f-130">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="2562f-130">Return value</span></span>

<span data-ttu-id="2562f-131">Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üst bilgi dosyası veya tanımlayabilirsiniz bunları sabitleri kodunuzda:</span><span class="sxs-lookup"><span data-stu-id="2562f-131">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="2562f-132">Sabit</span><span class="sxs-lookup"><span data-stu-id="2562f-132">Constant</span></span>  |<span data-ttu-id="2562f-133">Değer</span><span class="sxs-lookup"><span data-stu-id="2562f-133">Value</span></span>  |<span data-ttu-id="2562f-134">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2562f-134">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_CANNOT_BE_KEY` | <span data-ttu-id="2562f-135">0x8004101f</span><span class="sxs-lookup"><span data-stu-id="2562f-135">0x8004101f</span></span> | <span data-ttu-id="2562f-136">Belirtmek için geçersiz bir girişimde bulunuldu oluştu **anahtar** niteleyici bir özellikte bir anahtar olamaz.</span><span class="sxs-lookup"><span data-stu-id="2562f-136">There was an illegal attempt to specify the **Key** qualifier on a property that cannot be a key.</span></span> <span data-ttu-id="2562f-137">Anahtarları belirtilen om c; bir nesne için sınıf tanımı ve örnek başına temelinde değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="2562f-137">The keys are specified om tje c;ass definition for an object and cannot be altered on a per-instance basis.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="2562f-138">0x80041008</span><span class="sxs-lookup"><span data-stu-id="2562f-138">0x80041008</span></span> | <span data-ttu-id="2562f-139">Bir parametre geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="2562f-139">A parameter is not valid.</span></span> |
| `WBEM_E_INVALID_QUALIFIER_TYPE` | <span data-ttu-id="2562f-140">0x80041029</span><span class="sxs-lookup"><span data-stu-id="2562f-140">0x80041029</span></span> | <span data-ttu-id="2562f-141">`pVal` Parametresi geçerli bir niteleyici türü değil.</span><span class="sxs-lookup"><span data-stu-id="2562f-141">The `pVal` parameter is not of a legal qualifier type.</span></span> |
| `WBEM_E_OVERRIDE_NOT_ALLOWED` | <span data-ttu-id="2562f-142">0x8004101a</span><span class="sxs-lookup"><span data-stu-id="2562f-142">0x8004101a</span></span> | <span data-ttu-id="2562f-143">Çağrı mümkün değil `QualifierSet_Put` edinilen nesneyi izin vermediğinden niteleyici yöntemini geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="2562f-143">It is not possible to call the `QualifierSet_Put` method on the qualifier because the owning object does not permit overrides.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="2562f-144">0</span><span class="sxs-lookup"><span data-stu-id="2562f-144">0</span></span> | <span data-ttu-id="2562f-145">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="2562f-145">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="2562f-146">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2562f-146">Remarks</span></span>

<span data-ttu-id="2562f-147">Bu işlev bir çağrı sarılır [IWbemQualifierSet::Put](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-put) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="2562f-147">This function wraps a call to the [IWbemQualifierSet::Put](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-put) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="2562f-148">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2562f-148">Requirements</span></span>  
 <span data-ttu-id="2562f-149">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2562f-149">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2562f-150">**Üst bilgi:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="2562f-150">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="2562f-151">**.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="2562f-151">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2562f-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2562f-152">See also</span></span>
- [<span data-ttu-id="2562f-153">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="2562f-153">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
