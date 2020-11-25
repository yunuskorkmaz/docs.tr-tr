---
title: BeginEnumeration işlevi (yönetilmeyen API Başvurusu)
description: BeginEnumeration işlevi bir Numaralandırıcı numaralandırmanın başlangıcına sıfırlanır
ms.date: 11/06/2017
api_name:
- BeginEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- BeginEnumeration
helpviewer_keywords:
- BeginEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 6057526ddbe2efed65f8569e829c35524829e43e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95708224"
---
# <a name="beginenumeration-function"></a><span data-ttu-id="50724-103">BeginEnumeration işlevi</span><span class="sxs-lookup"><span data-stu-id="50724-103">BeginEnumeration function</span></span>

<span data-ttu-id="50724-104">Bir numaralandırıcıyı numaralandırmanın başına geri döndürür.</span><span class="sxs-lookup"><span data-stu-id="50724-104">Resets an enumerator back to the beginning of the enumeration.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="50724-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="50724-105">Syntax</span></span>  
  
```cpp  
HRESULT BeginEnumeration (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LONG              lEnumFlags
);
```  

## <a name="parameters"></a><span data-ttu-id="50724-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="50724-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="50724-107">'ndaki Bu parametre kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="50724-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="50724-108">'ndaki [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneğine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="50724-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lEnumFlags`\
<span data-ttu-id="50724-109">'ndaki Numaralandırmada içerilen özellikleri denetleyen [açıklamalar](#remarks) bölümünde açıklanan bayrakların veya değerlerin bit düzeyinde birleşimi.</span><span class="sxs-lookup"><span data-stu-id="50724-109">[in] A bitwise combination of the flags or values described in the [Remarks](#remarks) section that controls the properties included in the enumeration.</span></span>

## <a name="return-value"></a><span data-ttu-id="50724-110">Döndürülen değer</span><span class="sxs-lookup"><span data-stu-id="50724-110">Return value</span></span>

