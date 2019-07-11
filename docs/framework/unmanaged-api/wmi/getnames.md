---
title: GetNames işlevi (yönetilmeyen API Başvurusu)
description: GetNames işlevi, bir nesnenin özellik adlarını alır.
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
ms.openlocfilehash: e75bf9aab820216373f2f33fe8aa567f10befcb1
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67746522"
---
# <a name="getnames-function"></a><span data-ttu-id="84b92-103">GetNames işlevi</span><span class="sxs-lookup"><span data-stu-id="84b92-103">GetNames function</span></span>
<span data-ttu-id="84b92-104">Bir alt veya tümünü bir nesnenin özellik adlarını alır.</span><span class="sxs-lookup"><span data-stu-id="84b92-104">Retrieves either a subset or all of the names of the properties of an object.</span></span> 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="84b92-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="84b92-105">Syntax</span></span>  
  
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

## <a name="parameters"></a><span data-ttu-id="84b92-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="84b92-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="84b92-107">[in] Bu parametre kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="84b92-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="84b92-108">[in] Bir işaretçi bir [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneği.</span><span class="sxs-lookup"><span data-stu-id="84b92-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszQualifierName`  
<span data-ttu-id="84b92-109">[in] Geçerli bir işaretçi `LPCWSTR` filtre kapsamında işleyen bir niteleyici adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="84b92-109">[in] A pointer to a valid `LPCWSTR` that specifies a qualifier name that operates as part of a filter.</span></span> <span data-ttu-id="84b92-110">Daha fazla bilgi için [açıklamalar](#remarks) bölümü.</span><span class="sxs-lookup"><span data-stu-id="84b92-110">For more information, see the [Remarks](#remarks) section.</span></span> <span data-ttu-id="84b92-111">Bu parametre olabilir `null`.</span><span class="sxs-lookup"><span data-stu-id="84b92-111">This parameter can be `null`.</span></span> 

`lFlags`  
<span data-ttu-id="84b92-112">[in] Bit alanları bileşimi.</span><span class="sxs-lookup"><span data-stu-id="84b92-112">[in] A combination of bit fields.</span></span> <span data-ttu-id="84b92-113">Daha fazla bilgi için [açıklamalar](#remarks) bölümü.</span><span class="sxs-lookup"><span data-stu-id="84b92-113">For more information, see the [Remarks](#remarks) section.</span></span>

`pQualifierValue`   
<span data-ttu-id="84b92-114">[in] Geçerli bir işaretçi `VARIANT` yapısı için bir filtre değeri başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="84b92-114">[in] A pointer to a valid `VARIANT` structure initialized to a filter value.</span></span> <span data-ttu-id="84b92-115">Bu parametre olabilir `null`.</span><span class="sxs-lookup"><span data-stu-id="84b92-115">This parameter can be `null`.</span></span> 

`pstrNames`  
<span data-ttu-id="84b92-116">[out] A `SAFEARRAY` özellik adları içeren yapısı.</span><span class="sxs-lookup"><span data-stu-id="84b92-116">[out] A `SAFEARRAY` structure that contains property names.</span></span> <span data-ttu-id="84b92-117">Girişte, bu parametre her zaman bir işaretçi olmalıdır `null`.</span><span class="sxs-lookup"><span data-stu-id="84b92-117">On entry, this parameter must always be a pointer to `null`.</span></span> <span data-ttu-id="84b92-118">Bkz: [açıklamalar](#remarks) bölümünde daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="84b92-118">See the [Remarks](#remarks) section for more information.</span></span> 

## <a name="return-value"></a><span data-ttu-id="84b92-119">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="84b92-119">Return value</span></span>

<span data-ttu-id="84b92-120">Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üst bilgi dosyası veya tanımlayabilirsiniz bunları sabitleri kodunuzda:</span><span class="sxs-lookup"><span data-stu-id="84b92-120">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="84b92-121">Sabit</span><span class="sxs-lookup"><span data-stu-id="84b92-121">Constant</span></span>  |<span data-ttu-id="84b92-122">Değer</span><span class="sxs-lookup"><span data-stu-id="84b92-122">Value</span></span>  |<span data-ttu-id="84b92-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="84b92-123">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="84b92-124">0x80041001</span><span class="sxs-lookup"><span data-stu-id="84b92-124">0x80041001</span></span> | <span data-ttu-id="84b92-125">Genel bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="84b92-125">There has been a general failure.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="84b92-126">0x80041008</span><span class="sxs-lookup"><span data-stu-id="84b92-126">0x80041008</span></span> | <span data-ttu-id="84b92-127">Bir veya daha fazla parametre geçerli değil veya yanlış bir birleşimi bayrakları ve parametreleri belirtildi.</span><span class="sxs-lookup"><span data-stu-id="84b92-127">One or more parameters are not valid, or an incorrect combination of flags and parameters was specified.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="84b92-128">0x80041006</span><span class="sxs-lookup"><span data-stu-id="84b92-128">0x80041006</span></span> | <span data-ttu-id="84b92-129">İşlemi tamamlamak yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="84b92-129">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="84b92-130">0</span><span class="sxs-lookup"><span data-stu-id="84b92-130">0</span></span> | <span data-ttu-id="84b92-131">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="84b92-131">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="84b92-132">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="84b92-132">Remarks</span></span>

<span data-ttu-id="84b92-133">Bu işlev bir çağrı sarılır [IWbemClassObject::GetNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getnames) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="84b92-133">This function wraps a call to the [IWbemClassObject::GetNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getnames) method.</span></span>

<span data-ttu-id="84b92-134">Adlandırılmış döndürülen bayrakları ve parametre birleşimi tarafından denetlenir.</span><span class="sxs-lookup"><span data-stu-id="84b92-134">The named returned are controlled by a combination of flags and parameters.</span></span> <span data-ttu-id="84b92-135">Örneğin, işlevi, tüm özelliklerin adları veya yalnızca anahtar özellikler adları döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="84b92-135">For example, the function can return the names of all properties or only the names of the key properties.</span></span>  <span data-ttu-id="84b92-136">Birincil filtre belirtilen `lFlags` parametre ve diğer parametreler, bağlı olarak değişir.</span><span class="sxs-lookup"><span data-stu-id="84b92-136">The primary filter is specified in the `lFlags` parameter, and the other parameters vary depending on it.</span></span>

<span data-ttu-id="84b92-137">Bayrak değeri `lFlags` bit alanları</span><span class="sxs-lookup"><span data-stu-id="84b92-137">The flag values in `lFlags` are bit fields</span></span>

<span data-ttu-id="84b92-138">Olarak geçirilen bayraklar `lEnumFlags` bağımsız değişkeni olan tanımlanan bit alanları *WbemCli.h* üst bilgi dosyası veya tanımlayabilirsiniz bunları sabitleri kodunuzda.</span><span class="sxs-lookup"><span data-stu-id="84b92-138">The flags that can be passed as the `lEnumFlags` argument are bit fields that are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span>  <span data-ttu-id="84b92-139">Herhangi diğer bir grup bayrağı ile her bir gruptan bir bayrak birleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="84b92-139">You can combine one flag from each group with any flag from any other group.</span></span> <span data-ttu-id="84b92-140">Ancak, aynı grup bayrakları birbirini dışlar.</span><span class="sxs-lookup"><span data-stu-id="84b92-140">However, flags from the same group are mutually exclusive.</span></span> 

| <span data-ttu-id="84b92-141">Grup 1 bayrakları</span><span class="sxs-lookup"><span data-stu-id="84b92-141">Group 1 flags</span></span> |<span data-ttu-id="84b92-142">Değer</span><span class="sxs-lookup"><span data-stu-id="84b92-142">Value</span></span>  |<span data-ttu-id="84b92-143">Açıklama</span><span class="sxs-lookup"><span data-stu-id="84b92-143">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_ALWAYS` | <span data-ttu-id="84b92-144">0</span><span class="sxs-lookup"><span data-stu-id="84b92-144">0</span></span> | <span data-ttu-id="84b92-145">Tüm özellik adlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="84b92-145">Return all property names.</span></span> <span data-ttu-id="84b92-146">`strQualifierName` ve `pQualifierVal` kullanılmadı.</span><span class="sxs-lookup"><span data-stu-id="84b92-146">`strQualifierName` and `pQualifierVal` are unused.</span></span> |
| `WBEM_FLAG_ONLY_IF_TRUE` | <span data-ttu-id="84b92-147">1\.</span><span class="sxs-lookup"><span data-stu-id="84b92-147">1</span></span> | <span data-ttu-id="84b92-148">Tarafından belirtilen adının niteleyicisi olan özellikler yalnızca dönüş `strQualifierName` parametresi.</span><span class="sxs-lookup"><span data-stu-id="84b92-148">Return only properties that have a qualifier of the name specified by the `strQualifierName` parameter.</span></span> <span data-ttu-id="84b92-149">Bu bayrak kullanılırsa belirtmeniz gerekir `strQualifierName`.</span><span class="sxs-lookup"><span data-stu-id="84b92-149">If this flag is used, you must specify `strQualifierName`.</span></span> |
|`WBEM_FLAG_ONLY_IF_FALSE` | <span data-ttu-id="84b92-150">2</span><span class="sxs-lookup"><span data-stu-id="84b92-150">2</span></span> |  <span data-ttu-id="84b92-151">Tarafından belirtilen adının niteleyicisi olmayan özellikler yalnızca dönüş `strQualifierName` parametresi.</span><span class="sxs-lookup"><span data-stu-id="84b92-151">Return only properties that do not have a qualifier of the name specified by the `strQualifierName` parameter.</span></span> <span data-ttu-id="84b92-152">Bu bayrak kullanılırsa belirtmeniz gerekir `strQualifierName`.</span><span class="sxs-lookup"><span data-stu-id="84b92-152">If this flag is used, you must specify `strQualifierName`.</span></span> |
|`WBEM_FLAG_ONLY_IF_IDENTICAL` | <span data-ttu-id="84b92-153">3</span><span class="sxs-lookup"><span data-stu-id="84b92-153">3</span></span> | <span data-ttu-id="84b92-154">Yalnızca bir niteleyici tarafından belirtilen adı taşıyan özellikler dönüş `wszQualifierName` parametre ve bir değer tarafından belirtilen aynı de `pQualifierVal` yapısı.</span><span class="sxs-lookup"><span data-stu-id="84b92-154">Return only properties that have a qualifier of the name specified by the `wszQualifierName` parameter and also have a value identical to that specified by the `pQualifierVal` structure.</span></span> <span data-ttu-id="84b92-155">Bu bayrak kullanılırsa, her ikisini de belirtmelisiniz bir `wszQualifierName` ve `pQualifierValue`.</span><span class="sxs-lookup"><span data-stu-id="84b92-155">If this flag is used, you must specify both a `wszQualifierName` and a `pQualifierValue`.</span></span> |

| <span data-ttu-id="84b92-156">Grup 2 bayrakları</span><span class="sxs-lookup"><span data-stu-id="84b92-156">Group 2 flags</span></span> |<span data-ttu-id="84b92-157">Değer</span><span class="sxs-lookup"><span data-stu-id="84b92-157">Value</span></span>  |<span data-ttu-id="84b92-158">Açıklama</span><span class="sxs-lookup"><span data-stu-id="84b92-158">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | <span data-ttu-id="84b92-159">0x4</span><span class="sxs-lookup"><span data-stu-id="84b92-159">0x4</span></span> | <span data-ttu-id="84b92-160">Yalnızca anahtarları tanımlayan özellik adlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="84b92-160">Return only the names of properties that define the keys.</span></span> |
|`WBEM_FLAG_REFS_ONLY` | <span data-ttu-id="84b92-161">0x8</span><span class="sxs-lookup"><span data-stu-id="84b92-161">0x8</span></span> | <span data-ttu-id="84b92-162">Nesne başvuruları olan dönüş yalnızca özellik adları.</span><span class="sxs-lookup"><span data-stu-id="84b92-162">Return only property names that are object references.</span></span> |

| <span data-ttu-id="84b92-163">Grup 3 bayrakları</span><span class="sxs-lookup"><span data-stu-id="84b92-163">Group 3 flags</span></span> |<span data-ttu-id="84b92-164">Değer</span><span class="sxs-lookup"><span data-stu-id="84b92-164">Value</span></span>  |<span data-ttu-id="84b92-165">Açıklama</span><span class="sxs-lookup"><span data-stu-id="84b92-165">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="84b92-166">0x10</span><span class="sxs-lookup"><span data-stu-id="84b92-166">0x10</span></span> | <span data-ttu-id="84b92-167">En çok türetilen sınıfa ait özellik adlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="84b92-167">Return only property names that belong to the most derived class.</span></span> <span data-ttu-id="84b92-168">Özellikleri, üst sınıflardan hariç tutun.</span><span class="sxs-lookup"><span data-stu-id="84b92-168">Exclude properties from the parent classes.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="84b92-169">0x20</span><span class="sxs-lookup"><span data-stu-id="84b92-169">0x20</span></span> | <span data-ttu-id="84b92-170">Ana sınıfa ait özellik adlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="84b92-170">Return only property names that belong to the parent classes.</span></span> |
|`WBEM_FLAG_SYSTEM_ONLY` | <span data-ttu-id="84b92-171">0x30</span><span class="sxs-lookup"><span data-stu-id="84b92-171">0x30</span></span> | <span data-ttu-id="84b92-172">Yalnızca Sistem özellikleri adlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="84b92-172">Return only the names of system properties.</span></span> |
|`WBEM_FLAG_NONSYSTEM_ONLY` | <span data-ttu-id="84b92-173">0x40</span><span class="sxs-lookup"><span data-stu-id="84b92-173">0x40</span></span> | <span data-ttu-id="84b92-174">Yalnızca sistem dışı özellik adlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="84b92-174">Return only the names of non-system properties.</span></span> |

<span data-ttu-id="84b92-175">İşlev her zaman yeni bir ayırır `SAFEARRAY` döndürürse `WBEM_S_NO_ERROR`, ve `pstrNames` her zaman için işaret edecek şekilde ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="84b92-175">The function always allocates a new `SAFEARRAY` if it returns `WBEM_S_NO_ERROR`, and `pstrNames` is always set to point to it.</span></span> <span data-ttu-id="84b92-176">Döndürülen dizi hiçbir özellik belirtilen filtrelerle eşleşen 0 öğeleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="84b92-176">The returned array can have 0 elements if no properties match the specified filters.</span></span> <span data-ttu-id="84b92-177">İşlev dışında bir değer döndürürse `WBM_S_NO_ERROR`, yeni bir `SAFEARRAY` yapısı alınmadı.</span><span class="sxs-lookup"><span data-stu-id="84b92-177">If the function returns an value other than `WBM_S_NO_ERROR`, a new `SAFEARRAY` structure is not returned.</span></span>
 
## <a name="requirements"></a><span data-ttu-id="84b92-178">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="84b92-178">Requirements</span></span>  
 <span data-ttu-id="84b92-179">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="84b92-179">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84b92-180">**Üst bilgi:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="84b92-180">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="84b92-181">**.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="84b92-181">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84b92-182">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="84b92-182">See also</span></span>

- [<span data-ttu-id="84b92-183">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="84b92-183">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
