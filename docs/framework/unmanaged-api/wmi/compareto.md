---
title: CompareTo işlevi (yönetilmeyen API Başvurusu)
description: CompareTo işlevi bir nesneyi başka bir WMI nesnesiyle karşılaştırır.
ms.date: 11/06/2017
api_name:
- CompareTo
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- CompareTo
helpviewer_keywords:
- CompareTo function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 0d210795016cd2e0179b902a224ca0c62f4ac01f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128707"
---
# <a name="compareto-function"></a><span data-ttu-id="35fe2-103">CompareTo işlevi</span><span class="sxs-lookup"><span data-stu-id="35fe2-103">CompareTo function</span></span>

<span data-ttu-id="35fe2-104">Bir nesneyi başka bir Windows Yönetim nesnesiyle karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="35fe2-104">Compares an object to another Windows management object.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="35fe2-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="35fe2-105">Syntax</span></span>

```cpp
HRESULT CompareTo (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LONG              flags,
   [in] IWbemClassObject* pCompareTo
);
```

## <a name="parameters"></a><span data-ttu-id="35fe2-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="35fe2-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="35fe2-107">'ndaki Bu parametre kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="35fe2-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="35fe2-108">'ndaki [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneğine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="35fe2-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`flags`\
<span data-ttu-id="35fe2-109">'ndaki Karşılaştırma için göz önünde bulundurmanız gereken nesne özelliklerini belirten bayrakların bit düzeyinde birleşimi.</span><span class="sxs-lookup"><span data-stu-id="35fe2-109">[in] A bitwise combination of the flags that specify the object characteristics to consider for the comparison.</span></span> <span data-ttu-id="35fe2-110">Daha fazla bilgi için [açıklamalar](#remarks) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="35fe2-110">See the [Remarks](#remarks) section for more information.</span></span>

`pCompareTo`\
<span data-ttu-id="35fe2-111">'ndaki Karşılaştırılacak nesne.</span><span class="sxs-lookup"><span data-stu-id="35fe2-111">[in] The object for comparison.</span></span> <span data-ttu-id="35fe2-112">`pCompareTo` geçerli bir [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneği olmalıdır; `null`olamaz.</span><span class="sxs-lookup"><span data-stu-id="35fe2-112">`pCompareTo` must be a valid [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance; it cannot be `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="35fe2-113">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="35fe2-113">Return value</span></span>

<span data-ttu-id="35fe2-114">Bu işlev tarafından döndürülen aşağıdaki değerler, *Wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="35fe2-114">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="35fe2-115">Sabit</span><span class="sxs-lookup"><span data-stu-id="35fe2-115">Constant</span></span>  |<span data-ttu-id="35fe2-116">Değer</span><span class="sxs-lookup"><span data-stu-id="35fe2-116">Value</span></span>  |<span data-ttu-id="35fe2-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="35fe2-117">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="35fe2-118">0x80041001</span><span class="sxs-lookup"><span data-stu-id="35fe2-118">0x80041001</span></span> | <span data-ttu-id="35fe2-119">Belirtilmeyen bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="35fe2-119">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="35fe2-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="35fe2-120">0x80041008</span></span> | <span data-ttu-id="35fe2-121">Bir parametre geçersiz.</span><span class="sxs-lookup"><span data-stu-id="35fe2-121">A parameter is invalid.</span></span> |
| `WBEM_E_UNEXPECTED` | <span data-ttu-id="35fe2-122">0x8004101D</span><span class="sxs-lookup"><span data-stu-id="35fe2-122">0x8004101d</span></span> | <span data-ttu-id="35fe2-123">`BeginEnumeration` ikinci bir çağrısı, [`EndEnumeration`](endenumeration.md)için araya giren bir çağrı olmadan yapıldı.</span><span class="sxs-lookup"><span data-stu-id="35fe2-123">A second call to `BeginEnumeration` was made without an intervening call to [`EndEnumeration`](endenumeration.md).</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="35fe2-124">0</span><span class="sxs-lookup"><span data-stu-id="35fe2-124">0</span></span> | <span data-ttu-id="35fe2-125">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="35fe2-125">The function call was successful.</span></span>  |
| `WBEM_S_DIFFERENT` | <span data-ttu-id="35fe2-126">0x40003</span><span class="sxs-lookup"><span data-stu-id="35fe2-126">0x40003</span></span> | <span data-ttu-id="35fe2-127">Nesneler farklı.</span><span class="sxs-lookup"><span data-stu-id="35fe2-127">The objects are different.</span></span> |
| `WBEM_S_SAME` | <span data-ttu-id="35fe2-128">0</span><span class="sxs-lookup"><span data-stu-id="35fe2-128">0</span></span> | <span data-ttu-id="35fe2-129">Nesneler, karşılaştırma bayraklarına göre aynıdır.</span><span class="sxs-lookup"><span data-stu-id="35fe2-129">The objects are the same based on the comparison flags.</span></span> |

