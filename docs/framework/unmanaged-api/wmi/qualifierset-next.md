---
title: "QualifierSet_Next işlevi (yönetilmeyen API Başvurusu)"
description: "QualifierSet_Next işlevi numaralandırma sonraki niteleyicisinde alır."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: QualifierSet_Next
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: QualifierSet_Next
helpviewer_keywords: QualifierSet_Next function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 01a9c9d162039547849597aaa9c8a6fa38a31455
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="qualifiersetnext-function"></a><span data-ttu-id="d2921-103">QualifierSet_Next işlevi</span><span class="sxs-lookup"><span data-stu-id="d2921-103">QualifierSet_Next function</span></span>
<span data-ttu-id="d2921-104">Sonraki çağrı kullanmaya bir numaralandırma niteleyicisinde alır [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="d2921-104">Retrieves the next qualifier in an enumeration that started with a call to the [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) function.</span></span>   

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="d2921-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d2921-105">Syntax</span></span>  
  
```  
HRESULT QualifierSet_Next (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LONG                 lFlags,
   [out] BSTR*               pstrName,        
   [out] VARIANT*            pVal,
   [out] LONG*               plFlavor                 
); 
```  

## <a name="parameters"></a><span data-ttu-id="d2921-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d2921-106">Parameters</span></span>

`vFunc`   
<span data-ttu-id="d2921-107">[in] Bu parametre kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="d2921-107">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="d2921-108">[in] Bir işaretçi bir [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) örneği.</span><span class="sxs-lookup"><span data-stu-id="d2921-108">[in] A pointer to an [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) instance.</span></span>

`lFlags`   
<span data-ttu-id="d2921-109">[in] Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="d2921-109">[in] Reserved.</span></span> <span data-ttu-id="d2921-110">Bu parametre 0 olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d2921-110">This parameter must be 0.</span></span>

`pstrName`   
<span data-ttu-id="d2921-111">[out] Niteleyici adı.</span><span class="sxs-lookup"><span data-stu-id="d2921-111">[out] The name of the qualifier.</span></span> <span data-ttu-id="d2921-112">Varsa `null`, bu parametre, yoksayılan Aksi takdirde `pstrName` geçerli bir işaret etmelidir değil `BSTR` veya bellek sızıntısı oluşur.</span><span class="sxs-lookup"><span data-stu-id="d2921-112">If `null`, this parameter is ignored; otherwise, `pstrName` should not point to a valid `BSTR` or a memory leak occurs.</span></span> <span data-ttu-id="d2921-113">Null, işlevi her zaman yeni bir ayırır, `BSTR` zaman döndürür `WBEM_S_NO_ERROR`.</span><span class="sxs-lookup"><span data-stu-id="d2921-113">If not null, the function always allocates a new `BSTR` when it returns `WBEM_S_NO_ERROR`.</span></span>

`pVal`   
<span data-ttu-id="d2921-114">[out] Başarılı olduğunda, Niteleyici değeri.</span><span class="sxs-lookup"><span data-stu-id="d2921-114">[out] When successful, the value for the qualifier.</span></span> <span data-ttu-id="d2921-115">İşlev başarısız olursa, `VARIANT` gösterdiği `pVal` değiştirilmez.</span><span class="sxs-lookup"><span data-stu-id="d2921-115">If the function fails, the `VARIANT` pointed to by `pVal` is not modified.</span></span> <span data-ttu-id="d2921-116">Bu parametre ise `null`, parametre yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="d2921-116">If this parameter is `null`, the parameter is ignored.</span></span>

`plFlavor`   
<span data-ttu-id="d2921-117">[out] Niteleyici türü alan uzun bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d2921-117">[out] A pointer to a LONG that receives the qualifier flavor.</span></span> <span data-ttu-id="d2921-118">Özellik bilgileri değil istenirse, bu parametre olabilir `null`.</span><span class="sxs-lookup"><span data-stu-id="d2921-118">If flavor information is not desired, this parameter can be `null`.</span></span> 

## <a name="return-value"></a><span data-ttu-id="d2921-119">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="d2921-119">Return value</span></span>

<span data-ttu-id="d2921-120">Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üstbilgi dosyası, veya tanımlayabilirsiniz bunları sabitleri kodunuzda:</span><span class="sxs-lookup"><span data-stu-id="d2921-120">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="d2921-121">Sabit</span><span class="sxs-lookup"><span data-stu-id="d2921-121">Constant</span></span>  |<span data-ttu-id="d2921-122">Değer</span><span class="sxs-lookup"><span data-stu-id="d2921-122">Value</span></span>  |<span data-ttu-id="d2921-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d2921-123">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="d2921-124">0x80041008</span><span class="sxs-lookup"><span data-stu-id="d2921-124">0x80041008</span></span> | <span data-ttu-id="d2921-125">Parametre geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="d2921-125">A parameter is not valid.</span></span> |
|`WBEM_E_UNEXPECTED` | <span data-ttu-id="d2921-126">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="d2921-126">0x8004101d</span></span> | <span data-ttu-id="d2921-127">Arayan çağrılmayan [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="d2921-127">The caller did not call [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md).</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="d2921-128">0x80041006</span><span class="sxs-lookup"><span data-stu-id="d2921-128">0x80041006</span></span> | <span data-ttu-id="d2921-129">Yeni bir numaralandırma başlatmak yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="d2921-129">Not enough memory is available to begin a new enumeration.</span></span> |
| `WBEM_S_NO_MORE_DATA` | <span data-ttu-id="d2921-130">0x40005</span><span class="sxs-lookup"><span data-stu-id="d2921-130">0x40005</span></span> | <span data-ttu-id="d2921-131">Daha fazla hiçbir niteleyicileri numaralandırmada bırakılır.</span><span class="sxs-lookup"><span data-stu-id="d2921-131">No more qualifiers are left in the enumeration.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="d2921-132">0</span><span class="sxs-lookup"><span data-stu-id="d2921-132">0</span></span> | <span data-ttu-id="d2921-133">İşlev çağrısı başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="d2921-133">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="d2921-134">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d2921-134">Remarks</span></span>

<span data-ttu-id="d2921-135">Bu işlev çağrısı sarmalar [IWbemQualifierSet::Next](https://msdn.microsoft.com/library/aa391870(v=vs.85).aspx) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d2921-135">This function wraps a call to the [IWbemQualifierSet::Next](https://msdn.microsoft.com/library/aa391870(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="d2921-136">Çağırmanız `QualifierSet_Next` dönüş işlevi kadar tüm niteleyicileri art arda Numaralandırılacak işlevi `WBEM_S_NO_MORE_DATA`.</span><span class="sxs-lookup"><span data-stu-id="d2921-136">You call the `QualifierSet_Next` function repeatedly to enumerate all the qualifiers until the function return `WBEM_S_NO_MORE_DATA`.</span></span> <span data-ttu-id="d2921-137">Numaralandırma erken sonlandırmak için çağrı [QualifierSet_EndEnumeration](qualifierset-endenumeration.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="d2921-137">To terminate the enumeration early, call the [QualifierSet_EndEnumeration](qualifierset-endenumeration.md) function.</span></span>

<span data-ttu-id="d2921-138">Numaralandırma sırasında döndürülen niteleyicileri sırası tanımlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="d2921-138">The order of the qualifiers returned during the enumeration is undefined.</span></span>

## <a name="requirements"></a><span data-ttu-id="d2921-139">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d2921-139">Requirements</span></span>  
 <span data-ttu-id="d2921-140">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d2921-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2921-141">**Başlık:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="d2921-141">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="d2921-142">**.NET framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="d2921-142">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2921-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d2921-143">See also</span></span>  
[<span data-ttu-id="d2921-144">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="d2921-144">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
