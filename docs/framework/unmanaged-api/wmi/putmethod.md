---
title: PutMethod işlevi (Yönetilmeyen API Başvurusu)
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
ms.openlocfilehash: 93347b7290211b5d62829604678261fdf4da1ec3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174920"
---
# <a name="putmethod-function"></a><span data-ttu-id="dec8b-103">PutMethod fonksiyonu</span><span class="sxs-lookup"><span data-stu-id="dec8b-103">PutMethod function</span></span>
<span data-ttu-id="dec8b-104">Bir yöntem oluşturur.</span><span class="sxs-lookup"><span data-stu-id="dec8b-104">Creates a method.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="dec8b-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dec8b-105">Syntax</span></span>  
  
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

## <a name="parameters"></a><span data-ttu-id="dec8b-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="dec8b-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="dec8b-107">[içinde] Bu parametre kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="dec8b-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="dec8b-108">[içinde] [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneğine işaretçi.</span><span class="sxs-lookup"><span data-stu-id="dec8b-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszName`  
<span data-ttu-id="dec8b-109">[içinde] Oluşturulacak yöntemin adı.</span><span class="sxs-lookup"><span data-stu-id="dec8b-109">[in] The name of the method to create.</span></span>

`lFlags`  
<span data-ttu-id="dec8b-110">[içinde] Saklı -dır.</span><span class="sxs-lookup"><span data-stu-id="dec8b-110">[in] Reserved.</span></span> <span data-ttu-id="dec8b-111">Bu parametre 0 olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="dec8b-111">This parameter must be 0.</span></span>

`pSignatureIn`  
<span data-ttu-id="dec8b-112">[içinde] Yöntem parametrelerini içeren [__Parameters sistem sınıfının](/windows/desktop/WmiSdk/--parameters) `in` bir kopyasına işaretçi.</span><span class="sxs-lookup"><span data-stu-id="dec8b-112">[in] A pointer to a copy of the [__Parameters system class](/windows/desktop/WmiSdk/--parameters) that contains the `in` parameters for the method.</span></span> <span data-ttu-id="dec8b-113">Bu parametre ' olarak `null`ayarlanmışsa yoksayılır</span><span class="sxs-lookup"><span data-stu-id="dec8b-113">This parameter is ignored if set to `null`.</span></span>  

`pSignatureOut`  
<span data-ttu-id="dec8b-114">[içinde]  Yöntem parametrelerini içeren [__Parameters sistem sınıfının](/windows/desktop/WmiSdk/--parameters) `out` bir kopyasına işaretçi.</span><span class="sxs-lookup"><span data-stu-id="dec8b-114">[in]  A pointer to a copy of the [__Parameters system class](/windows/desktop/WmiSdk/--parameters) that contains the `out` parameters for the method.</span></span> <span data-ttu-id="dec8b-115">Bu parametre ' olarak `null`ayarlanmışsa yoksayılır</span><span class="sxs-lookup"><span data-stu-id="dec8b-115">This parameter is ignored if set to `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="dec8b-116">Döndürülen değer</span><span class="sxs-lookup"><span data-stu-id="dec8b-116">Return value</span></span>

<span data-ttu-id="dec8b-117">Bu işlev tarafından döndürülen aşağıdaki değerler *WbemCli.h* üstbilgi dosyasında tanımlanır veya bunları kodunuzdaki sabitler olarak tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="dec8b-117">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="dec8b-118">Sabit</span><span class="sxs-lookup"><span data-stu-id="dec8b-118">Constant</span></span>  |<span data-ttu-id="dec8b-119">Değer</span><span class="sxs-lookup"><span data-stu-id="dec8b-119">Value</span></span>  |<span data-ttu-id="dec8b-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dec8b-120">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="dec8b-121">0x80041008</span><span class="sxs-lookup"><span data-stu-id="dec8b-121">0x80041008</span></span> | <span data-ttu-id="dec8b-122">Bir veya daha fazla parametre geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="dec8b-122">One or more parameters are not valid.</span></span> |
| `WBEM_E_INVALID_DUPLICATE_PARAMETER` | <span data-ttu-id="dec8b-123">0x80041043</span><span class="sxs-lookup"><span data-stu-id="dec8b-123">0x80041043</span></span> | <span data-ttu-id="dec8b-124">Hem `[in, out]` *pInSignature* hem de *pOutSignature* nesnelerinde belirtilen yöntem parametresi farklı niteleyicilere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="dec8b-124">The `[in, out]` method parameter specified in both the *pInSignature* and *pOutSignature* objects have different qualifiers.</span></span>
| `WBEM_E_MISSING_PARAMETER_ID` | <span data-ttu-id="dec8b-125">0x80041036</span><span class="sxs-lookup"><span data-stu-id="dec8b-125">0x80041036</span></span> | <span data-ttu-id="dec8b-126">Bir yöntem parametresi **kimlik** niteleyicisinin belirtimini eksik.</span><span class="sxs-lookup"><span data-stu-id="dec8b-126">A method parameter is missing the specification of the **ID** qualifier.</span></span> |
| `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS` | <span data-ttu-id="dec8b-127">0x80041038</span><span class="sxs-lookup"><span data-stu-id="dec8b-127">0x80041038</span></span> | <span data-ttu-id="dec8b-128">Yöntem parametrelerine atanan kimlik serisi ardışık değildir veya 0'da başlamaz.</span><span class="sxs-lookup"><span data-stu-id="dec8b-128">The ID series that is assigned to the method parameters is not consecutive or does not start at 0.</span></span> |
| `WBEM_E_PARAMETER_ID_ON_RETVAL` | <span data-ttu-id="dec8b-129">0x80041039</span><span class="sxs-lookup"><span data-stu-id="dec8b-129">0x80041039</span></span> | <span data-ttu-id="dec8b-130">Bir yöntemin dönüş değerinin **bir kimlik** niteleyicisi vardır.</span><span class="sxs-lookup"><span data-stu-id="dec8b-130">The return value for a method has an **ID** qualifier.</span></span> |
| `WBEM_E_PROPAGATED_METHOD` | <span data-ttu-id="dec8b-131">0x80041034</span><span class="sxs-lookup"><span data-stu-id="dec8b-131">0x80041034</span></span> | <span data-ttu-id="dec8b-132">Bir üst sınıftan varolan bir yöntem adını yeniden kullanma girişiminde bulunuldu ve imzalar eşleşmedi.</span><span class="sxs-lookup"><span data-stu-id="dec8b-132">An attempt was made to reuse an existing method name from a parent class, and the signatures did not match.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="dec8b-133">0</span><span class="sxs-lookup"><span data-stu-id="dec8b-133">0</span></span> | <span data-ttu-id="dec8b-134">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="dec8b-134">The function call was successful.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="dec8b-135">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dec8b-135">Remarks</span></span>

