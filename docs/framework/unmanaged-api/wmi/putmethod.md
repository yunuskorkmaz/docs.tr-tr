---
title: PutMethod işlevi (yönetilmeyen API Başvurusu)
description: PutMethod işlevi bir yöntem oluşturur.
ms.date: 11/06/2017
api_name:
- PutMethod
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- PutMethod
helpviewer_keywords:
- PutMethod function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7f74b0d30a1a8899d3c8d0a2bf0f108ea11165cc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33461863"
---
# <a name="putmethod-function"></a><span data-ttu-id="f9382-103">PutMethod işlevi</span><span class="sxs-lookup"><span data-stu-id="f9382-103">PutMethod function</span></span>
<span data-ttu-id="f9382-104">Bir yöntem oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f9382-104">Creates a method.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="f9382-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f9382-105">Syntax</span></span>  
  
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

## <a name="parameters"></a><span data-ttu-id="f9382-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f9382-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="f9382-107">[in] Bu parametre kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="f9382-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="f9382-108">[in] Bir işaretçi bir [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) örneği.</span><span class="sxs-lookup"><span data-stu-id="f9382-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`wszName`  
<span data-ttu-id="f9382-109">[in] Oluşturmak için yöntemin adı.</span><span class="sxs-lookup"><span data-stu-id="f9382-109">[in] The name of the method to create.</span></span> 

`lFlags`  
<span data-ttu-id="f9382-110">[in] Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="f9382-110">[in] Reserved.</span></span> <span data-ttu-id="f9382-111">Bu parametre 0 olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f9382-111">This parameter must be 0.</span></span>

