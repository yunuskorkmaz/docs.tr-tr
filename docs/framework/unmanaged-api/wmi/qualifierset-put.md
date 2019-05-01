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
ms.openlocfilehash: 0e42cf3440bef030f5c7bec71ed1b4b875b79a61
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62000278"
---
# <a name="qualifiersetput-function"></a><span data-ttu-id="103b1-103">QualifierSet_Put işlevi</span><span class="sxs-lookup"><span data-stu-id="103b1-103">QualifierSet_Put function</span></span>

<span data-ttu-id="103b1-104">Değer ve adlandırılmış niteleyicisi yazar.</span><span class="sxs-lookup"><span data-stu-id="103b1-104">Writes the named qualifier and value.</span></span> <span data-ttu-id="103b1-105">Yeni niteleyici aynı adlı önceki değerin üzerine yazar.</span><span class="sxs-lookup"><span data-stu-id="103b1-105">The new qualifier overwrites the previous value of the same name.</span></span> <span data-ttu-id="103b1-106">Niteleyici mevcut değilse oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="103b1-106">If the qualifier does not exist, it is created.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="103b1-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="103b1-107">Syntax</span></span>

```cpp
HRESULT QualifierSet_Put (
   [in] int                  vFunc,
   [in] IWbemQualifierSet*   ptr,
   [in] LPCWSTR              wszName,
   [in] VARIANT*             pVal,
   [in] LONG                 lFlavor
);
```

## <a name="parameters"></a><span data-ttu-id="103b1-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="103b1-108">Parameters</span></span>

