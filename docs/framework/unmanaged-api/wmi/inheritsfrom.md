---
title: "InheritsFrom işlevi (yönetilmeyen API Başvurusu)"
description: "InheritsFrom işlevi bir sınıf veya örnek belirli üst sınıftan türetilen olup olmadığını belirler."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: reference
api_name:
- InheritsFrom
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- InheritsFrom
helpviewer_keywords:
- InheritsFrom function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0dce964829399e6761152a8ff424671b47cc6eb3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="inheritsfrom-function"></a><span data-ttu-id="af910-103">InheritsFrom işlevi</span><span class="sxs-lookup"><span data-stu-id="af910-103">InheritsFrom function</span></span>
<span data-ttu-id="af910-104">Geçerli sınıf veya örnek belirtilen üst sınıftan türetilen olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="af910-104">Determines whether the current class or instance derives from a specified parent class.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="af910-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="af910-105">Syntax</span></span>  
  
```
HRESULT InheritsFrom (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszAncestor 
); 
```  

## <a name="parameters"></a><span data-ttu-id="af910-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="af910-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="af910-107">[in] Bu parametre kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="af910-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="af910-108">[in] Bir işaretçi bir [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) örneği.</span><span class="sxs-lookup"><span data-stu-id="af910-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`wszAncestor`  
<span data-ttu-id="af910-109">[in] Sınıfın adı.</span><span class="sxs-lookup"><span data-stu-id="af910-109">[in] The name of the class.</span></span> <span data-ttu-id="af910-110">`wszAncestor`Geçerli bir işaret etmelidir `LPCWSTR`.</span><span class="sxs-lookup"><span data-stu-id="af910-110">`wszAncestor` must point to a valid `LPCWSTR`.</span></span>

## <a name="return-value"></a><span data-ttu-id="af910-111">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="af910-111">Return value</span></span>

<span data-ttu-id="af910-112">Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üstbilgi dosyası, veya tanımlayabilirsiniz bunları sabitleri kodunuzda:</span><span class="sxs-lookup"><span data-stu-id="af910-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="af910-113">Sabit</span><span class="sxs-lookup"><span data-stu-id="af910-113">Constant</span></span>  |<span data-ttu-id="af910-114">Değer</span><span class="sxs-lookup"><span data-stu-id="af910-114">Value</span></span>  |<span data-ttu-id="af910-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="af910-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_S_NO_ERROR` | <span data-ttu-id="af910-116">0</span><span class="sxs-lookup"><span data-stu-id="af910-116">0</span></span> | <span data-ttu-id="af910-117">Geçerli nesnenin devraldığı `wszAncestor`.</span><span class="sxs-lookup"><span data-stu-id="af910-117">The current object inherits from `wszAncestor`.</span></span>  |
| `WBEM_S_FALSE` | <span data-ttu-id="af910-118">1.</span><span class="sxs-lookup"><span data-stu-id="af910-118">1</span></span> | <span data-ttu-id="af910-119">Geçerli nesne öğesinden devralmıyor `wszAncestor`.</span><span class="sxs-lookup"><span data-stu-id="af910-119">The current object does not inherit from `wszAncestor`.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="af910-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="af910-120">0x80041008</span></span> | <span data-ttu-id="af910-121">`wszAncestor`olan `null`.</span><span class="sxs-lookup"><span data-stu-id="af910-121">`wszAncestor` is `null`.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="af910-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="af910-122">Remarks</span></span>

<span data-ttu-id="af910-123">Bu işlev çağrısı sarmalar [IWbemClassObject::InheritsFrom](https://msdn.microsoft.com/library/aa391452(v=vs.85).aspx) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="af910-123">This function wraps a call to the [IWbemClassObject::InheritsFrom](https://msdn.microsoft.com/library/aa391452(v=vs.85).aspx) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="af910-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="af910-124">Requirements</span></span>  
 <span data-ttu-id="af910-125">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="af910-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af910-126">**Başlık:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="af910-126">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="af910-127">**.NET framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="af910-127">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af910-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="af910-128">See also</span></span>  
[<span data-ttu-id="af910-129">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="af910-129">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
