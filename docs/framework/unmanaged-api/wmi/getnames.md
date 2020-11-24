---
title: GetNames işlevi (yönetilmeyen API Başvurusu)
description: GetNames işlevi bir nesnenin özelliklerinin adlarını alır.
ms.date: 11/06/2017
api_name:
- GetNames
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetNames
helpviewer_keywords:
- GetNames function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: fd889158e61b86f42d88bcf86eda7d816277e6ac
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95687664"
---
# <a name="getnames-function"></a><span data-ttu-id="e983b-103">GetNames işlevi</span><span class="sxs-lookup"><span data-stu-id="e983b-103">GetNames function</span></span>

<span data-ttu-id="e983b-104">Bir nesnenin özelliklerinin bir alt kümesini ya da tümünü alır.</span><span class="sxs-lookup"><span data-stu-id="e983b-104">Retrieves either a subset or all of the names of the properties of an object.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="e983b-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="e983b-105">Syntax</span></span>  
  
```cpp  
HRESULT GetNames (
   [in] int                 vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LPCWSTR             wszQualifierName,
   [in] LONG                lFlags,
   [in] VARIANT*            pQualifierValue,
   [out] SAFEARRAY (BSTR)** pstrNames
);
```  

## <a name="parameters"></a><span data-ttu-id="e983b-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e983b-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="e983b-107">'ndaki Bu parametre kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="e983b-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="e983b-108">'ndaki [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneğine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e983b-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszQualifierName`  
<span data-ttu-id="e983b-109">'ndaki Bir `LPCWSTR` filtrenin parçası olarak çalışan bir niteleyici adı belirten geçerli bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="e983b-109">[in] A pointer to a valid `LPCWSTR` that specifies a qualifier name that operates as part of a filter.</span></span> <span data-ttu-id="e983b-110">Daha fazla bilgi için, [açıklamalar](#remarks) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="e983b-110">For more information, see the [Remarks](#remarks) section.</span></span> <span data-ttu-id="e983b-111">Bu parametre olabilir `null` .</span><span class="sxs-lookup"><span data-stu-id="e983b-111">This parameter can be `null`.</span></span>

`lFlags`  
<span data-ttu-id="e983b-112">'ndaki Bit alanlarının birleşimi.</span><span class="sxs-lookup"><span data-stu-id="e983b-112">[in] A combination of bit fields.</span></span> <span data-ttu-id="e983b-113">Daha fazla bilgi için, [açıklamalar](#remarks) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="e983b-113">For more information, see the [Remarks](#remarks) section.</span></span>

<span data-ttu-id="e983b-114">`pQualifierValue` 'ndaki `VARIANT` Filtre değerine başlatılan geçerli bir yapıya yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e983b-114">`pQualifierValue` [in] A pointer to a valid `VARIANT` structure initialized to a filter value.</span></span> <span data-ttu-id="e983b-115">Bu parametre olabilir `null` .</span><span class="sxs-lookup"><span data-stu-id="e983b-115">This parameter can be `null`.</span></span>

