---
title: QualifierSet_Next işlevi (Yönetilmeyen API Başvurusu)
description: QualifierSet_Next işlevi bir sonraki elemeyi bir numaralandırmada alır.
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
ms.openlocfilehash: d3702426bc409d601ccfc6b7a8e93e8d9729c64e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174881"
---
# <a name="qualifierset_next-function"></a><span data-ttu-id="7df05-103">QualifierSet_Next fonksiyonu</span><span class="sxs-lookup"><span data-stu-id="7df05-103">QualifierSet_Next function</span></span>
<span data-ttu-id="7df05-104">[QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) işlevine yapılan bir çağrıyla başlayan bir numaralandırmada bir sonraki elemeyi alır.</span><span class="sxs-lookup"><span data-stu-id="7df05-104">Retrieves the next qualifier in an enumeration that started with a call to the [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) function.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="7df05-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7df05-105">Syntax</span></span>  
  
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

## <a name="parameters"></a><span data-ttu-id="7df05-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7df05-106">Parameters</span></span>

<span data-ttu-id="7df05-107">`vFunc`[içinde] Bu parametre kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="7df05-107">`vFunc` [in] This parameter is unused.</span></span>

<span data-ttu-id="7df05-108">`ptr`[içinde] [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) örneğine işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7df05-108">`ptr` [in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

<span data-ttu-id="7df05-109">`lFlags`[içinde] Saklı -dır.</span><span class="sxs-lookup"><span data-stu-id="7df05-109">`lFlags` [in] Reserved.</span></span> <span data-ttu-id="7df05-110">Bu parametre 0 olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7df05-110">This parameter must be 0.</span></span>

<span data-ttu-id="7df05-111">`pstrName`[çıkış] Elemenin adı.</span><span class="sxs-lookup"><span data-stu-id="7df05-111">`pstrName` [out] The name of the qualifier.</span></span> <span data-ttu-id="7df05-112">`null`Bu parametre yoksayılmazsa; aksi `pstrName` takdirde, geçerli `BSTR` bir veya bellek sızıntısı oluşur işaret etmemelidir.</span><span class="sxs-lookup"><span data-stu-id="7df05-112">If `null`, this parameter is ignored; otherwise, `pstrName` should not point to a valid `BSTR` or a memory leak occurs.</span></span> <span data-ttu-id="7df05-113">Null değilse, işlev her zaman `BSTR` döndürdüğünde `WBEM_S_NO_ERROR`yeni bir ayırır.</span><span class="sxs-lookup"><span data-stu-id="7df05-113">If not null, the function always allocates a new `BSTR` when it returns `WBEM_S_NO_ERROR`.</span></span>

<span data-ttu-id="7df05-114">`pVal`[çıkış] Başarılı olduğunda, eleme değeri.</span><span class="sxs-lookup"><span data-stu-id="7df05-114">`pVal` [out] When successful, the value for the qualifier.</span></span> <span data-ttu-id="7df05-115">İşlev başarısız olursa, işaret edilen `VARIANT` ler `pVal` değiştirilmez.</span><span class="sxs-lookup"><span data-stu-id="7df05-115">If the function fails, the `VARIANT` pointed to by `pVal` is not modified.</span></span> <span data-ttu-id="7df05-116">Bu parametre `null`ise, parametre yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="7df05-116">If this parameter is `null`, the parameter is ignored.</span></span>

<span data-ttu-id="7df05-117">`plFlavor`[çıkış] Niteleyici lezzet alan bir UZUN için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7df05-117">`plFlavor` [out] A pointer to a LONG that receives the qualifier flavor.</span></span> <span data-ttu-id="7df05-118">Lezzet bilgisi istenemiyorsa, `null`bu parametre .</span><span class="sxs-lookup"><span data-stu-id="7df05-118">If flavor information is not desired, this parameter can be `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="7df05-119">Döndürülen değer</span><span class="sxs-lookup"><span data-stu-id="7df05-119">Return value</span></span>

