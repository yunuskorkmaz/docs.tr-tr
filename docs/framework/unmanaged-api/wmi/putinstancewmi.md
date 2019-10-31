---
title: Putınstancewmi işlevi (yönetilmeyen API Başvurusu)
description: Putınstancewmi işlevi, var olan bir sınıfın örneğini oluşturur veya güncelleştirir.
ms.date: 11/06/2017
api_name:
- PutInstanceWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- PutInstanceWmi
helpviewer_keywords:
- PutInstanceWmi function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: b33f31d69c64ce520580c29f1014c058c78d0953
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127348"
---
# <a name="putinstancewmi-function"></a><span data-ttu-id="b490f-103">Putınstancewmi işlevi</span><span class="sxs-lookup"><span data-stu-id="b490f-103">PutInstanceWmi function</span></span>

<span data-ttu-id="b490f-104">Var olan bir sınıfın örneğini oluşturur veya güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="b490f-104">Creates or updates an instance of an existing class.</span></span> <span data-ttu-id="b490f-105">Örnek, WMI deposuna yazılır.</span><span class="sxs-lookup"><span data-stu-id="b490f-105">The instance is written to the WMI repository.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="b490f-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b490f-106">Syntax</span></span>

```cpp
HRESULT PutInstanceWmi (
   [in] IWbemClassObject*    pInst,
   [in] long                 lFlags,
   [in] IWbemContext*        pCtx,
   [out] IWbemCallResult**   ppCallResult
);
```

## <a name="parameters"></a><span data-ttu-id="b490f-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b490f-107">Parameters</span></span>

`pInst`\
<span data-ttu-id="b490f-108">'ndaki Yazılacak örneğe yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b490f-108">[in] A pointer to the instance to be written.</span></span>

`lFlags`\
<span data-ttu-id="b490f-109">'ndaki Bu işlevin davranışını etkileyen bayrakların birleşimi.</span><span class="sxs-lookup"><span data-stu-id="b490f-109">[in] A combination of flags that affect the behavior of this function.</span></span> <span data-ttu-id="b490f-110">Aşağıdaki değerler *Wbemcli. h* üstbilgi dosyasında tanımlanmıştır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="b490f-110">The following values are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="b490f-111">Sabit</span><span class="sxs-lookup"><span data-stu-id="b490f-111">Constant</span></span>  |<span data-ttu-id="b490f-112">Değer</span><span class="sxs-lookup"><span data-stu-id="b490f-112">Value</span></span>  |<span data-ttu-id="b490f-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b490f-113">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | <span data-ttu-id="b490f-114">0x20000</span><span class="sxs-lookup"><span data-stu-id="b490f-114">0x20000</span></span> | <span data-ttu-id="b490f-115">Ayarlanırsa **, WMI değişiklik yapılan Flavor ile** hiçbir niteleyicileri depolamaz.</span><span class="sxs-lookup"><span data-stu-id="b490f-115">If set, WMI does not store any qualifiers with the **Amended** flavor.</span></span> <br> <span data-ttu-id="b490f-116">Ayarlanmamışsa, bu nesnenin yerelleştirilmemiş olduğu varsayılır ve tüm niteleyiciler bu örnekle birlikte depolanır.</span><span class="sxs-lookup"><span data-stu-id="b490f-116">If not set, it is assumed that this object is not localized, and all qualifiers are stored with this instance.</span></span> |
| `WBEM_FLAG_CREATE_OR_UPDATE` | <span data-ttu-id="b490f-117">0</span><span class="sxs-lookup"><span data-stu-id="b490f-117">0</span></span> | <span data-ttu-id="b490f-118">Yoksa örneği oluşturun veya zaten varsa üzerine yazın.</span><span class="sxs-lookup"><span data-stu-id="b490f-118">Create the instance if it does not exist, or overwrite it if it exists already.</span></span> |
| `WBEM_FLAG_UPDATE_ONLY` | <span data-ttu-id="b490f-119">1\.</span><span class="sxs-lookup"><span data-stu-id="b490f-119">1</span></span> | <span data-ttu-id="b490f-120">Örneği güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="b490f-120">Update the instance.</span></span> <span data-ttu-id="b490f-121">Çağrının başarılı olması için örneğin mevcut olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="b490f-121">The instance must exist for the call to be successful.</span></span> |
| `WBEM_FLAG_CREATE_ONLY` | <span data-ttu-id="b490f-122">2</span><span class="sxs-lookup"><span data-stu-id="b490f-122">2</span></span> | <span data-ttu-id="b490f-123">Örneği oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b490f-123">Create the instance.</span></span> <span data-ttu-id="b490f-124">Örnek zaten mevcutsa çağrı başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="b490f-124">The call fails if the instance already exists.</span></span> |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | <span data-ttu-id="b490f-125">0x10</span><span class="sxs-lookup"><span data-stu-id="b490f-125">0x10</span></span> | <span data-ttu-id="b490f-126">Bayrak, yarı zaman uyumlu bir çağrıya neden olur.</span><span class="sxs-lookup"><span data-stu-id="b490f-126">The flag causes a semisynchronous call.</span></span> |

