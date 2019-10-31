---
title: GetObjectText işlevi (yönetilmeyen API Başvurusu)
description: GetObjectText işlevi, MOF sözdiziminde bir nesnenin metinsel işlemesini döndürür.
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
ms.openlocfilehash: 412e1ad503fa0e0b4f813298c0ac96ae80098c06
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73102462"
---
# <a name="getobjecttext-function"></a><span data-ttu-id="391e7-103">GetObjectText işlevi</span><span class="sxs-lookup"><span data-stu-id="391e7-103">GetObjectText function</span></span>
<span data-ttu-id="391e7-104">Yönetilen Nesne Biçimi (MOF) sözdiziminde nesnenin metinsel işlemesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="391e7-104">Returns a textual rendering of the object in the Managed Object Format (MOF) syntax.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="391e7-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="391e7-105">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectText (
   [in] int                vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LONG                lFlags,
   [out] BSTR*              pstrObjectText
); 
```  

## <a name="parameters"></a><span data-ttu-id="391e7-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="391e7-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="391e7-107">'ndaki Bu parametre kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="391e7-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="391e7-108">'ndaki [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneğine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="391e7-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lFlags`  
<span data-ttu-id="391e7-109">'ndaki Normalde 0.</span><span class="sxs-lookup"><span data-stu-id="391e7-109">[in] Normally 0.</span></span> <span data-ttu-id="391e7-110">`WBEM_FLAG_NO_FLAVORS` (veya 0x1) belirtilmişse, niteleyiciler yayma veya Flavor bilgileri olmaksızın dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="391e7-110">If `WBEM_FLAG_NO_FLAVORS` (or 0x1) is specified, qualifiers are included without propagation or flavor information.</span></span>

`pstrObjectText`   
<span data-ttu-id="391e7-111">dışı Girişteki `null` için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="391e7-111">[out] A pointer to a `null` on entry.</span></span> <span data-ttu-id="391e7-112">Dönüşte, nesnenin MOF sözdizimi işleme içeren yeni bir ayrılmış `BSTR`.</span><span class="sxs-lookup"><span data-stu-id="391e7-112">On return, a newly allocated `BSTR` that contains a MOF syntax rendering of the object.</span></span>  

## <a name="return-value"></a><span data-ttu-id="391e7-113">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="391e7-113">Return value</span></span>

<span data-ttu-id="391e7-114">Bu işlev tarafından döndürülen aşağıdaki değerler, *Wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="391e7-114">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="391e7-115">Sabit</span><span class="sxs-lookup"><span data-stu-id="391e7-115">Constant</span></span>  |<span data-ttu-id="391e7-116">Değer</span><span class="sxs-lookup"><span data-stu-id="391e7-116">Value</span></span>  |<span data-ttu-id="391e7-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="391e7-117">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="391e7-118">0x80041001</span><span class="sxs-lookup"><span data-stu-id="391e7-118">0x80041001</span></span> | <span data-ttu-id="391e7-119">Genel bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="391e7-119">There has been a general failure.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="391e7-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="391e7-120">0x80041008</span></span> | <span data-ttu-id="391e7-121">Parametre geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="391e7-121">A parameter is not valid.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="391e7-122">0x80041006</span><span class="sxs-lookup"><span data-stu-id="391e7-122">0x80041006</span></span> | <span data-ttu-id="391e7-123">İşlemi gerçekleştirmek için yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="391e7-123">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="391e7-124">0</span><span class="sxs-lookup"><span data-stu-id="391e7-124">0</span></span> | <span data-ttu-id="391e7-125">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="391e7-125">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="391e7-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="391e7-126">Remarks</span></span>

<span data-ttu-id="391e7-127">Bu işlev, [IWbemClassObject:: GetObjectText](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getobjecttext) yöntemine bir çağrı kaydırır.</span><span class="sxs-lookup"><span data-stu-id="391e7-127">This function wraps a call to the [IWbemClassObject::GetObjectText](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getobjecttext) method.</span></span>

<span data-ttu-id="391e7-128">Döndürülen MOF metni nesneyle ilgili tüm bilgileri içermiyor, ancak özgün nesneyi yeniden oluşturmak için yalnızca MOF derleyicisi için yeterli bilgi yok.</span><span class="sxs-lookup"><span data-stu-id="391e7-128">The MOF text returned does not contain all the information about the object, but only enough information for the MOF compiler to be able to recreate the original object.</span></span> <span data-ttu-id="391e7-129">Örneğin, hiçbir yayılmış niteleyici veya üst sınıf özelliği dahil değildir.</span><span class="sxs-lookup"><span data-stu-id="391e7-129">For instance, no propagated qualifiers or parent class properties are included.</span></span>

<span data-ttu-id="391e7-130">Aşağıdaki algoritma bir yöntemin parametrelerinin metnini yeniden oluşturmak için kullanılır:</span><span class="sxs-lookup"><span data-stu-id="391e7-130">The following algorithm is used to reconstruct the text of the parameters of a method:</span></span>

1. <span data-ttu-id="391e7-131">Parametreler, tanımlayıcı değerlerinin sırasıyla yeniden sıralandır.</span><span class="sxs-lookup"><span data-stu-id="391e7-131">Parameters are resequenced in the order of their identifier values.</span></span>
1. <span data-ttu-id="391e7-132">`[in]` ve `[out]` olarak belirtilen parametreler tek bir parametre içinde birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="391e7-132">Parameters that are specified as `[in]` and `[out]` are combined into a single parameter.</span></span>
 
<span data-ttu-id="391e7-133">`pstrObjectText`, işlev çağrıldığında bir `null` işaretçisi olmalıdır; işaretçi serbest bırakılmayacak olduğundan, yöntem çağrısından önce geçerli olan bir dizeye işaret etmelidir.</span><span class="sxs-lookup"><span data-stu-id="391e7-133">`pstrObjectText` must be a pointer to a `null` when the function is called; it must not point to a string that is valid before the method call, because the pointer will not be deallocated.</span></span>

## <a name="requirements"></a><span data-ttu-id="391e7-134">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="391e7-134">Requirements</span></span>  
<span data-ttu-id="391e7-135">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="391e7-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="391e7-136">**Üst bilgi:** WMINet_Utils. IDL</span><span class="sxs-lookup"><span data-stu-id="391e7-136">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="391e7-137">**.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="391e7-137">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="391e7-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="391e7-138">See also</span></span>

- [<span data-ttu-id="391e7-139">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="391e7-139">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
