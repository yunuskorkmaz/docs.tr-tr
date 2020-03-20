---
title: GetNames işlevi (Yönetilmeyen API Başvurusu)
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
ms.openlocfilehash: 449f0ce9c291d4bbcad4947214e56ff46f55beed
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174959"
---
# <a name="getnames-function"></a><span data-ttu-id="2eb09-103">GetNames işlevi</span><span class="sxs-lookup"><span data-stu-id="2eb09-103">GetNames function</span></span>
<span data-ttu-id="2eb09-104">Bir alt kümeyi veya nesnenin özelliklerinin tüm adlarını alır.</span><span class="sxs-lookup"><span data-stu-id="2eb09-104">Retrieves either a subset or all of the names of the properties of an object.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="2eb09-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2eb09-105">Syntax</span></span>  
  
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

## <a name="parameters"></a><span data-ttu-id="2eb09-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2eb09-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="2eb09-107">[içinde] Bu parametre kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="2eb09-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="2eb09-108">[içinde] [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneğine işaretçi.</span><span class="sxs-lookup"><span data-stu-id="2eb09-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszQualifierName`  
<span data-ttu-id="2eb09-109">[içinde] Bir filtrenin `LPCWSTR` parçası olarak çalışan bir niteleyici adı belirten bir geçerli için işaretçi.</span><span class="sxs-lookup"><span data-stu-id="2eb09-109">[in] A pointer to a valid `LPCWSTR` that specifies a qualifier name that operates as part of a filter.</span></span> <span data-ttu-id="2eb09-110">Daha fazla bilgi için [Açıklamalar](#remarks) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="2eb09-110">For more information, see the [Remarks](#remarks) section.</span></span> <span data-ttu-id="2eb09-111">Bu parametre `null`olabilir .</span><span class="sxs-lookup"><span data-stu-id="2eb09-111">This parameter can be `null`.</span></span>

`lFlags`  
<span data-ttu-id="2eb09-112">[içinde] Bit alanlarının birleşimi.</span><span class="sxs-lookup"><span data-stu-id="2eb09-112">[in] A combination of bit fields.</span></span> <span data-ttu-id="2eb09-113">Daha fazla bilgi için [Açıklamalar](#remarks) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="2eb09-113">For more information, see the [Remarks](#remarks) section.</span></span>

<span data-ttu-id="2eb09-114">`pQualifierValue`[içinde] Filtre değerine `VARIANT` başlattı geçerli bir yapıiçin işaretçi.</span><span class="sxs-lookup"><span data-stu-id="2eb09-114">`pQualifierValue` [in] A pointer to a valid `VARIANT` structure initialized to a filter value.</span></span> <span data-ttu-id="2eb09-115">Bu parametre `null`olabilir .</span><span class="sxs-lookup"><span data-stu-id="2eb09-115">This parameter can be `null`.</span></span>

`pstrNames`  
<span data-ttu-id="2eb09-116">[çıkış] Özellik `SAFEARRAY` adları içeren bir yapı.</span><span class="sxs-lookup"><span data-stu-id="2eb09-116">[out] A `SAFEARRAY` structure that contains property names.</span></span> <span data-ttu-id="2eb09-117">Girişte, bu parametre her zaman `null`bir işaretçi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2eb09-117">On entry, this parameter must always be a pointer to `null`.</span></span> <span data-ttu-id="2eb09-118">Daha fazla bilgi için [Açıklamalar](#remarks) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="2eb09-118">See the [Remarks](#remarks) section for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="2eb09-119">Döndürülen değer</span><span class="sxs-lookup"><span data-stu-id="2eb09-119">Return value</span></span>

<span data-ttu-id="2eb09-120">Bu işlev tarafından döndürülen aşağıdaki değerler *WbemCli.h* üstbilgi dosyasında tanımlanır veya bunları kodunuzdaki sabitler olarak tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="2eb09-120">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="2eb09-121">Sabit</span><span class="sxs-lookup"><span data-stu-id="2eb09-121">Constant</span></span>  |<span data-ttu-id="2eb09-122">Değer</span><span class="sxs-lookup"><span data-stu-id="2eb09-122">Value</span></span>  |<span data-ttu-id="2eb09-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2eb09-123">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="2eb09-124">0x80041001</span><span class="sxs-lookup"><span data-stu-id="2eb09-124">0x80041001</span></span> | <span data-ttu-id="2eb09-125">Genel bir başarısızlık oldu.</span><span class="sxs-lookup"><span data-stu-id="2eb09-125">There has been a general failure.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="2eb09-126">0x80041008</span><span class="sxs-lookup"><span data-stu-id="2eb09-126">0x80041008</span></span> | <span data-ttu-id="2eb09-127">Bir veya daha fazla parametre geçerli değildir veya bayraklar ve parametrelerin yanlış bir birleşimi belirtilmiş.</span><span class="sxs-lookup"><span data-stu-id="2eb09-127">One or more parameters are not valid, or an incorrect combination of flags and parameters was specified.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="2eb09-128">0x80041006</span><span class="sxs-lookup"><span data-stu-id="2eb09-128">0x80041006</span></span> | <span data-ttu-id="2eb09-129">İşlemi tamamlamak için yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="2eb09-129">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="2eb09-130">0</span><span class="sxs-lookup"><span data-stu-id="2eb09-130">0</span></span> | <span data-ttu-id="2eb09-131">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="2eb09-131">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="2eb09-132">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2eb09-132">Remarks</span></span>

<span data-ttu-id="2eb09-133">Bu [işlev, IWbemClassObject::GetNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getnames) yöntemine bir çağrı yıkıyor.</span><span class="sxs-lookup"><span data-stu-id="2eb09-133">This function wraps a call to the [IWbemClassObject::GetNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getnames) method.</span></span>

<span data-ttu-id="2eb09-134">Döndürülen ad, bayraklar ve parametrelerin birleşimi tarafından denetlenir.</span><span class="sxs-lookup"><span data-stu-id="2eb09-134">The named returned are controlled by a combination of flags and parameters.</span></span> <span data-ttu-id="2eb09-135">Örneğin, işlev tüm özelliklerin adlarını veya yalnızca anahtar özelliklerinin adlarını döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="2eb09-135">For example, the function can return the names of all properties or only the names of the key properties.</span></span>  <span data-ttu-id="2eb09-136">Birincil filtre `lFlags` parametrede belirtilir ve diğer parametreler buna bağlı olarak değişir.</span><span class="sxs-lookup"><span data-stu-id="2eb09-136">The primary filter is specified in the `lFlags` parameter, and the other parameters vary depending on it.</span></span>

<span data-ttu-id="2eb09-137">Bayrak değerleri `lFlags` bit alanlarıdır</span><span class="sxs-lookup"><span data-stu-id="2eb09-137">The flag values in `lFlags` are bit fields</span></span>

<span data-ttu-id="2eb09-138">`lEnumFlags` Bağımsız değişken olarak geçirilebilen *bayraklar, WbemCli.h* üstbilgi dosyasında tanımlanan bit alanlarıdır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2eb09-138">The flags that can be passed as the `lEnumFlags` argument are bit fields that are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span>  <span data-ttu-id="2eb09-139">Her gruptan bir bayrağı başka bir gruptan herhangi bir bayrakla birleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2eb09-139">You can combine one flag from each group with any flag from any other group.</span></span> <span data-ttu-id="2eb09-140">Ancak, aynı grubun bayrakları birbirini dışlar.</span><span class="sxs-lookup"><span data-stu-id="2eb09-140">However, flags from the same group are mutually exclusive.</span></span>

| <span data-ttu-id="2eb09-141">Grup 1 bayrakları</span><span class="sxs-lookup"><span data-stu-id="2eb09-141">Group 1 flags</span></span> |<span data-ttu-id="2eb09-142">Değer</span><span class="sxs-lookup"><span data-stu-id="2eb09-142">Value</span></span>  |<span data-ttu-id="2eb09-143">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2eb09-143">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_ALWAYS` | <span data-ttu-id="2eb09-144">0</span><span class="sxs-lookup"><span data-stu-id="2eb09-144">0</span></span> | <span data-ttu-id="2eb09-145">Tüm özellik adlarını döndürün.</span><span class="sxs-lookup"><span data-stu-id="2eb09-145">Return all property names.</span></span> <span data-ttu-id="2eb09-146">`strQualifierName`ve `pQualifierVal` kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="2eb09-146">`strQualifierName` and `pQualifierVal` are unused.</span></span> |
| `WBEM_FLAG_ONLY_IF_TRUE` | <span data-ttu-id="2eb09-147">1</span><span class="sxs-lookup"><span data-stu-id="2eb09-147">1</span></span> | <span data-ttu-id="2eb09-148">Yalnızca parametre tarafından belirtilen adı niteleyen `strQualifierName` özellikleri döndürün.</span><span class="sxs-lookup"><span data-stu-id="2eb09-148">Return only properties that have a qualifier of the name specified by the `strQualifierName` parameter.</span></span> <span data-ttu-id="2eb09-149">Bu bayrak kullanılırsa, `strQualifierName`belirtmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="2eb09-149">If this flag is used, you must specify `strQualifierName`.</span></span> |
|`WBEM_FLAG_ONLY_IF_FALSE` | <span data-ttu-id="2eb09-150">2</span><span class="sxs-lookup"><span data-stu-id="2eb09-150">2</span></span> |  <span data-ttu-id="2eb09-151">Yalnızca parametre tarafından belirtilen adınitelemeye sahip `strQualifierName` olmayan özellikleri döndürün.</span><span class="sxs-lookup"><span data-stu-id="2eb09-151">Return only properties that do not have a qualifier of the name specified by the `strQualifierName` parameter.</span></span> <span data-ttu-id="2eb09-152">Bu bayrak kullanılırsa, `strQualifierName`belirtmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="2eb09-152">If this flag is used, you must specify `strQualifierName`.</span></span> |
|`WBEM_FLAG_ONLY_IF_IDENTICAL` | <span data-ttu-id="2eb09-153">3</span><span class="sxs-lookup"><span data-stu-id="2eb09-153">3</span></span> | <span data-ttu-id="2eb09-154">Yalnızca `wszQualifierName` parametre tarafından belirtilen adı niteleyen ve yapı tarafından belirtilen değere sahip `pQualifierVal` özellikleri döndürün.</span><span class="sxs-lookup"><span data-stu-id="2eb09-154">Return only properties that have a qualifier of the name specified by the `wszQualifierName` parameter and also have a value identical to that specified by the `pQualifierVal` structure.</span></span> <span data-ttu-id="2eb09-155">Bu bayrak kullanılırsa, hem `wszQualifierName` a `pQualifierValue`hem de bir . belirtmeniz gerekir</span><span class="sxs-lookup"><span data-stu-id="2eb09-155">If this flag is used, you must specify both a `wszQualifierName` and a `pQualifierValue`.</span></span> |

| <span data-ttu-id="2eb09-156">Grup 2 bayrakları</span><span class="sxs-lookup"><span data-stu-id="2eb09-156">Group 2 flags</span></span> |<span data-ttu-id="2eb09-157">Değer</span><span class="sxs-lookup"><span data-stu-id="2eb09-157">Value</span></span>  |<span data-ttu-id="2eb09-158">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2eb09-158">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | <span data-ttu-id="2eb09-159">0x4</span><span class="sxs-lookup"><span data-stu-id="2eb09-159">0x4</span></span> | <span data-ttu-id="2eb09-160">Yalnızca anahtarları tanımlayan özelliklerin adlarını döndürün.</span><span class="sxs-lookup"><span data-stu-id="2eb09-160">Return only the names of properties that define the keys.</span></span> |
|`WBEM_FLAG_REFS_ONLY` | <span data-ttu-id="2eb09-161">0x8</span><span class="sxs-lookup"><span data-stu-id="2eb09-161">0x8</span></span> | <span data-ttu-id="2eb09-162">Yalnızca nesne başvuruları olan özellik adlarını döndürün.</span><span class="sxs-lookup"><span data-stu-id="2eb09-162">Return only property names that are object references.</span></span> |

| <span data-ttu-id="2eb09-163">Grup 3 bayrakları</span><span class="sxs-lookup"><span data-stu-id="2eb09-163">Group 3 flags</span></span> |<span data-ttu-id="2eb09-164">Değer</span><span class="sxs-lookup"><span data-stu-id="2eb09-164">Value</span></span>  |<span data-ttu-id="2eb09-165">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2eb09-165">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="2eb09-166">0x10</span><span class="sxs-lookup"><span data-stu-id="2eb09-166">0x10</span></span> | <span data-ttu-id="2eb09-167">Yalnızca en çok türetilmiş sınıfa ait özellik adlarını döndürün.</span><span class="sxs-lookup"><span data-stu-id="2eb09-167">Return only property names that belong to the most derived class.</span></span> <span data-ttu-id="2eb09-168">Özellikleri üst sınıflardan hariç tinler.</span><span class="sxs-lookup"><span data-stu-id="2eb09-168">Exclude properties from the parent classes.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="2eb09-169">0x20</span><span class="sxs-lookup"><span data-stu-id="2eb09-169">0x20</span></span> | <span data-ttu-id="2eb09-170">Yalnızca üst sınıflara ait özellik adlarını döndürün.</span><span class="sxs-lookup"><span data-stu-id="2eb09-170">Return only property names that belong to the parent classes.</span></span> |
|`WBEM_FLAG_SYSTEM_ONLY` | <span data-ttu-id="2eb09-171">0x30</span><span class="sxs-lookup"><span data-stu-id="2eb09-171">0x30</span></span> | <span data-ttu-id="2eb09-172">Yalnızca sistem özelliklerinin adlarını döndürün.</span><span class="sxs-lookup"><span data-stu-id="2eb09-172">Return only the names of system properties.</span></span> |
|`WBEM_FLAG_NONSYSTEM_ONLY` | <span data-ttu-id="2eb09-173">0x40</span><span class="sxs-lookup"><span data-stu-id="2eb09-173">0x40</span></span> | <span data-ttu-id="2eb09-174">Yalnızca sistem dışı özelliklerin adlarını döndürün.</span><span class="sxs-lookup"><span data-stu-id="2eb09-174">Return only the names of non-system properties.</span></span> |

<span data-ttu-id="2eb09-175">İşlev her zaman `SAFEARRAY` yeni `WBEM_S_NO_ERROR` `pstrNames` bir döner ve her zaman onu işaret etmek için ayarlanır ayırır.</span><span class="sxs-lookup"><span data-stu-id="2eb09-175">The function always allocates a new `SAFEARRAY` if it returns `WBEM_S_NO_ERROR`, and `pstrNames` is always set to point to it.</span></span> <span data-ttu-id="2eb09-176">Döndürülen dizi, belirtilen filtrelerle hiçbir özellik eşleşmezse 0 elemana sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="2eb09-176">The returned array can have 0 elements if no properties match the specified filters.</span></span> <span data-ttu-id="2eb09-177">İşlev, yeni bir `WBM_S_NO_ERROR` `SAFEARRAY` yapının döndürülmesi dışında bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="2eb09-177">If the function returns an value other than `WBM_S_NO_ERROR`, a new `SAFEARRAY` structure is not returned.</span></span>

## <a name="requirements"></a><span data-ttu-id="2eb09-178">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2eb09-178">Requirements</span></span>  
 <span data-ttu-id="2eb09-179">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2eb09-179">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2eb09-180">**Üstbilgi:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="2eb09-180">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="2eb09-181">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="2eb09-181">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2eb09-182">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2eb09-182">See also</span></span>

- [<span data-ttu-id="2eb09-183">WMI ve Performans Sayaçları (Yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="2eb09-183">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