<span data-ttu-id="dec8b-136">Bu [işlev, IWbemClassObject::PutMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod) yöntemine bir çağrı yıkıyor.</span><span class="sxs-lookup"><span data-stu-id="dec8b-136">This function wraps a call to the [IWbemClassObject::PutMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod) method.</span></span>

<span data-ttu-id="dec8b-137">Bu yöntem çağrısı yalnızca `ptr` CIM sınıf tanımı ise desteklenir.</span><span class="sxs-lookup"><span data-stu-id="dec8b-137">This method call is only supported if `ptr` is a CIM class definition.</span></span> <span data-ttu-id="dec8b-138">Yöntem işleme cim örneklerine işaret [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) işaretçileri kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="dec8b-138">Method manipulation is not available from [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) pointers that point to CIM instances.</span></span>

<span data-ttu-id="dec8b-139">Kullanıcılar, alt puanla başlayan veya biten adlarla yöntem oluşturamaz.</span><span class="sxs-lookup"><span data-stu-id="dec8b-139">Users cannot create methods with names that begin or end with an underscore.</span></span> <span data-ttu-id="dec8b-140">Bu sistem sınıfları ve özellikleri için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="dec8b-140">This is reserved for system classes and properties.</span></span>

<span data-ttu-id="dec8b-141">Bir yöntem `in` için, `out` ve parametreler [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) nesnelerinde özellikler olarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="dec8b-141">For a method, the `in` and `out` parameters are described as properties in [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) objects.</span></span>

<span data-ttu-id="dec8b-142">Parametre, `[in/out]` her iki nesneye `pInSignature` de `pOutSignature` aynı özellik eklenerek tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="dec8b-142">An `[in/out]` parameter can be defined by adding the same property to both objects pointed to by the `pInSignature` and `pOutSignature` parameters.</span></span> <span data-ttu-id="dec8b-143">Bu durumda, özellikler aynı **kimlik** niteleyici değerini paylaşır.</span><span class="sxs-lookup"><span data-stu-id="dec8b-143">In this case, the properties share the same **ID** qualifier value.</span></span>

<span data-ttu-id="dec8b-144">[__Parameters](/windows/desktop/WmiSdk/--parameters) sınıf nesnesindeki `ReturnValue` her özelliğin, parametrelerin görüntülenme sırasını tanımlayan sıfır tabanlı sayısal bir değer olan **kimlik** niteleyicisi olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="dec8b-144">Each property in a [__Parameters](/windows/desktop/WmiSdk/--parameters) class object other than `ReturnValue` must have an **ID** qualifier, a zero-based numeric value that identifies the order in which the parameters appear.</span></span> <span data-ttu-id="dec8b-145">İki parametre aynı **kimlik** değerine sahip olamaz ve **hiçbir kimlik** değeri atlanabilir.</span><span class="sxs-lookup"><span data-stu-id="dec8b-145">No two parameters can have the same **ID** value, and no **ID** value can be skipped.</span></span> <span data-ttu-id="dec8b-146">Her iki durum oluşursa, `PutMethod` işlev döndürür. `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS`</span><span class="sxs-lookup"><span data-stu-id="dec8b-146">If either condition occurs, the `PutMethod` function returns `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS`.</span></span>

## <a name="example"></a><span data-ttu-id="dec8b-147">Örnek</span><span class="sxs-lookup"><span data-stu-id="dec8b-147">Example</span></span>

<span data-ttu-id="dec8b-148">Örneğin, [IWbemClassObject::PutMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod) yöntemine bakın.</span><span class="sxs-lookup"><span data-stu-id="dec8b-148">For an example, see the [IWbemClassObject::PutMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="dec8b-149">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dec8b-149">Requirements</span></span>  
 <span data-ttu-id="dec8b-150">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dec8b-150">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dec8b-151">**Üstbilgi:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="dec8b-151">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="dec8b-152">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="dec8b-152">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dec8b-153">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dec8b-153">See also</span></span>

- [<span data-ttu-id="dec8b-154">WMI ve Performans Sayaçları (Yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="dec8b-154">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
