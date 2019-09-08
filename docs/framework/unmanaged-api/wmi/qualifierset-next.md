---
title: QualifierSet_Next işlevi (yönetilmeyen API Başvurusu)
description: QualifierSet_Next işlevi bir Numaralandırmadaki bir sonraki niteleyiciyi alır.
ms.date: 11/06/2017
api_name:
- QualifierSet_Next
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_Next
helpviewer_keywords:
- QualifierSet_Next function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f97a19f236b87a7f4c5b2014aca6ee4abd338c63
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798287"
---
# <a name="qualifierset_next-function"></a><span data-ttu-id="07bcd-103">QualifierSet_Next işlevi</span><span class="sxs-lookup"><span data-stu-id="07bcd-103">QualifierSet_Next function</span></span>
<span data-ttu-id="07bcd-104">Bir [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) işlevi çağrısıyla başlatılan bir Numaralandırmadaki bir sonraki niteleyiciyi alır.</span><span class="sxs-lookup"><span data-stu-id="07bcd-104">Retrieves the next qualifier in an enumeration that started with a call to the [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) function.</span></span>   

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="07bcd-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="07bcd-105">Syntax</span></span>  
  
```cpp  
HRESULT QualifierSet_Next (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LONG                 lFlags,
   [out] BSTR*               pstrName,        
   [out] VARIANT*            pVal,
   [out] LONG*               plFlavor                 
); 
```  

## <a name="parameters"></a><span data-ttu-id="07bcd-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="07bcd-106">Parameters</span></span>