`pCtx`\
<span data-ttu-id="b490f-127">'ndaki Genellikle, bu değer `null`.</span><span class="sxs-lookup"><span data-stu-id="b490f-127">[in] Typically, this value is `null`.</span></span> <span data-ttu-id="b490f-128">Aksi takdirde, istenen sınıfları sağlayan sağlayıcı tarafından kullanılabilen bir [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) örneğine yönelik bir işaretçidir.</span><span class="sxs-lookup"><span data-stu-id="b490f-128">Otherwise, it is a pointer to an [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) instance that can be used by the provider that is providing the requested classes.</span></span>

`ppCallResult`\
<span data-ttu-id="b490f-129">dışı `null`, bu parametre kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="b490f-129">[out] If `null`, this parameter is unused.</span></span> <span data-ttu-id="b490f-130">`lFlags` `WBEM_FLAG_RETURN_IMMEDIATELY`içeriyorsa, işlev hemen `WBEM_S_NO_ERROR`ile döndürür.</span><span class="sxs-lookup"><span data-stu-id="b490f-130">If `lFlags` contains `WBEM_FLAG_RETURN_IMMEDIATELY`, the function returns immediately with `WBEM_S_NO_ERROR`.</span></span> <span data-ttu-id="b490f-131">`ppCallResult` parametresi, yeni bir [ıwbemcallresult](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcallresult) nesnesine bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="b490f-131">The `ppCallResult` parameter receives a pointer to a new [IWbemCallResult](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcallresult) object.</span></span>

## <a name="return-value"></a><span data-ttu-id="b490f-132">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="b490f-132">Return value</span></span>

