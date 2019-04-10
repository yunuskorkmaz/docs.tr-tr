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
ms.openlocfilehash: d34cb399ac0e8780c442eeb2e95cebfd0a22ca02
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59208325"
---
# <a name="getobjecttext-function"></a><span data-ttu-id="944a0-103">GetObjectText işlevi</span><span class="sxs-lookup"><span data-stu-id="944a0-103">GetObjectText function</span></span>
<span data-ttu-id="944a0-104">Nesnenin değerinin metinsel bir işleme Yönetilen Nesne Biçimi (MOF) söz diziminde döndürür.</span><span class="sxs-lookup"><span data-stu-id="944a0-104">Returns a textual rendering of the object in the Managed Object Format (MOF) syntax.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="944a0-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="944a0-105">Syntax</span></span>  
  
```  
HRESULT GetObjectText (
   [in] int                vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LONG                lFlags,
   [out] BSTR*              pstrObjectText
); 
```  

## <a name="parameters"></a><span data-ttu-id="944a0-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="944a0-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="944a0-107">[in] Bu parametre kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="944a0-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="944a0-108">[in] Bir işaretçi bir [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneği.</span><span class="sxs-lookup"><span data-stu-id="944a0-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lFlags`  
<span data-ttu-id="944a0-109">[in] Normalde 0.</span><span class="sxs-lookup"><span data-stu-id="944a0-109">[in] Normally 0.</span></span> <span data-ttu-id="944a0-110">Varsa `WBEM_FLAG_NO_FLAVORS` (veya 0x1) belirtilirse, niteleyicileri yayma veya flavor bilgileri olmadan dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="944a0-110">If `WBEM_FLAG_NO_FLAVORS` (or 0x1) is specified, qualifiers are included without propagation or flavor information.</span></span>

`pstrObjectText`   
<span data-ttu-id="944a0-111">[out] Bir işaretçi bir `null` girişi.</span><span class="sxs-lookup"><span data-stu-id="944a0-111">[out] A pointer to a `null` on entry.</span></span> <span data-ttu-id="944a0-112">Üzerinde iade, yeni ayrılan `BSTR` , içeren nesnenin MOF sözdizimi işleme.</span><span class="sxs-lookup"><span data-stu-id="944a0-112">On return, a newly allocated `BSTR` that contains a MOF syntax rendering of the object.</span></span>  

## <a name="return-value"></a><span data-ttu-id="944a0-113">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="944a0-113">Return value</span></span>

<span data-ttu-id="944a0-114">Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üst bilgi dosyası veya tanımlayabilirsiniz bunları sabitleri kodunuzda:</span><span class="sxs-lookup"><span data-stu-id="944a0-114">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="944a0-115">Sabit</span><span class="sxs-lookup"><span data-stu-id="944a0-115">Constant</span></span>  |<span data-ttu-id="944a0-116">Değer</span><span class="sxs-lookup"><span data-stu-id="944a0-116">Value</span></span>  |<span data-ttu-id="944a0-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="944a0-117">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="944a0-118">0x80041001</span><span class="sxs-lookup"><span data-stu-id="944a0-118">0x80041001</span></span> | <span data-ttu-id="944a0-119">Genel bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="944a0-119">There has been a general failure.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="944a0-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="944a0-120">0x80041008</span></span> | <span data-ttu-id="944a0-121">Bir parametre geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="944a0-121">A parameter is not valid.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="944a0-122">0x80041006</span><span class="sxs-lookup"><span data-stu-id="944a0-122">0x80041006</span></span> | <span data-ttu-id="944a0-123">İşlemi tamamlamak yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="944a0-123">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="944a0-124">0</span><span class="sxs-lookup"><span data-stu-id="944a0-124">0</span></span> | <span data-ttu-id="944a0-125">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="944a0-125">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="944a0-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="944a0-126">Remarks</span></span>

<span data-ttu-id="944a0-127">Bu işlev bir çağrı sarılır [IWbemClassObject::GetObjectText](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getobjecttext) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="944a0-127">This function wraps a call to the [IWbemClassObject::GetObjectText](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getobjecttext) method.</span></span>

<span data-ttu-id="944a0-128">Döndürülen MOF metin nesnesine ilişkin tüm bilgileri, ancak orijinal nesneyi yeniden oluşturmaya yapabilmek MOF derleyicisi için yeterli bilgi içermiyor.</span><span class="sxs-lookup"><span data-stu-id="944a0-128">The MOF text returned does not contain all the information about the object, but only enough information for the MOF compiler to be able to recreate the original object.</span></span> <span data-ttu-id="944a0-129">Örneğin, yayılan niteleyicileri ya da üst sınıfı özellikleri dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="944a0-129">For instance, no propagated qualifiers or parent class properties are included.</span></span>

<span data-ttu-id="944a0-130">Aşağıdaki algoritması, bir yöntemin parametre metin yeniden oluşturmak için kullanılır:</span><span class="sxs-lookup"><span data-stu-id="944a0-130">The following algorithm is used to reconstruct the text of the parameters of a method:</span></span>

1. <span data-ttu-id="944a0-131">Parametre tanımlayıcı değerlerini sırasına göre yeniden sıralanmış.</span><span class="sxs-lookup"><span data-stu-id="944a0-131">Parameters are resequenced in the order of their identifier values.</span></span>
1. <span data-ttu-id="944a0-132">Parametre olarak belirtilen `[in]` ve `[out]` tek bir parametre birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="944a0-132">Parameters that are specified as `[in]` and `[out]` are combined into a single parameter.</span></span>
 
`pstrObjectText` <span data-ttu-id="944a0-133">bir işaretçi olmalıdır bir `null` işlev çağrıldığında; bu işaretçisi serbest çünkü yöntem çağrısından önce geçerli bir dizeye işaret etmelidir değil.</span><span class="sxs-lookup"><span data-stu-id="944a0-133">must be a pointer to a `null` when the function is called; it must not point to a string that is valid before the method call, because the pointer will not be deallocated.</span></span>

## <a name="requirements"></a><span data-ttu-id="944a0-134">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="944a0-134">Requirements</span></span>  
<span data-ttu-id="944a0-135">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="944a0-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="944a0-136">**Üst bilgi:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="944a0-136">**Header:** WMINet_Utils.idl</span></span>  
  
 **<span data-ttu-id="944a0-137">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="944a0-137">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a><span data-ttu-id="944a0-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="944a0-138">See also</span></span>

- [<span data-ttu-id="944a0-139">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="944a0-139">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
