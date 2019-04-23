---
title: QualifierSet_Get işlevi (yönetilmeyen API Başvurusu)
description: Adlandırılmış bir niteleyici QualifierSet_Get işlevi alır.
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b0dc76a2732bf9c1e4f3a26fa2d045bfbcd837ec
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59181096"
---
# <a name="qualifiersetget-function"></a><span data-ttu-id="5b4f0-103">QualifierSet_Get işlevi</span><span class="sxs-lookup"><span data-stu-id="5b4f0-103">QualifierSet_Get function</span></span>
<span data-ttu-id="5b4f0-104">Belirtilen adlandırılmış niteleyicisi alır.</span><span class="sxs-lookup"><span data-stu-id="5b4f0-104">Gets the specified named qualifier.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="5b4f0-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5b4f0-105">Syntax</span></span>  
  
```  
HRESULT QualifierSet_Get (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LPCWSTR              wszName,
   [in] LONG                 lFlags,
   [out] VARIANT*            pVal,
   [out] LONG*               plFlavor                 
); 
```  

## <a name="parameters"></a><span data-ttu-id="5b4f0-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5b4f0-106">Parameters</span></span>

`vFunc`   
<span data-ttu-id="5b4f0-107">[in] Bu parametre kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="5b4f0-107">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="5b4f0-108">[in] Bir işaretçi bir [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) örneği.</span><span class="sxs-lookup"><span data-stu-id="5b4f0-108">[in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

`wszName`   
<span data-ttu-id="5b4f0-109">[in] Değeri istenen niteleyicisi adı.</span><span class="sxs-lookup"><span data-stu-id="5b4f0-109">[in] The name of the qualifier whose value is requested.</span></span>

`lFlags`   
<span data-ttu-id="5b4f0-110">[in] Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="5b4f0-110">[in] Reserved.</span></span> <span data-ttu-id="5b4f0-111">Bu parametre 0 olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5b4f0-111">This parameter must be 0.</span></span>

`pVal`   
<span data-ttu-id="5b4f0-112">[out] Başarılı olduğunda, Niteleyici değeri ve doğru türde.</span><span class="sxs-lookup"><span data-stu-id="5b4f0-112">[out] When successful, the correct type and value for the qualifier.</span></span> <span data-ttu-id="5b4f0-113">İşlev başarısız olursa `VARIANT` işaret ettiği `pVal` değiştirilmez.</span><span class="sxs-lookup"><span data-stu-id="5b4f0-113">If the function fails, the `VARIANT` pointed to by `pVal` is not modified.</span></span> <span data-ttu-id="5b4f0-114">Bu parametre `null`, parametre yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="5b4f0-114">If this parameter is `null`, the parameter is ignored.</span></span>

`plFlavor`   
<span data-ttu-id="5b4f0-115">[out] İstenen niteleyicisi niteleyicisi flavor parçaları alan uzun bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5b4f0-115">[out] A pointer to a LONG that receives the qualifier flavor bits for the requested qualifier.</span></span> <span data-ttu-id="5b4f0-116">Flavor bilgi istenildiği gibi değilse, bu parametre olabilir `null`.</span><span class="sxs-lookup"><span data-stu-id="5b4f0-116">If flavor information is not desired, this parameter can be `null`.</span></span> 

## <a name="return-value"></a><span data-ttu-id="5b4f0-117">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="5b4f0-117">Return value</span></span>

<span data-ttu-id="5b4f0-118">Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üst bilgi dosyası veya tanımlayabilirsiniz bunları sabitleri kodunuzda:</span><span class="sxs-lookup"><span data-stu-id="5b4f0-118">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="5b4f0-119">Sabit</span><span class="sxs-lookup"><span data-stu-id="5b4f0-119">Constant</span></span>  |<span data-ttu-id="5b4f0-120">Değer</span><span class="sxs-lookup"><span data-stu-id="5b4f0-120">Value</span></span>  |<span data-ttu-id="5b4f0-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5b4f0-121">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="5b4f0-122">0x80041008</span><span class="sxs-lookup"><span data-stu-id="5b4f0-122">0x80041008</span></span> | <span data-ttu-id="5b4f0-123">Bir parametre geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="5b4f0-123">A parameter is not valid.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="5b4f0-124">0x80041002</span><span class="sxs-lookup"><span data-stu-id="5b4f0-124">0x80041002</span></span> | <span data-ttu-id="5b4f0-125">Belirtilen niteleyicisi yok.</span><span class="sxs-lookup"><span data-stu-id="5b4f0-125">The specified qualifier does not exist.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="5b4f0-126">0</span><span class="sxs-lookup"><span data-stu-id="5b4f0-126">0</span></span> | <span data-ttu-id="5b4f0-127">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="5b4f0-127">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="5b4f0-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5b4f0-128">Remarks</span></span>

<span data-ttu-id="5b4f0-129">Bu işlev bir çağrı sarılır [IWbemQualifierSet::Get](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-get) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5b4f0-129">This function wraps a call to the [IWbemQualifierSet::Get](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-get) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="5b4f0-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5b4f0-130">Requirements</span></span>  
 <span data-ttu-id="5b4f0-131">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5b4f0-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b4f0-132">**Üst bilgi:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="5b4f0-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="5b4f0-133">**.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="5b4f0-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b4f0-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5b4f0-134">See also</span></span>

- [<span data-ttu-id="5b4f0-135">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="5b4f0-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
