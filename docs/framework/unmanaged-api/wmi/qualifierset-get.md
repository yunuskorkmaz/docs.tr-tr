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
ms.openlocfilehash: dc09cd30c43647fa00cccc1dc00da4f8de367e84
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127272"
---
# <a name="qualifierset_get-function"></a><span data-ttu-id="e7e63-103">QualifierSet_Get işlevi</span><span class="sxs-lookup"><span data-stu-id="e7e63-103">QualifierSet_Get function</span></span>
<span data-ttu-id="e7e63-104">Belirtilen adlandırılmış niteleyiciyi alır.</span><span class="sxs-lookup"><span data-stu-id="e7e63-104">Gets the specified named qualifier.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="e7e63-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e7e63-105">Syntax</span></span>  
  
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

## <a name="parameters"></a><span data-ttu-id="e7e63-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e7e63-106">Parameters</span></span>

`vFunc`   
<span data-ttu-id="e7e63-107">'ndaki Bu parametre kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="e7e63-107">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="e7e63-108">'ndaki Bir [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) örneği işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="e7e63-108">[in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

`wszName`   
<span data-ttu-id="e7e63-109">'ndaki Değeri istenen niteleyicinin adı.</span><span class="sxs-lookup"><span data-stu-id="e7e63-109">[in] The name of the qualifier whose value is requested.</span></span>

`lFlags`   
<span data-ttu-id="e7e63-110">'ndaki Ayrılamadı.</span><span class="sxs-lookup"><span data-stu-id="e7e63-110">[in] Reserved.</span></span> <span data-ttu-id="e7e63-111">Bu parametre 0 olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e7e63-111">This parameter must be 0.</span></span>

`pVal`   
<span data-ttu-id="e7e63-112">dışı Başarılı olduğunda, niteleyicisi için doğru tür ve değer.</span><span class="sxs-lookup"><span data-stu-id="e7e63-112">[out] When successful, the correct type and value for the qualifier.</span></span> <span data-ttu-id="e7e63-113">İşlev başarısız olursa, `pVal` tarafından işaret edilen `VARIANT` değiştirilmez.</span><span class="sxs-lookup"><span data-stu-id="e7e63-113">If the function fails, the `VARIANT` pointed to by `pVal` is not modified.</span></span> <span data-ttu-id="e7e63-114">Bu parametre `null`, parametre yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="e7e63-114">If this parameter is `null`, the parameter is ignored.</span></span>

`plFlavor`   
<span data-ttu-id="e7e63-115">dışı İstenen niteleyici için niteleyici Flavor bitlerini alan bir LONG işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="e7e63-115">[out] A pointer to a LONG that receives the qualifier flavor bits for the requested qualifier.</span></span> <span data-ttu-id="e7e63-116">Flavor bilgileri istenmiyorsa, bu parametre `null`olabilir.</span><span class="sxs-lookup"><span data-stu-id="e7e63-116">If flavor information is not desired, this parameter can be `null`.</span></span> 

## <a name="return-value"></a><span data-ttu-id="e7e63-117">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="e7e63-117">Return value</span></span>

<span data-ttu-id="e7e63-118">Bu işlev tarafından döndürülen aşağıdaki değerler, *Wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e7e63-118">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="e7e63-119">Sabit</span><span class="sxs-lookup"><span data-stu-id="e7e63-119">Constant</span></span>  |<span data-ttu-id="e7e63-120">Değer</span><span class="sxs-lookup"><span data-stu-id="e7e63-120">Value</span></span>  |<span data-ttu-id="e7e63-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e7e63-121">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="e7e63-122">0x80041008</span><span class="sxs-lookup"><span data-stu-id="e7e63-122">0x80041008</span></span> | <span data-ttu-id="e7e63-123">Parametre geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="e7e63-123">A parameter is not valid.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="e7e63-124">0x80041002</span><span class="sxs-lookup"><span data-stu-id="e7e63-124">0x80041002</span></span> | <span data-ttu-id="e7e63-125">Belirtilen niteleyici yok.</span><span class="sxs-lookup"><span data-stu-id="e7e63-125">The specified qualifier does not exist.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="e7e63-126">0</span><span class="sxs-lookup"><span data-stu-id="e7e63-126">0</span></span> | <span data-ttu-id="e7e63-127">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="e7e63-127">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="e7e63-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e7e63-128">Remarks</span></span>

<span data-ttu-id="e7e63-129">Bu işlev, [IWbemQualifierSet:: Get](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-get) yöntemine bir çağrı kaydırır.</span><span class="sxs-lookup"><span data-stu-id="e7e63-129">This function wraps a call to the [IWbemQualifierSet::Get](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-get) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="e7e63-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e7e63-130">Requirements</span></span>  
 <span data-ttu-id="e7e63-131">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e7e63-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7e63-132">**Üst bilgi:** WMINet_Utils. IDL</span><span class="sxs-lookup"><span data-stu-id="e7e63-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="e7e63-133">**.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="e7e63-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7e63-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e7e63-134">See also</span></span>

- [<span data-ttu-id="e7e63-135">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="e7e63-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
