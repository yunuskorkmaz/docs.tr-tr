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
ms.openlocfilehash: 0d2af1b41f47a3906c0e573c104847aa3ff36cf8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59158437"
---
# <a name="inheritsfrom-function"></a><span data-ttu-id="bc68f-103">InheritsFrom işlevi</span><span class="sxs-lookup"><span data-stu-id="bc68f-103">InheritsFrom function</span></span>
<span data-ttu-id="bc68f-104">Geçerli sınıf veya örnek belirtilen üst sınıftan türetilen olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="bc68f-104">Determines whether the current class or instance derives from a specified parent class.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="bc68f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bc68f-105">Syntax</span></span>  
  
```
HRESULT InheritsFrom (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszAncestor 
); 
```  

## <a name="parameters"></a><span data-ttu-id="bc68f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bc68f-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="bc68f-107">[in] Bu parametre kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="bc68f-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="bc68f-108">[in] Bir işaretçi bir [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneği.</span><span class="sxs-lookup"><span data-stu-id="bc68f-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszAncestor`  
<span data-ttu-id="bc68f-109">[in] Sınıf adı.</span><span class="sxs-lookup"><span data-stu-id="bc68f-109">[in] The name of the class.</span></span> <span data-ttu-id="bc68f-110">`wszAncestor` Geçerli bir işaret etmelidir `LPCWSTR`.</span><span class="sxs-lookup"><span data-stu-id="bc68f-110">`wszAncestor` must point to a valid `LPCWSTR`.</span></span>

## <a name="return-value"></a><span data-ttu-id="bc68f-111">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="bc68f-111">Return value</span></span>

<span data-ttu-id="bc68f-112">Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üst bilgi dosyası veya tanımlayabilirsiniz bunları sabitleri kodunuzda:</span><span class="sxs-lookup"><span data-stu-id="bc68f-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="bc68f-113">Sabit</span><span class="sxs-lookup"><span data-stu-id="bc68f-113">Constant</span></span>  |<span data-ttu-id="bc68f-114">Değer</span><span class="sxs-lookup"><span data-stu-id="bc68f-114">Value</span></span>  |<span data-ttu-id="bc68f-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bc68f-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_S_NO_ERROR` | <span data-ttu-id="bc68f-116">0</span><span class="sxs-lookup"><span data-stu-id="bc68f-116">0</span></span> | <span data-ttu-id="bc68f-117">Geçerli nesnenin miras `wszAncestor`.</span><span class="sxs-lookup"><span data-stu-id="bc68f-117">The current object inherits from `wszAncestor`.</span></span>  |
| `WBEM_S_FALSE` | <span data-ttu-id="bc68f-118">1.</span><span class="sxs-lookup"><span data-stu-id="bc68f-118">1</span></span> | <span data-ttu-id="bc68f-119">Geçerli nesne öğesinden devralmayan `wszAncestor`.</span><span class="sxs-lookup"><span data-stu-id="bc68f-119">The current object does not inherit from `wszAncestor`.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="bc68f-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="bc68f-120">0x80041008</span></span> | <span data-ttu-id="bc68f-121">`wszAncestor` olan `null`.</span><span class="sxs-lookup"><span data-stu-id="bc68f-121">`wszAncestor` is `null`.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="bc68f-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bc68f-122">Remarks</span></span>

<span data-ttu-id="bc68f-123">Bu işlev bir çağrı sarılır [IWbemClassObject::InheritsFrom](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-inheritsfrom) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="bc68f-123">This function wraps a call to the [IWbemClassObject::InheritsFrom](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-inheritsfrom) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="bc68f-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bc68f-124">Requirements</span></span>  
 <span data-ttu-id="bc68f-125">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bc68f-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc68f-126">**Üst bilgi:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="bc68f-126">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="bc68f-127">**.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="bc68f-127">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc68f-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bc68f-128">See also</span></span>

- [<span data-ttu-id="bc68f-129">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="bc68f-129">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
