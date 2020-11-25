---
title: QualifierSet_Get işlevi (yönetilmeyen API Başvurusu)
description: QualifierSet_Get işlevi adlandırılmış bir niteleyiciyi alır.
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
ms.openlocfilehash: fd096287b85b4a51a8cae85dddcca95cc1a8dbae
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721146"
---
# <a name="qualifierset_get-function"></a><span data-ttu-id="36cef-103">QualifierSet_Get işlevi</span><span class="sxs-lookup"><span data-stu-id="36cef-103">QualifierSet_Get function</span></span>

<span data-ttu-id="36cef-104">Belirtilen adlandırılmış niteleyiciyi alır.</span><span class="sxs-lookup"><span data-stu-id="36cef-104">Gets the specified named qualifier.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="36cef-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="36cef-105">Syntax</span></span>  
  
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

## <a name="parameters"></a><span data-ttu-id="36cef-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="36cef-106">Parameters</span></span>

<span data-ttu-id="36cef-107">`vFunc` 'ndaki Bu parametre kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="36cef-107">`vFunc` [in] This parameter is unused.</span></span>

<span data-ttu-id="36cef-108">`ptr` 'ndaki Bir [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) örneği işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="36cef-108">`ptr` [in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

<span data-ttu-id="36cef-109">`wszName` 'ndaki Değeri istenen niteleyicinin adı.</span><span class="sxs-lookup"><span data-stu-id="36cef-109">`wszName` [in] The name of the qualifier whose value is requested.</span></span>

<span data-ttu-id="36cef-110">`lFlags` 'ndaki Ayrılamadı.</span><span class="sxs-lookup"><span data-stu-id="36cef-110">`lFlags` [in] Reserved.</span></span> <span data-ttu-id="36cef-111">Bu parametre 0 olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="36cef-111">This parameter must be 0.</span></span>

<span data-ttu-id="36cef-112">`pVal` dışı Başarılı olduğunda, niteleyicisi için doğru tür ve değer.</span><span class="sxs-lookup"><span data-stu-id="36cef-112">`pVal` [out] When successful, the correct type and value for the qualifier.</span></span> <span data-ttu-id="36cef-113">İşlev başarısız olursa, `VARIANT` tarafından işaret edilen `pVal` değiştirilmez.</span><span class="sxs-lookup"><span data-stu-id="36cef-113">If the function fails, the `VARIANT` pointed to by `pVal` is not modified.</span></span> <span data-ttu-id="36cef-114">Bu parametre ise `null` parametresi yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="36cef-114">If this parameter is `null`, the parameter is ignored.</span></span>

<span data-ttu-id="36cef-115">`plFlavor` dışı İstenen niteleyici için niteleyici Flavor bitlerini alan bir LONG işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="36cef-115">`plFlavor` [out] A pointer to a LONG that receives the qualifier flavor bits for the requested qualifier.</span></span> <span data-ttu-id="36cef-116">Flavor bilgileri istenmiyorsa, bu parametre olabilir `null` .</span><span class="sxs-lookup"><span data-stu-id="36cef-116">If flavor information is not desired, this parameter can be `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="36cef-117">Döndürülen değer</span><span class="sxs-lookup"><span data-stu-id="36cef-117">Return value</span></span>

<span data-ttu-id="36cef-118">Bu işlev tarafından döndürülen aşağıdaki değerler, *Wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="36cef-118">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="36cef-119">Sabit</span><span class="sxs-lookup"><span data-stu-id="36cef-119">Constant</span></span>  |<span data-ttu-id="36cef-120">Değer</span><span class="sxs-lookup"><span data-stu-id="36cef-120">Value</span></span>  |<span data-ttu-id="36cef-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="36cef-121">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="36cef-122">0x80041008</span><span class="sxs-lookup"><span data-stu-id="36cef-122">0x80041008</span></span> | <span data-ttu-id="36cef-123">Parametre geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="36cef-123">A parameter is not valid.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="36cef-124">0x80041002</span><span class="sxs-lookup"><span data-stu-id="36cef-124">0x80041002</span></span> | <span data-ttu-id="36cef-125">Belirtilen niteleyici yok.</span><span class="sxs-lookup"><span data-stu-id="36cef-125">The specified qualifier does not exist.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="36cef-126">0</span><span class="sxs-lookup"><span data-stu-id="36cef-126">0</span></span> | <span data-ttu-id="36cef-127">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="36cef-127">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="36cef-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="36cef-128">Remarks</span></span>

<span data-ttu-id="36cef-129">Bu işlev, [IWbemQualifierSet:: Get](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-get) yöntemine bir çağrı kaydırır.</span><span class="sxs-lookup"><span data-stu-id="36cef-129">This function wraps a call to the [IWbemQualifierSet::Get](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-get) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="36cef-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="36cef-130">Requirements</span></span>  

 <span data-ttu-id="36cef-131">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="36cef-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="36cef-132">**Üst bilgi:** WMINet_Utils. IDL</span><span class="sxs-lookup"><span data-stu-id="36cef-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="36cef-133">**.NET Framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="36cef-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36cef-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="36cef-134">See also</span></span>

- [<span data-ttu-id="36cef-135">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="36cef-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
