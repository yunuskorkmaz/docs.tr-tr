---
title: NextMethod işlevi (yönetilmeyen API Başvurusu)
description: Bir numaralandırma sonraki yöntem NextMethod işlevi alır.
ms.date: 11/06/2017
api_name:
- NextMethod
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- NextMethod
helpviewer_keywords:
- NextMethod function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1d019c67849197cd24171ff607e60e9f08d5ff70
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "44040882"
---
# <a name="nextmethod-function"></a><span data-ttu-id="279c2-103">NextMethod işlevi</span><span class="sxs-lookup"><span data-stu-id="279c2-103">NextMethod function</span></span>
<span data-ttu-id="279c2-104">Sonraki yöntem çağrısı ile başlayan bir numaralandırma alır [BeginMethodEnumeration](beginmethodenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="279c2-104">Retrieves the next method in an enumeration that begins with a call to [BeginMethodEnumeration](beginmethodenumeration.md).</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="279c2-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="279c2-105">Syntax</span></span>  
  
```  
HRESULT NextMethod (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LONG                lFlags,
   [out] BSTR*              pName,
   [out] IWbemClassObject** ppInSignature,
   [out] IWbemClassObject** ppOutSignature   
); 
```  

## <a name="parameters"></a><span data-ttu-id="279c2-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="279c2-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="279c2-107">[in] Bu parametre kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="279c2-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="279c2-108">[in] Bir işaretçi bir [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneği.</span><span class="sxs-lookup"><span data-stu-id="279c2-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lFlags`  
<span data-ttu-id="279c2-109">[in] Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="279c2-109">[in] Reserved.</span></span> <span data-ttu-id="279c2-110">Bu parametre 0 olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="279c2-110">This parameter must be 0.</span></span>

`pName`  
<span data-ttu-id="279c2-111">[out] İşaret eden bir işaretçi `null` çağrıdan önce.</span><span class="sxs-lookup"><span data-stu-id="279c2-111">[out] A pointer that points to `null` prior to the call.</span></span> <span data-ttu-id="279c2-112">İşlevi döndüğünde, yeni bir adres `BSTR` içeren yöntem adı.</span><span class="sxs-lookup"><span data-stu-id="279c2-112">When the function returns, the address of a new `BSTR` that contains the method name.</span></span> 

`ppSignatureIn`  
<span data-ttu-id="279c2-113">[out] Bir işaretçi alır bir işaretçi bir [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) içeren `in` yönteminin parametreleri.</span><span class="sxs-lookup"><span data-stu-id="279c2-113">[out] A pointer that receives a pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) that contains the `in` parameters for the method.</span></span> 

`ppSignatureOut`  
<span data-ttu-id="279c2-114">[out] Bir işaretçi alır bir işaretçi bir [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) içeren `out` yönteminin parametreleri.</span><span class="sxs-lookup"><span data-stu-id="279c2-114">[out] A pointer that receives a pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) that contains the `out` parameters for the method.</span></span> 

## <a name="return-value"></a><span data-ttu-id="279c2-115">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="279c2-115">Return value</span></span>

<span data-ttu-id="279c2-116">Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üst bilgi dosyası veya tanımlayabilirsiniz bunları sabitleri kodunuzda:</span><span class="sxs-lookup"><span data-stu-id="279c2-116">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="279c2-117">Sabit</span><span class="sxs-lookup"><span data-stu-id="279c2-117">Constant</span></span>  |<span data-ttu-id="279c2-118">Değer</span><span class="sxs-lookup"><span data-stu-id="279c2-118">Value</span></span>  |<span data-ttu-id="279c2-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="279c2-119">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_UNEXPECTED` | <span data-ttu-id="279c2-120">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="279c2-120">0x8004101d</span></span> | <span data-ttu-id="279c2-121">Hiçbir çağrı oluştu [ `BeginEnumeration` ](beginenumeration.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="279c2-121">There was no call to the [`BeginEnumeration`](beginenumeration.md) function.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="279c2-122">0</span><span class="sxs-lookup"><span data-stu-id="279c2-122">0</span></span> | <span data-ttu-id="279c2-123">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="279c2-123">The function call was successful.</span></span>  |
| `WBEM_S_NO_MORE_DATA` | <span data-ttu-id="279c2-124">0x40005</span><span class="sxs-lookup"><span data-stu-id="279c2-124">0x40005</span></span> | <span data-ttu-id="279c2-125">Sabit listede daha fazla özellik vardır.</span><span class="sxs-lookup"><span data-stu-id="279c2-125">There are no more properties in the enumeration.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="279c2-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="279c2-126">Remarks</span></span>

<span data-ttu-id="279c2-127">Bu işlev bir çağrı sarılır [IWbemClassObject::NextMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-nextmethod) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="279c2-127">This function wraps a call to the [IWbemClassObject::NextMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-nextmethod) method.</span></span>

<span data-ttu-id="279c2-128">Çağıranın çağırarak sabit listesi sırası başlar [BeginMethodEnumeration](beginmethodenumeration.md) işlev ve işlev dönene kadar sonra [NextMethod] işlevini çağırır `WBEM_S_NO_MORE_DATA`.</span><span class="sxs-lookup"><span data-stu-id="279c2-128">The caller begins the enumeration sequence by calling the [BeginMethodEnumeration](beginmethodenumeration.md) function, and then calls the [NextMethod] function until the function returns `WBEM_S_NO_MORE_DATA`.</span></span> <span data-ttu-id="279c2-129">İsteğe bağlı olarak, çağıran çağırarak sırası tamamlandıktan [EndMethodEnumeration](endmethodenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="279c2-129">Optionally, the caller finishes the sequence by calling [EndMethodEnumeration](endmethodenumeration.md).</span></span> <span data-ttu-id="279c2-130">Çağıranın numaralandırma erken çağırarak sonlandırabilir [EndMethodEnumeration](endmethodenumeration.md) dilediğiniz zaman.</span><span class="sxs-lookup"><span data-stu-id="279c2-130">The caller may terminate the enumeration early by calling [EndMethodEnumeration](endmethodenumeration.md) at any time.</span></span>

## <a name="example"></a><span data-ttu-id="279c2-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="279c2-131">Example</span></span>

<span data-ttu-id="279c2-132">C++ örnek için bkz: [IWbemClassObject::NextMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-nextmethod) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="279c2-132">For a C++ example, see the [IWbemClassObject::NextMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-nextmethod) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="279c2-133">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="279c2-133">Requirements</span></span>  
 <span data-ttu-id="279c2-134">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="279c2-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="279c2-135">**Başlık:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="279c2-135">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="279c2-136">**.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="279c2-136">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="279c2-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="279c2-137">See also</span></span>  
[<span data-ttu-id="279c2-138">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="279c2-138">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