`vFunc`   
<span data-ttu-id="07bcd-107">'ndaki Bu parametre kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="07bcd-107">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="07bcd-108">'ndaki Bir [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) örneği işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="07bcd-108">[in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

`lFlags`   
<span data-ttu-id="07bcd-109">'ndaki Ayrılamadı.</span><span class="sxs-lookup"><span data-stu-id="07bcd-109">[in] Reserved.</span></span> <span data-ttu-id="07bcd-110">Bu parametre 0 olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="07bcd-110">This parameter must be 0.</span></span>

`pstrName`   
<span data-ttu-id="07bcd-111">dışı Niteleyicinin adı.</span><span class="sxs-lookup"><span data-stu-id="07bcd-111">[out] The name of the qualifier.</span></span> <span data-ttu-id="07bcd-112">Bu parametre yok sayılır; Aksi takdirde, `pstrName` geçerli `BSTR` bir veya bir Bellek sızıntısının gerçekleşmemelidir. `null`</span><span class="sxs-lookup"><span data-stu-id="07bcd-112">If `null`, this parameter is ignored; otherwise, `pstrName` should not point to a valid `BSTR` or a memory leak occurs.</span></span> <span data-ttu-id="07bcd-113">Null değilse, işlev her zaman döndürüldüğünde `BSTR` `WBEM_S_NO_ERROR`yeni bir değer ayırır.</span><span class="sxs-lookup"><span data-stu-id="07bcd-113">If not null, the function always allocates a new `BSTR` when it returns `WBEM_S_NO_ERROR`.</span></span>

`pVal`   
<span data-ttu-id="07bcd-114">dışı Başarılı olduğunda, niteleyicinin değeri.</span><span class="sxs-lookup"><span data-stu-id="07bcd-114">[out] When successful, the value for the qualifier.</span></span> <span data-ttu-id="07bcd-115">İşlev başarısız olursa, `VARIANT` tarafından `pVal` işaret edilen değiştirilmez.</span><span class="sxs-lookup"><span data-stu-id="07bcd-115">If the function fails, the `VARIANT` pointed to by `pVal` is not modified.</span></span> <span data-ttu-id="07bcd-116">Bu parametre ise `null`parametresi yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="07bcd-116">If this parameter is `null`, the parameter is ignored.</span></span>

`plFlavor`   
<span data-ttu-id="07bcd-117">dışı Niteleyiciyi alan bir LONG işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="07bcd-117">[out] A pointer to a LONG that receives the qualifier flavor.</span></span> <span data-ttu-id="07bcd-118">Flavor bilgileri istenmiyorsa, bu parametre olabilir `null`.</span><span class="sxs-lookup"><span data-stu-id="07bcd-118">If flavor information is not desired, this parameter can be `null`.</span></span> 

## <a name="return-value"></a><span data-ttu-id="07bcd-119">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="07bcd-119">Return value</span></span>

<span data-ttu-id="07bcd-120">Bu işlev tarafından döndürülen aşağıdaki değerler, *Wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="07bcd-120">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="07bcd-121">Sabit</span><span class="sxs-lookup"><span data-stu-id="07bcd-121">Constant</span></span>  |<span data-ttu-id="07bcd-122">Değer</span><span class="sxs-lookup"><span data-stu-id="07bcd-122">Value</span></span>  |<span data-ttu-id="07bcd-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="07bcd-123">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="07bcd-124">0x80041008</span><span class="sxs-lookup"><span data-stu-id="07bcd-124">0x80041008</span></span> | <span data-ttu-id="07bcd-125">Parametre geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="07bcd-125">A parameter is not valid.</span></span> |
|`WBEM_E_UNEXPECTED` | <span data-ttu-id="07bcd-126">0x8004101D</span><span class="sxs-lookup"><span data-stu-id="07bcd-126">0x8004101d</span></span> | <span data-ttu-id="07bcd-127">Çağıran, [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md)çağrısını gerçekleştirmedi.</span><span class="sxs-lookup"><span data-stu-id="07bcd-127">The caller did not call [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md).</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="07bcd-128">0x80041006</span><span class="sxs-lookup"><span data-stu-id="07bcd-128">0x80041006</span></span> | <span data-ttu-id="07bcd-129">Yeni bir sabit listesi başlatmak için yeterli kullanılabilir bellek yok.</span><span class="sxs-lookup"><span data-stu-id="07bcd-129">Not enough memory is available to begin a new enumeration.</span></span> |
| `WBEM_S_NO_MORE_DATA` | <span data-ttu-id="07bcd-130">0x40005</span><span class="sxs-lookup"><span data-stu-id="07bcd-130">0x40005</span></span> | <span data-ttu-id="07bcd-131">Numaralandırmada başka niteleyiciler kalmadı.</span><span class="sxs-lookup"><span data-stu-id="07bcd-131">No more qualifiers are left in the enumeration.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="07bcd-132">0</span><span class="sxs-lookup"><span data-stu-id="07bcd-132">0</span></span> | <span data-ttu-id="07bcd-133">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="07bcd-133">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="07bcd-134">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="07bcd-134">Remarks</span></span>

<span data-ttu-id="07bcd-135">Bu işlev, [IWbemQualifierSet:: Next](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-next) yöntemine bir çağrı kaydırır.</span><span class="sxs-lookup"><span data-stu-id="07bcd-135">This function wraps a call to the [IWbemQualifierSet::Next](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-next) method.</span></span>

<span data-ttu-id="07bcd-136">İşlev döndürülünceye `QualifierSet_Next` `WBEM_S_NO_MORE_DATA`kadar tüm niteleyicileri numaralandırmak için işlevi tekrar tekrar çağırın.</span><span class="sxs-lookup"><span data-stu-id="07bcd-136">You call the `QualifierSet_Next` function repeatedly to enumerate all the qualifiers until the function return `WBEM_S_NO_MORE_DATA`.</span></span> <span data-ttu-id="07bcd-137">Numaralandırmayı erken sonlandırmak için [QualifierSet_EndEnumeration](qualifierset-endenumeration.md) işlevini çağırın.</span><span class="sxs-lookup"><span data-stu-id="07bcd-137">To terminate the enumeration early, call the [QualifierSet_EndEnumeration](qualifierset-endenumeration.md) function.</span></span>

<span data-ttu-id="07bcd-138">Numaralandırma sırasında döndürülen niteleyicilerin sırası tanımsız.</span><span class="sxs-lookup"><span data-stu-id="07bcd-138">The order of the qualifiers returned during the enumeration is undefined.</span></span>

## <a name="requirements"></a><span data-ttu-id="07bcd-139">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="07bcd-139">Requirements</span></span>  
 <span data-ttu-id="07bcd-140">**Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="07bcd-140">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="07bcd-141">**Üst bilgi** WMINet_Utils. IDL</span><span class="sxs-lookup"><span data-stu-id="07bcd-141">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="07bcd-142">**.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="07bcd-142">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07bcd-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="07bcd-143">See also</span></span>

- [<span data-ttu-id="07bcd-144">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="07bcd-144">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
