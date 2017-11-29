---
title: "CompareTo işlevi (yönetilmeyen API Başvurusu)"
description: "CompareTo işlevi başka bir WMI nesnesi bir nesneyi karşılaştırır."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: CompareTo
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: CompareTo
helpviewer_keywords: CompareTo function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: dacb1516bebfc73ae9e16b03f3755ab49382e571
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/15/2017
---
# <a name="compareto-function"></a><span data-ttu-id="a4c40-103">CompareTo işlevi</span><span class="sxs-lookup"><span data-stu-id="a4c40-103">CompareTo function</span></span>
<span data-ttu-id="a4c40-104">Nesneyi başka bir Windows Yönetim nesnesi için karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="a4c40-104">Compares an object to another Windows management object.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="a4c40-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a4c40-105">Syntax</span></span>  
  
```
HRESULT CompareTo (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LONG              flags,
   [in] IWbemClassObject* pCompareTo 
); 
```  

## <a name="parameters"></a><span data-ttu-id="a4c40-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a4c40-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="a4c40-107">[in] Bu parametre kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="a4c40-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="a4c40-108">[in] Bir işaretçi bir [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) örneği.</span><span class="sxs-lookup"><span data-stu-id="a4c40-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`flags`  
<span data-ttu-id="a4c40-109">[in] Karşılaştırma için dikkate alınması gereken nesne özellikleri belirten bayrakları Bitsel bir birleşimi.</span><span class="sxs-lookup"><span data-stu-id="a4c40-109">[in] A bitwise combination of the flags that specify the object characteristics to consider for the comparison.</span></span> <span data-ttu-id="a4c40-110">Bkz: [açıklamalar](#remarks) daha fazla bilgi için bölüm.</span><span class="sxs-lookup"><span data-stu-id="a4c40-110">See the [Remarks](#remarks) section for more information.</span></span>

`pCompareTo`  

<span data-ttu-id="a4c40-111">[in] Karşılaştırma için nesnesi.</span><span class="sxs-lookup"><span data-stu-id="a4c40-111">[in] The object for comparison.</span></span> <span data-ttu-id="a4c40-112">`pcompareTo`Geçerli bir olmalıdır [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) örnek; olamaz `null`.</span><span class="sxs-lookup"><span data-stu-id="a4c40-112">`pcompareTo` must be a valid [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance; it cannot be `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="a4c40-113">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="a4c40-113">Return value</span></span>

<span data-ttu-id="a4c40-114">Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üstbilgi dosyası, veya tanımlayabilirsiniz bunları sabitleri kodunuzda:</span><span class="sxs-lookup"><span data-stu-id="a4c40-114">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="a4c40-115">Sabit</span><span class="sxs-lookup"><span data-stu-id="a4c40-115">Constant</span></span>  |<span data-ttu-id="a4c40-116">Değer</span><span class="sxs-lookup"><span data-stu-id="a4c40-116">Value</span></span>  |<span data-ttu-id="a4c40-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a4c40-117">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="a4c40-118">0x80041001</span><span class="sxs-lookup"><span data-stu-id="a4c40-118">0x80041001</span></span> | <span data-ttu-id="a4c40-119">Belirlenemeyen bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="a4c40-119">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="a4c40-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="a4c40-120">0x80041008</span></span> | <span data-ttu-id="a4c40-121">Bir parametre geçersiz.</span><span class="sxs-lookup"><span data-stu-id="a4c40-121">A parameter is invalid.</span></span> |
| `WBEM_E_UNEXPECTED` | <span data-ttu-id="a4c40-122">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="a4c40-122">0x8004101d</span></span> | <span data-ttu-id="a4c40-123">İkinci çağrı `BeginEnumeration` olmadan müdahalede bulunan bir çağrı yapıldı [ `EndEnumeration` ](endenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="a4c40-123">A second call to `BeginEnumeration` was made without an intervening call to [`EndEnumeration`](endenumeration.md).</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="a4c40-124">0</span><span class="sxs-lookup"><span data-stu-id="a4c40-124">0</span></span> | <span data-ttu-id="a4c40-125">İşlev çağrısı başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="a4c40-125">The function call was successful.</span></span>  |
| `WBEM_S_DIFFERENT` | <span data-ttu-id="a4c40-126">0x40003</span><span class="sxs-lookup"><span data-stu-id="a4c40-126">0x40003</span></span> | <span data-ttu-id="a4c40-127">Nesneleri farklıdır.</span><span class="sxs-lookup"><span data-stu-id="a4c40-127">The objects are different.</span></span> |
| `WBEM_S_SAME` | <span data-ttu-id="a4c40-128">0</span><span class="sxs-lookup"><span data-stu-id="a4c40-128">0</span></span> | <span data-ttu-id="a4c40-129">Nesneleri karşılaştırma bayrakları dayalı aynıdır.</span><span class="sxs-lookup"><span data-stu-id="a4c40-129">The objects are the same based on the comparison flags.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="a4c40-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a4c40-130">Remarks</span></span>

<span data-ttu-id="a4c40-131">Bu işlev çağrısı sarmalar [IWbemClassObject::CompareTo](https://msdn.microsoft.com/library/aa391437(v=vs.85).aspx) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="a4c40-131">This function wraps a call to the [IWbemClassObject::CompareTo](https://msdn.microsoft.com/library/aa391437(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="a4c40-132">Olarak geçirilen bayraklar `lEnumFlags` bağımsız değişkeni tanımlanmış *WbemCli.h* üstbilgi dosyası, veya tanımlayabilirsiniz bunları sabitleri kodunuzda.</span><span class="sxs-lookup"><span data-stu-id="a4c40-132">The flags that can be passed as the `lEnumFlags` argument are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span> <span data-ttu-id="a4c40-133">Aşağıdaki bayraklar Bitsel bir birleşimi belirterek Karşılaştırmada söz konusu tek tek özellikleri belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="a4c40-133">You can specify the individual characteristics involved in the comparison by specifying a bitwise combination of the following flags:</span></span>

|<span data-ttu-id="a4c40-134">Sabit</span><span class="sxs-lookup"><span data-stu-id="a4c40-134">Constant</span></span>  |<span data-ttu-id="a4c40-135">Değer</span><span class="sxs-lookup"><span data-stu-id="a4c40-135">Value</span></span>  |<span data-ttu-id="a4c40-136">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a4c40-136">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_IGNORE_OBJECT_SOURCE` | <span data-ttu-id="a4c40-137">2</span><span class="sxs-lookup"><span data-stu-id="a4c40-137">2</span></span> | <span data-ttu-id="a4c40-138">Kaynak (sunucu ve bunların nereden geldiğini ad alanı) yoksay.</span><span class="sxs-lookup"><span data-stu-id="a4c40-138">Ignore the source (the server and the namespace they came from).</span></span> |
| `WBEM_FLAG_IGNORE_QUALIFIERS` | <span data-ttu-id="a4c40-139">1.</span><span class="sxs-lookup"><span data-stu-id="a4c40-139">1</span></span> | <span data-ttu-id="a4c40-140">Tüm niteleyicileri yoksay (de dahil olmak üzere **anahtar** ve **dinamik**)</span><span class="sxs-lookup"><span data-stu-id="a4c40-140">Ignore all qualifiers (including **Key** and **Dynamic**)</span></span> |
| `WBEM_FLAG_IGNORE_DEFAULT_VALUES` | <span data-ttu-id="a4c40-141">4</span><span class="sxs-lookup"><span data-stu-id="a4c40-141">4</span></span> | <span data-ttu-id="a4c40-142">Özelliklerin varsayılan değerleri yok sayın.</span><span class="sxs-lookup"><span data-stu-id="a4c40-142">Ignore default values of properties.</span></span> <span data-ttu-id="a4c40-143">Bu bayrak, yalnızca sınıfları bir karşılaştırması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="a4c40-143">This flag only applies to comparison of classes.</span></span> |
| `WBEM_FLAG_IGNORE_FLAVOR` | <span data-ttu-id="a4c40-144">0x20</span><span class="sxs-lookup"><span data-stu-id="a4c40-144">0x20</span></span> | <span data-ttu-id="a4c40-145">Niteleyici özellikleri yoksay.</span><span class="sxs-lookup"><span data-stu-id="a4c40-145">Ignore qualifier flavors.</span></span> <span data-ttu-id="a4c40-146">Bu bayrak hala niteleyicileri, dikkate alır, ancak özellik farklılıklar yayma kurallar gibi yoksayar ve kısıtlamalarını geçersiz kılmak.</span><span class="sxs-lookup"><span data-stu-id="a4c40-146">This flag still takes qualifiers into account, but ignores flavor distinctions such as propagation rules and override restrictions.</span></span> |
| `WBEM_FLAG_IGNORE_CASE` | <span data-ttu-id="a4c40-147">0x10</span><span class="sxs-lookup"><span data-stu-id="a4c40-147">0x10</span></span> | <span data-ttu-id="a4c40-148">Dize değerleri karşılaştırma içinde durumu yoksay.</span><span class="sxs-lookup"><span data-stu-id="a4c40-148">Ignore case in comparing string values.</span></span> <span data-ttu-id="a4c40-149">Bu, hem dizeler ve niteleyicisi değerleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="a4c40-149">This applies both to strings and qualifier values.</span></span> <span data-ttu-id="a4c40-150">Özellik ve niteleyicisi adları karşılaştırması bu bayrağı ayarlanmış olduğundan bağımsız olarak her zaman duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="a4c40-150">The comparison of property and qualifier names is always case-sensitive regardless of whether this flag is set.</span></span> |
| `WBEM_FLAG_IGNORE_CLASS` | <span data-ttu-id="a4c40-151">0x8</span><span class="sxs-lookup"><span data-stu-id="a4c40-151">0x8</span></span> | <span data-ttu-id="a4c40-152">Karşılaştırılan nesnelerin aynı sınıf örneklerinin olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="a4c40-152">Assume that the objects being compared are instanes of the same class.</span></span> <span data-ttu-id="a4c40-153">Sonuç olarak, bu bayrak örneği ile ilgili bilgiler yalnızca karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="a4c40-153">Consequently, this flag compares instance-related information only.</span></span> <span data-ttu-id="a4c40-154">Bu bayrak, performansı iyileştirmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="a4c40-154">Use this flags to optimize performance.</span></span> <span data-ttu-id="a4c40-155">Nesneleri aynı sınıfının emin değilseniz, sonuçları tanımlanmamış.</span><span class="sxs-lookup"><span data-stu-id="a4c40-155">If the objects are not of the same class, the results are undefined.</span></span> |

<span data-ttu-id="a4c40-156">Veya tek bir birleşik bayrak aşağıdaki gibi belirtin:</span><span class="sxs-lookup"><span data-stu-id="a4c40-156">Or you can specify a single composite flag as follows:</span></span>

|<span data-ttu-id="a4c40-157">Sabit</span><span class="sxs-lookup"><span data-stu-id="a4c40-157">Constant</span></span>  |<span data-ttu-id="a4c40-158">Değer</span><span class="sxs-lookup"><span data-stu-id="a4c40-158">Value</span></span>  |<span data-ttu-id="a4c40-159">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a4c40-159">Description</span></span>  |
|---------|---------|---------|
|`WBEM_COMPARISON_INCLUDE_ALL` | <span data-ttu-id="a4c40-160">0</span><span class="sxs-lookup"><span data-stu-id="a4c40-160">0</span></span> | <span data-ttu-id="a4c40-161">Karşılaştırma tüm özelliklerini göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="a4c40-161">Consider all features in the comparison.</span></span> |

## <a name="requirements"></a><span data-ttu-id="a4c40-162">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a4c40-162">Requirements</span></span>  
 <span data-ttu-id="a4c40-163">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a4c40-163">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a4c40-164">**Başlık:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="a4c40-164">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="a4c40-165">**.NET framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="a4c40-165">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4c40-166">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a4c40-166">See also</span></span>  
[<span data-ttu-id="a4c40-167">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="a4c40-167">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
