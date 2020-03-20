---
title: Başlama fonksiyonu (Yönetilmeyen API Başvurusu)
description: BeginEnumeration işlevi numaralandırmanın başlangıcına kadar bir numaralandırıcıyı sıfırlar
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
ms.openlocfilehash: eac23916bd78ec3970a87566e2d2f4d79b379824
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176883"
---
# <a name="beginenumeration-function"></a><span data-ttu-id="2e4f5-103">BeginEnumeration işlevi</span><span class="sxs-lookup"><span data-stu-id="2e4f5-103">BeginEnumeration function</span></span>
<span data-ttu-id="2e4f5-104">Numaralandırmanın başına kadar bir numaralandırıcıyı sıfırlar.</span><span class="sxs-lookup"><span data-stu-id="2e4f5-104">Resets an enumerator back to the beginning of the enumeration.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="2e4f5-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2e4f5-105">Syntax</span></span>  
  
```cpp  
HRESULT BeginEnumeration (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LONG              lEnumFlags
);
```  

## <a name="parameters"></a><span data-ttu-id="2e4f5-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2e4f5-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="2e4f5-107">[içinde] Bu parametre kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="2e4f5-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="2e4f5-108">[içinde] [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneğine işaretçi.</span><span class="sxs-lookup"><span data-stu-id="2e4f5-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lEnumFlags`\
<span data-ttu-id="2e4f5-109">[içinde] [Numaralandırmada](#remarks) yer alan özellikleri denetleyen Açıklamalar bölümünde açıklanan bayrakların veya değerlerin bityişli bir birleşimi.</span><span class="sxs-lookup"><span data-stu-id="2e4f5-109">[in] A bitwise combination of the flags or values described in the [Remarks](#remarks) section that controls the properties included in the enumeration.</span></span>

## <a name="return-value"></a><span data-ttu-id="2e4f5-110">Döndürülen değer</span><span class="sxs-lookup"><span data-stu-id="2e4f5-110">Return value</span></span>

<span data-ttu-id="2e4f5-111">Bu işlev tarafından döndürülen aşağıdaki değerler *WbemCli.h* üstbilgi dosyasında tanımlanır veya bunları kodunuzdaki sabitler olarak tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="2e4f5-111">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="2e4f5-112">Sabit</span><span class="sxs-lookup"><span data-stu-id="2e4f5-112">Constant</span></span>  |<span data-ttu-id="2e4f5-113">Değer</span><span class="sxs-lookup"><span data-stu-id="2e4f5-113">Value</span></span>  |<span data-ttu-id="2e4f5-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2e4f5-114">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="2e4f5-115">0x80041008</span><span class="sxs-lookup"><span data-stu-id="2e4f5-115">0x80041008</span></span> | <span data-ttu-id="2e4f5-116">Bulunan bayrakların `lEnumFlags` birleşimi geçersiz veya geçersiz bir bağımsız değişken belirtilmiş.</span><span class="sxs-lookup"><span data-stu-id="2e4f5-116">The combination of flags in `lEnumFlags` is invalid, or an invalid argument was specified.</span></span> |
|`WBEM_E_UNEXPECTED` | <span data-ttu-id="2e4f5-117">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="2e4f5-117">0x8004101d</span></span> | <span data-ttu-id="2e4f5-118">İkinci bir `BeginEnumeration` arama, müdahale etmeden [`EndEnumeration`](endenumeration.md)yapıldı.</span><span class="sxs-lookup"><span data-stu-id="2e4f5-118">A second call to `BeginEnumeration` was made without an intervening call to [`EndEnumeration`](endenumeration.md).</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="2e4f5-119">0x80041006</span><span class="sxs-lookup"><span data-stu-id="2e4f5-119">0x80041006</span></span> | <span data-ttu-id="2e4f5-120">Yeni bir numaralandırmabaşlatmak için yeterli bellek kullanılabilir değil.</span><span class="sxs-lookup"><span data-stu-id="2e4f5-120">Not enough memory is available to begin a new enumeration.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="2e4f5-121">0</span><span class="sxs-lookup"><span data-stu-id="2e4f5-121">0</span></span> | <span data-ttu-id="2e4f5-122">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="2e4f5-122">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="2e4f5-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2e4f5-123">Remarks</span></span>

<span data-ttu-id="2e4f5-124">Bu [işlev, IWbemClassObject::BeginEnumeration](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) yöntemine bir çağrı yıkıyor.</span><span class="sxs-lookup"><span data-stu-id="2e4f5-124">This function wraps a call to the [IWbemClassObject::BeginEnumeration](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) method.</span></span>

<span data-ttu-id="2e4f5-125">`lEnumFlags` Bağımsız değişken *WbemCli.h* üstbilgi dosyasında tanımlandığı şekilde geçirilebilen bayraklar veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2e4f5-125">The flags that can be passed as the `lEnumFlags` argument are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span>  <span data-ttu-id="2e4f5-126">Her gruptan bir bayrağı başka bir gruptan herhangi bir bayrakla birleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2e4f5-126">You can combine one flag from each group with any flag from any other group.</span></span> <span data-ttu-id="2e4f5-127">Ancak, aynı grubun bayrakları birbirini dışlar.</span><span class="sxs-lookup"><span data-stu-id="2e4f5-127">However, flags from the same group are mutually exclusive.</span></span>

<span data-ttu-id="2e4f5-128">**Grup 1**</span><span class="sxs-lookup"><span data-stu-id="2e4f5-128">**Group 1**</span></span>

|<span data-ttu-id="2e4f5-129">Sabit</span><span class="sxs-lookup"><span data-stu-id="2e4f5-129">Constant</span></span>  |<span data-ttu-id="2e4f5-130">Değer</span><span class="sxs-lookup"><span data-stu-id="2e4f5-130">Value</span></span>  |<span data-ttu-id="2e4f5-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2e4f5-131">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | <span data-ttu-id="2e4f5-132">0x4</span><span class="sxs-lookup"><span data-stu-id="2e4f5-132">0x4</span></span> | <span data-ttu-id="2e4f5-133">Yalnızca anahtarı oluşturan özellikleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2e4f5-133">Include properties that constitute the key only.</span></span> |
|`WBEM_FLAG_REFS_ONLY` | <span data-ttu-id="2e4f5-134">0x8</span><span class="sxs-lookup"><span data-stu-id="2e4f5-134">0x8</span></span> | <span data-ttu-id="2e4f5-135">Yalnızca nesne başvuruları olan özellikleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2e4f5-135">Include properties that are object references only.</span></span> |

<span data-ttu-id="2e4f5-136">**Grup 2**</span><span class="sxs-lookup"><span data-stu-id="2e4f5-136">**Group 2**</span></span>

<span data-ttu-id="2e4f5-137">Sabit</span><span class="sxs-lookup"><span data-stu-id="2e4f5-137">Constant</span></span>  |<span data-ttu-id="2e4f5-138">Değer</span><span class="sxs-lookup"><span data-stu-id="2e4f5-138">Value</span></span>  |<span data-ttu-id="2e4f5-139">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2e4f5-139">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_SYSTEM_ONLY` | <span data-ttu-id="2e4f5-140">0x30</span><span class="sxs-lookup"><span data-stu-id="2e4f5-140">0x30</span></span> | <span data-ttu-id="2e4f5-141">Numaralandırmayı yalnızca sistem özellikleriyle sınırlandırın.</span><span class="sxs-lookup"><span data-stu-id="2e4f5-141">Limit the enumeration to system properties only.</span></span> |
|`WBEM_FLAG_NONSYSTEM_ONLY` | <span data-ttu-id="2e4f5-142">0x40</span><span class="sxs-lookup"><span data-stu-id="2e4f5-142">0x40</span></span> | <span data-ttu-id="2e4f5-143">Yerel ve yayılan özellikleri ekleyin, ancak sistem özelliklerini numaralandırmadan hariç tutar.</span><span class="sxs-lookup"><span data-stu-id="2e4f5-143">Include local and propagated properties but exclude system properties from the enumeration.</span></span> |

<span data-ttu-id="2e4f5-144">Sınıflar için:</span><span class="sxs-lookup"><span data-stu-id="2e4f5-144">For classes:</span></span>

<span data-ttu-id="2e4f5-145">Sabit</span><span class="sxs-lookup"><span data-stu-id="2e4f5-145">Constant</span></span>  |<span data-ttu-id="2e4f5-146">Değer</span><span class="sxs-lookup"><span data-stu-id="2e4f5-146">Value</span></span>  |<span data-ttu-id="2e4f5-147">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2e4f5-147">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_CLASS_OVERRIDES_ONLY` | <span data-ttu-id="2e4f5-148">0x100</span><span class="sxs-lookup"><span data-stu-id="2e4f5-148">0x100</span></span> | <span data-ttu-id="2e4f5-149">Numaralandırmayı sınıf tanımında geçersiz kılınan özelliklerle sınırlandırın.</span><span class="sxs-lookup"><span data-stu-id="2e4f5-149">Limit the enumeration to properties overridden in the class definition.</span></span> |
|`WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` | <span data-ttu-id="2e4f5-150">0x100</span><span class="sxs-lookup"><span data-stu-id="2e4f5-150">0x100</span></span> | <span data-ttu-id="2e4f5-151">Numaralandırmayı geçerli sınıf tanımında geçersiz kılınan özelliklerle ve sınıfta tanımlanan yeni özelliklerle sınırlandırın.</span><span class="sxs-lookup"><span data-stu-id="2e4f5-151">Limit the enumeration to properties overridden in the current class definition and to new properties defined in the class.</span></span> |
| `WBEM_MASK_CLASS_CONDITION` | <span data-ttu-id="2e4f5-152">0x300</span><span class="sxs-lookup"><span data-stu-id="2e4f5-152">0x300</span></span> | <span data-ttu-id="2e4f5-153">Bir maske (bayrak yerine) bir `lEnumFlags` değer karşı ya `WBEM_FLAG_CLASS_OVERRIDES_ONLY` `WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` da ayarlanmış olup olmadığını kontrol etmek için uygulamak için.</span><span class="sxs-lookup"><span data-stu-id="2e4f5-153">A mask (rather than a flag) to apply against a `lEnumFlags` value to check if either `WBEM_FLAG_CLASS_OVERRIDES_ONLY` or `WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` is set.</span></span> |
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="2e4f5-154">0x10</span><span class="sxs-lookup"><span data-stu-id="2e4f5-154">0x10</span></span> | <span data-ttu-id="2e4f5-155">Numaralandırmayı sınıfın kendisinde tanımlanan veya değiştirilen özelliklerle sınırlandırın.</span><span class="sxs-lookup"><span data-stu-id="2e4f5-155">Limit the enumeration to properties that are defined or modified in the class itself.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="2e4f5-156">0x20</span><span class="sxs-lookup"><span data-stu-id="2e4f5-156">0x20</span></span> | <span data-ttu-id="2e4f5-157">Numaralandırmayı temel sınıflardan devralınan özelliklerle sınırlandırın.</span><span class="sxs-lookup"><span data-stu-id="2e4f5-157">Limit the enumeration to properties that are inherited from base classes.</span></span> |

<span data-ttu-id="2e4f5-158">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="2e4f5-158">For instances:</span></span>

<span data-ttu-id="2e4f5-159">Sabit</span><span class="sxs-lookup"><span data-stu-id="2e4f5-159">Constant</span></span>  |<span data-ttu-id="2e4f5-160">Değer</span><span class="sxs-lookup"><span data-stu-id="2e4f5-160">Value</span></span>  |<span data-ttu-id="2e4f5-161">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2e4f5-161">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="2e4f5-162">0x10</span><span class="sxs-lookup"><span data-stu-id="2e4f5-162">0x10</span></span> | <span data-ttu-id="2e4f5-163">Numaralandırmayı sınıfın kendisinde tanımlanan veya değiştirilen özelliklerle sınırlandırın.</span><span class="sxs-lookup"><span data-stu-id="2e4f5-163">Limit the enumeration to properties that are defined or modified in the class itself.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="2e4f5-164">0x20</span><span class="sxs-lookup"><span data-stu-id="2e4f5-164">0x20</span></span> | <span data-ttu-id="2e4f5-165">Numaralandırmayı temel sınıflardan devralınan özelliklerle sınırlandırın.</span><span class="sxs-lookup"><span data-stu-id="2e4f5-165">Limit the enumeration to properties that are inherited from base classes.</span></span> |

## <a name="requirements"></a><span data-ttu-id="2e4f5-166">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2e4f5-166">Requirements</span></span>  
 <span data-ttu-id="2e4f5-167">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2e4f5-167">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e4f5-168">**Üstbilgi:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="2e4f5-168">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="2e4f5-169">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="2e4f5-169">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e4f5-170">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2e4f5-170">See also</span></span>

- [<span data-ttu-id="2e4f5-171">WMI ve Performans Sayaçları (Yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="2e4f5-171">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
