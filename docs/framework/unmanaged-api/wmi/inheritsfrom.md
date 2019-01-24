---
title: InheritsFrom işlevi (yönetilmeyen API Başvurusu)
description: InheritsFrom işlevi bir sınıf veya örnek belirli üst sınıftan türetilen olup olmadığını belirler.
ms.date: 11/06/2017
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
ms.openlocfilehash: 078950b4e46ea587c2f39986963ec129f4ec1f1e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54618389"
---
# <a name="inheritsfrom-function"></a><span data-ttu-id="e1678-103">InheritsFrom işlevi</span><span class="sxs-lookup"><span data-stu-id="e1678-103">InheritsFrom function</span></span>
<span data-ttu-id="e1678-104">Geçerli sınıf veya örnek belirtilen üst sınıftan türetilen olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="e1678-104">Determines whether the current class or instance derives from a specified parent class.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="e1678-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e1678-105">Syntax</span></span>  
  
```
HRESULT InheritsFrom (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszAncestor 
); 
```  

## <a name="parameters"></a><span data-ttu-id="e1678-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e1678-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="e1678-107">[in] Bu parametre kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="e1678-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="e1678-108">[in] Bir işaretçi bir [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneği.</span><span class="sxs-lookup"><span data-stu-id="e1678-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszAncestor`  
<span data-ttu-id="e1678-109">[in] Sınıf adı.</span><span class="sxs-lookup"><span data-stu-id="e1678-109">[in] The name of the class.</span></span> <span data-ttu-id="e1678-110">`wszAncestor` Geçerli bir işaret etmelidir `LPCWSTR`.</span><span class="sxs-lookup"><span data-stu-id="e1678-110">`wszAncestor` must point to a valid `LPCWSTR`.</span></span>

## <a name="return-value"></a><span data-ttu-id="e1678-111">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="e1678-111">Return value</span></span>

<span data-ttu-id="e1678-112">Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üst bilgi dosyası veya tanımlayabilirsiniz bunları sabitleri kodunuzda:</span><span class="sxs-lookup"><span data-stu-id="e1678-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="e1678-113">Sabit</span><span class="sxs-lookup"><span data-stu-id="e1678-113">Constant</span></span>  |<span data-ttu-id="e1678-114">Değer</span><span class="sxs-lookup"><span data-stu-id="e1678-114">Value</span></span>  |<span data-ttu-id="e1678-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e1678-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_S_NO_ERROR` | <span data-ttu-id="e1678-116">0</span><span class="sxs-lookup"><span data-stu-id="e1678-116">0</span></span> | <span data-ttu-id="e1678-117">Geçerli nesnenin miras `wszAncestor`.</span><span class="sxs-lookup"><span data-stu-id="e1678-117">The current object inherits from `wszAncestor`.</span></span>  |
| `WBEM_S_FALSE` | <span data-ttu-id="e1678-118">1.</span><span class="sxs-lookup"><span data-stu-id="e1678-118">1</span></span> | <span data-ttu-id="e1678-119">Geçerli nesne öğesinden devralmayan `wszAncestor`.</span><span class="sxs-lookup"><span data-stu-id="e1678-119">The current object does not inherit from `wszAncestor`.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="e1678-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="e1678-120">0x80041008</span></span> | <span data-ttu-id="e1678-121">`wszAncestor` olan `null`.</span><span class="sxs-lookup"><span data-stu-id="e1678-121">`wszAncestor` is `null`.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="e1678-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e1678-122">Remarks</span></span>

<span data-ttu-id="e1678-123">Bu işlev bir çağrı sarılır [IWbemClassObject::InheritsFrom](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-inheritsfrom) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e1678-123">This function wraps a call to the [IWbemClassObject::InheritsFrom](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-inheritsfrom) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="e1678-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e1678-124">Requirements</span></span>  
 <span data-ttu-id="e1678-125">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e1678-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1678-126">**Üst bilgi:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="e1678-126">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="e1678-127">**.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="e1678-127">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1678-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e1678-128">See also</span></span>
- [<span data-ttu-id="e1678-129">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="e1678-129">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
