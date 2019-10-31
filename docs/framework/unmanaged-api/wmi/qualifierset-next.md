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
ms.openlocfilehash: c9c824b0158618848c13183d92f88604460d5099
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141716"
---
# <a name="qualifierset_next-function"></a><span data-ttu-id="dd413-103">QualifierSet_Next işlevi</span><span class="sxs-lookup"><span data-stu-id="dd413-103">QualifierSet_Next function</span></span>
<span data-ttu-id="dd413-104">Bir [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) işlevi çağrısıyla başlatılan bir Numaralandırmadaki bir sonraki niteleyiciyi alır.</span><span class="sxs-lookup"><span data-stu-id="dd413-104">Retrieves the next qualifier in an enumeration that started with a call to the [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) function.</span></span>   

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="dd413-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dd413-105">Syntax</span></span>  
  
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

## <a name="parameters"></a><span data-ttu-id="dd413-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="dd413-106">Parameters</span></span>

`vFunc`   
<span data-ttu-id="dd413-107">'ndaki Bu parametre kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="dd413-107">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="dd413-108">'ndaki Bir [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) örneği işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="dd413-108">[in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

`lFlags`   
<span data-ttu-id="dd413-109">'ndaki Ayrılamadı.</span><span class="sxs-lookup"><span data-stu-id="dd413-109">[in] Reserved.</span></span> <span data-ttu-id="dd413-110">Bu parametre 0 olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="dd413-110">This parameter must be 0.</span></span>

`pstrName`   
<span data-ttu-id="dd413-111">dışı Niteleyicinin adı.</span><span class="sxs-lookup"><span data-stu-id="dd413-111">[out] The name of the qualifier.</span></span> <span data-ttu-id="dd413-112">`null`, bu parametre yok sayılır; Aksi takdirde, `pstrName` geçerli bir `BSTR` işaret etmelidir veya bir bellek sızıntısı oluşur.</span><span class="sxs-lookup"><span data-stu-id="dd413-112">If `null`, this parameter is ignored; otherwise, `pstrName` should not point to a valid `BSTR` or a memory leak occurs.</span></span> <span data-ttu-id="dd413-113">Null değilse, işlev `WBEM_S_NO_ERROR`döndürdüğünde her zaman yeni bir `BSTR` ayırır.</span><span class="sxs-lookup"><span data-stu-id="dd413-113">If not null, the function always allocates a new `BSTR` when it returns `WBEM_S_NO_ERROR`.</span></span>

`pVal`   
<span data-ttu-id="dd413-114">dışı Başarılı olduğunda, niteleyicinin değeri.</span><span class="sxs-lookup"><span data-stu-id="dd413-114">[out] When successful, the value for the qualifier.</span></span> <span data-ttu-id="dd413-115">İşlev başarısız olursa, `pVal` tarafından işaret edilen `VARIANT` değiştirilmez.</span><span class="sxs-lookup"><span data-stu-id="dd413-115">If the function fails, the `VARIANT` pointed to by `pVal` is not modified.</span></span> <span data-ttu-id="dd413-116">Bu parametre `null`, parametre yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="dd413-116">If this parameter is `null`, the parameter is ignored.</span></span>

`plFlavor`   
<span data-ttu-id="dd413-117">dışı Niteleyiciyi alan bir LONG işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="dd413-117">[out] A pointer to a LONG that receives the qualifier flavor.</span></span> <span data-ttu-id="dd413-118">Flavor bilgileri istenmiyorsa, bu parametre `null`olabilir.</span><span class="sxs-lookup"><span data-stu-id="dd413-118">If flavor information is not desired, this parameter can be `null`.</span></span> 

## <a name="return-value"></a><span data-ttu-id="dd413-119">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="dd413-119">Return value</span></span>

<span data-ttu-id="dd413-120">Bu işlev tarafından döndürülen aşağıdaki değerler, *Wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="dd413-120">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="dd413-121">Sabit</span><span class="sxs-lookup"><span data-stu-id="dd413-121">Constant</span></span>  |<span data-ttu-id="dd413-122">Değer</span><span class="sxs-lookup"><span data-stu-id="dd413-122">Value</span></span>  |<span data-ttu-id="dd413-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dd413-123">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="dd413-124">0x80041008</span><span class="sxs-lookup"><span data-stu-id="dd413-124">0x80041008</span></span> | <span data-ttu-id="dd413-125">Parametre geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="dd413-125">A parameter is not valid.</span></span> |
|`WBEM_E_UNEXPECTED` | <span data-ttu-id="dd413-126">0x8004101D</span><span class="sxs-lookup"><span data-stu-id="dd413-126">0x8004101d</span></span> | <span data-ttu-id="dd413-127">Çağıran, [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md)çağrısını gerçekleştirmedi.</span><span class="sxs-lookup"><span data-stu-id="dd413-127">The caller did not call [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md).</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="dd413-128">0x80041006</span><span class="sxs-lookup"><span data-stu-id="dd413-128">0x80041006</span></span> | <span data-ttu-id="dd413-129">Yeni bir sabit listesi başlatmak için yeterli kullanılabilir bellek yok.</span><span class="sxs-lookup"><span data-stu-id="dd413-129">Not enough memory is available to begin a new enumeration.</span></span> |
| `WBEM_S_NO_MORE_DATA` | <span data-ttu-id="dd413-130">0x40005</span><span class="sxs-lookup"><span data-stu-id="dd413-130">0x40005</span></span> | <span data-ttu-id="dd413-131">Numaralandırmada başka niteleyiciler kalmadı.</span><span class="sxs-lookup"><span data-stu-id="dd413-131">No more qualifiers are left in the enumeration.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="dd413-132">0</span><span class="sxs-lookup"><span data-stu-id="dd413-132">0</span></span> | <span data-ttu-id="dd413-133">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="dd413-133">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="dd413-134">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dd413-134">Remarks</span></span>

<span data-ttu-id="dd413-135">Bu işlev, [IWbemQualifierSet:: Next](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-next) yöntemine bir çağrı kaydırır.</span><span class="sxs-lookup"><span data-stu-id="dd413-135">This function wraps a call to the [IWbemQualifierSet::Next](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-next) method.</span></span>

<span data-ttu-id="dd413-136">İşlev `WBEM_S_NO_MORE_DATA`dönene kadar tüm niteleyicileri numaralandırmak için `QualifierSet_Next` işlevini tekrar tekrar çağırın.</span><span class="sxs-lookup"><span data-stu-id="dd413-136">You call the `QualifierSet_Next` function repeatedly to enumerate all the qualifiers until the function return `WBEM_S_NO_MORE_DATA`.</span></span> <span data-ttu-id="dd413-137">Numaralandırmayı erken sonlandırmak için [QualifierSet_EndEnumeration](qualifierset-endenumeration.md) işlevini çağırın.</span><span class="sxs-lookup"><span data-stu-id="dd413-137">To terminate the enumeration early, call the [QualifierSet_EndEnumeration](qualifierset-endenumeration.md) function.</span></span>

<span data-ttu-id="dd413-138">Numaralandırma sırasında döndürülen niteleyicilerin sırası tanımsız.</span><span class="sxs-lookup"><span data-stu-id="dd413-138">The order of the qualifiers returned during the enumeration is undefined.</span></span>

## <a name="requirements"></a><span data-ttu-id="dd413-139">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dd413-139">Requirements</span></span>  
 <span data-ttu-id="dd413-140">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dd413-140">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dd413-141">**Üst bilgi:** WMINet_Utils. IDL</span><span class="sxs-lookup"><span data-stu-id="dd413-141">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="dd413-142">**.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="dd413-142">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd413-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dd413-143">See also</span></span>

- [<span data-ttu-id="dd413-144">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="dd413-144">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
