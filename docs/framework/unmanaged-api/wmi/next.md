---
title: Next işlevi (yönetilmeyen API Başvurusu)
description: Sonraki işlev retireves numaralandırma sonraki özelliği.
ms.date: 11/06/2017
api_name:
- Next
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Next
helpviewer_keywords:
- Next function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e945930a9a668d0a1c1e4c26bf3add9cc574c261
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33461434"
---
# <a name="next-function"></a><span data-ttu-id="2b04a-103">Next işlevi</span><span class="sxs-lookup"><span data-stu-id="2b04a-103">Next function</span></span>
<span data-ttu-id="2b04a-104">Sonraki çağrı ile başlayan bir numaralandırma özelliğinde alır [BeginEnumeration](beginenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="2b04a-104">Retrieves the next property in an enumeration that begins with a call to [BeginEnumeration](beginenumeration.md).</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="2b04a-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2b04a-105">Syntax</span></span>  
  
```  
HRESULT Next (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LONG              lFlags,
   [out] BSTR*            pstrName,
   [out] VARIANT*         pVal,
   [out] CIMTYPE*         pvtType,
   [out] LONG*            plFlavor     
); 
```  

## <a name="parameters"></a><span data-ttu-id="2b04a-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2b04a-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="2b04a-107">[in] Bu parametre kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="2b04a-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="2b04a-108">[in] Bir işaretçi bir [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) örneği.</span><span class="sxs-lookup"><span data-stu-id="2b04a-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`lFlags`  
<span data-ttu-id="2b04a-109">[in] Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="2b04a-109">[in] Reserved.</span></span> <span data-ttu-id="2b04a-110">Bu parametre 0 olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2b04a-110">This parameter must be 0.</span></span>

`pstrName`  
<span data-ttu-id="2b04a-111">[out] Yeni bir `BSTR` özellik adını içerir.</span><span class="sxs-lookup"><span data-stu-id="2b04a-111">[out] A new `BSTR` that contains the property name.</span></span> <span data-ttu-id="2b04a-112">Bu parametre ayarlayabileceğiniz `null` adı gerekli değilse.</span><span class="sxs-lookup"><span data-stu-id="2b04a-112">You can set this parameter to `null` if the name is not required.</span></span>

`pVal`  
<span data-ttu-id="2b04a-113">[out] A `VARIANT` özelliğinin değeri ile doldurulur.</span><span class="sxs-lookup"><span data-stu-id="2b04a-113">[out] A `VARIANT` filled with the value of the property.</span></span> <span data-ttu-id="2b04a-114">Bu parametre ayarlayabileceğiniz `null` değeri gerekli değilse.</span><span class="sxs-lookup"><span data-stu-id="2b04a-114">You can set this parameter to `null` if the value is not required.</span></span> <span data-ttu-id="2b04a-115">İşlevi bir hata kodu döndürürse `VARIANT` geçirilen `pVal` sol değiştirilmemiş.</span><span class="sxs-lookup"><span data-stu-id="2b04a-115">If the function returns an error code, the `VARIANT` passed to `pVal` is left unmodified.</span></span> 

`pvtType`  
<span data-ttu-id="2b04a-116">[out] Bir işaretçi bir `CIMTYPE` değişken (bir `LONG` özelliğinin türü yerleştirildiği içine).</span><span class="sxs-lookup"><span data-stu-id="2b04a-116">[out] A pointer to a `CIMTYPE` variable (a `LONG` into which the type of the property is placed).</span></span> <span data-ttu-id="2b04a-117">Bu özelliğin değeri olabilir bir `VT_NULL_VARIANT`, gerçek tür özelliğinin belirlemek gerekli değildir; bu durumda.</span><span class="sxs-lookup"><span data-stu-id="2b04a-117">The value of this property can be a `VT_NULL_VARIANT`, in which case it is necessary to determine the actual type of the property.</span></span> <span data-ttu-id="2b04a-118">Bu parametre de olabilir `null`.</span><span class="sxs-lookup"><span data-stu-id="2b04a-118">This parameter can also be `null`.</span></span> 

`plFlavor`  
<span data-ttu-id="2b04a-119">[out] `null`, veya özelliğin kaynak hakkında bilgi alan bir değer.</span><span class="sxs-lookup"><span data-stu-id="2b04a-119">[out] `null`, or a value that receives information on the origin of the property.</span></span> <span data-ttu-id="2b04a-120">Olası değerler [uyarılar] bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="2b04a-120">See the [Remarks] section for possible values.</span></span> 

## <a name="return-value"></a><span data-ttu-id="2b04a-121">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="2b04a-121">Return value</span></span>

<span data-ttu-id="2b04a-122">Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üstbilgi dosyası, veya tanımlayabilirsiniz bunları sabitleri kodunuzda:</span><span class="sxs-lookup"><span data-stu-id="2b04a-122">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="2b04a-123">Sabit</span><span class="sxs-lookup"><span data-stu-id="2b04a-123">Constant</span></span>  |<span data-ttu-id="2b04a-124">Değer</span><span class="sxs-lookup"><span data-stu-id="2b04a-124">Value</span></span>  |<span data-ttu-id="2b04a-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2b04a-125">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="2b04a-126">0x80041001</span><span class="sxs-lookup"><span data-stu-id="2b04a-126">0x80041001</span></span> | <span data-ttu-id="2b04a-127">Genel bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="2b04a-127">There has been a general failure.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="2b04a-128">0x80041008</span><span class="sxs-lookup"><span data-stu-id="2b04a-128">0x80041008</span></span> | <span data-ttu-id="2b04a-129">Bir parametre geçersiz.</span><span class="sxs-lookup"><span data-stu-id="2b04a-129">A parameter is invalid.</span></span> |
| `WBEM_E_UNEXPECTED` | <span data-ttu-id="2b04a-130">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="2b04a-130">0x8004101d</span></span> | <span data-ttu-id="2b04a-131">Hiçbir çağrısına vardı [ `BeginEnumeration` ](beginenumeration.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="2b04a-131">There was no call to the [`BeginEnumeration`](beginenumeration.md) function.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="2b04a-132">0x80041006</span><span class="sxs-lookup"><span data-stu-id="2b04a-132">0x80041006</span></span> | <span data-ttu-id="2b04a-133">Yeni bir numaralandırma başlatmak yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="2b04a-133">Not enough memory is available to begin a new enumeration.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="2b04a-134">0x80041015</span><span class="sxs-lookup"><span data-stu-id="2b04a-134">0x80041015</span></span> | <span data-ttu-id="2b04a-135">Uzak yordam çağrısı zamanlamalar geçerli işlem ile Windows Yönetimi başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="2b04a-135">The remote procedure call betweeen the current process and Windows Management failed.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="2b04a-136">0</span><span class="sxs-lookup"><span data-stu-id="2b04a-136">0</span></span> | <span data-ttu-id="2b04a-137">İşlev çağrısı başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="2b04a-137">The function call was successful.</span></span>  |
| `WBEM_S_NO_MORE_DATA` | <span data-ttu-id="2b04a-138">0x40005</span><span class="sxs-lookup"><span data-stu-id="2b04a-138">0x40005</span></span> | <span data-ttu-id="2b04a-139">Sabit listede daha fazla özellik yok.</span><span class="sxs-lookup"><span data-stu-id="2b04a-139">There are no more properties in the enumeration.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="2b04a-140">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2b04a-140">Remarks</span></span>

<span data-ttu-id="2b04a-141">Bu işlev çağrısı sarmalar [IWbemClassObject::Next](https://msdn.microsoft.com/library/aa391453(v=vs.85).aspx) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="2b04a-141">This function wraps a call to the [IWbemClassObject::Next](https://msdn.microsoft.com/library/aa391453(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="2b04a-142">Bu yöntem aynı zamanda Sistem özellikleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="2b04a-142">This method also returns system properties.</span></span>

<span data-ttu-id="2b04a-143">Özelliğin temel türü bir nesne yolu, bir tarih veya saat veya başka bir özel tür ise, döndürülen tür yeterli bilgi içermiyor.</span><span class="sxs-lookup"><span data-stu-id="2b04a-143">If the underlying type of the property is an object path, a date or time, or another special type, then the returned type does not contain enough information.</span></span> <span data-ttu-id="2b04a-144">Arayan incelemelisiniz `CIMTYPE` özelliği bir nesne başvurusu, bir tarih veya saat veya başka bir özel tür olup olmadığını belirlemek belirtilen özellik için.</span><span class="sxs-lookup"><span data-stu-id="2b04a-144">The caller must examine the `CIMTYPE` for the specified property to determine if the property is an object reference, a date or time, or another special type.</span></span>

<span data-ttu-id="2b04a-145">Varsa `plFlavor` değil `null`, `LONG` değer özelliğinin kaynak hakkında bilgi aşağıdaki gibi alır:</span><span class="sxs-lookup"><span data-stu-id="2b04a-145">If `plFlavor` is not `null`, the `LONG` value receives information about the origin of the property, as follows:</span></span>

|<span data-ttu-id="2b04a-146">Sabit</span><span class="sxs-lookup"><span data-stu-id="2b04a-146">Constant</span></span>  |<span data-ttu-id="2b04a-147">Değer</span><span class="sxs-lookup"><span data-stu-id="2b04a-147">Value</span></span>  |<span data-ttu-id="2b04a-148">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2b04a-148">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAVOR_ORIGIN_SYSTEM` | <span data-ttu-id="2b04a-149">0x40</span><span class="sxs-lookup"><span data-stu-id="2b04a-149">0x40</span></span> | <span data-ttu-id="2b04a-150">Özelliği bir standart sistemi özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="2b04a-150">The property is a standard system property.</span></span> |
| `WBEM_FLAVOR_ORIGIN_PROPAGATED` | <span data-ttu-id="2b04a-151">0x20</span><span class="sxs-lookup"><span data-stu-id="2b04a-151">0x20</span></span> | <span data-ttu-id="2b04a-152">Bir sınıf için: özellik üst sınıftan devralındı.</span><span class="sxs-lookup"><span data-stu-id="2b04a-152">For a class: The property is inherited from the parent class.</span></span> </br> <span data-ttu-id="2b04a-153">Bir örneği için: özellik üst sınıftan devralındı ederken örneği tarafından değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="2b04a-153">For an instance: The property, while inherited from the parent class, has not been modified by the instance.</span></span>  |
| `WBEM_FLAVOR_ORIGIN_LOCAL` | <span data-ttu-id="2b04a-154">0</span><span class="sxs-lookup"><span data-stu-id="2b04a-154">0</span></span> | <span data-ttu-id="2b04a-155">Bir sınıf için: türetilmiş sınıf özellik ait.</span><span class="sxs-lookup"><span data-stu-id="2b04a-155">For a class: The property belongs to the derived class.</span></span> </br> <span data-ttu-id="2b04a-156">Bir örneği için: özelliğini örneği tarafından; değiştirdi diğer bir deyişle, bir değer sağlandı veya bir niteleyicisi eklenemez veya değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="2b04a-156">For an instance: The property is modified by the instance; that is, a value was supplied, or a qualifier was added or modified.</span></span> |

## <a name="requirements"></a><span data-ttu-id="2b04a-157">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2b04a-157">Requirements</span></span>  
 <span data-ttu-id="2b04a-158">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2b04a-158">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2b04a-159">**Başlık:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="2b04a-159">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="2b04a-160">**.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="2b04a-160">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b04a-161">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2b04a-161">See also</span></span>  
[<span data-ttu-id="2b04a-162">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="2b04a-162">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
