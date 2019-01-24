---
title: EndMethodEnumeration işlevi (yönetilmeyen API Başvurusu)
description: EndMethodEnumeration işlevi bir yöntem sabit listesi sırası sonlandırır.
ms.date: 11/06/2017
api_name:
- EndMethodEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- EndMethodEnumeration
helpviewer_keywords:
- EndMethodEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a098afe1702e9559a2784ea0716a0a61216e9fd4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54535222"
---
# <a name="endmethodenumeration-function"></a><span data-ttu-id="735f4-103">EndMethodEnumeration işlevi</span><span class="sxs-lookup"><span data-stu-id="735f4-103">EndMethodEnumeration function</span></span>
<span data-ttu-id="735f4-104">Bir çağrı ile başlatılan bir numaralandırma sırasını sonlandırıyor [BeginMethodEnumeration işlevi](beginmethodenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="735f4-104">Terminates an enumeration sequence started with a call to the [BeginMethodEnumeration function](beginmethodenumeration.md).</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="735f4-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="735f4-105">Syntax</span></span>  
  
```  
HRESULT EndMethodEnumeration (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr 
); 
```  

## <a name="parameters"></a><span data-ttu-id="735f4-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="735f4-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="735f4-107">[in] Bu parametre kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="735f4-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="735f4-108">[in] Bir işaretçi bir [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneği.</span><span class="sxs-lookup"><span data-stu-id="735f4-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

## <a name="return-value"></a><span data-ttu-id="735f4-109">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="735f4-109">Return value</span></span>

<span data-ttu-id="735f4-110">Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üst bilgi dosyası veya tanımlayabilirsiniz bunları sabitleri kodunuzda:</span><span class="sxs-lookup"><span data-stu-id="735f4-110">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="735f4-111">Sabit</span><span class="sxs-lookup"><span data-stu-id="735f4-111">Constant</span></span>  |<span data-ttu-id="735f4-112">Değer</span><span class="sxs-lookup"><span data-stu-id="735f4-112">Value</span></span>  |<span data-ttu-id="735f4-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="735f4-113">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_UNEXPECTED` | <span data-ttu-id="735f4-114">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="735f4-114">0x8004101d</span></span> | <span data-ttu-id="735f4-115">Bir iç hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="735f4-115">An internal error occurred.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="735f4-116">0</span><span class="sxs-lookup"><span data-stu-id="735f4-116">0</span></span> | <span data-ttu-id="735f4-117">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="735f4-117">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="735f4-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="735f4-118">Remarks</span></span>

<span data-ttu-id="735f4-119">Bu işlev bir çağrı sarılır [IWbemClassObject::EndMethodEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-endmethodenumeration) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="735f4-119">This function wraps a call to the [IWbemClassObject::EndMethodEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-endmethodenumeration) method.</span></span>

<span data-ttu-id="735f4-120">Sabit listesi sırası kullanılarak çağıran başlar [BeginMethodEnumeration işlevi](beginmethodenumeration.md)ve ardından çağırır [NextMethod işlevi](nextmethod.md )yöntemi dönene kadar `WBEM_S_NO_MORE_DATA`.</span><span class="sxs-lookup"><span data-stu-id="735f4-120">The caller begins the enumeration sequence using [BeginMethodEnumeration function](beginmethodenumeration.md), and then calls the [NextMethod function](nextmethod.md )until the method  returns `WBEM_S_NO_MORE_DATA`.</span></span> <span data-ttu-id="735f4-121">İsteğe bağlı olarak çağıran çağırarak sırası tamamlandıktan `EndMethodEnumeration`.</span><span class="sxs-lookup"><span data-stu-id="735f4-121">The caller optionally finishes the sequence by calling `EndMethodEnumeration`.</span></span> <span data-ttu-id="735f4-122">Çağıranın numaralandırma erken çağırarak sonlandırabilir `EndMethodEnumeration` dilediğiniz zaman.</span><span class="sxs-lookup"><span data-stu-id="735f4-122">The caller may terminate the enumeration early by calling `EndMethodEnumeration` at any time.</span></span>

## <a name="requirements"></a><span data-ttu-id="735f4-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="735f4-123">Requirements</span></span>  
 <span data-ttu-id="735f4-124">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="735f4-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="735f4-125">**Üst bilgi:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="735f4-125">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="735f4-126">**.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="735f4-126">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="735f4-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="735f4-127">See also</span></span>
- [<span data-ttu-id="735f4-128">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="735f4-128">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
