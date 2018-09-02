---
title: BeginEnumeration işlevi (yönetilmeyen API Başvurusu)
description: BeginEnumeration işlevi Numaralayıcı sabit başlangıcına sıfırlar.
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 08406f7d93671b406b3c7cd8719a7a0e5e423184
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43392363"
---
# <a name="beginenumeration-function"></a><span data-ttu-id="bba61-103">BeginEnumeration işlevi</span><span class="sxs-lookup"><span data-stu-id="bba61-103">BeginEnumeration function</span></span>
<span data-ttu-id="bba61-104">Bir numaralandırıcı geri numaralandırma başlangıç durumuna sıfırlar.</span><span class="sxs-lookup"><span data-stu-id="bba61-104">Resets an enumerator back to the beginning of the enumeration.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="bba61-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bba61-105">Syntax</span></span>  
  
```  
HRESULT BeginEnumeration (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LONG              lEnumFlags
); 
```  

## <a name="parameters"></a><span data-ttu-id="bba61-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bba61-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="bba61-107">[in] Bu parametre kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="bba61-107">[in] This parameter is unused.</span></span>

<span data-ttu-id="bba61-108">`ptr` [in] Bir işaretçi bir [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneği.</span><span class="sxs-lookup"><span data-stu-id="bba61-108">`ptr` [in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lEnumFlags`  
<span data-ttu-id="bba61-109">[in] Bayrakları veya açıklanan değerler Bitsel bir birleşimi [açıklamalar](#remarks) numaralandırmada özellikleri denetleyen bölümü.</span><span class="sxs-lookup"><span data-stu-id="bba61-109">[in] A bitwise combination of the flags or values described in the [Remarks](#remarks) section that controls the properties included in the enumeration.</span></span>

## <a name="return-value"></a><span data-ttu-id="bba61-110">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="bba61-110">Return value</span></span>

<span data-ttu-id="bba61-111">Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üst bilgi dosyası veya tanımlayabilirsiniz bunları sabitleri kodunuzda:</span><span class="sxs-lookup"><span data-stu-id="bba61-111">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="bba61-112">Sabit</span><span class="sxs-lookup"><span data-stu-id="bba61-112">Constant</span></span>  |<span data-ttu-id="bba61-113">Değer</span><span class="sxs-lookup"><span data-stu-id="bba61-113">Value</span></span>  |<span data-ttu-id="bba61-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bba61-114">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="bba61-115">0x80041008</span><span class="sxs-lookup"><span data-stu-id="bba61-115">0x80041008</span></span> | <span data-ttu-id="bba61-116">Bayrakları birleşimi `lEnumFlags` geçersiz veya geçersiz bir bağımsız değişken belirtildi.</span><span class="sxs-lookup"><span data-stu-id="bba61-116">The combination of flags in `lEnumFlags` is invalid, or an invalid argument was specified.</span></span> |
|`WBEM_E_UNEXPECTED` | <span data-ttu-id="bba61-117">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="bba61-117">0x8004101d</span></span> | <span data-ttu-id="bba61-118">İkinci çağrı `BeginEnumeration` bir çağrı göndermelisiniz olmadan yapılan [ `EndEnumeration` ](endenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="bba61-118">A second call to `BeginEnumeration` was made without an intervening call to [`EndEnumeration`](endenumeration.md).</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="bba61-119">0x80041006</span><span class="sxs-lookup"><span data-stu-id="bba61-119">0x80041006</span></span> | <span data-ttu-id="bba61-120">Yeni bir numaralandırma başlatmak yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="bba61-120">Not enough memory is available to begin a new enumeration.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="bba61-121">0</span><span class="sxs-lookup"><span data-stu-id="bba61-121">0</span></span> | <span data-ttu-id="bba61-122">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="bba61-122">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="bba61-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bba61-123">Remarks</span></span>

<span data-ttu-id="bba61-124">Bu işlev bir çağrı sarılır [IWbemClassObject::BeginEnumeration](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="bba61-124">This function wraps a call to the [IWbemClassObject::BeginEnumeration](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) method.</span></span>

<span data-ttu-id="bba61-125">Olarak geçirilen bayraklar `lEnumFlags` bağımsız değişken tanımlanmış *WbemCli.h* üst bilgi dosyası veya tanımlayabilirsiniz bunları sabitleri kodunuzda.</span><span class="sxs-lookup"><span data-stu-id="bba61-125">The flags that can be passed as the `lEnumFlags` argument are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span>  <span data-ttu-id="bba61-126">Herhangi diğer bir grup bayrağı ile her bir gruptan bir bayrak birleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bba61-126">You can combine one flag from each group with any flag from any other group.</span></span> <span data-ttu-id="bba61-127">Ancak, aynı grup bayrakları birbirini dışlar.</span><span class="sxs-lookup"><span data-stu-id="bba61-127">However, flags from the same group are mutually exclusive.</span></span> 

<span data-ttu-id="bba61-128">**Grup 1**</span><span class="sxs-lookup"><span data-stu-id="bba61-128">**Group 1**</span></span>

|<span data-ttu-id="bba61-129">Sabit</span><span class="sxs-lookup"><span data-stu-id="bba61-129">Constant</span></span>  |<span data-ttu-id="bba61-130">Değer</span><span class="sxs-lookup"><span data-stu-id="bba61-130">Value</span></span>  |<span data-ttu-id="bba61-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bba61-131">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | <span data-ttu-id="bba61-132">0x4</span><span class="sxs-lookup"><span data-stu-id="bba61-132">0x4</span></span> | <span data-ttu-id="bba61-133">Yalnızca anahtar oluşturan özellikleri içerir.</span><span class="sxs-lookup"><span data-stu-id="bba61-133">Include properties that constitute the key only.</span></span> |
|`WBEM_FLAG_REFS_ONLY` | <span data-ttu-id="bba61-134">0x8</span><span class="sxs-lookup"><span data-stu-id="bba61-134">0x8</span></span> | <span data-ttu-id="bba61-135">Nesne başvuruları yalnızca özellikleri içerir.</span><span class="sxs-lookup"><span data-stu-id="bba61-135">Include properties that are object references only.</span></span> |

<span data-ttu-id="bba61-136">**Grup 2**</span><span class="sxs-lookup"><span data-stu-id="bba61-136">**Group 2**</span></span>

<span data-ttu-id="bba61-137">Sabit</span><span class="sxs-lookup"><span data-stu-id="bba61-137">Constant</span></span>  |<span data-ttu-id="bba61-138">Değer</span><span class="sxs-lookup"><span data-stu-id="bba61-138">Value</span></span>  |<span data-ttu-id="bba61-139">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bba61-139">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_SYSTEM_ONLY` | <span data-ttu-id="bba61-140">0x30</span><span class="sxs-lookup"><span data-stu-id="bba61-140">0x30</span></span> | <span data-ttu-id="bba61-141">Sistem özellikleri yalnızca numaralandırma sınırlayın.</span><span class="sxs-lookup"><span data-stu-id="bba61-141">Limit the enumeration to system properties only.</span></span> |
|`WBEM_FLAG_NONSYSTEM_ONLY` | <span data-ttu-id="bba61-142">0x40</span><span class="sxs-lookup"><span data-stu-id="bba61-142">0x40</span></span> | <span data-ttu-id="bba61-143">Yerel ve yayılan özellikleri içerir, ancak Sistem özellikleri sabit listesinden alınmış hariç.</span><span class="sxs-lookup"><span data-stu-id="bba61-143">Include local and propagated properties but exclude system properties from the enumeration.</span></span> |

<span data-ttu-id="bba61-144">Sınıflar için:</span><span class="sxs-lookup"><span data-stu-id="bba61-144">For classes:</span></span>

<span data-ttu-id="bba61-145">Sabit</span><span class="sxs-lookup"><span data-stu-id="bba61-145">Constant</span></span>  |<span data-ttu-id="bba61-146">Değer</span><span class="sxs-lookup"><span data-stu-id="bba61-146">Value</span></span>  |<span data-ttu-id="bba61-147">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bba61-147">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_CLASS_OVERRIDES_ONLY` | <span data-ttu-id="bba61-148">0x100</span><span class="sxs-lookup"><span data-stu-id="bba61-148">0x100</span></span> | <span data-ttu-id="bba61-149">Sınıf tanımında geçersiz kılınan özellikleri için sabit sınırlar.</span><span class="sxs-lookup"><span data-stu-id="bba61-149">Limit the enumeration to properties overridden in the class definition.</span></span> |
|`WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` | <span data-ttu-id="bba61-150">0x100</span><span class="sxs-lookup"><span data-stu-id="bba61-150">0x100</span></span> | <span data-ttu-id="bba61-151">Geçerli sınıf tanımında geçersiz kılınan özellikleri ve yeni özellikleri sınıfta tanımlanan sabit sınırlar.</span><span class="sxs-lookup"><span data-stu-id="bba61-151">Limit the enumeration to properties overridden in the current class definition and to new properties defined in the class.</span></span> |
| `WBEM_MASK_CLASS_CONDITION` | <span data-ttu-id="bba61-152">0x300</span><span class="sxs-lookup"><span data-stu-id="bba61-152">0x300</span></span> | <span data-ttu-id="bba61-153">Karşı uygulamak için bir maske (yerine bir bayrak) bir `lEnumFlags` ya da denetlenecek değer `WBEM_FLAG_CLASS_OVERRIDES_ONLY` veya `WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="bba61-153">A mask (rather than a flag) to apply against a `lEnumFlags` value to check if either `WBEM_FLAG_CLASS_OVERRIDES_ONLY` or `WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` is set.</span></span> |
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="bba61-154">0x10</span><span class="sxs-lookup"><span data-stu-id="bba61-154">0x10</span></span> | <span data-ttu-id="bba61-155">Sabit listesi sınıfı, değiştiren veya tanımlanan özelliklere sınırlayın.</span><span class="sxs-lookup"><span data-stu-id="bba61-155">Limit the enumeration to properties that are defined or modified in the class itself.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="bba61-156">0x20</span><span class="sxs-lookup"><span data-stu-id="bba61-156">0x20</span></span> | <span data-ttu-id="bba61-157">Temel sınıftan devralınan özellikler için sabit sınırlar.</span><span class="sxs-lookup"><span data-stu-id="bba61-157">Limit the enumeration to properties that are inherited from base classes.</span></span> |

<span data-ttu-id="bba61-158">İçin örnek:</span><span class="sxs-lookup"><span data-stu-id="bba61-158">For instances:</span></span>

<span data-ttu-id="bba61-159">Sabit</span><span class="sxs-lookup"><span data-stu-id="bba61-159">Constant</span></span>  |<span data-ttu-id="bba61-160">Değer</span><span class="sxs-lookup"><span data-stu-id="bba61-160">Value</span></span>  |<span data-ttu-id="bba61-161">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bba61-161">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="bba61-162">0x10</span><span class="sxs-lookup"><span data-stu-id="bba61-162">0x10</span></span> | <span data-ttu-id="bba61-163">Sabit listesi sınıfı, değiştiren veya tanımlanan özelliklere sınırlayın.</span><span class="sxs-lookup"><span data-stu-id="bba61-163">Limit the enumeration to properties that are defined or modified in the class itself.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="bba61-164">0x20</span><span class="sxs-lookup"><span data-stu-id="bba61-164">0x20</span></span> | <span data-ttu-id="bba61-165">Temel sınıftan devralınan özellikler için sabit sınırlar.</span><span class="sxs-lookup"><span data-stu-id="bba61-165">Limit the enumeration to properties that are inherited from base classes.</span></span> |


## <a name="requirements"></a><span data-ttu-id="bba61-166">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bba61-166">Requirements</span></span>  
 <span data-ttu-id="bba61-167">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bba61-167">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bba61-168">**Başlık:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="bba61-168">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="bba61-169">**.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="bba61-169">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bba61-170">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bba61-170">See also</span></span>  
[<span data-ttu-id="bba61-171">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="bba61-171">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
