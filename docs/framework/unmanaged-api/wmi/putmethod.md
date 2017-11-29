---
title: "PutMethod işlevi (yönetilmeyen API Başvurusu)"
description: "PutMethod işlevi bir yöntem oluşturur."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: PutMethod
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: PutMethod
helpviewer_keywords: PutMethod function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 64e43165b34b74540931b308100c9ca942946bcf
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/15/2017
---
# <a name="putmethod-function"></a><span data-ttu-id="0a4e9-103">PutMethod işlevi</span><span class="sxs-lookup"><span data-stu-id="0a4e9-103">PutMethod function</span></span>
<span data-ttu-id="0a4e9-104">Bir yöntem oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0a4e9-104">Creates a method.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="0a4e9-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0a4e9-105">Syntax</span></span>  
  
```  
HRESULT PutMethod (
   [in] int                vFunc, 
   [in] IWbemClassObject*  ptr, 
   [in] LPCWSTR            wszName,
   [in] LONG               lFlags,
   [in] IWbemClassObject*  pInSignature,
   [in] IWbemClassObject*  pOutSignature
); 
```  

## <a name="parameters"></a><span data-ttu-id="0a4e9-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0a4e9-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="0a4e9-107">[in] Bu parametre kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="0a4e9-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="0a4e9-108">[in] Bir işaretçi bir [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) örneği.</span><span class="sxs-lookup"><span data-stu-id="0a4e9-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`wszName`  
<span data-ttu-id="0a4e9-109">[in] Oluşturmak için yöntemin adı.</span><span class="sxs-lookup"><span data-stu-id="0a4e9-109">[in] The name of the method to create.</span></span> 

`lFlags`  
<span data-ttu-id="0a4e9-110">[in] Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="0a4e9-110">[in] Reserved.</span></span> <span data-ttu-id="0a4e9-111">Bu parametre 0 olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0a4e9-111">This parameter must be 0.</span></span>