<span data-ttu-id="50724-111">Bu işlev tarafından döndürülen aşağıdaki değerler, *Wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="50724-111">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="50724-112">Sabit</span><span class="sxs-lookup"><span data-stu-id="50724-112">Constant</span></span>  |<span data-ttu-id="50724-113">Değer</span><span class="sxs-lookup"><span data-stu-id="50724-113">Value</span></span>  |<span data-ttu-id="50724-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="50724-114">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="50724-115">0x80041008</span><span class="sxs-lookup"><span data-stu-id="50724-115">0x80041008</span></span> | <span data-ttu-id="50724-116">İçindeki bayrakların birleşimi `lEnumFlags` geçersiz ya da geçersiz bir bağımsız değişken belirtildi.</span><span class="sxs-lookup"><span data-stu-id="50724-116">The combination of flags in `lEnumFlags` is invalid, or an invalid argument was specified.</span></span> |
|`WBEM_E_UNEXPECTED` | <span data-ttu-id="50724-117">0x8004101D</span><span class="sxs-lookup"><span data-stu-id="50724-117">0x8004101d</span></span> | <span data-ttu-id="50724-118">İçin bir `BeginEnumeration` araya giren çağrı yapılmadan ikinci bir çağrı yapıldı [`EndEnumeration`](endenumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="50724-118">A second call to `BeginEnumeration` was made without an intervening call to [`EndEnumeration`](endenumeration.md).</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="50724-119">0x80041006</span><span class="sxs-lookup"><span data-stu-id="50724-119">0x80041006</span></span> | <span data-ttu-id="50724-120">Yeni bir sabit listesi başlatmak için yeterli kullanılabilir bellek yok.</span><span class="sxs-lookup"><span data-stu-id="50724-120">Not enough memory is available to begin a new enumeration.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="50724-121">0</span><span class="sxs-lookup"><span data-stu-id="50724-121">0</span></span> | <span data-ttu-id="50724-122">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="50724-122">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="50724-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="50724-123">Remarks</span></span>

<span data-ttu-id="50724-124">Bu işlev, [IWbemClassObject:: BeginEnumeration](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) yöntemine bir çağrı kaydırır.</span><span class="sxs-lookup"><span data-stu-id="50724-124">This function wraps a call to the [IWbemClassObject::BeginEnumeration](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) method.</span></span>

<span data-ttu-id="50724-125">Bağımsız değişken olarak geçirilebilecek bayraklar, `lEnumFlags` *Wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="50724-125">The flags that can be passed as the `lEnumFlags` argument are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span>  <span data-ttu-id="50724-126">Her bir grup için herhangi bir bayrak ile bir bayrak birleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="50724-126">You can combine one flag from each group with any flag from any other group.</span></span> <span data-ttu-id="50724-127">Ancak, aynı gruptaki Bayraklar birbirini dışlıyor.</span><span class="sxs-lookup"><span data-stu-id="50724-127">However, flags from the same group are mutually exclusive.</span></span>

<span data-ttu-id="50724-128">**Grup 1**</span><span class="sxs-lookup"><span data-stu-id="50724-128">**Group 1**</span></span>

|<span data-ttu-id="50724-129">Sabit</span><span class="sxs-lookup"><span data-stu-id="50724-129">Constant</span></span>  |<span data-ttu-id="50724-130">Değer</span><span class="sxs-lookup"><span data-stu-id="50724-130">Value</span></span>  |<span data-ttu-id="50724-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="50724-131">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | <span data-ttu-id="50724-132">4,</span><span class="sxs-lookup"><span data-stu-id="50724-132">0x4</span></span> | <span data-ttu-id="50724-133">Yalnızca anahtarı oluşturan özellikleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="50724-133">Include properties that constitute the key only.</span></span> |
|`WBEM_FLAG_REFS_ONLY` | <span data-ttu-id="50724-134">0x8</span><span class="sxs-lookup"><span data-stu-id="50724-134">0x8</span></span> | <span data-ttu-id="50724-135">Yalnızca nesne başvuruları olan özellikleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="50724-135">Include properties that are object references only.</span></span> |

<span data-ttu-id="50724-136">**Grup 2**</span><span class="sxs-lookup"><span data-stu-id="50724-136">**Group 2**</span></span>

<span data-ttu-id="50724-137">Sabit</span><span class="sxs-lookup"><span data-stu-id="50724-137">Constant</span></span>  |<span data-ttu-id="50724-138">Değer</span><span class="sxs-lookup"><span data-stu-id="50724-138">Value</span></span>  |<span data-ttu-id="50724-139">Açıklama</span><span class="sxs-lookup"><span data-stu-id="50724-139">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_SYSTEM_ONLY` | <span data-ttu-id="50724-140">0x30</span><span class="sxs-lookup"><span data-stu-id="50724-140">0x30</span></span> | <span data-ttu-id="50724-141">Numaralandırmayı yalnızca sistem özellikleriyle sınırlayın.</span><span class="sxs-lookup"><span data-stu-id="50724-141">Limit the enumeration to system properties only.</span></span> |
|`WBEM_FLAG_NONSYSTEM_ONLY` | <span data-ttu-id="50724-142">0x40</span><span class="sxs-lookup"><span data-stu-id="50724-142">0x40</span></span> | <span data-ttu-id="50724-143">Yerel ve yayılmış özellikleri ekleyin, ancak Numaralandırmadaki sistem özelliklerini dışlayın.</span><span class="sxs-lookup"><span data-stu-id="50724-143">Include local and propagated properties but exclude system properties from the enumeration.</span></span> |

<span data-ttu-id="50724-144">Sınıflar için:</span><span class="sxs-lookup"><span data-stu-id="50724-144">For classes:</span></span>

<span data-ttu-id="50724-145">Sabit</span><span class="sxs-lookup"><span data-stu-id="50724-145">Constant</span></span>  |<span data-ttu-id="50724-146">Değer</span><span class="sxs-lookup"><span data-stu-id="50724-146">Value</span></span>  |<span data-ttu-id="50724-147">Açıklama</span><span class="sxs-lookup"><span data-stu-id="50724-147">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_CLASS_OVERRIDES_ONLY` | <span data-ttu-id="50724-148">0x100</span><span class="sxs-lookup"><span data-stu-id="50724-148">0x100</span></span> | <span data-ttu-id="50724-149">Sabit listesini, sınıf tanımında geçersiz kılınan özelliklerle sınırlayın.</span><span class="sxs-lookup"><span data-stu-id="50724-149">Limit the enumeration to properties overridden in the class definition.</span></span> |
|`WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` | <span data-ttu-id="50724-150">0x100</span><span class="sxs-lookup"><span data-stu-id="50724-150">0x100</span></span> | <span data-ttu-id="50724-151">Sabit listesini geçerli sınıf tanımında geçersiz kılınan özelliklerle ve sınıfta tanımlanan yeni özelliklerle sınırlayın.</span><span class="sxs-lookup"><span data-stu-id="50724-151">Limit the enumeration to properties overridden in the current class definition and to new properties defined in the class.</span></span> |
| `WBEM_MASK_CLASS_CONDITION` | <span data-ttu-id="50724-152">0x300</span><span class="sxs-lookup"><span data-stu-id="50724-152">0x300</span></span> | <span data-ttu-id="50724-153">Ya `lEnumFlags` da ayarlanmış olup olmadığını denetlemek için bir değere karşı uygulanacak bir maske (bayrak yerine) `WBEM_FLAG_CLASS_OVERRIDES_ONLY` `WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` .</span><span class="sxs-lookup"><span data-stu-id="50724-153">A mask (rather than a flag) to apply against a `lEnumFlags` value to check if either `WBEM_FLAG_CLASS_OVERRIDES_ONLY` or `WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` is set.</span></span> |
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="50724-154">0x10</span><span class="sxs-lookup"><span data-stu-id="50724-154">0x10</span></span> | <span data-ttu-id="50724-155">Sabit listesini, sınıfın kendisinde tanımlanan veya değiştirilen özelliklerle sınırlayın.</span><span class="sxs-lookup"><span data-stu-id="50724-155">Limit the enumeration to properties that are defined or modified in the class itself.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="50724-156">0x20</span><span class="sxs-lookup"><span data-stu-id="50724-156">0x20</span></span> | <span data-ttu-id="50724-157">Sabit listesini temel sınıflardan devralınan özelliklerle sınırlayın.</span><span class="sxs-lookup"><span data-stu-id="50724-157">Limit the enumeration to properties that are inherited from base classes.</span></span> |

<span data-ttu-id="50724-158">Örnekler için:</span><span class="sxs-lookup"><span data-stu-id="50724-158">For instances:</span></span>

<span data-ttu-id="50724-159">Sabit</span><span class="sxs-lookup"><span data-stu-id="50724-159">Constant</span></span>  |<span data-ttu-id="50724-160">Değer</span><span class="sxs-lookup"><span data-stu-id="50724-160">Value</span></span>  |<span data-ttu-id="50724-161">Açıklama</span><span class="sxs-lookup"><span data-stu-id="50724-161">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="50724-162">0x10</span><span class="sxs-lookup"><span data-stu-id="50724-162">0x10</span></span> | <span data-ttu-id="50724-163">Sabit listesini, sınıfın kendisinde tanımlanan veya değiştirilen özelliklerle sınırlayın.</span><span class="sxs-lookup"><span data-stu-id="50724-163">Limit the enumeration to properties that are defined or modified in the class itself.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="50724-164">0x20</span><span class="sxs-lookup"><span data-stu-id="50724-164">0x20</span></span> | <span data-ttu-id="50724-165">Sabit listesini temel sınıflardan devralınan özelliklerle sınırlayın.</span><span class="sxs-lookup"><span data-stu-id="50724-165">Limit the enumeration to properties that are inherited from base classes.</span></span> |

## <a name="requirements"></a><span data-ttu-id="50724-166">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="50724-166">Requirements</span></span>  

 <span data-ttu-id="50724-167">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="50724-167">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50724-168">**Üst bilgi:** WMINet_Utils. IDL</span><span class="sxs-lookup"><span data-stu-id="50724-168">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="50724-169">**.NET Framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="50724-169">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50724-170">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="50724-170">See also</span></span>

- [<span data-ttu-id="50724-171">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="50724-171">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
