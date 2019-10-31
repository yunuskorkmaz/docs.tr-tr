---
title: QualifierSet_Put işlevi (yönetilmeyen API Başvurusu)
description: QualifierSet_Put işlevi, adlandırılmış niteleyiciyi ve değerini yazar.
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
ms.openlocfilehash: a35025c6d16455a51b7b22d822ba77337ddd894a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120230"
---
# <a name="qualifierset_put-function"></a><span data-ttu-id="986d5-103">QualifierSet_Put işlevi</span><span class="sxs-lookup"><span data-stu-id="986d5-103">QualifierSet_Put function</span></span>

<span data-ttu-id="986d5-104">Adlandırılmış niteleyiciyi ve değeri yazar.</span><span class="sxs-lookup"><span data-stu-id="986d5-104">Writes the named qualifier and value.</span></span> <span data-ttu-id="986d5-105">Yeni niteleyici, aynı ada sahip bir önceki değerin üzerine yazar.</span><span class="sxs-lookup"><span data-stu-id="986d5-105">The new qualifier overwrites the previous value of the same name.</span></span> <span data-ttu-id="986d5-106">Niteleyici yoksa, oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="986d5-106">If the qualifier does not exist, it is created.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="986d5-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="986d5-107">Syntax</span></span>

```cpp
HRESULT QualifierSet_Put (
   [in] int                  vFunc,
   [in] IWbemQualifierSet*   ptr,
   [in] LPCWSTR              wszName,
   [in] VARIANT*             pVal,
   [in] LONG                 lFlavor
);
```

## <a name="parameters"></a><span data-ttu-id="986d5-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="986d5-108">Parameters</span></span>

