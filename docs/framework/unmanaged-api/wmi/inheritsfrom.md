---
title: Inhersfrom işlevi (yönetilmeyen API Başvurusu)
description: Inhersfrom işlevi bir sınıfın veya örneğin belirli bir üst sınıftan türeip türetilmediğini belirler.
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
ms.openlocfilehash: 0c32c54ec56ea0fe4f4039ca6438a91338edbadb
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798456"
---
# <a name="inheritsfrom-function"></a><span data-ttu-id="49dd8-103">Inhersfrom işlevi</span><span class="sxs-lookup"><span data-stu-id="49dd8-103">InheritsFrom function</span></span>
<span data-ttu-id="49dd8-104">Geçerli sınıfın veya örneğin belirtilen bir üst sınıftan türeip türetilmediğini belirler.</span><span class="sxs-lookup"><span data-stu-id="49dd8-104">Determines whether the current class or instance derives from a specified parent class.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="49dd8-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="49dd8-105">Syntax</span></span>  
  
```cpp
HRESULT InheritsFrom (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszAncestor 
); 
```  

## <a name="parameters"></a><span data-ttu-id="49dd8-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="49dd8-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="49dd8-107">'ndaki Bu parametre kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="49dd8-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="49dd8-108">'ndaki [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneğine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="49dd8-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszAncestor`  
<span data-ttu-id="49dd8-109">'ndaki Sınıfın adı.</span><span class="sxs-lookup"><span data-stu-id="49dd8-109">[in] The name of the class.</span></span> <span data-ttu-id="49dd8-110">`wszAncestor`geçerli `LPCWSTR`bir işaret etmelidir.</span><span class="sxs-lookup"><span data-stu-id="49dd8-110">`wszAncestor` must point to a valid `LPCWSTR`.</span></span>

## <a name="return-value"></a><span data-ttu-id="49dd8-111">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="49dd8-111">Return value</span></span>

<span data-ttu-id="49dd8-112">Bu işlev tarafından döndürülen aşağıdaki değerler, *Wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="49dd8-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="49dd8-113">Sabit</span><span class="sxs-lookup"><span data-stu-id="49dd8-113">Constant</span></span>  |<span data-ttu-id="49dd8-114">Değer</span><span class="sxs-lookup"><span data-stu-id="49dd8-114">Value</span></span>  |<span data-ttu-id="49dd8-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="49dd8-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_S_NO_ERROR` | <span data-ttu-id="49dd8-116">0</span><span class="sxs-lookup"><span data-stu-id="49dd8-116">0</span></span> | <span data-ttu-id="49dd8-117">Geçerli nesne öğesinden `wszAncestor`devralır.</span><span class="sxs-lookup"><span data-stu-id="49dd8-117">The current object inherits from `wszAncestor`.</span></span>  |
| `WBEM_S_FALSE` | <span data-ttu-id="49dd8-118">1\.</span><span class="sxs-lookup"><span data-stu-id="49dd8-118">1</span></span> | <span data-ttu-id="49dd8-119">Geçerli nesne öğesinden `wszAncestor`almıyor.</span><span class="sxs-lookup"><span data-stu-id="49dd8-119">The current object does not inherit from `wszAncestor`.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="49dd8-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="49dd8-120">0x80041008</span></span> | <span data-ttu-id="49dd8-121">`wszAncestor``null`.</span><span class="sxs-lookup"><span data-stu-id="49dd8-121">`wszAncestor` is `null`.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="49dd8-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="49dd8-122">Remarks</span></span>

<span data-ttu-id="49dd8-123">Bu işlev, [IWbemClassObject:: ınhersfrom](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-inheritsfrom) yöntemine bir çağrı kaydırır.</span><span class="sxs-lookup"><span data-stu-id="49dd8-123">This function wraps a call to the [IWbemClassObject::InheritsFrom](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-inheritsfrom) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="49dd8-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="49dd8-124">Requirements</span></span>  
 <span data-ttu-id="49dd8-125">**Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="49dd8-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49dd8-126">**Üst bilgi** WMINet_Utils. IDL</span><span class="sxs-lookup"><span data-stu-id="49dd8-126">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="49dd8-127">**.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="49dd8-127">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49dd8-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="49dd8-128">See also</span></span>

- [<span data-ttu-id="49dd8-129">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="49dd8-129">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
