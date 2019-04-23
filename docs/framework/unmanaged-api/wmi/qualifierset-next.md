---
title: QualifierSet_Next işlevi (yönetilmeyen API Başvurusu)
description: Bir listedeki sonraki niteleyicisi QualifierSet_Next işlevi alır.
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
ms.openlocfilehash: e8b96957467b0acb100f7eea137b3294a60e208a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59180914"
---
# <a name="qualifiersetnext-function"></a><span data-ttu-id="88eb4-103">QualifierSet_Next işlevi</span><span class="sxs-lookup"><span data-stu-id="88eb4-103">QualifierSet_Next function</span></span>
<span data-ttu-id="88eb4-104">Bir çağrı ile başlatılan bir listedeki sonraki niteleyicisi alır [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="88eb4-104">Retrieves the next qualifier in an enumeration that started with a call to the [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) function.</span></span>   

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="88eb4-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="88eb4-105">Syntax</span></span>  
  
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

## <a name="parameters"></a><span data-ttu-id="88eb4-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="88eb4-106">Parameters</span></span>

`vFunc`   
<span data-ttu-id="88eb4-107">[in] Bu parametre kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="88eb4-107">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="88eb4-108">[in] Bir işaretçi bir [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) örneği.</span><span class="sxs-lookup"><span data-stu-id="88eb4-108">[in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

`lFlags`   
<span data-ttu-id="88eb4-109">[in] Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="88eb4-109">[in] Reserved.</span></span> <span data-ttu-id="88eb4-110">Bu parametre 0 olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="88eb4-110">This parameter must be 0.</span></span>

`pstrName`   
<span data-ttu-id="88eb4-111">[out] Niteleyicisi adı.</span><span class="sxs-lookup"><span data-stu-id="88eb4-111">[out] The name of the qualifier.</span></span> <span data-ttu-id="88eb4-112">Varsa `null`, bu parametre yoksayıldı; Aksi takdirde `pstrName` geçerli bir işaret etmelidir değil `BSTR` veya bir bellek sızıntısı olur.</span><span class="sxs-lookup"><span data-stu-id="88eb4-112">If `null`, this parameter is ignored; otherwise, `pstrName` should not point to a valid `BSTR` or a memory leak occurs.</span></span> <span data-ttu-id="88eb4-113">Null, işlev her zaman yeni bir ayırır, `BSTR` döndüğünde, `WBEM_S_NO_ERROR`.</span><span class="sxs-lookup"><span data-stu-id="88eb4-113">If not null, the function always allocates a new `BSTR` when it returns `WBEM_S_NO_ERROR`.</span></span>

`pVal`   
<span data-ttu-id="88eb4-114">[out] Başarılı olduğunda, Niteleyici değeri.</span><span class="sxs-lookup"><span data-stu-id="88eb4-114">[out] When successful, the value for the qualifier.</span></span> <span data-ttu-id="88eb4-115">İşlev başarısız olursa `VARIANT` işaret ettiği `pVal` değiştirilmez.</span><span class="sxs-lookup"><span data-stu-id="88eb4-115">If the function fails, the `VARIANT` pointed to by `pVal` is not modified.</span></span> <span data-ttu-id="88eb4-116">Bu parametre `null`, parametre yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="88eb4-116">If this parameter is `null`, the parameter is ignored.</span></span>

`plFlavor`   
<span data-ttu-id="88eb4-117">[out] Niteleyici özelliği alan uzun bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="88eb4-117">[out] A pointer to a LONG that receives the qualifier flavor.</span></span> <span data-ttu-id="88eb4-118">Flavor bilgi istenildiği gibi değilse, bu parametre olabilir `null`.</span><span class="sxs-lookup"><span data-stu-id="88eb4-118">If flavor information is not desired, this parameter can be `null`.</span></span> 

## <a name="return-value"></a><span data-ttu-id="88eb4-119">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="88eb4-119">Return value</span></span>

<span data-ttu-id="88eb4-120">Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üst bilgi dosyası veya tanımlayabilirsiniz bunları sabitleri kodunuzda:</span><span class="sxs-lookup"><span data-stu-id="88eb4-120">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="88eb4-121">Sabit</span><span class="sxs-lookup"><span data-stu-id="88eb4-121">Constant</span></span>  |<span data-ttu-id="88eb4-122">Değer</span><span class="sxs-lookup"><span data-stu-id="88eb4-122">Value</span></span>  |<span data-ttu-id="88eb4-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="88eb4-123">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="88eb4-124">0x80041008</span><span class="sxs-lookup"><span data-stu-id="88eb4-124">0x80041008</span></span> | <span data-ttu-id="88eb4-125">Bir parametre geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="88eb4-125">A parameter is not valid.</span></span> |
|`WBEM_E_UNEXPECTED` | <span data-ttu-id="88eb4-126">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="88eb4-126">0x8004101d</span></span> | <span data-ttu-id="88eb4-127">Çağıranın çağrılmayan [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="88eb4-127">The caller did not call [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md).</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="88eb4-128">0x80041006</span><span class="sxs-lookup"><span data-stu-id="88eb4-128">0x80041006</span></span> | <span data-ttu-id="88eb4-129">Yeni bir numaralandırma başlatmak yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="88eb4-129">Not enough memory is available to begin a new enumeration.</span></span> |
| `WBEM_S_NO_MORE_DATA` | <span data-ttu-id="88eb4-130">0x40005</span><span class="sxs-lookup"><span data-stu-id="88eb4-130">0x40005</span></span> | <span data-ttu-id="88eb4-131">Hiçbir daha fazla niteleyici numaralandırmada bırakılır.</span><span class="sxs-lookup"><span data-stu-id="88eb4-131">No more qualifiers are left in the enumeration.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="88eb4-132">0</span><span class="sxs-lookup"><span data-stu-id="88eb4-132">0</span></span> | <span data-ttu-id="88eb4-133">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="88eb4-133">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="88eb4-134">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="88eb4-134">Remarks</span></span>

<span data-ttu-id="88eb4-135">Bu işlev bir çağrı sarılır [IWbemQualifierSet::Next](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-next) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="88eb4-135">This function wraps a call to the [IWbemQualifierSet::Next](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-next) method.</span></span>

<span data-ttu-id="88eb4-136">Çağırmanızı `QualifierSet_Next` işlevi dönüş işlevi kadar tüm niteleyicileri art arda Numaralandırılacak `WBEM_S_NO_MORE_DATA`.</span><span class="sxs-lookup"><span data-stu-id="88eb4-136">You call the `QualifierSet_Next` function repeatedly to enumerate all the qualifiers until the function return `WBEM_S_NO_MORE_DATA`.</span></span> <span data-ttu-id="88eb4-137">Numaralandırma erken sonlandırmak için çağrı [QualifierSet_EndEnumeration](qualifierset-endenumeration.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="88eb4-137">To terminate the enumeration early, call the [QualifierSet_EndEnumeration](qualifierset-endenumeration.md) function.</span></span>

<span data-ttu-id="88eb4-138">Numaralandırma sırasında döndürülen niteleyici sırası tanımlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="88eb4-138">The order of the qualifiers returned during the enumeration is undefined.</span></span>

## <a name="requirements"></a><span data-ttu-id="88eb4-139">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="88eb4-139">Requirements</span></span>  
 <span data-ttu-id="88eb4-140">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="88eb4-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="88eb4-141">**Üst bilgi:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="88eb4-141">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="88eb4-142">**.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="88eb4-142">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88eb4-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="88eb4-143">See also</span></span>

- [<span data-ttu-id="88eb4-144">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="88eb4-144">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
