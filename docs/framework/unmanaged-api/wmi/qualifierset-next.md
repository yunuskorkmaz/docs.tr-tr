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
ms.openlocfilehash: 5ac5cc8633881749bdc167e1b3925a83f7adf3b3
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760293"
---
# <a name="qualifiersetnext-function"></a><span data-ttu-id="57bff-103">QualifierSet_Next işlevi</span><span class="sxs-lookup"><span data-stu-id="57bff-103">QualifierSet_Next function</span></span>
<span data-ttu-id="57bff-104">Bir çağrı ile başlatılan bir listedeki sonraki niteleyicisi alır [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="57bff-104">Retrieves the next qualifier in an enumeration that started with a call to the [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) function.</span></span>   

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="57bff-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="57bff-105">Syntax</span></span>  
  
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

## <a name="parameters"></a><span data-ttu-id="57bff-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="57bff-106">Parameters</span></span>

`vFunc`   
<span data-ttu-id="57bff-107">[in] Bu parametre kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="57bff-107">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="57bff-108">[in] Bir işaretçi bir [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) örneği.</span><span class="sxs-lookup"><span data-stu-id="57bff-108">[in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

`lFlags`   
<span data-ttu-id="57bff-109">[in] Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="57bff-109">[in] Reserved.</span></span> <span data-ttu-id="57bff-110">Bu parametre 0 olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="57bff-110">This parameter must be 0.</span></span>

`pstrName`   
<span data-ttu-id="57bff-111">[out] Niteleyicisi adı.</span><span class="sxs-lookup"><span data-stu-id="57bff-111">[out] The name of the qualifier.</span></span> <span data-ttu-id="57bff-112">Varsa `null`, bu parametre yoksayıldı; Aksi takdirde `pstrName` geçerli bir işaret etmelidir değil `BSTR` veya bir bellek sızıntısı olur.</span><span class="sxs-lookup"><span data-stu-id="57bff-112">If `null`, this parameter is ignored; otherwise, `pstrName` should not point to a valid `BSTR` or a memory leak occurs.</span></span> <span data-ttu-id="57bff-113">Null, işlev her zaman yeni bir ayırır, `BSTR` döndüğünde, `WBEM_S_NO_ERROR`.</span><span class="sxs-lookup"><span data-stu-id="57bff-113">If not null, the function always allocates a new `BSTR` when it returns `WBEM_S_NO_ERROR`.</span></span>

`pVal`   
<span data-ttu-id="57bff-114">[out] Başarılı olduğunda, Niteleyici değeri.</span><span class="sxs-lookup"><span data-stu-id="57bff-114">[out] When successful, the value for the qualifier.</span></span> <span data-ttu-id="57bff-115">İşlev başarısız olursa `VARIANT` işaret ettiği `pVal` değiştirilmez.</span><span class="sxs-lookup"><span data-stu-id="57bff-115">If the function fails, the `VARIANT` pointed to by `pVal` is not modified.</span></span> <span data-ttu-id="57bff-116">Bu parametre `null`, parametre yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="57bff-116">If this parameter is `null`, the parameter is ignored.</span></span>

`plFlavor`   
<span data-ttu-id="57bff-117">[out] Niteleyici özelliği alan uzun bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="57bff-117">[out] A pointer to a LONG that receives the qualifier flavor.</span></span> <span data-ttu-id="57bff-118">Flavor bilgi istenildiği gibi değilse, bu parametre olabilir `null`.</span><span class="sxs-lookup"><span data-stu-id="57bff-118">If flavor information is not desired, this parameter can be `null`.</span></span> 

## <a name="return-value"></a><span data-ttu-id="57bff-119">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="57bff-119">Return value</span></span>

<span data-ttu-id="57bff-120">Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üst bilgi dosyası veya tanımlayabilirsiniz bunları sabitleri kodunuzda:</span><span class="sxs-lookup"><span data-stu-id="57bff-120">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="57bff-121">Sabit</span><span class="sxs-lookup"><span data-stu-id="57bff-121">Constant</span></span>  |<span data-ttu-id="57bff-122">Değer</span><span class="sxs-lookup"><span data-stu-id="57bff-122">Value</span></span>  |<span data-ttu-id="57bff-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="57bff-123">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="57bff-124">0x80041008</span><span class="sxs-lookup"><span data-stu-id="57bff-124">0x80041008</span></span> | <span data-ttu-id="57bff-125">Bir parametre geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="57bff-125">A parameter is not valid.</span></span> |
|`WBEM_E_UNEXPECTED` | <span data-ttu-id="57bff-126">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="57bff-126">0x8004101d</span></span> | <span data-ttu-id="57bff-127">Çağıranın çağrılmayan [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="57bff-127">The caller did not call [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md).</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="57bff-128">0x80041006</span><span class="sxs-lookup"><span data-stu-id="57bff-128">0x80041006</span></span> | <span data-ttu-id="57bff-129">Yeni bir numaralandırma başlatmak yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="57bff-129">Not enough memory is available to begin a new enumeration.</span></span> |
| `WBEM_S_NO_MORE_DATA` | <span data-ttu-id="57bff-130">0x40005</span><span class="sxs-lookup"><span data-stu-id="57bff-130">0x40005</span></span> | <span data-ttu-id="57bff-131">Hiçbir daha fazla niteleyici numaralandırmada bırakılır.</span><span class="sxs-lookup"><span data-stu-id="57bff-131">No more qualifiers are left in the enumeration.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="57bff-132">0</span><span class="sxs-lookup"><span data-stu-id="57bff-132">0</span></span> | <span data-ttu-id="57bff-133">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="57bff-133">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="57bff-134">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="57bff-134">Remarks</span></span>

<span data-ttu-id="57bff-135">Bu işlev bir çağrı sarılır [IWbemQualifierSet::Next](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-next) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="57bff-135">This function wraps a call to the [IWbemQualifierSet::Next](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-next) method.</span></span>

<span data-ttu-id="57bff-136">Çağırmanızı `QualifierSet_Next` işlevi dönüş işlevi kadar tüm niteleyicileri art arda Numaralandırılacak `WBEM_S_NO_MORE_DATA`.</span><span class="sxs-lookup"><span data-stu-id="57bff-136">You call the `QualifierSet_Next` function repeatedly to enumerate all the qualifiers until the function return `WBEM_S_NO_MORE_DATA`.</span></span> <span data-ttu-id="57bff-137">Numaralandırma erken sonlandırmak için çağrı [QualifierSet_EndEnumeration](qualifierset-endenumeration.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="57bff-137">To terminate the enumeration early, call the [QualifierSet_EndEnumeration](qualifierset-endenumeration.md) function.</span></span>

<span data-ttu-id="57bff-138">Numaralandırma sırasında döndürülen niteleyici sırası tanımlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="57bff-138">The order of the qualifiers returned during the enumeration is undefined.</span></span>

## <a name="requirements"></a><span data-ttu-id="57bff-139">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="57bff-139">Requirements</span></span>  
 <span data-ttu-id="57bff-140">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="57bff-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57bff-141">**Üst bilgi:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="57bff-141">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="57bff-142">**.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="57bff-142">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57bff-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="57bff-143">See also</span></span>

- [<span data-ttu-id="57bff-144">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="57bff-144">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
