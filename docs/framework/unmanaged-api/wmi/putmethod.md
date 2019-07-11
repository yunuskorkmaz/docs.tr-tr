---
title: PutMethod işlevi (yönetilmeyen API Başvurusu)
description: PutMethod işlevi, bir metot oluşturur.
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
ms.openlocfilehash: 0ca510f30f0f38ae54eb83046b0e9d5541db882d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67758682"
---
# <a name="putmethod-function"></a><span data-ttu-id="7f7ea-103">PutMethod işlevi</span><span class="sxs-lookup"><span data-stu-id="7f7ea-103">PutMethod function</span></span>
<span data-ttu-id="7f7ea-104">Bir metot oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7f7ea-104">Creates a method.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="7f7ea-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7f7ea-105">Syntax</span></span>  
  
```cpp  
HRESULT PutMethod (
   [in] int                vFunc, 
   [in] IWbemClassObject*  ptr, 
   [in] LPCWSTR            wszName,
   [in] LONG               lFlags,
   [in] IWbemClassObject*  pInSignature,
   [in] IWbemClassObject*  pOutSignature
); 
```  

## <a name="parameters"></a><span data-ttu-id="7f7ea-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7f7ea-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="7f7ea-107">[in] Bu parametre kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="7f7ea-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="7f7ea-108">[in] Bir işaretçi bir [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneği.</span><span class="sxs-lookup"><span data-stu-id="7f7ea-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszName`  
<span data-ttu-id="7f7ea-109">[in] Oluşturmak için yöntemin adı.</span><span class="sxs-lookup"><span data-stu-id="7f7ea-109">[in] The name of the method to create.</span></span> 

`lFlags`  
<span data-ttu-id="7f7ea-110">[in] Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="7f7ea-110">[in] Reserved.</span></span> <span data-ttu-id="7f7ea-111">Bu parametre 0 olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7f7ea-111">This parameter must be 0.</span></span>

`pSignatureIn`  
<span data-ttu-id="7f7ea-112">[in] Bir kopyasını bir işaretçiye [__Parameters sistem sınıfı](/windows/desktop/WmiSdk/--parameters) içeren `in` yönteminin parametreleri.</span><span class="sxs-lookup"><span data-stu-id="7f7ea-112">[in] A pointer to a copy of the [__Parameters system class](/windows/desktop/WmiSdk/--parameters) that contains the `in` parameters for the method.</span></span> <span data-ttu-id="7f7ea-113">Bu parametre yoksayılır kümesine `null`.</span><span class="sxs-lookup"><span data-stu-id="7f7ea-113">This parameter is ignored if set to `null`.</span></span>  

