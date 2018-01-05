---
title: "GetMethod işlevi (yönetilmeyen API Başvurusu)"
description: "GetMethod işlevi bir yöntem hakkında bilgi alır."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: GetMethod
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: GetMethod
helpviewer_keywords: GetMethod function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f22a2dfa7aae411cac960cbad2017718df8057e1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="getmethod-function"></a><span data-ttu-id="0b558-103">GetMethod işlevi</span><span class="sxs-lookup"><span data-stu-id="0b558-103">GetMethod function</span></span>
<span data-ttu-id="0b558-104">Belirtilen yöntem bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="0b558-104">Retrieves information about the specified method.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="0b558-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0b558-105">Syntax</span></span>  
  
```  
HRESULT GetMethod (
   [in] int                vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LPCWSTR             wszName,
   [in] LONG                lFlags,
   [out] IWbemClassObject** ppInSignature,
   [out] IWbemClassObject** ppOutSignature
); 
```  

## <a name="parameters"></a><span data-ttu-id="0b558-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0b558-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="0b558-107">[in] Bu parametre kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="0b558-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="0b558-108">[in] Bir işaretçi bir [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) örneği.</span><span class="sxs-lookup"><span data-stu-id="0b558-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`wszName`  
<span data-ttu-id="0b558-109">[in] Yöntem adı.</span><span class="sxs-lookup"><span data-stu-id="0b558-109">[in] The method name.</span></span> <span data-ttu-id="0b558-110">Bu parametre olamaz `null` ve geçerli bir işaret etmelidir `LPCWSTR`.</span><span class="sxs-lookup"><span data-stu-id="0b558-110">This parameter cannot be `null` and must point to a valid `LPCWSTR`.</span></span>

`lFlags`  
<span data-ttu-id="0b558-111">[in] Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="0b558-111">[in] Reserved.</span></span> <span data-ttu-id="0b558-112">Bu parametre 0 olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0b558-112">This parameter must be 0.</span></span>

`ppInSignature`   
<span data-ttu-id="0b558-113">[out] Adresine bir işaretçi bir [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) yöntemine içinde paramteers açıklar örneği.</span><span class="sxs-lookup"><span data-stu-id="0b558-113">[out] A pointer to the address of an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance that describes the in paramteers to the method.</span></span> <span data-ttu-id="0b558-114">Bu ayarı etkinse, bu parametre yoksayılır `null`.</span><span class="sxs-lookup"><span data-stu-id="0b558-114">This parameter is ignored if it is set to `null`.</span></span> 

`ppOutSignature`  
<span data-ttu-id="0b558-115">[out] Adresine bir işaretçi bir [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) yöntemine out Parametreleri açıklayan örneği.</span><span class="sxs-lookup"><span data-stu-id="0b558-115">[out] A pointer to the address of an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance that describes the out parameters to the method.</span></span> <span data-ttu-id="0b558-116">Bu ayarı etkinse, bu parametre yoksayılır `null`.</span><span class="sxs-lookup"><span data-stu-id="0b558-116">This parameter is ignored if it is set to `null`.</span></span> 

## <a name="return-value"></a><span data-ttu-id="0b558-117">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="0b558-117">Return value</span></span>

<span data-ttu-id="0b558-118">Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üstbilgi dosyası, veya tanımlayabilirsiniz bunları sabitleri kodunuzda:</span><span class="sxs-lookup"><span data-stu-id="0b558-118">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="0b558-119">Sabit</span><span class="sxs-lookup"><span data-stu-id="0b558-119">Constant</span></span>  |<span data-ttu-id="0b558-120">Değer</span><span class="sxs-lookup"><span data-stu-id="0b558-120">Value</span></span>  |<span data-ttu-id="0b558-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0b558-121">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="0b558-122">0x80041002</span><span class="sxs-lookup"><span data-stu-id="0b558-122">0x80041002</span></span> | <span data-ttu-id="0b558-123">Belirtilen özellik bulunamadı.</span><span class="sxs-lookup"><span data-stu-id="0b558-123">The specified property was not found.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="0b558-124">0x80041006</span><span class="sxs-lookup"><span data-stu-id="0b558-124">0x80041006</span></span> | <span data-ttu-id="0b558-125">İşlemi tamamlamak yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="0b558-125">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="0b558-126">0</span><span class="sxs-lookup"><span data-stu-id="0b558-126">0</span></span> | <span data-ttu-id="0b558-127">İşlev çağrısı başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="0b558-127">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="0b558-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0b558-128">Remarks</span></span>

<span data-ttu-id="0b558-129">Bu işlev çağrısı sarmalar [IWbemClassObject::GetMethod](https://msdn.microsoft.com/library/aa391443(v=vs.85).aspx) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0b558-129">This function wraps a call to the [IWbemClassObject::GetMethod](https://msdn.microsoft.com/library/aa391443(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="0b558-130">Windows Yönetim ayarlayabilirsiniz [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) işaretçi `null` yöntemi hiçbir parametreleri varsa.</span><span class="sxs-lookup"><span data-stu-id="0b558-130">Windows Management can set the [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) pointer to `null` if the method has no in parameters.</span></span>

<span data-ttu-id="0b558-131">İçinde `ppInSignature` ve `ppOutSignature` ve out parametreleri, sırasıyla özellikleri olarak açıklayan bir `IWbemClassObject` sistem sınıfının örneği [_Parameters](https://msdn.microsoft.com/library/aa394667(v=vs.85).aspx).</span><span class="sxs-lookup"><span data-stu-id="0b558-131">In `ppInSignature` and `ppOutSignature` describe in and out parameters, respectively, as properties in a `IWbemClassObject` instance of the system class [_Parameters](https://msdn.microsoft.com/library/aa394667(v=vs.85).aspx).</span></span> <span data-ttu-id="0b558-132">Özelliklerinde `ppInsignature` adlandırıldığı **Param***n*, burada  *n*  yöntem imzası (örneğin parametresi konumunda olarak `Param1`, `Param2`vb..).</span><span class="sxs-lookup"><span data-stu-id="0b558-132">The properties in `ppInsignature` are named **Param***n*, where *n* is the position of the parameter in the method signature (such as `Param1`, `Param2`, etc.).</span></span> <span data-ttu-id="0b558-133">Özelliklerinde `ppOutSignature` olarak da adlandırılır **Param***n*, ve dönüş değeri adlı **ReturnValue**.</span><span class="sxs-lookup"><span data-stu-id="0b558-133">The properties in `ppOutSignature` are also named **Param***n*, and the return value is named **ReturnValue**.</span></span> <span data-ttu-id="0b558-134">Daha fazla bilgi ve bir örnek için bkz: [IWbemClassObject::GetMethod yöntemi](https://msdn.microsoft.com/library/aa391443(v=vs.85).aspx).</span><span class="sxs-lookup"><span data-stu-id="0b558-134">For more information and an example, see [IWbemClassObject::GetMethod method](https://msdn.microsoft.com/library/aa391443(v=vs.85).aspx).</span></span>

## <a name="requirements"></a><span data-ttu-id="0b558-135">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0b558-135">Requirements</span></span>  
<span data-ttu-id="0b558-136">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b558-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b558-137">**Başlık:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="0b558-137">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="0b558-138">**.NET framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="0b558-138">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b558-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0b558-139">See also</span></span>  
[<span data-ttu-id="0b558-140">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="0b558-140">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
