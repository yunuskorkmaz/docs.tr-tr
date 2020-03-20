---
title: QualifierSet_Get işlevi (Yönetilmeyen API Başvurusu)
description: QualifierSet_Get işlevi adlandırılmış bir niteleyici alır.
ms.date: 11/06/2017
api_name:
- QualifierSet_Get
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_Get
helpviewer_keywords:
- QualifierSet_Get function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 2f4e2d4518e01f3415b8f17ce5778dd98b2a45c3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174894"
---
# <a name="qualifierset_get-function"></a><span data-ttu-id="7b66d-103">QualifierSet_Get fonksiyonu</span><span class="sxs-lookup"><span data-stu-id="7b66d-103">QualifierSet_Get function</span></span>
<span data-ttu-id="7b66d-104">Belirtilen adlandırılmış niteleyiciyi alır.</span><span class="sxs-lookup"><span data-stu-id="7b66d-104">Gets the specified named qualifier.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="7b66d-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7b66d-105">Syntax</span></span>  
  
```cpp  
HRESULT QualifierSet_Get (
   [in] int                  vFunc,
   [in] IWbemQualifierSet*   ptr,
   [in] LPCWSTR              wszName,
   [in] LONG                 lFlags,
   [out] VARIANT*            pVal,
   [out] LONG*               plFlavor
);
```  

## <a name="parameters"></a><span data-ttu-id="7b66d-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7b66d-106">Parameters</span></span>

<span data-ttu-id="7b66d-107">`vFunc`[içinde] Bu parametre kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="7b66d-107">`vFunc` [in] This parameter is unused.</span></span>

<span data-ttu-id="7b66d-108">`ptr`[içinde] [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) örneğine işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7b66d-108">`ptr` [in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

<span data-ttu-id="7b66d-109">`wszName`[içinde] Değeri istenen niteleyicinin adı.</span><span class="sxs-lookup"><span data-stu-id="7b66d-109">`wszName` [in] The name of the qualifier whose value is requested.</span></span>

<span data-ttu-id="7b66d-110">`lFlags`[içinde] Saklı -dır.</span><span class="sxs-lookup"><span data-stu-id="7b66d-110">`lFlags` [in] Reserved.</span></span> <span data-ttu-id="7b66d-111">Bu parametre 0 olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7b66d-111">This parameter must be 0.</span></span>

<span data-ttu-id="7b66d-112">`pVal`[çıkış] Başarılı olduğunda, niteleyici için doğru tür ve değer.</span><span class="sxs-lookup"><span data-stu-id="7b66d-112">`pVal` [out] When successful, the correct type and value for the qualifier.</span></span> <span data-ttu-id="7b66d-113">İşlev başarısız olursa, işaret edilen `VARIANT` ler `pVal` değiştirilmez.</span><span class="sxs-lookup"><span data-stu-id="7b66d-113">If the function fails, the `VARIANT` pointed to by `pVal` is not modified.</span></span> <span data-ttu-id="7b66d-114">Bu parametre `null`ise, parametre yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="7b66d-114">If this parameter is `null`, the parameter is ignored.</span></span>

<span data-ttu-id="7b66d-115">`plFlavor`[çıkış] İstenen niteleyici niteleyici için niteleyici lezzet bitlerini alan bir UZUN işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7b66d-115">`plFlavor` [out] A pointer to a LONG that receives the qualifier flavor bits for the requested qualifier.</span></span> <span data-ttu-id="7b66d-116">Lezzet bilgisi istenemiyorsa, `null`bu parametre .</span><span class="sxs-lookup"><span data-stu-id="7b66d-116">If flavor information is not desired, this parameter can be `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="7b66d-117">Döndürülen değer</span><span class="sxs-lookup"><span data-stu-id="7b66d-117">Return value</span></span>

<span data-ttu-id="7b66d-118">Bu işlev tarafından döndürülen aşağıdaki değerler *WbemCli.h* üstbilgi dosyasında tanımlanır veya bunları kodunuzdaki sabitler olarak tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="7b66d-118">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="7b66d-119">Sabit</span><span class="sxs-lookup"><span data-stu-id="7b66d-119">Constant</span></span>  |<span data-ttu-id="7b66d-120">Değer</span><span class="sxs-lookup"><span data-stu-id="7b66d-120">Value</span></span>  |<span data-ttu-id="7b66d-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7b66d-121">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="7b66d-122">0x80041008</span><span class="sxs-lookup"><span data-stu-id="7b66d-122">0x80041008</span></span> | <span data-ttu-id="7b66d-123">Parametre geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="7b66d-123">A parameter is not valid.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="7b66d-124">0x80041002</span><span class="sxs-lookup"><span data-stu-id="7b66d-124">0x80041002</span></span> | <span data-ttu-id="7b66d-125">Belirtilen niteleyici yok.</span><span class="sxs-lookup"><span data-stu-id="7b66d-125">The specified qualifier does not exist.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="7b66d-126">0</span><span class="sxs-lookup"><span data-stu-id="7b66d-126">0</span></span> | <span data-ttu-id="7b66d-127">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="7b66d-127">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="7b66d-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7b66d-128">Remarks</span></span>

<span data-ttu-id="7b66d-129">Bu işlev [IWbemQualifierSet](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-get) bir çağrı sarar::Get yöntemi.</span><span class="sxs-lookup"><span data-stu-id="7b66d-129">This function wraps a call to the [IWbemQualifierSet::Get](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-get) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="7b66d-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7b66d-130">Requirements</span></span>  
 <span data-ttu-id="7b66d-131">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7b66d-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b66d-132">**Üstbilgi:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="7b66d-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="7b66d-133">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="7b66d-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b66d-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7b66d-134">See also</span></span>

- [<span data-ttu-id="7b66d-135">WMI ve Performans Sayaçları (Yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="7b66d-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
