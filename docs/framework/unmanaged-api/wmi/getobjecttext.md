---
title: GetObjectText işlevi (Yönetilmeyen API Başvurusu)
description: GetObjectText işlevi, MOF sözdiziminde bir nesnenin metinsel bir işlemesini döndürür.
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
ms.openlocfilehash: 6881125760e0f1dc38e6b01917d5829edc95e3ca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176792"
---
# <a name="getobjecttext-function"></a><span data-ttu-id="0cf1d-103">GetObjectText işlevi</span><span class="sxs-lookup"><span data-stu-id="0cf1d-103">GetObjectText function</span></span>
<span data-ttu-id="0cf1d-104">Yönetilen Nesne Biçimi (MOF) sözdiziminde nesnenin metin oluşturma biçimini döndürür.</span><span class="sxs-lookup"><span data-stu-id="0cf1d-104">Returns a textual rendering of the object in the Managed Object Format (MOF) syntax.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="0cf1d-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0cf1d-105">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectText (
   [in] int                vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LONG                lFlags,
   [out] BSTR*              pstrObjectText
);
```  

## <a name="parameters"></a><span data-ttu-id="0cf1d-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0cf1d-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="0cf1d-107">[içinde] Bu parametre kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="0cf1d-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="0cf1d-108">[içinde] [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneğine işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0cf1d-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lFlags`  
<span data-ttu-id="0cf1d-109">[içinde] Normalde 0.</span><span class="sxs-lookup"><span data-stu-id="0cf1d-109">[in] Normally 0.</span></span> <span data-ttu-id="0cf1d-110">`WBEM_FLAG_NO_FLAVORS` (veya 0x1) belirtilirse, elemeler yayılma veya lezzet bilgisi olmadan dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="0cf1d-110">If `WBEM_FLAG_NO_FLAVORS` (or 0x1) is specified, qualifiers are included without propagation or flavor information.</span></span>

<span data-ttu-id="0cf1d-111">`pstrObjectText`[çıkış] Giriş için `null` bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0cf1d-111">`pstrObjectText` [out] A pointer to a `null` on entry.</span></span> <span data-ttu-id="0cf1d-112">Döndükten sonra, `BSTR` nesnenin MOF sözdizimi oluşturmasını içeren yeni ayrılmış bir.</span><span class="sxs-lookup"><span data-stu-id="0cf1d-112">On return, a newly allocated `BSTR` that contains a MOF syntax rendering of the object.</span></span>  

## <a name="return-value"></a><span data-ttu-id="0cf1d-113">Döndürülen değer</span><span class="sxs-lookup"><span data-stu-id="0cf1d-113">Return value</span></span>

<span data-ttu-id="0cf1d-114">Bu işlev tarafından döndürülen aşağıdaki değerler *WbemCli.h* üstbilgi dosyasında tanımlanır veya bunları kodunuzdaki sabitler olarak tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="0cf1d-114">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="0cf1d-115">Sabit</span><span class="sxs-lookup"><span data-stu-id="0cf1d-115">Constant</span></span>  |<span data-ttu-id="0cf1d-116">Değer</span><span class="sxs-lookup"><span data-stu-id="0cf1d-116">Value</span></span>  |<span data-ttu-id="0cf1d-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0cf1d-117">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="0cf1d-118">0x80041001</span><span class="sxs-lookup"><span data-stu-id="0cf1d-118">0x80041001</span></span> | <span data-ttu-id="0cf1d-119">Genel bir başarısızlık oldu.</span><span class="sxs-lookup"><span data-stu-id="0cf1d-119">There has been a general failure.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="0cf1d-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="0cf1d-120">0x80041008</span></span> | <span data-ttu-id="0cf1d-121">Parametre geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="0cf1d-121">A parameter is not valid.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="0cf1d-122">0x80041006</span><span class="sxs-lookup"><span data-stu-id="0cf1d-122">0x80041006</span></span> | <span data-ttu-id="0cf1d-123">İşlemi tamamlamak için yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="0cf1d-123">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="0cf1d-124">0</span><span class="sxs-lookup"><span data-stu-id="0cf1d-124">0</span></span> | <span data-ttu-id="0cf1d-125">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="0cf1d-125">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="0cf1d-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0cf1d-126">Remarks</span></span>

<span data-ttu-id="0cf1d-127">Bu [işlev, IWbemClassObject::GetObjectText](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getobjecttext) yöntemine bir çağrı yıkLar.</span><span class="sxs-lookup"><span data-stu-id="0cf1d-127">This function wraps a call to the [IWbemClassObject::GetObjectText](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getobjecttext) method.</span></span>

<span data-ttu-id="0cf1d-128">Döndürülen MOF metni nesne yle ilgili tüm bilgileri içermez, ancak mof derleyicisinin özgün nesneyi yeniden oluşturabilmesi için yeterli bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="0cf1d-128">The MOF text returned does not contain all the information about the object, but only enough information for the MOF compiler to be able to recreate the original object.</span></span> <span data-ttu-id="0cf1d-129">Örneğin, hiçbir yayılan niteleyiciler veya üst sınıf özellikleri dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="0cf1d-129">For instance, no propagated qualifiers or parent class properties are included.</span></span>

<span data-ttu-id="0cf1d-130">Bir yöntemin parametrelerinin metnini yeniden oluşturmak için aşağıdaki algoritma kullanılır:</span><span class="sxs-lookup"><span data-stu-id="0cf1d-130">The following algorithm is used to reconstruct the text of the parameters of a method:</span></span>

1. <span data-ttu-id="0cf1d-131">Parametreler tanımlayıcı değerleri sırasına göre yeniden sıralanır.</span><span class="sxs-lookup"><span data-stu-id="0cf1d-131">Parameters are resequenced in the order of their identifier values.</span></span>
1. <span data-ttu-id="0cf1d-132">Olarak `[in]` belirtilen ve `[out]` tek bir parametrede birleştirilen parametreler.</span><span class="sxs-lookup"><span data-stu-id="0cf1d-132">Parameters that are specified as `[in]` and `[out]` are combined into a single parameter.</span></span>

<span data-ttu-id="0cf1d-133">`pstrObjectText`işlev çağrıldığında `null` bir işaretçi olmalıdır; işaretçi ayrılmayacağı için yöntem çağrısından önce geçerli olan bir dizeyi işaret etmemelidir.</span><span class="sxs-lookup"><span data-stu-id="0cf1d-133">`pstrObjectText` must be a pointer to a `null` when the function is called; it must not point to a string that is valid before the method call, because the pointer will not be deallocated.</span></span>

## <a name="requirements"></a><span data-ttu-id="0cf1d-134">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0cf1d-134">Requirements</span></span>  
<span data-ttu-id="0cf1d-135">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0cf1d-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0cf1d-136">**Üstbilgi:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="0cf1d-136">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="0cf1d-137">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="0cf1d-137">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cf1d-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0cf1d-138">See also</span></span>

- [<span data-ttu-id="0cf1d-139">WMI ve Performans Sayaçları (Yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="0cf1d-139">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
