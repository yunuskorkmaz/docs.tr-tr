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
ms.openlocfilehash: 8edbb8074573b98c017f98197d370c2ad37db80c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726762"
---
# <a name="putmethod-function"></a><span data-ttu-id="0e15c-103">PutMethod işlevi</span><span class="sxs-lookup"><span data-stu-id="0e15c-103">PutMethod function</span></span>

<span data-ttu-id="0e15c-104">Bir yöntem oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0e15c-104">Creates a method.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="0e15c-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="0e15c-105">Syntax</span></span>  
  
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

## <a name="parameters"></a><span data-ttu-id="0e15c-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0e15c-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="0e15c-107">'ndaki Bu parametre kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="0e15c-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="0e15c-108">'ndaki [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneğine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0e15c-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszName`  
<span data-ttu-id="0e15c-109">'ndaki Oluşturulacak yöntemin adı.</span><span class="sxs-lookup"><span data-stu-id="0e15c-109">[in] The name of the method to create.</span></span>

`lFlags`  
<span data-ttu-id="0e15c-110">'ndaki Ayrılamadı.</span><span class="sxs-lookup"><span data-stu-id="0e15c-110">[in] Reserved.</span></span> <span data-ttu-id="0e15c-111">Bu parametre 0 olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0e15c-111">This parameter must be 0.</span></span>

`pSignatureIn`  
<span data-ttu-id="0e15c-112">'ndaki Yöntemi için parametreleri içeren [__Parameters sistem sınıfının](/windows/desktop/WmiSdk/--parameters) kopyasına yönelik bir işaretçi `in` .</span><span class="sxs-lookup"><span data-stu-id="0e15c-112">[in] A pointer to a copy of the [__Parameters system class](/windows/desktop/WmiSdk/--parameters) that contains the `in` parameters for the method.</span></span> <span data-ttu-id="0e15c-113">Olarak ayarlanırsa, bu parametre yoksayılır `null` .</span><span class="sxs-lookup"><span data-stu-id="0e15c-113">This parameter is ignored if set to `null`.</span></span>  

`pSignatureOut`  
<span data-ttu-id="0e15c-114">'ndaki  Yöntemi için parametreleri içeren [__Parameters sistem sınıfının](/windows/desktop/WmiSdk/--parameters) kopyasına yönelik bir işaretçi `out` .</span><span class="sxs-lookup"><span data-stu-id="0e15c-114">[in]  A pointer to a copy of the [__Parameters system class](/windows/desktop/WmiSdk/--parameters) that contains the `out` parameters for the method.</span></span> <span data-ttu-id="0e15c-115">Olarak ayarlanırsa, bu parametre yoksayılır `null` .</span><span class="sxs-lookup"><span data-stu-id="0e15c-115">This parameter is ignored if set to `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="0e15c-116">Döndürülen değer</span><span class="sxs-lookup"><span data-stu-id="0e15c-116">Return value</span></span>

<span data-ttu-id="0e15c-117">Bu işlev tarafından döndürülen aşağıdaki değerler, *Wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="0e15c-117">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="0e15c-118">Sabit</span><span class="sxs-lookup"><span data-stu-id="0e15c-118">Constant</span></span>  |<span data-ttu-id="0e15c-119">Değer</span><span class="sxs-lookup"><span data-stu-id="0e15c-119">Value</span></span>  |<span data-ttu-id="0e15c-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0e15c-120">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="0e15c-121">0x80041008</span><span class="sxs-lookup"><span data-stu-id="0e15c-121">0x80041008</span></span> | <span data-ttu-id="0e15c-122">Bir veya daha fazla parametre geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="0e15c-122">One or more parameters are not valid.</span></span> |
| `WBEM_E_INVALID_DUPLICATE_PARAMETER` | <span data-ttu-id="0e15c-123">0x80041043</span><span class="sxs-lookup"><span data-stu-id="0e15c-123">0x80041043</span></span> | <span data-ttu-id="0e15c-124">`[in, out]`Hem *pinsignature* hem de *poutsignature* nesnelerinde belirtilen method parametresi farklı niteleyicilere sahip.</span><span class="sxs-lookup"><span data-stu-id="0e15c-124">The `[in, out]` method parameter specified in both the *pInSignature* and *pOutSignature* objects have different qualifiers.</span></span>
| `WBEM_E_MISSING_PARAMETER_ID` | <span data-ttu-id="0e15c-125">0x80041036</span><span class="sxs-lookup"><span data-stu-id="0e15c-125">0x80041036</span></span> | <span data-ttu-id="0e15c-126">Yöntem parametresinde **kimlik** niteleyicisi belirtimi eksik.</span><span class="sxs-lookup"><span data-stu-id="0e15c-126">A method parameter is missing the specification of the **ID** qualifier.</span></span> |
| `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS` | <span data-ttu-id="0e15c-127">0x80041038</span><span class="sxs-lookup"><span data-stu-id="0e15c-127">0x80041038</span></span> | <span data-ttu-id="0e15c-128">Yöntem parametrelerine atanan KIMLIK serisi ardışık değildir veya 0 ' dan başlamaz.</span><span class="sxs-lookup"><span data-stu-id="0e15c-128">The ID series that is assigned to the method parameters is not consecutive or does not start at 0.</span></span> |
| `WBEM_E_PARAMETER_ID_ON_RETVAL` | <span data-ttu-id="0e15c-129">0x80041039</span><span class="sxs-lookup"><span data-stu-id="0e15c-129">0x80041039</span></span> | <span data-ttu-id="0e15c-130">Bir yöntemin dönüş değeri bir **kimlik** niteleyicisi içeriyor.</span><span class="sxs-lookup"><span data-stu-id="0e15c-130">The return value for a method has an **ID** qualifier.</span></span> |
| `WBEM_E_PROPAGATED_METHOD` | <span data-ttu-id="0e15c-131">0x80041034</span><span class="sxs-lookup"><span data-stu-id="0e15c-131">0x80041034</span></span> | <span data-ttu-id="0e15c-132">Bir üst sınıftan var olan bir yöntem adının yeniden kullanılması denendi ve imzalar eşleşmedi.</span><span class="sxs-lookup"><span data-stu-id="0e15c-132">An attempt was made to reuse an existing method name from a parent class, and the signatures did not match.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="0e15c-133">0</span><span class="sxs-lookup"><span data-stu-id="0e15c-133">0</span></span> | <span data-ttu-id="0e15c-134">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="0e15c-134">The function call was successful.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="0e15c-135">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0e15c-135">Remarks</span></span>