`vFunc`\
<span data-ttu-id="103b1-109">[in] Bu parametre kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="103b1-109">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="103b1-110">[in] Bir işaretçi bir [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) örneği.</span><span class="sxs-lookup"><span data-stu-id="103b1-110">[in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

`wszName`\
<span data-ttu-id="103b1-111">[in] Yazılacak niteleyicisi adı.</span><span class="sxs-lookup"><span data-stu-id="103b1-111">[in] The name of the qualifier to write.</span></span>

`pVal`\
<span data-ttu-id="103b1-112">[in] Geçerli bir işaretçi `VARIANT` yazılacak niteleyicisi içeriyor.</span><span class="sxs-lookup"><span data-stu-id="103b1-112">[in] A pointer to a valid `VARIANT` that contains the qualifier to write.</span></span> <span data-ttu-id="103b1-113">Bu parametre olamaz `null`.</span><span class="sxs-lookup"><span data-stu-id="103b1-113">This parameter cannot be `null`.</span></span>

`lFlavor`\
<span data-ttu-id="103b1-114">[in] Bu niteleyici için'istenen niteleyici özelliği tanımlayan sabitlerden biri.</span><span class="sxs-lookup"><span data-stu-id="103b1-114">[in] One of the following constants that defines the desired qualifier flavors for this qualifier.</span></span> <span data-ttu-id="103b1-115">Varsayılan değer `WBEM_FLAVOR_OVERRIDABLE` (0).</span><span class="sxs-lookup"><span data-stu-id="103b1-115">The default value is `WBEM_FLAVOR_OVERRIDABLE` (0).</span></span>

|<span data-ttu-id="103b1-116">Sabit</span><span class="sxs-lookup"><span data-stu-id="103b1-116">Constant</span></span>  |<span data-ttu-id="103b1-117">Değer</span><span class="sxs-lookup"><span data-stu-id="103b1-117">Value</span></span>  |<span data-ttu-id="103b1-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="103b1-118">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAVOR_OVERRIDABLE` | <span data-ttu-id="103b1-119">0</span><span class="sxs-lookup"><span data-stu-id="103b1-119">0</span></span> | <span data-ttu-id="103b1-120">Niteleyici bir türetilmiş sınıf veya örnek geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="103b1-120">The qualifier can be overridden in a derived class or instance.</span></span> <span data-ttu-id="103b1-121">**Varsayılan değer budur.**</span><span class="sxs-lookup"><span data-stu-id="103b1-121">**This is the default value.**</span></span> |
| `WBEM_FLAVOR_FLAG_PROPAGATE_TO_INSTANCE` | <span data-ttu-id="103b1-122">1.</span><span class="sxs-lookup"><span data-stu-id="103b1-122">1</span></span> | <span data-ttu-id="103b1-123">Niteleyici örneklere yayılır.</span><span class="sxs-lookup"><span data-stu-id="103b1-123">The qualifier is propagated to instances.</span></span> |
| `WBEM_FLAVOR_FLAG_PROPAGATE_TO_DERIVED_CLASS` | <span data-ttu-id="103b1-124">2</span><span class="sxs-lookup"><span data-stu-id="103b1-124">2</span></span> | <span data-ttu-id="103b1-125">Türetilmiş sınıflara niteleyici yayılır.</span><span class="sxs-lookup"><span data-stu-id="103b1-125">The qualifier is propagated to derived classes.</span></span> |
| `WBEM_FLAVOR_NOT_OVERRIDABLE` | <span data-ttu-id="103b1-126">0x10</span><span class="sxs-lookup"><span data-stu-id="103b1-126">0x10</span></span> | <span data-ttu-id="103b1-127">Niteleyici bir türetilmiş sınıf veya örnek geçersiz kılınamaz.</span><span class="sxs-lookup"><span data-stu-id="103b1-127">The qualifier cannot be overridden in a derived class or instance.</span></span> |
| `WBEM_FLAVOR_AMENDED` | <span data-ttu-id="103b1-128">0x80</span><span class="sxs-lookup"><span data-stu-id="103b1-128">0x80</span></span> | <span data-ttu-id="103b1-129">Niteleyici yerelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="103b1-129">The qualifier is localized.</span></span> |

## <a name="return-value"></a><span data-ttu-id="103b1-130">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="103b1-130">Return value</span></span>

<span data-ttu-id="103b1-131">Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üst bilgi dosyası veya tanımlayabilirsiniz bunları sabitleri kodunuzda:</span><span class="sxs-lookup"><span data-stu-id="103b1-131">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="103b1-132">Sabit</span><span class="sxs-lookup"><span data-stu-id="103b1-132">Constant</span></span>  |<span data-ttu-id="103b1-133">Değer</span><span class="sxs-lookup"><span data-stu-id="103b1-133">Value</span></span>  |<span data-ttu-id="103b1-134">Açıklama</span><span class="sxs-lookup"><span data-stu-id="103b1-134">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_CANNOT_BE_KEY` | <span data-ttu-id="103b1-135">0x8004101f</span><span class="sxs-lookup"><span data-stu-id="103b1-135">0x8004101f</span></span> | <span data-ttu-id="103b1-136">Belirtmek için geçersiz bir girişimde bulunuldu oluştu **anahtar** niteleyici bir özellikte bir anahtar olamaz.</span><span class="sxs-lookup"><span data-stu-id="103b1-136">There was an illegal attempt to specify the **Key** qualifier on a property that cannot be a key.</span></span> <span data-ttu-id="103b1-137">Anahtarları belirtilen om c; bir nesne için sınıf tanımı ve örnek başına temelinde değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="103b1-137">The keys are specified om tje c;ass definition for an object and cannot be altered on a per-instance basis.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="103b1-138">0x80041008</span><span class="sxs-lookup"><span data-stu-id="103b1-138">0x80041008</span></span> | <span data-ttu-id="103b1-139">Bir parametre geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="103b1-139">A parameter is not valid.</span></span> |
| `WBEM_E_INVALID_QUALIFIER_TYPE` | <span data-ttu-id="103b1-140">0x80041029</span><span class="sxs-lookup"><span data-stu-id="103b1-140">0x80041029</span></span> | <span data-ttu-id="103b1-141">`pVal` Parametresi geçerli bir niteleyici türü değil.</span><span class="sxs-lookup"><span data-stu-id="103b1-141">The `pVal` parameter is not of a legal qualifier type.</span></span> |
| `WBEM_E_OVERRIDE_NOT_ALLOWED` | <span data-ttu-id="103b1-142">0x8004101a</span><span class="sxs-lookup"><span data-stu-id="103b1-142">0x8004101a</span></span> | <span data-ttu-id="103b1-143">Çağrı mümkün değil `QualifierSet_Put` edinilen nesneyi izin vermediğinden niteleyici yöntemini geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="103b1-143">It is not possible to call the `QualifierSet_Put` method on the qualifier because the owning object does not permit overrides.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="103b1-144">0</span><span class="sxs-lookup"><span data-stu-id="103b1-144">0</span></span> | <span data-ttu-id="103b1-145">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="103b1-145">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="103b1-146">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="103b1-146">Remarks</span></span>

<span data-ttu-id="103b1-147">Bu işlev bir çağrı sarılır [IWbemQualifierSet::Put](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-put) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="103b1-147">This function wraps a call to the [IWbemQualifierSet::Put](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-put) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="103b1-148">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="103b1-148">Requirements</span></span>

<span data-ttu-id="103b1-149">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="103b1-149">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="103b1-150">**Üst bilgi:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="103b1-150">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="103b1-151">**.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="103b1-151">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="103b1-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="103b1-152">See also</span></span>

- [<span data-ttu-id="103b1-153">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="103b1-153">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)