---
title: "GetObjectText işlevi (yönetilmeyen API Başvurusu)"
description: "GetObjectText işlevi bir nesnenin bir metinsel oluşturma MOF sözdiziminde döndürür."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: GetObjectText
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: GetObjectText
helpviewer_keywords: GetObjectText function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0b47dc73bb9da71b0c8593aa5758179327d7572d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="getobjecttext-function"></a><span data-ttu-id="4292a-103">GetObjectText işlevi</span><span class="sxs-lookup"><span data-stu-id="4292a-103">GetObjectText function</span></span>
<span data-ttu-id="4292a-104">Nesnenin metinsel işleme Yönetilen Nesne Biçimi (MOF) sözdiziminde döndürür.</span><span class="sxs-lookup"><span data-stu-id="4292a-104">Returns a textual rendering of the object in the Managed Object Format (MOF) syntax.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="4292a-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4292a-105">Syntax</span></span>  
  
```  
HRESULT GetObjectText (
   [in] int                vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LONG                lFlags,
   [out] BSTR*              pstrObjectText
); 
```  

## <a name="parameters"></a><span data-ttu-id="4292a-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4292a-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="4292a-107">[in] Bu parametre kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="4292a-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="4292a-108">[in] Bir işaretçi bir [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) örneği.</span><span class="sxs-lookup"><span data-stu-id="4292a-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`lFlags`  
<span data-ttu-id="4292a-109">[in] Normalde 0.</span><span class="sxs-lookup"><span data-stu-id="4292a-109">[in] Normally 0.</span></span> <span data-ttu-id="4292a-110">Varsa `WBEM_FLAG_NO_FLAVORS` (veya 0x1) belirtilirse, niteleyicileri yayma veya özellik bilgileri olmadan dahil.</span><span class="sxs-lookup"><span data-stu-id="4292a-110">If `WBEM_FLAG_NO_FLAVORS` (or 0x1) is specified, qualifiers are included without propagation or flavor information.</span></span>

`pstrObjectText`   
<span data-ttu-id="4292a-111">[out] Bir işaretçi bir `null` girişi.</span><span class="sxs-lookup"><span data-stu-id="4292a-111">[out] A pointer to a `null` on entry.</span></span> <span data-ttu-id="4292a-112">Üzerinde dönün, yeni ayrılan `BSTR` nesnenin MOF sözdizimi işleme içerir.</span><span class="sxs-lookup"><span data-stu-id="4292a-112">On return, a newly allocated `BSTR` that contains a MOF syntax rendering of the object.</span></span>  

## <a name="return-value"></a><span data-ttu-id="4292a-113">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="4292a-113">Return value</span></span>

<span data-ttu-id="4292a-114">Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üstbilgi dosyası, veya tanımlayabilirsiniz bunları sabitleri kodunuzda:</span><span class="sxs-lookup"><span data-stu-id="4292a-114">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="4292a-115">Sabit</span><span class="sxs-lookup"><span data-stu-id="4292a-115">Constant</span></span>  |<span data-ttu-id="4292a-116">Değer</span><span class="sxs-lookup"><span data-stu-id="4292a-116">Value</span></span>  |<span data-ttu-id="4292a-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4292a-117">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="4292a-118">0x80041001</span><span class="sxs-lookup"><span data-stu-id="4292a-118">0x80041001</span></span> | <span data-ttu-id="4292a-119">Genel bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="4292a-119">There has been a general failure.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="4292a-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="4292a-120">0x80041008</span></span> | <span data-ttu-id="4292a-121">Parametre geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="4292a-121">A parameter is not valid.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="4292a-122">0x80041006</span><span class="sxs-lookup"><span data-stu-id="4292a-122">0x80041006</span></span> | <span data-ttu-id="4292a-123">İşlemi tamamlamak yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="4292a-123">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="4292a-124">0</span><span class="sxs-lookup"><span data-stu-id="4292a-124">0</span></span> | <span data-ttu-id="4292a-125">İşlev çağrısı başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="4292a-125">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="4292a-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4292a-126">Remarks</span></span>

<span data-ttu-id="4292a-127">Bu işlev çağrısı sarmalar [IWbemClassObject::GetObjectText](https://msdn.microsoft.com/library/aa391448(v=vs.85).aspx) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="4292a-127">This function wraps a call to the [IWbemClassObject::GetObjectText](https://msdn.microsoft.com/library/aa391448(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="4292a-128">Döndürülen MOF metni nesneyle ilgili tüm bilgileri, ancak yalnızca orijinal nesneyi yeniden yapabilmek MOF Derleyici yeterli bilgi içermiyor.</span><span class="sxs-lookup"><span data-stu-id="4292a-128">The MOF text returned does not contain all the information about the object, but only enough information for the MOF compiler to be able to recreate the original object.</span></span> <span data-ttu-id="4292a-129">Örneğin, hiçbir yayılan niteleyicileri veya üst sınıf özellikleri dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="4292a-129">For instance, no propagated qualifiers or parent class properties are included.</span></span>

<span data-ttu-id="4292a-130">Aşağıdaki algoritması, bir yöntemin parametrelerini metnin yeniden oluşturmak için kullanılır:</span><span class="sxs-lookup"><span data-stu-id="4292a-130">The following algorithm is used to reconstruct the text of the parameters of a method:</span></span>

1. <span data-ttu-id="4292a-131">Parametre tanımlayıcı değerlerini sırasına göre yeniden sıralanmış.</span><span class="sxs-lookup"><span data-stu-id="4292a-131">Parameters are resequenced in the order of their identifier values.</span></span>
1. <span data-ttu-id="4292a-132">Olarak belirtilen parametreleri `[in]` ve `[out]` tek bir parametre birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="4292a-132">Parameters that are specified as `[in]` and `[out]` are combined into a single parameter.</span></span>
 
<span data-ttu-id="4292a-133">`pstrObjectText`bir işaretçi olmalıdır bir `null` işlevi çağrıldığında; Bu işaretçinin değil serbest olduğundan yöntem çağrısı önce geçerli bir dize işaret etmelidir değil.</span><span class="sxs-lookup"><span data-stu-id="4292a-133">`pstrObjectText` must be a pointer to a `null` when the function is called; it must not point to a string that is valid before the method call, because the pointer will not be deallocated.</span></span>

## <a name="requirements"></a><span data-ttu-id="4292a-134">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4292a-134">Requirements</span></span>  
<span data-ttu-id="4292a-135">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4292a-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4292a-136">**Başlık:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="4292a-136">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="4292a-137">**.NET framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="4292a-137">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4292a-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4292a-138">See also</span></span>  
[<span data-ttu-id="4292a-139">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="4292a-139">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
