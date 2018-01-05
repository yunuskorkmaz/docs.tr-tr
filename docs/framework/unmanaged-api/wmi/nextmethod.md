---
title: "NextMethod işlevi (yönetilmeyen API Başvurusu)"
description: "NextMethod işlevi numaralandırma sonraki yöntem alır."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: NextMethod
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: NextMethod
helpviewer_keywords: NextMethod function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6b886b3ecbd1d5b5b8d212846b2bd8291fa43909
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="nextmethod-function"></a><span data-ttu-id="8dc62-103">NextMethod işlevi</span><span class="sxs-lookup"><span data-stu-id="8dc62-103">NextMethod function</span></span>
<span data-ttu-id="8dc62-104">Sonraki yöntem çağrısı ile başlayan bir numaralandırmasını alır [BeginMethodEnumeration](beginmethodenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="8dc62-104">Retrieves the next method in an enumeration that begins with a call to [BeginMethodEnumeration](beginmethodenumeration.md).</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="8dc62-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8dc62-105">Syntax</span></span>  
  
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

## <a name="parameters"></a><span data-ttu-id="8dc62-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8dc62-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="8dc62-107">[in] Bu parametre kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="8dc62-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="8dc62-108">[in] Bir işaretçi bir [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) örneği.</span><span class="sxs-lookup"><span data-stu-id="8dc62-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`lFlags`  
<span data-ttu-id="8dc62-109">[in] Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="8dc62-109">[in] Reserved.</span></span> <span data-ttu-id="8dc62-110">Bu parametre 0 olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8dc62-110">This parameter must be 0.</span></span>

`pName`  
<span data-ttu-id="8dc62-111">[out] İşaret eden bir işaretçi `null` çağrı önce.</span><span class="sxs-lookup"><span data-stu-id="8dc62-111">[out] A pointer that points to `null` prior to the call.</span></span> <span data-ttu-id="8dc62-112">İşlevi döndüğünde, yeni bir adres `BSTR` yöntem adını içerir.</span><span class="sxs-lookup"><span data-stu-id="8dc62-112">When the function returns, the address of a new `BSTR` that contains the method name.</span></span> 

`ppSignatureIn`  
<span data-ttu-id="8dc62-113">[out] Bir işaretçi alır bir işaretçi bir [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) içeren `in` yöntemi için parametreler.</span><span class="sxs-lookup"><span data-stu-id="8dc62-113">[out] A pointer that receives a pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) that contains the `in` parameters for the method.</span></span> 

`ppSignatureOut`  
<span data-ttu-id="8dc62-114">[out] Bir işaretçi alır bir işaretçi bir [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) içeren `out` yöntemi için parametreler.</span><span class="sxs-lookup"><span data-stu-id="8dc62-114">[out] A pointer that receives a pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) that contains the `out` parameters for the method.</span></span> 

## <a name="return-value"></a><span data-ttu-id="8dc62-115">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="8dc62-115">Return value</span></span>

<span data-ttu-id="8dc62-116">Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üstbilgi dosyası, veya tanımlayabilirsiniz bunları sabitleri kodunuzda:</span><span class="sxs-lookup"><span data-stu-id="8dc62-116">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="8dc62-117">Sabit</span><span class="sxs-lookup"><span data-stu-id="8dc62-117">Constant</span></span>  |<span data-ttu-id="8dc62-118">Değer</span><span class="sxs-lookup"><span data-stu-id="8dc62-118">Value</span></span>  |<span data-ttu-id="8dc62-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8dc62-119">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_UNEXPECTED` | <span data-ttu-id="8dc62-120">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="8dc62-120">0x8004101d</span></span> | <span data-ttu-id="8dc62-121">Hiçbir çağrısına vardı [ `BeginEnumeration` ](beginenumeration.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="8dc62-121">There was no call to the [`BeginEnumeration`](beginenumeration.md) function.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="8dc62-122">0</span><span class="sxs-lookup"><span data-stu-id="8dc62-122">0</span></span> | <span data-ttu-id="8dc62-123">İşlev çağrısı başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="8dc62-123">The function call was successful.</span></span>  |
| `WBEM_S_NO_MORE_DATA` | <span data-ttu-id="8dc62-124">0x40005</span><span class="sxs-lookup"><span data-stu-id="8dc62-124">0x40005</span></span> | <span data-ttu-id="8dc62-125">Sabit listede daha fazla özellik yok.</span><span class="sxs-lookup"><span data-stu-id="8dc62-125">There are no more properties in the enumeration.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="8dc62-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8dc62-126">Remarks</span></span>

<span data-ttu-id="8dc62-127">Bu işlev çağrısı sarmalar [IWbemClassObject::NextMethod](https://msdn.microsoft.com/library/aa391454(v=vs.85).aspx) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8dc62-127">This function wraps a call to the [IWbemClassObject::NextMethod](https://msdn.microsoft.com/library/aa391454(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="8dc62-128">Arayan çağırarak numaralandırma sırası başlar [BeginMethodEnumeration](beginmethodenumeration.md) işlev ve işlev döndürünceye kadar [NextMethod] işlevi çağırır `WBEM_S_NO_MORE_DATA`.</span><span class="sxs-lookup"><span data-stu-id="8dc62-128">The caller begins the enumeration sequence by calling the [BeginMethodEnumeration](beginmethodenumeration.md) function, and then calls the [NextMethod] function until the function returns `WBEM_S_NO_MORE_DATA`.</span></span> <span data-ttu-id="8dc62-129">İsteğe bağlı olarak, çağıran çağırarak sırası tamamlandıktan [EndMethodEnumeration](endmethodenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="8dc62-129">Optionally, the caller finishes the sequence by calling [EndMethodEnumeration](endmethodenumeration.md).</span></span> <span data-ttu-id="8dc62-130">Arayan numaralandırması erken çağırarak sonlandırabilir [EndMethodEnumeration](endmethodenumeration.md) dilediğiniz zaman.</span><span class="sxs-lookup"><span data-stu-id="8dc62-130">The caller may terminate the enumeration early by calling [EndMethodEnumeration](endmethodenumeration.md) at any time.</span></span>

## <a name="example"></a><span data-ttu-id="8dc62-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="8dc62-131">Example</span></span>

<span data-ttu-id="8dc62-132">C++ örnek için bkz: [IWbemClassObject::NextMethod](https://msdn.microsoft.com/library/aa391454(v=vs.85).aspx) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8dc62-132">For a C++ example, see the [IWbemClassObject::NextMethod](https://msdn.microsoft.com/library/aa391454(v=vs.85).aspx) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="8dc62-133">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8dc62-133">Requirements</span></span>  
 <span data-ttu-id="8dc62-134">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8dc62-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8dc62-135">**Başlık:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="8dc62-135">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="8dc62-136">**.NET framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="8dc62-136">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8dc62-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8dc62-137">See also</span></span>  
[<span data-ttu-id="8dc62-138">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="8dc62-138">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