<span data-ttu-id="0e15c-136">Bu işlev, [IWbemClassObject::P utMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod) yöntemine bir çağrı kaydırır.</span><span class="sxs-lookup"><span data-stu-id="0e15c-136">This function wraps a call to the [IWbemClassObject::PutMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod) method.</span></span>

<span data-ttu-id="0e15c-137">Bu yöntem çağrısı yalnızca `ptr` BIR CIM sınıf tanımınise desteklenir.</span><span class="sxs-lookup"><span data-stu-id="0e15c-137">This method call is only supported if `ptr` is a CIM class definition.</span></span> <span data-ttu-id="0e15c-138">Yöntem işleme, CıM örneklerine işaret eden [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) işaretçilerinden kullanılamıyor.</span><span class="sxs-lookup"><span data-stu-id="0e15c-138">Method manipulation is not available from [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) pointers that point to CIM instances.</span></span>

<span data-ttu-id="0e15c-139">Kullanıcılar alt çizgiyle başlayan veya biten adlara sahip Yöntemler oluşturamaz.</span><span class="sxs-lookup"><span data-stu-id="0e15c-139">Users cannot create methods with names that begin or end with an underscore.</span></span> <span data-ttu-id="0e15c-140">Bu sistem sınıfları ve özellikleri için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="0e15c-140">This is reserved for system classes and properties.</span></span>

<span data-ttu-id="0e15c-141">Bir yöntem için, `in` ve `out` parametreleri [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) nesnelerinde özellikler olarak açıklanır.</span><span class="sxs-lookup"><span data-stu-id="0e15c-141">For a method, the `in` and `out` parameters are described as properties in [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) objects.</span></span>

<span data-ttu-id="0e15c-142">Bir `[in/out]` parametre, ve parametreleri tarafından işaret edilen her iki nesneye aynı özelliği eklenerek tanımlanabilir `pInSignature` `pOutSignature` .</span><span class="sxs-lookup"><span data-stu-id="0e15c-142">An `[in/out]` parameter can be defined by adding the same property to both objects pointed to by the `pInSignature` and `pOutSignature` parameters.</span></span> <span data-ttu-id="0e15c-143">Bu durumda, özellikler aynı **kimlik** niteleyicisi değerini paylaşır.</span><span class="sxs-lookup"><span data-stu-id="0e15c-143">In this case, the properties share the same **ID** qualifier value.</span></span>

<span data-ttu-id="0e15c-144">Farklı bir [__Parameters](/windows/desktop/WmiSdk/--parameters) sınıf nesnesindeki her `ReturnValue` bir özelliğin, parametrelerin göründüğü sırayı belirleyen sıfır tabanlı sayısal bir değer olan bir **ID** niteleyicisi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0e15c-144">Each property in a [__Parameters](/windows/desktop/WmiSdk/--parameters) class object other than `ReturnValue` must have an **ID** qualifier, a zero-based numeric value that identifies the order in which the parameters appear.</span></span> <span data-ttu-id="0e15c-145">İki parametre aynı **kimlik** değerine sahip olamaz ve hiçbir **kimlik** değeri atlanmaz.</span><span class="sxs-lookup"><span data-stu-id="0e15c-145">No two parameters can have the same **ID** value, and no **ID** value can be skipped.</span></span> <span data-ttu-id="0e15c-146">Herhangi bir koşul oluşursa, `PutMethod` işlev döndürür `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS` .</span><span class="sxs-lookup"><span data-stu-id="0e15c-146">If either condition occurs, the `PutMethod` function returns `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS`.</span></span>

## <a name="example"></a><span data-ttu-id="0e15c-147">Örnek</span><span class="sxs-lookup"><span data-stu-id="0e15c-147">Example</span></span>

<span data-ttu-id="0e15c-148">Bir örnek için, bkz. [IWbemClassObject::P utMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0e15c-148">For an example, see the [IWbemClassObject::PutMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="0e15c-149">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0e15c-149">Requirements</span></span>  

 <span data-ttu-id="0e15c-150">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0e15c-150">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e15c-151">**Üst bilgi:** WMINet_Utils. IDL</span><span class="sxs-lookup"><span data-stu-id="0e15c-151">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="0e15c-152">**.NET Framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="0e15c-152">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e15c-153">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0e15c-153">See also</span></span>

- [<span data-ttu-id="0e15c-154">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="0e15c-154">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