`pstrNames`  
<span data-ttu-id="e983b-116">dışı `SAFEARRAY` Özellik adlarını içeren bir yapı.</span><span class="sxs-lookup"><span data-stu-id="e983b-116">[out] A `SAFEARRAY` structure that contains property names.</span></span> <span data-ttu-id="e983b-117">Girişte, bu parametrenin her zaman bir işaretçi olması gerekir `null` .</span><span class="sxs-lookup"><span data-stu-id="e983b-117">On entry, this parameter must always be a pointer to `null`.</span></span> <span data-ttu-id="e983b-118">Daha fazla bilgi için [açıklamalar](#remarks) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="e983b-118">See the [Remarks](#remarks) section for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="e983b-119">Döndürülen değer</span><span class="sxs-lookup"><span data-stu-id="e983b-119">Return value</span></span>

<span data-ttu-id="e983b-120">Bu işlev tarafından döndürülen aşağıdaki değerler, *Wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e983b-120">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="e983b-121">Sabit</span><span class="sxs-lookup"><span data-stu-id="e983b-121">Constant</span></span>  |<span data-ttu-id="e983b-122">Değer</span><span class="sxs-lookup"><span data-stu-id="e983b-122">Value</span></span>  |<span data-ttu-id="e983b-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e983b-123">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="e983b-124">0x80041001</span><span class="sxs-lookup"><span data-stu-id="e983b-124">0x80041001</span></span> | <span data-ttu-id="e983b-125">Genel bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="e983b-125">There has been a general failure.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="e983b-126">0x80041008</span><span class="sxs-lookup"><span data-stu-id="e983b-126">0x80041008</span></span> | <span data-ttu-id="e983b-127">Bir veya daha fazla parametre geçerli değil veya bayrakların ve parametrelerin yanlış birleşimi belirtildi.</span><span class="sxs-lookup"><span data-stu-id="e983b-127">One or more parameters are not valid, or an incorrect combination of flags and parameters was specified.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="e983b-128">0x80041006</span><span class="sxs-lookup"><span data-stu-id="e983b-128">0x80041006</span></span> | <span data-ttu-id="e983b-129">İşlemi gerçekleştirmek için yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="e983b-129">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="e983b-130">0</span><span class="sxs-lookup"><span data-stu-id="e983b-130">0</span></span> | <span data-ttu-id="e983b-131">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="e983b-131">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="e983b-132">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e983b-132">Remarks</span></span>

<span data-ttu-id="e983b-133">Bu işlev, [IWbemClassObject:: GetNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getnames) yöntemine bir çağrı kaydırır.</span><span class="sxs-lookup"><span data-stu-id="e983b-133">This function wraps a call to the [IWbemClassObject::GetNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getnames) method.</span></span>

<span data-ttu-id="e983b-134">Döndürülen adlı ad, bayrakların ve parametrelerin birleşimiyle denetlenir.</span><span class="sxs-lookup"><span data-stu-id="e983b-134">The named returned are controlled by a combination of flags and parameters.</span></span> <span data-ttu-id="e983b-135">Örneğin, işlev tüm özelliklerin adlarını veya yalnızca anahtar özelliklerinin adlarını döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="e983b-135">For example, the function can return the names of all properties or only the names of the key properties.</span></span>  <span data-ttu-id="e983b-136">Birincil filtre `lFlags` parametresinde belirtilir ve diğer parametreler buna bağlı olarak farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="e983b-136">The primary filter is specified in the `lFlags` parameter, and the other parameters vary depending on it.</span></span>

<span data-ttu-id="e983b-137">İçindeki bayrak değerleri `lFlags` bit alanlardır</span><span class="sxs-lookup"><span data-stu-id="e983b-137">The flag values in `lFlags` are bit fields</span></span>

<span data-ttu-id="e983b-138">Bağımsız değişken olarak geçirilebilecek bayraklar, `lEnumFlags` *Wbemcli. h* üstbilgi dosyasında tanımlanan bit alanlardır veya kodunuzda sabitler olarak tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e983b-138">The flags that can be passed as the `lEnumFlags` argument are bit fields that are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span>  <span data-ttu-id="e983b-139">Her bir grup için herhangi bir bayrak ile bir bayrak birleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e983b-139">You can combine one flag from each group with any flag from any other group.</span></span> <span data-ttu-id="e983b-140">Ancak, aynı gruptaki Bayraklar birbirini dışlıyor.</span><span class="sxs-lookup"><span data-stu-id="e983b-140">However, flags from the same group are mutually exclusive.</span></span>

| <span data-ttu-id="e983b-141">Grup 1 bayrakları</span><span class="sxs-lookup"><span data-stu-id="e983b-141">Group 1 flags</span></span> |<span data-ttu-id="e983b-142">Değer</span><span class="sxs-lookup"><span data-stu-id="e983b-142">Value</span></span>  |<span data-ttu-id="e983b-143">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e983b-143">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_ALWAYS` | <span data-ttu-id="e983b-144">0</span><span class="sxs-lookup"><span data-stu-id="e983b-144">0</span></span> | <span data-ttu-id="e983b-145">Tüm özellik adlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="e983b-145">Return all property names.</span></span> <span data-ttu-id="e983b-146">`strQualifierName` ve `pQualifierVal` kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="e983b-146">`strQualifierName` and `pQualifierVal` are unused.</span></span> |
| `WBEM_FLAG_ONLY_IF_TRUE` | <span data-ttu-id="e983b-147">1</span><span class="sxs-lookup"><span data-stu-id="e983b-147">1</span></span> | <span data-ttu-id="e983b-148">Yalnızca parametresi tarafından belirtilen ad niteleyicisi olan özellikleri döndürür `strQualifierName` .</span><span class="sxs-lookup"><span data-stu-id="e983b-148">Return only properties that have a qualifier of the name specified by the `strQualifierName` parameter.</span></span> <span data-ttu-id="e983b-149">Bu bayrak kullanılırsa, belirtmeniz gerekir `strQualifierName` .</span><span class="sxs-lookup"><span data-stu-id="e983b-149">If this flag is used, you must specify `strQualifierName`.</span></span> |
|`WBEM_FLAG_ONLY_IF_FALSE` | <span data-ttu-id="e983b-150">2</span><span class="sxs-lookup"><span data-stu-id="e983b-150">2</span></span> |  <span data-ttu-id="e983b-151">Yalnızca parametresi tarafından belirtilen adın niteleyicisi olmayan özellikleri döndürür `strQualifierName` .</span><span class="sxs-lookup"><span data-stu-id="e983b-151">Return only properties that do not have a qualifier of the name specified by the `strQualifierName` parameter.</span></span> <span data-ttu-id="e983b-152">Bu bayrak kullanılırsa, belirtmeniz gerekir `strQualifierName` .</span><span class="sxs-lookup"><span data-stu-id="e983b-152">If this flag is used, you must specify `strQualifierName`.</span></span> |
|`WBEM_FLAG_ONLY_IF_IDENTICAL` | <span data-ttu-id="e983b-153">3</span><span class="sxs-lookup"><span data-stu-id="e983b-153">3</span></span> | <span data-ttu-id="e983b-154">Yalnızca parametresi tarafından belirtilen ad niteleyicisi olan `wszQualifierName` ve aynı zamanda yapı tarafından belirtilen bir değere sahip olan özellikleri döndürür `pQualifierVal` .</span><span class="sxs-lookup"><span data-stu-id="e983b-154">Return only properties that have a qualifier of the name specified by the `wszQualifierName` parameter and also have a value identical to that specified by the `pQualifierVal` structure.</span></span> <span data-ttu-id="e983b-155">Bu bayrak kullanılırsa, hem a hem de belirtmeniz gerekir `wszQualifierName` `pQualifierValue` .</span><span class="sxs-lookup"><span data-stu-id="e983b-155">If this flag is used, you must specify both a `wszQualifierName` and a `pQualifierValue`.</span></span> |

| <span data-ttu-id="e983b-156">Grup 2 bayrakları</span><span class="sxs-lookup"><span data-stu-id="e983b-156">Group 2 flags</span></span> |<span data-ttu-id="e983b-157">Değer</span><span class="sxs-lookup"><span data-stu-id="e983b-157">Value</span></span>  |<span data-ttu-id="e983b-158">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e983b-158">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | <span data-ttu-id="e983b-159">4,</span><span class="sxs-lookup"><span data-stu-id="e983b-159">0x4</span></span> | <span data-ttu-id="e983b-160">Yalnızca anahtarları tanımlayan özelliklerin adlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="e983b-160">Return only the names of properties that define the keys.</span></span> |
|`WBEM_FLAG_REFS_ONLY` | <span data-ttu-id="e983b-161">0x8</span><span class="sxs-lookup"><span data-stu-id="e983b-161">0x8</span></span> | <span data-ttu-id="e983b-162">Yalnızca nesne başvuruları olan özellik adlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="e983b-162">Return only property names that are object references.</span></span> |

| <span data-ttu-id="e983b-163">Grup 3 bayrakları</span><span class="sxs-lookup"><span data-stu-id="e983b-163">Group 3 flags</span></span> |<span data-ttu-id="e983b-164">Değer</span><span class="sxs-lookup"><span data-stu-id="e983b-164">Value</span></span>  |<span data-ttu-id="e983b-165">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e983b-165">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="e983b-166">0x10</span><span class="sxs-lookup"><span data-stu-id="e983b-166">0x10</span></span> | <span data-ttu-id="e983b-167">Yalnızca en türetilmiş sınıfa ait olan özellik adlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="e983b-167">Return only property names that belong to the most derived class.</span></span> <span data-ttu-id="e983b-168">Üst sınıflardan özellikleri dışlayın.</span><span class="sxs-lookup"><span data-stu-id="e983b-168">Exclude properties from the parent classes.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="e983b-169">0x20</span><span class="sxs-lookup"><span data-stu-id="e983b-169">0x20</span></span> | <span data-ttu-id="e983b-170">Yalnızca üst sınıflara ait olan özellik adlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="e983b-170">Return only property names that belong to the parent classes.</span></span> |
|`WBEM_FLAG_SYSTEM_ONLY` | <span data-ttu-id="e983b-171">0x30</span><span class="sxs-lookup"><span data-stu-id="e983b-171">0x30</span></span> | <span data-ttu-id="e983b-172">Yalnızca sistem özelliklerinin adlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="e983b-172">Return only the names of system properties.</span></span> |
|`WBEM_FLAG_NONSYSTEM_ONLY` | <span data-ttu-id="e983b-173">0x40</span><span class="sxs-lookup"><span data-stu-id="e983b-173">0x40</span></span> | <span data-ttu-id="e983b-174">Yalnızca sistem dışı özelliklerin adlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="e983b-174">Return only the names of non-system properties.</span></span> |

<span data-ttu-id="e983b-175">İşlevi, döndürürse her zaman yeni bir ayırır `SAFEARRAY` `WBEM_S_NO_ERROR` ve `pstrNames` her zaman onu işaret etmek üzere ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="e983b-175">The function always allocates a new `SAFEARRAY` if it returns `WBEM_S_NO_ERROR`, and `pstrNames` is always set to point to it.</span></span> <span data-ttu-id="e983b-176">Belirtilen filtrelerle eşleşen hiçbir özellik yoksa döndürülen dizide 0 öğesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="e983b-176">The returned array can have 0 elements if no properties match the specified filters.</span></span> <span data-ttu-id="e983b-177">İşlev dışında bir değer döndürürse `WBM_S_NO_ERROR` , yeni bir `SAFEARRAY` Yapı döndürülmez.</span><span class="sxs-lookup"><span data-stu-id="e983b-177">If the function returns an value other than `WBM_S_NO_ERROR`, a new `SAFEARRAY` structure is not returned.</span></span>

## <a name="requirements"></a><span data-ttu-id="e983b-178">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e983b-178">Requirements</span></span>  

 <span data-ttu-id="e983b-179">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e983b-179">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e983b-180">**Üst bilgi:** WMINet_Utils. IDL</span><span class="sxs-lookup"><span data-stu-id="e983b-180">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="e983b-181">**.NET Framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="e983b-181">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e983b-182">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e983b-182">See also</span></span>

- [<span data-ttu-id="e983b-183">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="e983b-183">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