`pSignatureIn`  
<span data-ttu-id="f9382-112">[in] Bir işaretçi bir kopyasını [__Parameters sistem sınıfı](https://msdn.microsoft.com/library/aa394667(v=vs.85).aspx) içeren `in` yöntemi için parametreler.</span><span class="sxs-lookup"><span data-stu-id="f9382-112">[in] A pointer to a copy of the [__Parameters system class](https://msdn.microsoft.com/library/aa394667(v=vs.85).aspx) that contains the `in` parameters for the method.</span></span> <span data-ttu-id="f9382-113">Bu parametre yoksayılır kümesine `null`.</span><span class="sxs-lookup"><span data-stu-id="f9382-113">This parameter is ignored if set to `null`.</span></span>  

`pSignatureOut`  
<span data-ttu-id="f9382-114">[in]  Bir işaretçi bir kopyasını [__Parameters sistem sınıfı](https://msdn.microsoft.com/library/aa394667(v=vs.85).aspx) içeren `out` yöntemi için parametreler.</span><span class="sxs-lookup"><span data-stu-id="f9382-114">[in]  A pointer to a copy of the [__Parameters system class](https://msdn.microsoft.com/library/aa394667(v=vs.85).aspx) that contains the `out` parameters for the method.</span></span> <span data-ttu-id="f9382-115">Bu parametre yoksayılır kümesine `null`.</span><span class="sxs-lookup"><span data-stu-id="f9382-115">This parameter is ignored if set to `null`.</span></span>
 

## <a name="return-value"></a><span data-ttu-id="f9382-116">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="f9382-116">Return value</span></span>

<span data-ttu-id="f9382-117">Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üstbilgi dosyası, veya tanımlayabilirsiniz bunları sabitleri kodunuzda:</span><span class="sxs-lookup"><span data-stu-id="f9382-117">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="f9382-118">Sabit</span><span class="sxs-lookup"><span data-stu-id="f9382-118">Constant</span></span>  |<span data-ttu-id="f9382-119">Değer</span><span class="sxs-lookup"><span data-stu-id="f9382-119">Value</span></span>  |<span data-ttu-id="f9382-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f9382-120">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="f9382-121">0x80041008</span><span class="sxs-lookup"><span data-stu-id="f9382-121">0x80041008</span></span> | <span data-ttu-id="f9382-122">Bir veya daha fazla parametre geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="f9382-122">One or more parameters are not valid.</span></span> |
| `WBEM_E_INVALID_DUPLICATE_PARAMETER` | <span data-ttu-id="f9382-123">0x80041043</span><span class="sxs-lookup"><span data-stu-id="f9382-123">0x80041043</span></span> | <span data-ttu-id="f9382-124">`[in, out]` Hem de belirtilen yöntem parametresi *pInSignature* ve *pOutSignature* nesneleri farklı niteleyicileri sahiptir.</span><span class="sxs-lookup"><span data-stu-id="f9382-124">The `[in, out]` method parameter specified in both the *pInSignature* and *pOutSignature* objects have different qualifiers.</span></span>
| `WBEM_E_MISSING_PARAMETER_ID` | <span data-ttu-id="f9382-125">0x80041036</span><span class="sxs-lookup"><span data-stu-id="f9382-125">0x80041036</span></span> | <span data-ttu-id="f9382-126">Yöntem parametresi belirtimi eksik **kimliği** niteleyicisi.</span><span class="sxs-lookup"><span data-stu-id="f9382-126">A method parameter is missing the specification of the **ID** qualifier.</span></span> |
| `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS` | <span data-ttu-id="f9382-127">0x80041038</span><span class="sxs-lookup"><span data-stu-id="f9382-127">0x80041038</span></span> | <span data-ttu-id="f9382-128">Yöntem parametreleri atanan kimliği seri ardışık değil veya 0'da başlatılmaz.</span><span class="sxs-lookup"><span data-stu-id="f9382-128">The ID series that is assigned to the method parameters is not consecutive or does not start at 0.</span></span> |
| `WBEM_E_PARAMETER_ID_ON_RETVAL` | <span data-ttu-id="f9382-129">0x80041039</span><span class="sxs-lookup"><span data-stu-id="f9382-129">0x80041039</span></span> | <span data-ttu-id="f9382-130">Bir yöntemin dönüş değerine sahip bir **kimliği** niteleyicisi.</span><span class="sxs-lookup"><span data-stu-id="f9382-130">The return value for a method has an **ID** qualifier.</span></span> |
| `WBEM_E_PROPAGATED_METHOD` | <span data-ttu-id="f9382-131">0x80041034</span><span class="sxs-lookup"><span data-stu-id="f9382-131">0x80041034</span></span> | <span data-ttu-id="f9382-132">Varolan bir yöntem adı bir üst sınıftan yeniden çalışıldı ve imzalar eşleşmedi.</span><span class="sxs-lookup"><span data-stu-id="f9382-132">An attempt was made to reuse an existing method name from a parent class, and the signatures did not match.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="f9382-133">0</span><span class="sxs-lookup"><span data-stu-id="f9382-133">0</span></span> | <span data-ttu-id="f9382-134">İşlev çağrısı başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="f9382-134">The function call was successful.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="f9382-135">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f9382-135">Remarks</span></span>

<span data-ttu-id="f9382-136">Bu işlev çağrısı sarmalar [IWbemClassObject::PutMethod](https://msdn.microsoft.com/library/aa391456(v=vs.85).aspx) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f9382-136">This function wraps a call to the [IWbemClassObject::PutMethod](https://msdn.microsoft.com/library/aa391456(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="f9382-137">Bu yöntem çağrısı yalnızca, desteklenen `ptr` bir CIM sınıfı tanımıdır.</span><span class="sxs-lookup"><span data-stu-id="f9382-137">This method call is only supported if `ptr` is a CIM class definition.</span></span> <span data-ttu-id="f9382-138">Yöntem işleme kullanılabilir değil [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx?f=255&MSPPError=-2147217396) CIM örneklerine noktası işaretçileri.</span><span class="sxs-lookup"><span data-stu-id="f9382-138">Method manipulation is not available from [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx?f=255&MSPPError=-2147217396) pointers that point to CIM instances.</span></span>

<span data-ttu-id="f9382-139">Kullanıcılar, başlayamaz veya alt çizgiyle bitemez adlarla yöntemleri oluşturamaz.</span><span class="sxs-lookup"><span data-stu-id="f9382-139">Users cannot create methods with names that begin or end with an underscore.</span></span> <span data-ttu-id="f9382-140">Bu, sistem sınıfları ve özellikleri için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="f9382-140">This is reserved for system classes and properties.</span></span>

<span data-ttu-id="f9382-141">Bir yöntem için `in` ve `out` parametreleri özellikleri olarak açıklanmıştır [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx?f=255&MSPPError=-2147217396) nesneleri.</span><span class="sxs-lookup"><span data-stu-id="f9382-141">For a method, the `in` and `out` parameters are described as properties in [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx?f=255&MSPPError=-2147217396) objects.</span></span>

<span data-ttu-id="f9382-142">Bir `[in/out]` parametresi gösterdiği her iki nesnenin aynı özelliği ekleyerek tanımlanabilir `pInSignature` ve `pOutSignature` parametreleri.</span><span class="sxs-lookup"><span data-stu-id="f9382-142">An `[in/out]` parameter can be defined by adding the same property to both objects pointed to by the `pInSignature` and `pOutSignature` parameters.</span></span> <span data-ttu-id="f9382-143">Bu durumda, aynı özellikleri paylaşır **kimliği** niteleyici değeri.</span><span class="sxs-lookup"><span data-stu-id="f9382-143">In this case, the properties share the same **ID** qualifier value.</span></span>

<span data-ttu-id="f9382-144">Her bir özellik bir [__Parameters](https://msdn.microsoft.com/library/aa394667(v=vs.85).aspx) nesne dışında sınıfının `ReturnValue` olmalıdır bir **kimliği** Niteleyici, parametreleri görünme sırasını tanımlar sıfır tabanlı bir sayısal değer.</span><span class="sxs-lookup"><span data-stu-id="f9382-144">Each property in a [__Parameters](https://msdn.microsoft.com/library/aa394667(v=vs.85).aspx) class object other than `ReturnValue` must have an **ID** qualifier, a zero-based numeric value that identifies the order in which the parameters appear.</span></span> <span data-ttu-id="f9382-145">İki parametresi'nın aynı olmayan **kimliği** değeri ve no **kimliği** değeri atlandı.</span><span class="sxs-lookup"><span data-stu-id="f9382-145">No two parameters can have the same **ID** value, and no **ID** value can be skipped.</span></span> <span data-ttu-id="f9382-146">Her iki durum ortaya çıkarsa, `PutMethod` işlev döndürür `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS`.</span><span class="sxs-lookup"><span data-stu-id="f9382-146">If either condition occurs, the `PutMethod` function returns `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS`.</span></span>

## <a name="example"></a><span data-ttu-id="f9382-147">Örnek</span><span class="sxs-lookup"><span data-stu-id="f9382-147">Example</span></span>

<span data-ttu-id="f9382-148">Bir örnek için bkz: [IWbemClassObject::PutMethod](https://msdn.microsoft.com/library/aa391456(v=vs.85).aspx) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f9382-148">For an example, see the [IWbemClassObject::PutMethod](https://msdn.microsoft.com/library/aa391456(v=vs.85).aspx) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="f9382-149">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f9382-149">Requirements</span></span>  
 <span data-ttu-id="f9382-150">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f9382-150">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9382-151">**Başlık:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="f9382-151">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="f9382-152">**.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="f9382-152">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9382-153">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f9382-153">See also</span></span>  
[<span data-ttu-id="f9382-154">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="f9382-154">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
