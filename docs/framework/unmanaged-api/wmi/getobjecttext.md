---
title: GetObjectText işlevi (yönetilmeyen API Başvurusu)
description: GetObjectText işlevi bir metin işleme bir nesnenin MOF sözdiziminde döndürür.
ms.date: 11/06/2017
api_name:
- GetObjectText
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetObjectText
helpviewer_keywords:
- GetObjectText function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4438b000a8ecf95949350d3665267276a1d959ec
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67746487"
---
# <a name="getobjecttext-function"></a><span data-ttu-id="dbbc9-103">GetObjectText işlevi</span><span class="sxs-lookup"><span data-stu-id="dbbc9-103">GetObjectText function</span></span>
<span data-ttu-id="dbbc9-104">Nesnenin değerinin metinsel bir işleme Yönetilen Nesne Biçimi (MOF) söz diziminde döndürür.</span><span class="sxs-lookup"><span data-stu-id="dbbc9-104">Returns a textual rendering of the object in the Managed Object Format (MOF) syntax.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="dbbc9-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dbbc9-105">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectText (
   [in] int                vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LONG                lFlags,
   [out] BSTR*              pstrObjectText
); 
```  

## <a name="parameters"></a><span data-ttu-id="dbbc9-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="dbbc9-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="dbbc9-107">[in] Bu parametre kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="dbbc9-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="dbbc9-108">[in] Bir işaretçi bir [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneği.</span><span class="sxs-lookup"><span data-stu-id="dbbc9-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lFlags`  
<span data-ttu-id="dbbc9-109">[in] Normalde 0.</span><span class="sxs-lookup"><span data-stu-id="dbbc9-109">[in] Normally 0.</span></span> <span data-ttu-id="dbbc9-110">Varsa `WBEM_FLAG_NO_FLAVORS` (veya 0x1) belirtilirse, niteleyicileri yayma veya flavor bilgileri olmadan dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="dbbc9-110">If `WBEM_FLAG_NO_FLAVORS` (or 0x1) is specified, qualifiers are included without propagation or flavor information.</span></span>

`pstrObjectText`   
<span data-ttu-id="dbbc9-111">[out] Bir işaretçi bir `null` girişi.</span><span class="sxs-lookup"><span data-stu-id="dbbc9-111">[out] A pointer to a `null` on entry.</span></span> <span data-ttu-id="dbbc9-112">Üzerinde iade, yeni ayrılan `BSTR` , içeren nesnenin MOF sözdizimi işleme.</span><span class="sxs-lookup"><span data-stu-id="dbbc9-112">On return, a newly allocated `BSTR` that contains a MOF syntax rendering of the object.</span></span>  

## <a name="return-value"></a><span data-ttu-id="dbbc9-113">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="dbbc9-113">Return value</span></span>

<span data-ttu-id="dbbc9-114">Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üst bilgi dosyası veya tanımlayabilirsiniz bunları sabitleri kodunuzda:</span><span class="sxs-lookup"><span data-stu-id="dbbc9-114">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="dbbc9-115">Sabit</span><span class="sxs-lookup"><span data-stu-id="dbbc9-115">Constant</span></span>  |<span data-ttu-id="dbbc9-116">Değer</span><span class="sxs-lookup"><span data-stu-id="dbbc9-116">Value</span></span>  |<span data-ttu-id="dbbc9-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dbbc9-117">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="dbbc9-118">0x80041001</span><span class="sxs-lookup"><span data-stu-id="dbbc9-118">0x80041001</span></span> | <span data-ttu-id="dbbc9-119">Genel bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="dbbc9-119">There has been a general failure.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="dbbc9-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="dbbc9-120">0x80041008</span></span> | <span data-ttu-id="dbbc9-121">Bir parametre geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="dbbc9-121">A parameter is not valid.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="dbbc9-122">0x80041006</span><span class="sxs-lookup"><span data-stu-id="dbbc9-122">0x80041006</span></span> | <span data-ttu-id="dbbc9-123">İşlemi tamamlamak yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="dbbc9-123">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="dbbc9-124">0</span><span class="sxs-lookup"><span data-stu-id="dbbc9-124">0</span></span> | <span data-ttu-id="dbbc9-125">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="dbbc9-125">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="dbbc9-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dbbc9-126">Remarks</span></span>

<span data-ttu-id="dbbc9-127">Bu işlev bir çağrı sarılır [IWbemClassObject::GetObjectText](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getobjecttext) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="dbbc9-127">This function wraps a call to the [IWbemClassObject::GetObjectText](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getobjecttext) method.</span></span>

<span data-ttu-id="dbbc9-128">Döndürülen MOF metin nesnesine ilişkin tüm bilgileri, ancak orijinal nesneyi yeniden oluşturmaya yapabilmek MOF derleyicisi için yeterli bilgi içermiyor.</span><span class="sxs-lookup"><span data-stu-id="dbbc9-128">The MOF text returned does not contain all the information about the object, but only enough information for the MOF compiler to be able to recreate the original object.</span></span> <span data-ttu-id="dbbc9-129">Örneğin, yayılan niteleyicileri ya da üst sınıfı özellikleri dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="dbbc9-129">For instance, no propagated qualifiers or parent class properties are included.</span></span>

<span data-ttu-id="dbbc9-130">Aşağıdaki algoritması, bir yöntemin parametre metin yeniden oluşturmak için kullanılır:</span><span class="sxs-lookup"><span data-stu-id="dbbc9-130">The following algorithm is used to reconstruct the text of the parameters of a method:</span></span>

1. <span data-ttu-id="dbbc9-131">Parametre tanımlayıcı değerlerini sırasına göre yeniden sıralanmış.</span><span class="sxs-lookup"><span data-stu-id="dbbc9-131">Parameters are resequenced in the order of their identifier values.</span></span>
1. <span data-ttu-id="dbbc9-132">Parametre olarak belirtilen `[in]` ve `[out]` tek bir parametre birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="dbbc9-132">Parameters that are specified as `[in]` and `[out]` are combined into a single parameter.</span></span>
 
<span data-ttu-id="dbbc9-133">`pstrObjectText` bir işaretçi olmalıdır bir `null` işlev çağrıldığında; bu işaretçisi serbest çünkü yöntem çağrısından önce geçerli bir dizeye işaret etmelidir değil.</span><span class="sxs-lookup"><span data-stu-id="dbbc9-133">`pstrObjectText` must be a pointer to a `null` when the function is called; it must not point to a string that is valid before the method call, because the pointer will not be deallocated.</span></span>

## <a name="requirements"></a><span data-ttu-id="dbbc9-134">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dbbc9-134">Requirements</span></span>  
<span data-ttu-id="dbbc9-135">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dbbc9-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dbbc9-136">**Üst bilgi:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="dbbc9-136">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="dbbc9-137">**.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="dbbc9-137">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbbc9-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dbbc9-138">See also</span></span>

- [<span data-ttu-id="dbbc9-139">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="dbbc9-139">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