<span data-ttu-id="b490f-133">Bu işlev tarafından döndürülen aşağıdaki değerler, *Wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="b490f-133">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="b490f-134">Sabit</span><span class="sxs-lookup"><span data-stu-id="b490f-134">Constant</span></span>  |<span data-ttu-id="b490f-135">Değer</span><span class="sxs-lookup"><span data-stu-id="b490f-135">Value</span></span>  |<span data-ttu-id="b490f-136">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b490f-136">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | <span data-ttu-id="b490f-137">0x80041003</span><span class="sxs-lookup"><span data-stu-id="b490f-137">0x80041003</span></span> | <span data-ttu-id="b490f-138">Kullanıcının belirtilen sınıfın bir örneğini güncelleştirme izni yok.</span><span class="sxs-lookup"><span data-stu-id="b490f-138">The user does not have permission to update an instance of the specified class.</span></span> |
| `WBEM_E_FAILED` | <span data-ttu-id="b490f-139">0x80041001</span><span class="sxs-lookup"><span data-stu-id="b490f-139">0x80041001</span></span> | <span data-ttu-id="b490f-140">Belirtilmeyen bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="b490f-140">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_CLASS` | <span data-ttu-id="b490f-141">0x80041010</span><span class="sxs-lookup"><span data-stu-id="b490f-141">0x80041010</span></span> | <span data-ttu-id="b490f-142">Bu örneği destekleyen sınıf geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="b490f-142">The class supporting this instance is not valid.</span></span> |
| `WBEM_E_ILLEGAL_NULL` | <span data-ttu-id="b490f-143">0x80041028</span><span class="sxs-lookup"><span data-stu-id="b490f-143">0x80041028</span></span> | <span data-ttu-id="b490f-144">**dizinli** veya **Not_Null** niteleyicisi tarafından işaretlenen bir özellik gibi, `null`olmayan bir özellik için `null` belirtildi.</span><span class="sxs-lookup"><span data-stu-id="b490f-144">a `null` was specified for a property that cannot be `null`, such as one that is marked by an **Indexed** or **Not_Null** qualifier.</span></span> |
| `WBEM_E_INVALID_OBJECT` | <span data-ttu-id="b490f-145">0x8004100f</span><span class="sxs-lookup"><span data-stu-id="b490f-145">0x8004100f</span></span> | <span data-ttu-id="b490f-146">Belirtilen örnek geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="b490f-146">The specified instance is not valid.</span></span> <span data-ttu-id="b490f-147">(Örneğin, bir sınıfıyla `PutInstanceWmi` çağırmak bu değeri döndürür.)</span><span class="sxs-lookup"><span data-stu-id="b490f-147">(For example, calling `PutInstanceWmi` with a class returns this value.)</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="b490f-148">0x80041008</span><span class="sxs-lookup"><span data-stu-id="b490f-148">0x80041008</span></span> | <span data-ttu-id="b490f-149">Parametre geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="b490f-149">A parameter is not valid.</span></span> |
| `WBEM_E_ALREADY_EXISTS` | <span data-ttu-id="b490f-150">0x80041019</span><span class="sxs-lookup"><span data-stu-id="b490f-150">0x80041019</span></span> | <span data-ttu-id="b490f-151">`WBEM_FLAG_CREATE_ONLY` bayrağı belirtildi, ancak örnek zaten var.</span><span class="sxs-lookup"><span data-stu-id="b490f-151">The `WBEM_FLAG_CREATE_ONLY` flag was specified, but the instance already exists.</span></span> |
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="b490f-152">0x80041002</span><span class="sxs-lookup"><span data-stu-id="b490f-152">0x80041002</span></span> | <span data-ttu-id="b490f-153">`WBEM_FLAG_UPDATE_ONLY` `lFlags`belirtildi, ancak örnek yok.</span><span class="sxs-lookup"><span data-stu-id="b490f-153">`WBEM_FLAG_UPDATE_ONLY` was specified in `lFlags`, but the instance does not exist.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="b490f-154">0x80041006</span><span class="sxs-lookup"><span data-stu-id="b490f-154">0x80041006</span></span> | <span data-ttu-id="b490f-155">İşlemi gerçekleştirmek için yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="b490f-155">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_SHUTTING_DOWN` | <span data-ttu-id="b490f-156">0x80041033</span><span class="sxs-lookup"><span data-stu-id="b490f-156">0x80041033</span></span> | <span data-ttu-id="b490f-157">WMI, büyük olasılıkla durmuş ve yeniden başlatılıyor.</span><span class="sxs-lookup"><span data-stu-id="b490f-157">WMI was probably stopped and restarting.</span></span> <span data-ttu-id="b490f-158">[Connectserverwmi](connectserverwmi.md) ' i yeniden çağırın.</span><span class="sxs-lookup"><span data-stu-id="b490f-158">Call [ConnectServerWmi](connectserverwmi.md) again.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="b490f-159">0x80041015</span><span class="sxs-lookup"><span data-stu-id="b490f-159">0x80041015</span></span> | <span data-ttu-id="b490f-160">Geçerli işlem ve WMI arasındaki uzak yordam çağrısı (RPC) bağlantısı başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="b490f-160">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="b490f-161">0</span><span class="sxs-lookup"><span data-stu-id="b490f-161">0</span></span> | <span data-ttu-id="b490f-162">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="b490f-162">The function call was successful.</span></span> |

## <a name="remarks"></a><span data-ttu-id="b490f-163">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b490f-163">Remarks</span></span>

<span data-ttu-id="b490f-164">Bu işlev, [IWbemServices::P Utınstance](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-putinstance) yöntemine bir çağrı kaydırır.</span><span class="sxs-lookup"><span data-stu-id="b490f-164">This function wraps a call to the [IWbemServices::PutInstance](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-putinstance) method.</span></span>

<span data-ttu-id="b490f-165">`PutInstanceWmi` işlevi örnekleri oluşturmayı ve yalnızca varolan sınıfların örneklerini güncellemeyi destekler.</span><span class="sxs-lookup"><span data-stu-id="b490f-165">The `PutInstanceWmi` function supports creating instances and updating instances of existing classes only.</span></span>  <span data-ttu-id="b490f-166">`pCtx` parametresinin nasıl ayarlandığına bağlı olarak, örneğin özelliklerinin bazıları veya tümü güncellenir.</span><span class="sxs-lookup"><span data-stu-id="b490f-166">Depending on how the `pCtx` parameter is set, either some or all of the properties of the instance are updated.</span></span>