`vFunc`\
<span data-ttu-id="986d5-109">'ndaki Bu parametre kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="986d5-109">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="986d5-110">'ndaki Bir [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) örneği işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="986d5-110">[in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

`wszName`\
<span data-ttu-id="986d5-111">'ndaki Yazılacak niteleyicinin adı.</span><span class="sxs-lookup"><span data-stu-id="986d5-111">[in] The name of the qualifier to write.</span></span>

`pVal`\
<span data-ttu-id="986d5-112">'ndaki Yazılacak niteleyiciyi içeren geçerli bir `VARIANT` işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="986d5-112">[in] A pointer to a valid `VARIANT` that contains the qualifier to write.</span></span> <span data-ttu-id="986d5-113">Bu parametre `null`olamaz.</span><span class="sxs-lookup"><span data-stu-id="986d5-113">This parameter cannot be `null`.</span></span>

`lFlavor`\
<span data-ttu-id="986d5-114">'ndaki Bu niteleyici için istenen niteleyici türlerini tanımlayan aşağıdaki sabitlerden biri.</span><span class="sxs-lookup"><span data-stu-id="986d5-114">[in] One of the following constants that defines the desired qualifier flavors for this qualifier.</span></span> <span data-ttu-id="986d5-115">Varsayılan değer `WBEM_FLAVOR_OVERRIDABLE` (0).</span><span class="sxs-lookup"><span data-stu-id="986d5-115">The default value is `WBEM_FLAVOR_OVERRIDABLE` (0).</span></span>

|<span data-ttu-id="986d5-116">Sabit</span><span class="sxs-lookup"><span data-stu-id="986d5-116">Constant</span></span>  |<span data-ttu-id="986d5-117">Değer</span><span class="sxs-lookup"><span data-stu-id="986d5-117">Value</span></span>  |<span data-ttu-id="986d5-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="986d5-118">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAVOR_OVERRIDABLE` | <span data-ttu-id="986d5-119">0</span><span class="sxs-lookup"><span data-stu-id="986d5-119">0</span></span> | <span data-ttu-id="986d5-120">Niteleyici, türetilmiş bir sınıfta veya örnekte geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="986d5-120">The qualifier can be overridden in a derived class or instance.</span></span> <span data-ttu-id="986d5-121">**Bu varsayılan değerdir.**</span><span class="sxs-lookup"><span data-stu-id="986d5-121">**This is the default value.**</span></span> |
| `WBEM_FLAVOR_FLAG_PROPAGATE_TO_INSTANCE` | <span data-ttu-id="986d5-122">1\.</span><span class="sxs-lookup"><span data-stu-id="986d5-122">1</span></span> | <span data-ttu-id="986d5-123">Niteleyici örneklere yayılır.</span><span class="sxs-lookup"><span data-stu-id="986d5-123">The qualifier is propagated to instances.</span></span> |
| `WBEM_FLAVOR_FLAG_PROPAGATE_TO_DERIVED_CLASS` | <span data-ttu-id="986d5-124">2</span><span class="sxs-lookup"><span data-stu-id="986d5-124">2</span></span> | <span data-ttu-id="986d5-125">Niteleyici türetilmiş sınıflara yayılır.</span><span class="sxs-lookup"><span data-stu-id="986d5-125">The qualifier is propagated to derived classes.</span></span> |
| `WBEM_FLAVOR_NOT_OVERRIDABLE` | <span data-ttu-id="986d5-126">0x10</span><span class="sxs-lookup"><span data-stu-id="986d5-126">0x10</span></span> | <span data-ttu-id="986d5-127">Niteleyici, türetilmiş bir sınıfta veya örnekte geçersiz kılınamaz.</span><span class="sxs-lookup"><span data-stu-id="986d5-127">The qualifier cannot be overridden in a derived class or instance.</span></span> |
| `WBEM_FLAVOR_AMENDED` | <span data-ttu-id="986d5-128">0x80</span><span class="sxs-lookup"><span data-stu-id="986d5-128">0x80</span></span> | <span data-ttu-id="986d5-129">Niteleyici yereldir.</span><span class="sxs-lookup"><span data-stu-id="986d5-129">The qualifier is localized.</span></span> |

## <a name="return-value"></a><span data-ttu-id="986d5-130">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="986d5-130">Return value</span></span>

<span data-ttu-id="986d5-131">Bu işlev tarafından döndürülen aşağıdaki değerler, *Wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="986d5-131">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="986d5-132">Sabit</span><span class="sxs-lookup"><span data-stu-id="986d5-132">Constant</span></span>  |<span data-ttu-id="986d5-133">Değer</span><span class="sxs-lookup"><span data-stu-id="986d5-133">Value</span></span>  |<span data-ttu-id="986d5-134">Açıklama</span><span class="sxs-lookup"><span data-stu-id="986d5-134">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_CANNOT_BE_KEY` | <span data-ttu-id="986d5-135">0x8004101f</span><span class="sxs-lookup"><span data-stu-id="986d5-135">0x8004101f</span></span> | <span data-ttu-id="986d5-136">Anahtar olmayan bir özellikte **anahtar** niteleyicisi belirtmeye yönelik geçersiz bir girişim vardı.</span><span class="sxs-lookup"><span data-stu-id="986d5-136">There was an illegal attempt to specify the **Key** qualifier on a property that cannot be a key.</span></span> <span data-ttu-id="986d5-137">Anahtarlar bir nesne için sınıf tanımında belirtilir ve örnek temelinde değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="986d5-137">The keys are specified in the class definition for an object and cannot be altered on a per-instance basis.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="986d5-138">0x80041008</span><span class="sxs-lookup"><span data-stu-id="986d5-138">0x80041008</span></span> | <span data-ttu-id="986d5-139">Parametre geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="986d5-139">A parameter is not valid.</span></span> |
| `WBEM_E_INVALID_QUALIFIER_TYPE` | <span data-ttu-id="986d5-140">0x80041029</span><span class="sxs-lookup"><span data-stu-id="986d5-140">0x80041029</span></span> | <span data-ttu-id="986d5-141">`pVal` parametresi geçerli bir niteleyici türü değil.</span><span class="sxs-lookup"><span data-stu-id="986d5-141">The `pVal` parameter is not of a legal qualifier type.</span></span> |
| `WBEM_E_OVERRIDE_NOT_ALLOWED` | <span data-ttu-id="986d5-142">0x8004101a</span><span class="sxs-lookup"><span data-stu-id="986d5-142">0x8004101a</span></span> | <span data-ttu-id="986d5-143">Sahip olan nesne geçersiz kılmalara izin vermediğinden, niteleyicisi üzerinde `QualifierSet_Put` yöntemini çağırmak mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="986d5-143">It is not possible to call the `QualifierSet_Put` method on the qualifier because the owning object does not permit overrides.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="986d5-144">0</span><span class="sxs-lookup"><span data-stu-id="986d5-144">0</span></span> | <span data-ttu-id="986d5-145">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="986d5-145">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="986d5-146">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="986d5-146">Remarks</span></span>

<span data-ttu-id="986d5-147">Bu işlev, [IWbemQualifierSet::P UT](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-put) yöntemine bir çağrı kaydırır.</span><span class="sxs-lookup"><span data-stu-id="986d5-147">This function wraps a call to the [IWbemQualifierSet::Put](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-put) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="986d5-148">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="986d5-148">Requirements</span></span>

<span data-ttu-id="986d5-149">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="986d5-149">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="986d5-150">**Üst bilgi:** WMINet_Utils. IDL</span><span class="sxs-lookup"><span data-stu-id="986d5-150">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="986d5-151">**.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="986d5-151">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="986d5-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="986d5-152">See also</span></span>

- [<span data-ttu-id="986d5-153">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="986d5-153">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