`pSignatureIn`  
<span data-ttu-id="0a4e9-112">[in] Bir işaretçi bir kopyasını [__Parameters sistem sınıfı](https://msdn.microsoft.com/library/aa394667(v=vs.85).aspx) içeren `in` yöntemi için parametreler.</span><span class="sxs-lookup"><span data-stu-id="0a4e9-112">[in] A pointer to a copy of the [__Parameters system class](https://msdn.microsoft.com/library/aa394667(v=vs.85).aspx) that contains the `in` parameters for the method.</span></span> <span data-ttu-id="0a4e9-113">Bu parametre yoksayılır kümesine `null`.</span><span class="sxs-lookup"><span data-stu-id="0a4e9-113">This parameter is ignored if set to `null`.</span></span>  

`pSignatureOut`  
<span data-ttu-id="0a4e9-114">[in]  Bir işaretçi bir kopyasını [__Parameters sistem sınıfı](https://msdn.microsoft.com/library/aa394667(v=vs.85).aspx) içeren `out` yöntemi için parametreler.</span><span class="sxs-lookup"><span data-stu-id="0a4e9-114">[in]  A pointer to a copy of the [__Parameters system class](https://msdn.microsoft.com/library/aa394667(v=vs.85).aspx) that contains the `out` parameters for the method.</span></span> <span data-ttu-id="0a4e9-115">Bu parametre yoksayılır kümesine `null`.</span><span class="sxs-lookup"><span data-stu-id="0a4e9-115">This parameter is ignored if set to `null`.</span></span>
 

## <a name="return-value"></a><span data-ttu-id="0a4e9-116">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="0a4e9-116">Return value</span></span>

<span data-ttu-id="0a4e9-117">Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üstbilgi dosyası, veya tanımlayabilirsiniz bunları sabitleri kodunuzda:</span><span class="sxs-lookup"><span data-stu-id="0a4e9-117">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="0a4e9-118">Sabit</span><span class="sxs-lookup"><span data-stu-id="0a4e9-118">Constant</span></span>  |<span data-ttu-id="0a4e9-119">Değer</span><span class="sxs-lookup"><span data-stu-id="0a4e9-119">Value</span></span>  |<span data-ttu-id="0a4e9-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0a4e9-120">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="0a4e9-121">0x80041008</span><span class="sxs-lookup"><span data-stu-id="0a4e9-121">0x80041008</span></span> | <span data-ttu-id="0a4e9-122">Bir veya daha fazla parametre geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="0a4e9-122">One or more parameters are not valid.</span></span> |
| `WBEM_E_INVALID_DUPLICATE_PARAMETER` | <span data-ttu-id="0a4e9-123">0x80041043</span><span class="sxs-lookup"><span data-stu-id="0a4e9-123">0x80041043</span></span> | <span data-ttu-id="0a4e9-124">`[in, out]` Hem de belirtilen yöntem parametresi *pInSignature* ve *pOutSignature* nesneleri farklı niteleyicileri sahiptir.</span><span class="sxs-lookup"><span data-stu-id="0a4e9-124">The `[in, out]` method parameter specified in both the *pInSignature* and *pOutSignature* objects have different qualifiers.</span></span>
| `WBEM_E_MISSING_PARAMETER_ID` | <span data-ttu-id="0a4e9-125">0x80041036</span><span class="sxs-lookup"><span data-stu-id="0a4e9-125">0x80041036</span></span> | <span data-ttu-id="0a4e9-126">Yöntem parametresi belirtimi eksik **kimliği** niteleyicisi.</span><span class="sxs-lookup"><span data-stu-id="0a4e9-126">A method parameter is missing the specification of the **ID** qualifier.</span></span> |
| `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS` | <span data-ttu-id="0a4e9-127">0x80041038</span><span class="sxs-lookup"><span data-stu-id="0a4e9-127">0x80041038</span></span> | <span data-ttu-id="0a4e9-128">Yöntem parametreleri atanan kimliği seri ardışık değil veya 0'da başlatılmaz.</span><span class="sxs-lookup"><span data-stu-id="0a4e9-128">The ID series that is assigned to the method parameters is not consecutive or does not start at 0.</span></span> |
| `WBEM_E_PARAMETER_ID_ON_RETVAL` | <span data-ttu-id="0a4e9-129">0x80041039</span><span class="sxs-lookup"><span data-stu-id="0a4e9-129">0x80041039</span></span> | <span data-ttu-id="0a4e9-130">Bir yöntemin dönüş değerine sahip bir **kimliği** niteleyicisi.</span><span class="sxs-lookup"><span data-stu-id="0a4e9-130">The return value for a method has an **ID** qualifier.</span></span> |
| `WBEM_E_PROPAGATED_METHOD` | <span data-ttu-id="0a4e9-131">0x80041034</span><span class="sxs-lookup"><span data-stu-id="0a4e9-131">0x80041034</span></span> | <span data-ttu-id="0a4e9-132">Varolan bir yöntem adı bir üst sınıftan yeniden çalışıldı ve imzalar eşleşmedi.</span><span class="sxs-lookup"><span data-stu-id="0a4e9-132">An attempt was made to reuse an existing method name from a parent class, and the signatures did not match.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="0a4e9-133">0</span><span class="sxs-lookup"><span data-stu-id="0a4e9-133">0</span></span> | <span data-ttu-id="0a4e9-134">İşlev çağrısı başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="0a4e9-134">The function call was successful.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="0a4e9-135">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0a4e9-135">Remarks</span></span>

<span data-ttu-id="0a4e9-136">Bu işlev çağrısı sarmalar [IWbemClassObject::PutMethod](https://msdn.microsoft.com/library/aa391456(v=vs.85).aspx) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0a4e9-136">This function wraps a call to the [IWbemClassObject::PutMethod](https://msdn.microsoft.com/library/aa391456(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="0a4e9-137">Bu yöntem çağrısı yalnızca, desteklenen `ptr` bir CIM sınıfı tanımıdır.</span><span class="sxs-lookup"><span data-stu-id="0a4e9-137">This method call is only supported if `ptr` is a CIM class definition.</span></span> <span data-ttu-id="0a4e9-138">Yöntem işleme kullanılabilir değil [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx?f=255&MSPPError=-2147217396) CIM örneklerine noktası işaretçileri.</span><span class="sxs-lookup"><span data-stu-id="0a4e9-138">Method manipulation is not available from [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx?f=255&MSPPError=-2147217396) pointers that point to CIM instances.</span></span>

<span data-ttu-id="0a4e9-139">Kullanıcılar, başlayamaz veya alt çizgiyle bitemez adlarla yöntemleri oluşturamaz.</span><span class="sxs-lookup"><span data-stu-id="0a4e9-139">Users cannot create methods with names that begin or end with an underscore.</span></span> <span data-ttu-id="0a4e9-140">Bu, sistem sınıfları ve özellikleri için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="0a4e9-140">This is reserved for system classes and properties.</span></span>

<span data-ttu-id="0a4e9-141">Bir yöntem için `in` ve `out` parametreleri özellikleri olarak açıklanmıştır [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx?f=255&MSPPError=-2147217396) nesneleri.</span><span class="sxs-lookup"><span data-stu-id="0a4e9-141">For a method, the `in` and `out` parameters are described as properties in [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx?f=255&MSPPError=-2147217396) objects.</span></span>

<span data-ttu-id="0a4e9-142">Bir `[in/out]` parametresi gösterdiği her iki nesnenin aynı özelliği ekleyerek tanımlanabilir `pInSignature` ve `pOutSignature` parametreleri.</span><span class="sxs-lookup"><span data-stu-id="0a4e9-142">An `[in/out]` parameter can be defined by adding the same property to both objects pointed to by the `pInSignature` and `pOutSignature` parameters.</span></span> <span data-ttu-id="0a4e9-143">Bu durumda, aynı özellikleri paylaşır **kimliği** niteleyici değeri.</span><span class="sxs-lookup"><span data-stu-id="0a4e9-143">In this case, the properties share the same **ID** qualifier value.</span></span>

<span data-ttu-id="0a4e9-144">Her bir özellik bir [__Parameters](https://msdn.microsoft.com/library/aa394667(v=vs.85).aspx) nesne dışında sınıfının `ReturnValue` olmalıdır bir **kimliği** Niteleyici, parametreleri görünme sırasını tanımlar sıfır tabanlı bir sayısal değer.</span><span class="sxs-lookup"><span data-stu-id="0a4e9-144">Each property in a [__Parameters](https://msdn.microsoft.com/library/aa394667(v=vs.85).aspx) class object other than `ReturnValue` must have an **ID** qualifier, a zero-based numeric value that identifies the order in which the parameters appear.</span></span> <span data-ttu-id="0a4e9-145">İki parametresi'nın aynı olmayan **kimliği** değeri ve no **kimliği** değeri atlandı.</span><span class="sxs-lookup"><span data-stu-id="0a4e9-145">No two parameters can have the same **ID** value, and no **ID** value can be skipped.</span></span> <span data-ttu-id="0a4e9-146">Her iki durum ortaya çıkarsa, `PutMethod` işlev döndürür `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS`.</span><span class="sxs-lookup"><span data-stu-id="0a4e9-146">If either condition occurs, the `PutMethod` function returns `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS`.</span></span>

## <a name="example"></a><span data-ttu-id="0a4e9-147">Örnek</span><span class="sxs-lookup"><span data-stu-id="0a4e9-147">Example</span></span>

<span data-ttu-id="0a4e9-148">Bir örnek için bkz: [IWbemClassObject::PutMethod](https://msdn.microsoft.com/library/aa391456(v=vs.85).aspx) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0a4e9-148">For an example, see the [IWbemClassObject::PutMethod](https://msdn.microsoft.com/library/aa391456(v=vs.85).aspx) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="0a4e9-149">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0a4e9-149">Requirements</span></span>  
 <span data-ttu-id="0a4e9-150">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0a4e9-150">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a4e9-151">**Başlık:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="0a4e9-151">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="0a4e9-152">**.NET framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="0a4e9-152">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a4e9-153">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0a4e9-153">See also</span></span>  
[<span data-ttu-id="0a4e9-154">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="0a4e9-154">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
