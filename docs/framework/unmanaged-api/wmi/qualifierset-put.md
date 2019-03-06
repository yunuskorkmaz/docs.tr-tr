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
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57378850"
---
# <a name="qualifiersetput-function"></a><span data-ttu-id="1957d-103">QualifierSet_Put işlevi</span><span class="sxs-lookup"><span data-stu-id="1957d-103">QualifierSet_Put function</span></span>

<span data-ttu-id="1957d-104">Değer ve adlandırılmış niteleyicisi yazar.</span><span class="sxs-lookup"><span data-stu-id="1957d-104">Writes the named qualifier and value.</span></span> <span data-ttu-id="1957d-105">Yeni niteleyici aynı adlı önceki değerin üzerine yazar.</span><span class="sxs-lookup"><span data-stu-id="1957d-105">The new qualifier overwrites the previous value of the same name.</span></span> <span data-ttu-id="1957d-106">Niteleyici mevcut değilse oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="1957d-106">If the qualifier does not exist, it is created.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="1957d-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1957d-107">Syntax</span></span>

```cpp
HRESULT QualifierSet_Put (
   [in] int                  vFunc,
   [in] IWbemQualifierSet*   ptr,
   [in] LPCWSTR              wszName,
   [in] VARIANT*             pVal,
   [in] LONG                 lFlavor
);
```

## <a name="parameters"></a><span data-ttu-id="1957d-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1957d-108">Parameters</span></span>