<span data-ttu-id="7df05-120">Bu işlev tarafından döndürülen aşağıdaki değerler *WbemCli.h* üstbilgi dosyasında tanımlanır veya bunları kodunuzdaki sabitler olarak tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="7df05-120">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="7df05-121">Sabit</span><span class="sxs-lookup"><span data-stu-id="7df05-121">Constant</span></span>  |<span data-ttu-id="7df05-122">Değer</span><span class="sxs-lookup"><span data-stu-id="7df05-122">Value</span></span>  |<span data-ttu-id="7df05-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7df05-123">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="7df05-124">0x80041008</span><span class="sxs-lookup"><span data-stu-id="7df05-124">0x80041008</span></span> | <span data-ttu-id="7df05-125">Parametre geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="7df05-125">A parameter is not valid.</span></span> |
|`WBEM_E_UNEXPECTED` | <span data-ttu-id="7df05-126">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="7df05-126">0x8004101d</span></span> | <span data-ttu-id="7df05-127">Arayan [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md)aramadı.</span><span class="sxs-lookup"><span data-stu-id="7df05-127">The caller did not call [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md).</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="7df05-128">0x80041006</span><span class="sxs-lookup"><span data-stu-id="7df05-128">0x80041006</span></span> | <span data-ttu-id="7df05-129">Yeni bir numaralandırmabaşlatmak için yeterli bellek kullanılabilir değil.</span><span class="sxs-lookup"><span data-stu-id="7df05-129">Not enough memory is available to begin a new enumeration.</span></span> |
| `WBEM_S_NO_MORE_DATA` | <span data-ttu-id="7df05-130">0x40005</span><span class="sxs-lookup"><span data-stu-id="7df05-130">0x40005</span></span> | <span data-ttu-id="7df05-131">Numaralandırmada artık eleme ler kalmamaktadır.</span><span class="sxs-lookup"><span data-stu-id="7df05-131">No more qualifiers are left in the enumeration.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="7df05-132">0</span><span class="sxs-lookup"><span data-stu-id="7df05-132">0</span></span> | <span data-ttu-id="7df05-133">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="7df05-133">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="7df05-134">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7df05-134">Remarks</span></span>

<span data-ttu-id="7df05-135">Bu işlev [IWbemQualifierSet](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-next) bir çağrı sarar::Sonraki yöntem.</span><span class="sxs-lookup"><span data-stu-id="7df05-135">This function wraps a call to the [IWbemQualifierSet::Next](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-next) method.</span></span>

<span data-ttu-id="7df05-136">`QualifierSet_Next` İşlev dönene `WBEM_S_NO_MORE_DATA`kadar tüm niteleyicileri sayısallandırmak için işlevi tekrar tekrar çağırırsınız.</span><span class="sxs-lookup"><span data-stu-id="7df05-136">You call the `QualifierSet_Next` function repeatedly to enumerate all the qualifiers until the function return `WBEM_S_NO_MORE_DATA`.</span></span> <span data-ttu-id="7df05-137">Numaralandırmayı erken sonlandırmak için [QualifierSet_EndEnumeration](qualifierset-endenumeration.md) işlevini arayın.</span><span class="sxs-lookup"><span data-stu-id="7df05-137">To terminate the enumeration early, call the [QualifierSet_EndEnumeration](qualifierset-endenumeration.md) function.</span></span>

<span data-ttu-id="7df05-138">Numaralandırma sırasında döndürülen niteleyicilerin sırası tanımsızdır.</span><span class="sxs-lookup"><span data-stu-id="7df05-138">The order of the qualifiers returned during the enumeration is undefined.</span></span>

## <a name="requirements"></a><span data-ttu-id="7df05-139">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7df05-139">Requirements</span></span>  
 <span data-ttu-id="7df05-140">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7df05-140">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7df05-141">**Üstbilgi:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="7df05-141">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="7df05-142">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="7df05-142">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7df05-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7df05-143">See also</span></span>

- [<span data-ttu-id="7df05-144">WMI ve Performans Sayaçları (Yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="7df05-144">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