<span data-ttu-id="b490f-167">`pInst` tarafından işaret edilen örnek bir alt sınıfa aitse, Windows yönetimi, alt sınıfın türetildiği sınıflardan sorumlu tüm sağlayıcıları çağırır.</span><span class="sxs-lookup"><span data-stu-id="b490f-167">When the instance pointed to by `pInst` belongs to a subclass, Windows Management calls all the providers responsible for the classes from which the subclass derives.</span></span> <span data-ttu-id="b490f-168">Özgün `PutInstanceWmi` isteğinin başarılı olması için bu sağlayıcıların tümünün başarılı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="b490f-168">All of these providers must succeed for the original `PutInstanceWmi` request to succeed.</span></span> <span data-ttu-id="b490f-169">Hiyerarşide en üstteki sınıfı destekleyen sağlayıcı ilk olarak çağırılır.</span><span class="sxs-lookup"><span data-stu-id="b490f-169">The provider supporting the topmost class in the hierarchy is called first.</span></span> <span data-ttu-id="b490f-170">Arama sırası, en üstteki sınıfın alt sınıfıyla devam eder ve Windows yönetimi, `pInst`tarafından işaret edilen örneğe sahip olan sınıfa ait sağlayıcıya ulaşana kadar yukarıdan aşağıya doğru ilerler.</span><span class="sxs-lookup"><span data-stu-id="b490f-170">The calling order continues with the subclass of the topmost class and proceeds from top to bottom until Windows Management reaches the provider for the class owning the instance pointed to by `pInst`.</span></span>
<span data-ttu-id="b490f-171">Windows yönetimi, bir örneğin alt sınıflarının herhangi biri için sağlayıcıları çağırmaz.</span><span class="sxs-lookup"><span data-stu-id="b490f-171">Windows Management does not call the providers for any of the child classes of an instance.</span></span>

<span data-ttu-id="b490f-172">Bir uygulamanın bir sınıf hiyerarşisine ait bir örneği güncelleştirmesi gerektiğinde `pInst` parametresi, değiştirilecek özellikleri içeren örneğe işaret etmelidir.</span><span class="sxs-lookup"><span data-stu-id="b490f-172">When an application must update an instance that belongs to a class hierarchy, the `pInst` parameter must point to the instance containing the properties to be modified.</span></span> <span data-ttu-id="b490f-173">Diğer bir deyişle, **ClassB**'ye ait bir hedef örneği göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="b490f-173">That is, consider a target instance that belongs to **ClassB**.</span></span> <span data-ttu-id="b490f-174">**ClassB** örneği **ClassA**'Dan türetilir ve **ClassA** , **Propa**özelliğini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b490f-174">The **ClassB** instance derives from **ClassA**, and **ClassA** defines the property **PropA**.</span></span> <span data-ttu-id="b490f-175">Bir uygulama, **ClassB** örneğinde **Propa** değerinde bir değişiklik yapmak Istiyorsa, `pInst` bir **ClassA**örneği yerine bu örneğe ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b490f-175">If an application wants to make a change to the value of **PropA** in the **ClassB** instance, it must set `pInst` to that instance rather than an instance of **ClassA**.</span></span>

<span data-ttu-id="b490f-176">Soyut sınıfın bir örneğinde `PutInstanceWmi` çağırmaya izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="b490f-176">Calling `PutInstanceWmi` on an instance of an abstract class is not allowed.</span></span>

<span data-ttu-id="b490f-177">İşlev çağrısı başarısız olursa, [GetErrorInfo](geterrorinfo.md) işlevini çağırarak ek hata bilgileri alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b490f-177">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="b490f-178">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b490f-178">Requirements</span></span>

<span data-ttu-id="b490f-179">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b490f-179">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="b490f-180">**Üst bilgi:** WMINet_Utils. IDL</span><span class="sxs-lookup"><span data-stu-id="b490f-180">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="b490f-181">**.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="b490f-181">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="b490f-182">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b490f-182">See also</span></span>

- [<span data-ttu-id="b490f-183">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="b490f-183">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