`vFunc`\
<span data-ttu-id="1957d-109">[in] Bu parametre kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="1957d-109">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="1957d-110">[in] Bir işaretçi bir [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) örneği.</span><span class="sxs-lookup"><span data-stu-id="1957d-110">[in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

`wszName`\
<span data-ttu-id="1957d-111">[in] Yazılacak niteleyicisi adı.</span><span class="sxs-lookup"><span data-stu-id="1957d-111">[in] The name of the qualifier to write.</span></span>

`pVal`\
<span data-ttu-id="1957d-112">[in] Geçerli bir işaretçi `VARIANT` yazılacak niteleyicisi içeriyor.</span><span class="sxs-lookup"><span data-stu-id="1957d-112">[in] A pointer to a valid `VARIANT` that contains the qualifier to write.</span></span> <span data-ttu-id="1957d-113">Bu parametre olamaz `null`.</span><span class="sxs-lookup"><span data-stu-id="1957d-113">This parameter cannot be `null`.</span></span>

`lFlavor`\
<span data-ttu-id="1957d-114">[in] Bu niteleyici için'istenen niteleyici özelliği tanımlayan sabitlerden biri.</span><span class="sxs-lookup"><span data-stu-id="1957d-114">[in] One of the following constants that defines the desired qualifier flavors for this qualifier.</span></span> <span data-ttu-id="1957d-115">Varsayılan değer `WBEM_FLAVOR_OVERRIDABLE` (0).</span><span class="sxs-lookup"><span data-stu-id="1957d-115">The default value is `WBEM_FLAVOR_OVERRIDABLE` (0).</span></span>

|<span data-ttu-id="1957d-116">Sabit</span><span class="sxs-lookup"><span data-stu-id="1957d-116">Constant</span></span>  |<span data-ttu-id="1957d-117">Değer</span><span class="sxs-lookup"><span data-stu-id="1957d-117">Value</span></span>  |<span data-ttu-id="1957d-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1957d-118">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAVOR_OVERRIDABLE` | <span data-ttu-id="1957d-119">0</span><span class="sxs-lookup"><span data-stu-id="1957d-119">0</span></span> | <span data-ttu-id="1957d-120">Niteleyici bir türetilmiş sınıf veya örnek geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="1957d-120">The qualifier can be overridden in a derived class or instance.</span></span> <span data-ttu-id="1957d-121">**Varsayılan değer budur.**</span><span class="sxs-lookup"><span data-stu-id="1957d-121">**This is the default value.**</span></span> |
| `WBEM_FLAVOR_FLAG_PROPAGATE_TO_INSTANCE` | <span data-ttu-id="1957d-122">1.</span><span class="sxs-lookup"><span data-stu-id="1957d-122">1</span></span> | <span data-ttu-id="1957d-123">Niteleyici örneklere yayılır.</span><span class="sxs-lookup"><span data-stu-id="1957d-123">The qualifier is propagated to instances.</span></span> |
| `WBEM_FLAVOR_FLAG_PROPAGATE_TO_DERIVED_CLASS` | <span data-ttu-id="1957d-124">2</span><span class="sxs-lookup"><span data-stu-id="1957d-124">2</span></span> | <span data-ttu-id="1957d-125">Türetilmiş sınıflara niteleyici yayılır.</span><span class="sxs-lookup"><span data-stu-id="1957d-125">The qualifier is propagated to derived classes.</span></span> |
| `WBEM_FLAVOR_NOT_OVERRIDABLE` | <span data-ttu-id="1957d-126">0x10</span><span class="sxs-lookup"><span data-stu-id="1957d-126">0x10</span></span> | <span data-ttu-id="1957d-127">Niteleyici bir türetilmiş sınıf veya örnek geçersiz kılınamaz.</span><span class="sxs-lookup"><span data-stu-id="1957d-127">The qualifier cannot be overridden in a derived class or instance.</span></span> |
| `WBEM_FLAVOR_AMENDED` | <span data-ttu-id="1957d-128">0x80</span><span class="sxs-lookup"><span data-stu-id="1957d-128">0x80</span></span> | <span data-ttu-id="1957d-129">Niteleyici yerelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="1957d-129">The qualifier is localized.</span></span> |

## <a name="return-value"></a><span data-ttu-id="1957d-130">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="1957d-130">Return value</span></span>

<span data-ttu-id="1957d-131">Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üst bilgi dosyası veya tanımlayabilirsiniz bunları sabitleri kodunuzda:</span><span class="sxs-lookup"><span data-stu-id="1957d-131">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="1957d-132">Sabit</span><span class="sxs-lookup"><span data-stu-id="1957d-132">Constant</span></span>  |<span data-ttu-id="1957d-133">Değer</span><span class="sxs-lookup"><span data-stu-id="1957d-133">Value</span></span>  |<span data-ttu-id="1957d-134">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1957d-134">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_CANNOT_BE_KEY` | <span data-ttu-id="1957d-135">0x8004101f</span><span class="sxs-lookup"><span data-stu-id="1957d-135">0x8004101f</span></span> | <span data-ttu-id="1957d-136">Belirtmek için geçersiz bir girişimde bulunuldu oluştu **anahtar** niteleyici bir özellikte bir anahtar olamaz.</span><span class="sxs-lookup"><span data-stu-id="1957d-136">There was an illegal attempt to specify the **Key** qualifier on a property that cannot be a key.</span></span> <span data-ttu-id="1957d-137">Anahtarları belirtilen om c; bir nesne için sınıf tanımı ve örnek başına temelinde değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="1957d-137">The keys are specified om tje c;ass definition for an object and cannot be altered on a per-instance basis.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="1957d-138">0x80041008</span><span class="sxs-lookup"><span data-stu-id="1957d-138">0x80041008</span></span> | <span data-ttu-id="1957d-139">Bir parametre geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="1957d-139">A parameter is not valid.</span></span> |
| `WBEM_E_INVALID_QUALIFIER_TYPE` | <span data-ttu-id="1957d-140">0x80041029</span><span class="sxs-lookup"><span data-stu-id="1957d-140">0x80041029</span></span> | <span data-ttu-id="1957d-141">`pVal` Parametresi geçerli bir niteleyici türü değil.</span><span class="sxs-lookup"><span data-stu-id="1957d-141">The `pVal` parameter is not of a legal qualifier type.</span></span> |
| `WBEM_E_OVERRIDE_NOT_ALLOWED` | <span data-ttu-id="1957d-142">0x8004101a</span><span class="sxs-lookup"><span data-stu-id="1957d-142">0x8004101a</span></span> | <span data-ttu-id="1957d-143">Çağrı mümkün değil `QualifierSet_Put` edinilen nesneyi izin vermediğinden niteleyici yöntemini geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="1957d-143">It is not possible to call the `QualifierSet_Put` method on the qualifier because the owning object does not permit overrides.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="1957d-144">0</span><span class="sxs-lookup"><span data-stu-id="1957d-144">0</span></span> | <span data-ttu-id="1957d-145">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="1957d-145">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="1957d-146">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1957d-146">Remarks</span></span>

<span data-ttu-id="1957d-147">Bu işlev bir çağrı sarılır [IWbemQualifierSet::Put](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-put) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="1957d-147">This function wraps a call to the [IWbemQualifierSet::Put](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-put) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="1957d-148">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1957d-148">Requirements</span></span>

<span data-ttu-id="1957d-149">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1957d-149">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="1957d-150">**Üst bilgi:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="1957d-150">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="1957d-151">**.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="1957d-151">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="1957d-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1957d-152">See also</span></span>

- [<span data-ttu-id="1957d-153">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="1957d-153">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)