`pSignatureOut`  
<span data-ttu-id="7f7ea-114">[in]  Bir kopyasını bir işaretçiye [__Parameters sistem sınıfı](/windows/desktop/WmiSdk/--parameters) içeren `out` yönteminin parametreleri.</span><span class="sxs-lookup"><span data-stu-id="7f7ea-114">[in]  A pointer to a copy of the [__Parameters system class](/windows/desktop/WmiSdk/--parameters) that contains the `out` parameters for the method.</span></span> <span data-ttu-id="7f7ea-115">Bu parametre yoksayılır kümesine `null`.</span><span class="sxs-lookup"><span data-stu-id="7f7ea-115">This parameter is ignored if set to `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="7f7ea-116">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="7f7ea-116">Return value</span></span>

<span data-ttu-id="7f7ea-117">Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üst bilgi dosyası veya tanımlayabilirsiniz bunları sabitleri kodunuzda:</span><span class="sxs-lookup"><span data-stu-id="7f7ea-117">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="7f7ea-118">Sabit</span><span class="sxs-lookup"><span data-stu-id="7f7ea-118">Constant</span></span>  |<span data-ttu-id="7f7ea-119">Değer</span><span class="sxs-lookup"><span data-stu-id="7f7ea-119">Value</span></span>  |<span data-ttu-id="7f7ea-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7f7ea-120">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="7f7ea-121">0x80041008</span><span class="sxs-lookup"><span data-stu-id="7f7ea-121">0x80041008</span></span> | <span data-ttu-id="7f7ea-122">Bir veya daha fazla parametre geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="7f7ea-122">One or more parameters are not valid.</span></span> |
| `WBEM_E_INVALID_DUPLICATE_PARAMETER` | <span data-ttu-id="7f7ea-123">0x80041043</span><span class="sxs-lookup"><span data-stu-id="7f7ea-123">0x80041043</span></span> | <span data-ttu-id="7f7ea-124">`[in, out]` Hem de belirtilen yöntem parametresi *pInSignature* ve *pOutSignature* nesneleri farklı niteleyicileri sahiptir.</span><span class="sxs-lookup"><span data-stu-id="7f7ea-124">The `[in, out]` method parameter specified in both the *pInSignature* and *pOutSignature* objects have different qualifiers.</span></span>
| `WBEM_E_MISSING_PARAMETER_ID` | <span data-ttu-id="7f7ea-125">0x80041036</span><span class="sxs-lookup"><span data-stu-id="7f7ea-125">0x80041036</span></span> | <span data-ttu-id="7f7ea-126">Bir yöntem parametresi belirtimi eksik **kimliği** niteleyicisi.</span><span class="sxs-lookup"><span data-stu-id="7f7ea-126">A method parameter is missing the specification of the **ID** qualifier.</span></span> |
| `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS` | <span data-ttu-id="7f7ea-127">0x80041038</span><span class="sxs-lookup"><span data-stu-id="7f7ea-127">0x80041038</span></span> | <span data-ttu-id="7f7ea-128">Yöntem parametreleri için atanan kimliği serisi ardışık değil veya 0'da başlamaz.</span><span class="sxs-lookup"><span data-stu-id="7f7ea-128">The ID series that is assigned to the method parameters is not consecutive or does not start at 0.</span></span> |
| `WBEM_E_PARAMETER_ID_ON_RETVAL` | <span data-ttu-id="7f7ea-129">0x80041039</span><span class="sxs-lookup"><span data-stu-id="7f7ea-129">0x80041039</span></span> | <span data-ttu-id="7f7ea-130">Bir yöntemin dönüş değerine sahip bir **kimliği** niteleyicisi.</span><span class="sxs-lookup"><span data-stu-id="7f7ea-130">The return value for a method has an **ID** qualifier.</span></span> |
| `WBEM_E_PROPAGATED_METHOD` | <span data-ttu-id="7f7ea-131">0x80041034</span><span class="sxs-lookup"><span data-stu-id="7f7ea-131">0x80041034</span></span> | <span data-ttu-id="7f7ea-132">Varolan bir yöntem adı bir üst sınıftan yeniden kullanmak için bir girişimde bulunuldu ve imzalar eşleşmez.</span><span class="sxs-lookup"><span data-stu-id="7f7ea-132">An attempt was made to reuse an existing method name from a parent class, and the signatures did not match.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="7f7ea-133">0</span><span class="sxs-lookup"><span data-stu-id="7f7ea-133">0</span></span> | <span data-ttu-id="7f7ea-134">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="7f7ea-134">The function call was successful.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="7f7ea-135">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7f7ea-135">Remarks</span></span>

<span data-ttu-id="7f7ea-136">Bu işlev bir çağrı sarılır [IWbemClassObject::PutMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="7f7ea-136">This function wraps a call to the [IWbemClassObject::PutMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod) method.</span></span>

<span data-ttu-id="7f7ea-137">Bu yöntem çağrısı, yalnızca desteklenen `ptr` bir CIM sınıfı tanımıdır.</span><span class="sxs-lookup"><span data-stu-id="7f7ea-137">This method call is only supported if `ptr` is a CIM class definition.</span></span> <span data-ttu-id="7f7ea-138">Yöntem işleme kullanılabilir değil [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) CIM örneklerine işaret eden işaretçilerin.</span><span class="sxs-lookup"><span data-stu-id="7f7ea-138">Method manipulation is not available from [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) pointers that point to CIM instances.</span></span>

<span data-ttu-id="7f7ea-139">Kullanıcılar, başlayamaz veya bir alt çizgiyle bitemez adlara sahip yöntemleri oluşturamaz.</span><span class="sxs-lookup"><span data-stu-id="7f7ea-139">Users cannot create methods with names that begin or end with an underscore.</span></span> <span data-ttu-id="7f7ea-140">Bu, sistem sınıfları ve özellikleri için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="7f7ea-140">This is reserved for system classes and properties.</span></span>

<span data-ttu-id="7f7ea-141">Bir yöntem için `in` ve `out` özellikleri olarak parametreler açıklanmıştır [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) nesneleri.</span><span class="sxs-lookup"><span data-stu-id="7f7ea-141">For a method, the `in` and `out` parameters are described as properties in [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) objects.</span></span>

<span data-ttu-id="7f7ea-142">Bir `[in/out]` parametresinin işaret ettiği her iki nesnenin aynı özellik ekleyerek tanımlanabilir `pInSignature` ve `pOutSignature` parametreleri.</span><span class="sxs-lookup"><span data-stu-id="7f7ea-142">An `[in/out]` parameter can be defined by adding the same property to both objects pointed to by the `pInSignature` and `pOutSignature` parameters.</span></span> <span data-ttu-id="7f7ea-143">Bu durumda, aynı özellikleri paylaşır **kimliği** niteleyici değeri.</span><span class="sxs-lookup"><span data-stu-id="7f7ea-143">In this case, the properties share the same **ID** qualifier value.</span></span>

<span data-ttu-id="7f7ea-144">Her bir özellik bir [__Parameters](/windows/desktop/WmiSdk/--parameters) dışındaki nesne sınıfının `ReturnValue` olmalıdır bir **kimliği** niteleyicisi, parametreleri görünme sırasını belirleyen sıfır tabanlı bir sayısal değer.</span><span class="sxs-lookup"><span data-stu-id="7f7ea-144">Each property in a [__Parameters](/windows/desktop/WmiSdk/--parameters) class object other than `ReturnValue` must have an **ID** qualifier, a zero-based numeric value that identifies the order in which the parameters appear.</span></span> <span data-ttu-id="7f7ea-145">İki parametre aynı olabilir **kimliği** değeri ve Hayır **kimliği** değeri atlanacak.</span><span class="sxs-lookup"><span data-stu-id="7f7ea-145">No two parameters can have the same **ID** value, and no **ID** value can be skipped.</span></span> <span data-ttu-id="7f7ea-146">Her iki durum ortaya çıkarsa, `PutMethod` işlevinin döndürdükleriyle `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS`.</span><span class="sxs-lookup"><span data-stu-id="7f7ea-146">If either condition occurs, the `PutMethod` function returns `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS`.</span></span>

## <a name="example"></a><span data-ttu-id="7f7ea-147">Örnek</span><span class="sxs-lookup"><span data-stu-id="7f7ea-147">Example</span></span>

<span data-ttu-id="7f7ea-148">Bir örnek için bkz. [IWbemClassObject::PutMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="7f7ea-148">For an example, see the [IWbemClassObject::PutMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="7f7ea-149">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7f7ea-149">Requirements</span></span>  
 <span data-ttu-id="7f7ea-150">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7f7ea-150">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f7ea-151">**Üst bilgi:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="7f7ea-151">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="7f7ea-152">**.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="7f7ea-152">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f7ea-153">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7f7ea-153">See also</span></span>

- [<span data-ttu-id="7f7ea-154">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="7f7ea-154">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