## <a name="remarks"></a><span data-ttu-id="35fe2-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="35fe2-130">Remarks</span></span>

<span data-ttu-id="35fe2-131">Bu işlev, [IWbemClassObject:: CompareTo](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-compareto) yöntemine bir çağrı kaydırır.</span><span class="sxs-lookup"><span data-stu-id="35fe2-131">This function wraps a call to the [IWbemClassObject::CompareTo](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-compareto) method.</span></span>

<span data-ttu-id="35fe2-132">`lEnumFlags` bağımsız değişkeni olarak geçirilebilecek bayraklar, *Wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="35fe2-132">The flags that can be passed as the `lEnumFlags` argument are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span> <span data-ttu-id="35fe2-133">Aşağıdaki bayrakların bit düzeyinde birleşimini belirterek, karşılaştırmaya dahil olan tek tek özellikleri belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="35fe2-133">You can specify the individual characteristics involved in the comparison by specifying a bitwise combination of the following flags:</span></span>

|<span data-ttu-id="35fe2-134">Sabit</span><span class="sxs-lookup"><span data-stu-id="35fe2-134">Constant</span></span>  |<span data-ttu-id="35fe2-135">Değer</span><span class="sxs-lookup"><span data-stu-id="35fe2-135">Value</span></span>  |<span data-ttu-id="35fe2-136">Açıklama</span><span class="sxs-lookup"><span data-stu-id="35fe2-136">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_IGNORE_OBJECT_SOURCE` | <span data-ttu-id="35fe2-137">2</span><span class="sxs-lookup"><span data-stu-id="35fe2-137">2</span></span> | <span data-ttu-id="35fe2-138">Kaynağı (sunucu ve geldiği ad alanı) yok sayın.</span><span class="sxs-lookup"><span data-stu-id="35fe2-138">Ignore the source (the server and the namespace they came from).</span></span> |
| `WBEM_FLAG_IGNORE_QUALIFIERS` | <span data-ttu-id="35fe2-139">1\.</span><span class="sxs-lookup"><span data-stu-id="35fe2-139">1</span></span> | <span data-ttu-id="35fe2-140">Tüm niteleyicileri yoksay ( **anahtar** ve **dinamik**dahil)</span><span class="sxs-lookup"><span data-stu-id="35fe2-140">Ignore all qualifiers (including **Key** and **Dynamic**)</span></span> |
| `WBEM_FLAG_IGNORE_DEFAULT_VALUES` | <span data-ttu-id="35fe2-141">4</span><span class="sxs-lookup"><span data-stu-id="35fe2-141">4</span></span> | <span data-ttu-id="35fe2-142">Özelliklerin varsayılan değerlerini yoksayın.</span><span class="sxs-lookup"><span data-stu-id="35fe2-142">Ignore default values of properties.</span></span> <span data-ttu-id="35fe2-143">Bu bayrak yalnızca sınıfların karşılaştırılması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="35fe2-143">This flag only applies to comparison of classes.</span></span> |
| `WBEM_FLAG_IGNORE_FLAVOR` | <span data-ttu-id="35fe2-144">0x20</span><span class="sxs-lookup"><span data-stu-id="35fe2-144">0x20</span></span> | <span data-ttu-id="35fe2-145">Niteleyici niteleyicisini yoksayın.</span><span class="sxs-lookup"><span data-stu-id="35fe2-145">Ignore qualifier flavors.</span></span> <span data-ttu-id="35fe2-146">Bu bayrak hala niteleyicileri hesaba ayırır, ancak yayma kuralları ve geçersiz kılma kısıtlamaları gibi özellik ayrımlarını yoksayar.</span><span class="sxs-lookup"><span data-stu-id="35fe2-146">This flag still takes qualifiers into account, but ignores flavor distinctions such as propagation rules and override restrictions.</span></span> |
| `WBEM_FLAG_IGNORE_CASE` | <span data-ttu-id="35fe2-147">0x10</span><span class="sxs-lookup"><span data-stu-id="35fe2-147">0x10</span></span> | <span data-ttu-id="35fe2-148">Dize değerlerini karşılaştıran büyük/küçük harf durumunu yoksayın.</span><span class="sxs-lookup"><span data-stu-id="35fe2-148">Ignore case in comparing string values.</span></span> <span data-ttu-id="35fe2-149">Bu, hem dizeler hem de niteleyici değerleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="35fe2-149">This applies both to strings and qualifier values.</span></span> <span data-ttu-id="35fe2-150">Özellik ve niteleyici adlarının karşılaştırılması, bu bayrağın ayarlanmış olup olmamasına bakılmaksızın her zaman büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="35fe2-150">The comparison of property and qualifier names is always case-sensitive regardless of whether this flag is set.</span></span> |
| `WBEM_FLAG_IGNORE_CLASS` | <span data-ttu-id="35fe2-151">0x8</span><span class="sxs-lookup"><span data-stu-id="35fe2-151">0x8</span></span> | <span data-ttu-id="35fe2-152">Karşılaştırılan nesnelerin aynı sınıfın örnekleri olduğunu varsayın.</span><span class="sxs-lookup"><span data-stu-id="35fe2-152">Assume that the objects being compared are instances of the same class.</span></span> <span data-ttu-id="35fe2-153">Sonuç olarak, bu bayrak yalnızca örnekle ilgili bilgileri karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="35fe2-153">Consequently, this flag compares instance-related information only.</span></span> <span data-ttu-id="35fe2-154">Performansı iyileştirmek için bu bayrakları kullanın.</span><span class="sxs-lookup"><span data-stu-id="35fe2-154">Use this flags to optimize performance.</span></span> <span data-ttu-id="35fe2-155">Nesneler aynı sınıftan değilse, sonuçlar tanımsızdır.</span><span class="sxs-lookup"><span data-stu-id="35fe2-155">If the objects are not of the same class, the results are undefined.</span></span> |

<span data-ttu-id="35fe2-156">Ya da şu şekilde tek bir bileşik bayrak belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="35fe2-156">Or you can specify a single composite flag as follows:</span></span>

|<span data-ttu-id="35fe2-157">Sabit</span><span class="sxs-lookup"><span data-stu-id="35fe2-157">Constant</span></span>  |<span data-ttu-id="35fe2-158">Değer</span><span class="sxs-lookup"><span data-stu-id="35fe2-158">Value</span></span>  |<span data-ttu-id="35fe2-159">Açıklama</span><span class="sxs-lookup"><span data-stu-id="35fe2-159">Description</span></span>  |
|---------|---------|---------|
|`WBEM_COMPARISON_INCLUDE_ALL` | <span data-ttu-id="35fe2-160">0</span><span class="sxs-lookup"><span data-stu-id="35fe2-160">0</span></span> | <span data-ttu-id="35fe2-161">Karşılaştırmayla tüm özellikleri göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="35fe2-161">Consider all features in the comparison.</span></span> |

## <a name="requirements"></a><span data-ttu-id="35fe2-162">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="35fe2-162">Requirements</span></span>

<span data-ttu-id="35fe2-163">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="35fe2-163">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="35fe2-164">**Üst bilgi:** WMINet_Utils. IDL</span><span class="sxs-lookup"><span data-stu-id="35fe2-164">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="35fe2-165">**.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="35fe2-165">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="35fe2-166">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="35fe2-166">See also</span></span>

- [<span data-ttu-id="35fe2-167">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="35fe2-167">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
