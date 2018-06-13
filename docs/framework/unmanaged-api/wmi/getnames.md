---
title: GetNames işlevi (yönetilmeyen API Başvurusu)
description: GetNames işlevi bir nesnenin özellik adlarını alır.
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 108946428cdfadcfb9c653b7e444bf278dfa2782
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33461987"
---
# <a name="getnames-function"></a><span data-ttu-id="b85dc-103">GetNames işlevi</span><span class="sxs-lookup"><span data-stu-id="b85dc-103">GetNames function</span></span>
<span data-ttu-id="b85dc-104">Bir alt veya tümünü bir nesnenin özellik adlarını alır.</span><span class="sxs-lookup"><span data-stu-id="b85dc-104">Retrieves either a subset or all of the names of the properties of an object.</span></span> 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="b85dc-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b85dc-105">Syntax</span></span>  
  
```  
HRESULT GetNames (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LPCWSTR             wszQualifierName,
   [in] LONG                lFlags,
   [in] VARIANT*            pQualifierValue,
   [out] SAFEARRAY (BSTR)** pstrNames
); 
```  

## <a name="parameters"></a><span data-ttu-id="b85dc-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b85dc-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="b85dc-107">[in] Bu parametre kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="b85dc-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="b85dc-108">[in] Bir işaretçi bir [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) örneği.</span><span class="sxs-lookup"><span data-stu-id="b85dc-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`wszQualifierName`  
<span data-ttu-id="b85dc-109">[in] Geçerli bir işaretçi `LPCWSTR` bir filtre bir parçası olarak çalışır bir niteleyici adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="b85dc-109">[in] A pointer to a valid `LPCWSTR` that specifies a qualifier name that operates as part of a filter.</span></span> <span data-ttu-id="b85dc-110">Daha fazla bilgi için bkz: [açıklamalar](#remarks) bölümü.</span><span class="sxs-lookup"><span data-stu-id="b85dc-110">For more information, see the [Remarks](#remarks) section.</span></span> <span data-ttu-id="b85dc-111">Bu parametre olabilir `null`.</span><span class="sxs-lookup"><span data-stu-id="b85dc-111">This parameter can be `null`.</span></span> 

`lFlags`  
<span data-ttu-id="b85dc-112">[in] Bit alanları birleşimi.</span><span class="sxs-lookup"><span data-stu-id="b85dc-112">[in] A combination of bit fields.</span></span> <span data-ttu-id="b85dc-113">Daha fazla bilgi için bkz: [açıklamalar](#remarks) bölümü.</span><span class="sxs-lookup"><span data-stu-id="b85dc-113">For more information, see the [Remarks](#remarks) section.</span></span>

`pQualifierValue`   
<span data-ttu-id="b85dc-114">[in] Geçerli bir işaretçi `VARIANT` yapısı için bir filtre değeri başlatılmadı.</span><span class="sxs-lookup"><span data-stu-id="b85dc-114">[in] A pointer to a valid `VARIANT` structure initialized to a filter value.</span></span> <span data-ttu-id="b85dc-115">Bu parametre olabilir `null`.</span><span class="sxs-lookup"><span data-stu-id="b85dc-115">This parameter can be `null`.</span></span> 

`pstrNames`  
<span data-ttu-id="b85dc-116">[out] A `SAFEARRAY` özellik adları içeren yapısı.</span><span class="sxs-lookup"><span data-stu-id="b85dc-116">[out] A `SAFEARRAY` structure that contains property names.</span></span> <span data-ttu-id="b85dc-117">Üzerinde bu parametre her zaman bir işaretçi girilmelidir `null`.</span><span class="sxs-lookup"><span data-stu-id="b85dc-117">On entry, this parameter must always be a pointer to `null`.</span></span> <span data-ttu-id="b85dc-118">Bkz: [açıklamalar](#remarks) daha fazla bilgi için bölüm.</span><span class="sxs-lookup"><span data-stu-id="b85dc-118">See the [Remarks](#remarks) section for more information.</span></span> 

## <a name="return-value"></a><span data-ttu-id="b85dc-119">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="b85dc-119">Return value</span></span>

<span data-ttu-id="b85dc-120">Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üstbilgi dosyası, veya tanımlayabilirsiniz bunları sabitleri kodunuzda:</span><span class="sxs-lookup"><span data-stu-id="b85dc-120">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="b85dc-121">Sabit</span><span class="sxs-lookup"><span data-stu-id="b85dc-121">Constant</span></span>  |<span data-ttu-id="b85dc-122">Değer</span><span class="sxs-lookup"><span data-stu-id="b85dc-122">Value</span></span>  |<span data-ttu-id="b85dc-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b85dc-123">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="b85dc-124">0x80041001</span><span class="sxs-lookup"><span data-stu-id="b85dc-124">0x80041001</span></span> | <span data-ttu-id="b85dc-125">Genel bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="b85dc-125">There has been a general failure.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="b85dc-126">0x80041008</span><span class="sxs-lookup"><span data-stu-id="b85dc-126">0x80041008</span></span> | <span data-ttu-id="b85dc-127">Bir veya daha fazla parametre geçerli değil veya yanlış bir birleşimi bayrakları ve parametreleri belirtildi.</span><span class="sxs-lookup"><span data-stu-id="b85dc-127">One or more parameters are not valid, or an incorrect combination of flags and parameters was specified.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="b85dc-128">0x80041006</span><span class="sxs-lookup"><span data-stu-id="b85dc-128">0x80041006</span></span> | <span data-ttu-id="b85dc-129">İşlemi tamamlamak yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="b85dc-129">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="b85dc-130">0</span><span class="sxs-lookup"><span data-stu-id="b85dc-130">0</span></span> | <span data-ttu-id="b85dc-131">İşlev çağrısı başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="b85dc-131">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="b85dc-132">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b85dc-132">Remarks</span></span>

<span data-ttu-id="b85dc-133">Bu işlev çağrısı sarmalar [IWbemClassObject::GetNames](https://msdn.microsoft.com/library/aa391447(v=vs.85).aspx) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b85dc-133">This function wraps a call to the [IWbemClassObject::GetNames](https://msdn.microsoft.com/library/aa391447(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="b85dc-134">Adlandırılmış döndürülen bayrakları ve parametre birleşimi tarafından denetlenir.</span><span class="sxs-lookup"><span data-stu-id="b85dc-134">The named returned are controlled by a combination of flags and parameters.</span></span> <span data-ttu-id="b85dc-135">Örneğin, işlev tüm özellik adlarını veya yalnızca anahtar özellikler adları döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="b85dc-135">For example, the function can return the names of all properties or only the names of the key properties.</span></span>  <span data-ttu-id="b85dc-136">Birincil filtre belirtilen `lFlags` parametresi ve diğer parametreler, bağlı olarak farklılık.</span><span class="sxs-lookup"><span data-stu-id="b85dc-136">The primary filter is specified in the `lFlags` parameter, and the other parameters vary depending on it.</span></span>

<span data-ttu-id="b85dc-137">Bayrak değerleri `lFlags` bit alanları</span><span class="sxs-lookup"><span data-stu-id="b85dc-137">The flag values in `lFlags` are bit fields</span></span>


<span data-ttu-id="b85dc-138">Olarak geçirilen bayraklar `lEnumFlags` bağımsız değişkeni olan tanımlanan bit alanları *WbemCli.h* üstbilgi dosyası, veya tanımlayabilirsiniz bunları sabitleri kodunuzda.</span><span class="sxs-lookup"><span data-stu-id="b85dc-138">The flags that can be passed as the `lEnumFlags` argument are bit fields that are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span>  <span data-ttu-id="b85dc-139">Diğer bir gruptaki tüm bayrağıyla her grubundan bir bayrak birleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b85dc-139">You can combine one flag from each group with any flag from any other group.</span></span> <span data-ttu-id="b85dc-140">Ancak, aynı gruptan bayrakları karşılıklı olarak birbirini dışlar.</span><span class="sxs-lookup"><span data-stu-id="b85dc-140">However, flags from the same group are mutually exclusive.</span></span> 

| <span data-ttu-id="b85dc-141">Grup 1 bayrakları</span><span class="sxs-lookup"><span data-stu-id="b85dc-141">Group 1 flags</span></span> |<span data-ttu-id="b85dc-142">Değer</span><span class="sxs-lookup"><span data-stu-id="b85dc-142">Value</span></span>  |<span data-ttu-id="b85dc-143">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b85dc-143">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_ALWAYS` | <span data-ttu-id="b85dc-144">0</span><span class="sxs-lookup"><span data-stu-id="b85dc-144">0</span></span> | <span data-ttu-id="b85dc-145">Tüm özellik adlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="b85dc-145">Return all property names.</span></span> <span data-ttu-id="b85dc-146">`strQualifierName` ve `pQualifierVal` kullanılmayan.</span><span class="sxs-lookup"><span data-stu-id="b85dc-146">`strQualifierName` and `pQualifierVal` are unused.</span></span> |
| `WBEM_FLAG_ONLY_IF_TRUE` | <span data-ttu-id="b85dc-147">1.</span><span class="sxs-lookup"><span data-stu-id="b85dc-147">1</span></span> | <span data-ttu-id="b85dc-148">Niteleyici tarafından belirtilen adının sahip yalnızca Özellikler `strQualifierName` parametresi.</span><span class="sxs-lookup"><span data-stu-id="b85dc-148">Return only properties that have a qualifier of the name specified by the `strQualifierName` parameter.</span></span> <span data-ttu-id="b85dc-149">Bu bayrak kullanılıp kullanılmadığını belirtmeniz gerekir `strQualifierName`.</span><span class="sxs-lookup"><span data-stu-id="b85dc-149">If this flag is used, you must specify `strQualifierName`.</span></span> |
|`WBEM_FLAG_ONLY_IF_FALSE` | <span data-ttu-id="b85dc-150">2</span><span class="sxs-lookup"><span data-stu-id="b85dc-150">2</span></span> |  <span data-ttu-id="b85dc-151">Tarafından belirtilen adının niteleyicisi yok yalnızca Özellikler `strQualifierName` parametresi.</span><span class="sxs-lookup"><span data-stu-id="b85dc-151">Return only properties that do not have a qualifier of the name specified by the `strQualifierName` parameter.</span></span> <span data-ttu-id="b85dc-152">Bu bayrak kullanılıp kullanılmadığını belirtmeniz gerekir `strQualifierName`.</span><span class="sxs-lookup"><span data-stu-id="b85dc-152">If this flag is used, you must specify `strQualifierName`.</span></span> |
|`WBEM_FLAG_ONLY_IF_IDENTICAL` | <span data-ttu-id="b85dc-153">3</span><span class="sxs-lookup"><span data-stu-id="b85dc-153">3</span></span> | <span data-ttu-id="b85dc-154">Niteleyici tarafından belirtilen adı olan özellikler `wszQualifierName` parametre ve ayrıca bir değer tarafından belirtilen aynı `pQualifierVal` yapısı.</span><span class="sxs-lookup"><span data-stu-id="b85dc-154">Return only properties that have a qualifier of the name specified by the `wszQualifierName` parameter and also have a value identical to that specified by the `pQualifierVal` structure.</span></span> <span data-ttu-id="b85dc-155">Bu bayrak kullanılırsa, her ikisini de belirtmelisiniz bir `wszQualifierName` ve `pQualifierValue`.</span><span class="sxs-lookup"><span data-stu-id="b85dc-155">If this flag is used, you must specify both a `wszQualifierName` and a `pQualifierValue`.</span></span> |

| <span data-ttu-id="b85dc-156">Grup 2 bayrakları</span><span class="sxs-lookup"><span data-stu-id="b85dc-156">Group 2 flags</span></span> |<span data-ttu-id="b85dc-157">Değer</span><span class="sxs-lookup"><span data-stu-id="b85dc-157">Value</span></span>  |<span data-ttu-id="b85dc-158">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b85dc-158">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | <span data-ttu-id="b85dc-159">0x4</span><span class="sxs-lookup"><span data-stu-id="b85dc-159">0x4</span></span> | <span data-ttu-id="b85dc-160">Yalnızca anahtarları tanımlayan özellikleri adlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="b85dc-160">Return only the names of properties that define the keys.</span></span> |
|`WBEM_FLAG_REFS_ONLY` | <span data-ttu-id="b85dc-161">0x8</span><span class="sxs-lookup"><span data-stu-id="b85dc-161">0x8</span></span> | <span data-ttu-id="b85dc-162">Nesne başvuruları dönüş yalnızca özellik adları.</span><span class="sxs-lookup"><span data-stu-id="b85dc-162">Return only property names that are object references.</span></span> |

| <span data-ttu-id="b85dc-163">Grup 3 bayrakları</span><span class="sxs-lookup"><span data-stu-id="b85dc-163">Group 3 flags</span></span> |<span data-ttu-id="b85dc-164">Değer</span><span class="sxs-lookup"><span data-stu-id="b85dc-164">Value</span></span>  |<span data-ttu-id="b85dc-165">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b85dc-165">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="b85dc-166">0x10</span><span class="sxs-lookup"><span data-stu-id="b85dc-166">0x10</span></span> | <span data-ttu-id="b85dc-167">En çok türetilen sınıfına ait özellik adlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="b85dc-167">Return only property names that belong to the most derived class.</span></span> <span data-ttu-id="b85dc-168">Özellikleri üst sınıflardan çıkarın.</span><span class="sxs-lookup"><span data-stu-id="b85dc-168">Exclude properties from the parent classes.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="b85dc-169">0x20</span><span class="sxs-lookup"><span data-stu-id="b85dc-169">0x20</span></span> | <span data-ttu-id="b85dc-170">Üst sınıflarına ait özellik adlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="b85dc-170">Return only property names that belong to the parent classes.</span></span> |
|`WBEM_FLAG_SYSTEM_ONLY` | <span data-ttu-id="b85dc-171">0x30</span><span class="sxs-lookup"><span data-stu-id="b85dc-171">0x30</span></span> | <span data-ttu-id="b85dc-172">Yalnızca Sistem özellikleri adlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="b85dc-172">Return only the names of system properties.</span></span> |
|`WBEM_FLAG_NONSYSTEM_ONLY` | <span data-ttu-id="b85dc-173">0x40</span><span class="sxs-lookup"><span data-stu-id="b85dc-173">0x40</span></span> | <span data-ttu-id="b85dc-174">Yalnızca sistem dışı özellik adlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="b85dc-174">Return only the names of non-system properties.</span></span> |

<span data-ttu-id="b85dc-175">İşlevi her zaman yeni bir ayırır `SAFEARRAY` döndürürse `WBEM_S_NO_ERROR`, ve `pstrNames` her zaman üzerine ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="b85dc-175">The function always allocates a new `SAFEARRAY` if it returns `WBEM_S_NO_ERROR`, and `pstrNames` is always set to point to it.</span></span> <span data-ttu-id="b85dc-176">Verilen dizi özellik belirtilen filtrelerle eşleşen 0 öğeleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="b85dc-176">The returned array can have 0 elements if no properties match the specified filters.</span></span> <span data-ttu-id="b85dc-177">İşlevi dışındaki bir değer döndürürse `WBM_S_NO_ERROR`, yeni bir `SAFEARRAY` yapısı alınmadı.</span><span class="sxs-lookup"><span data-stu-id="b85dc-177">If the function returns an value other than `WBM_S_NO_ERROR`, a new `SAFEARRAY` structure is not returned.</span></span>
 
## <a name="requirements"></a><span data-ttu-id="b85dc-178">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b85dc-178">Requirements</span></span>  
 <span data-ttu-id="b85dc-179">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b85dc-179">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b85dc-180">**Başlık:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="b85dc-180">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="b85dc-181">**.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="b85dc-181">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b85dc-182">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b85dc-182">See also</span></span>  
[<span data-ttu-id="b85dc-183">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="b85dc-183">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
