---
title: PutInstanceWmi işlevi (yönetilmeyen API Başvurusu)
description: PutInstanceWmi işlevi oluşturur veya mevcut bir sınıfın bir örneğini güncelleştirir.
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 67abf017040b9e6bbe9b10e560c8d57c124ae84e
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45743311"
---
# <a name="putinstancewmi-function"></a><span data-ttu-id="2c9dd-103">PutInstanceWmi işlevi</span><span class="sxs-lookup"><span data-stu-id="2c9dd-103">PutInstanceWmi function</span></span>
<span data-ttu-id="2c9dd-104">Oluşturur veya mevcut bir sınıfın bir örneğini güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="2c9dd-104">Creates or updates an instance of an existing class.</span></span> <span data-ttu-id="2c9dd-105">Örneği, WMI deposuna yazılır.</span><span class="sxs-lookup"><span data-stu-id="2c9dd-105">The instance is written to the WMI repository.</span></span> 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="2c9dd-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2c9dd-106">Syntax</span></span>  
  
```  
HRESULT PutInstanceWmi (
   [in] IWbemClassObject*    pInst,
   [in] long                 lFlags,
   [in] IWbemContext*        pCtx,
   [out] IWbemCallResult**   ppCallResult
); 
```  

## <a name="parameters"></a><span data-ttu-id="2c9dd-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2c9dd-107">Parameters</span></span>

`pInst`    
<span data-ttu-id="2c9dd-108">[in] Writen olmasını örneğine bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="2c9dd-108">[in] A pointer to the instance to be writen.</span></span>

`lFlags`   
<span data-ttu-id="2c9dd-109">[in] Bu işlevin davranışını etkileyen bayrakların birleşimi.</span><span class="sxs-lookup"><span data-stu-id="2c9dd-109">[in] A combination of flags that affect the behavior of this function.</span></span> <span data-ttu-id="2c9dd-110">Aşağıdaki değerleri tanımlanan *WbemCli.h* üst bilgi dosyası veya tanımlayabilirsiniz bunları sabitleri kodunuzda:</span><span class="sxs-lookup"><span data-stu-id="2c9dd-110">The following values are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span> 

|<span data-ttu-id="2c9dd-111">Sabit</span><span class="sxs-lookup"><span data-stu-id="2c9dd-111">Constant</span></span>  |<span data-ttu-id="2c9dd-112">Değer</span><span class="sxs-lookup"><span data-stu-id="2c9dd-112">Value</span></span>  |<span data-ttu-id="2c9dd-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2c9dd-113">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | <span data-ttu-id="2c9dd-114">0x20000</span><span class="sxs-lookup"><span data-stu-id="2c9dd-114">0x20000</span></span> | <span data-ttu-id="2c9dd-115">Ayarlanırsa, WMI ile ilgili tüm niteleyicileri depolamaz, **Amended** çeşidi.</span><span class="sxs-lookup"><span data-stu-id="2c9dd-115">If set, WMI does not store any qualifiers with the **Amended** flavor.</span></span> </br> <span data-ttu-id="2c9dd-116">Aksi durumda, küme bu nesne yerelleştirilmez ve tüm niteleyicileri storedwith başladığınız varsayılır Bu örneği.</span><span class="sxs-lookup"><span data-stu-id="2c9dd-116">If not set, it is assumed that this object is not localized, and all qualifiers are storedwith this instance.</span></span> |
| `WBEM_FLAG_CREATE_OR_UPDATE` | <span data-ttu-id="2c9dd-117">0</span><span class="sxs-lookup"><span data-stu-id="2c9dd-117">0</span></span> | <span data-ttu-id="2c9dd-118">Olmayan mevcut veya zaten varsa üzerine örneği oluşturun.</span><span class="sxs-lookup"><span data-stu-id="2c9dd-118">Create the instance if it does not exist, or overwrite it if it exists already.</span></span> |
| `WBEM_FLAG_UPDATE_ONLY` | <span data-ttu-id="2c9dd-119">1.</span><span class="sxs-lookup"><span data-stu-id="2c9dd-119">1</span></span> | <span data-ttu-id="2c9dd-120">Örnek güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="2c9dd-120">Update the instance.</span></span> <span data-ttu-id="2c9dd-121">Örnek çağrı başarılı olması mevcut olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="2c9dd-121">The instance must exist for the call to be successful.</span></span> |
| `WBEM_FLAG_CREATE_ONLY` | <span data-ttu-id="2c9dd-122">2</span><span class="sxs-lookup"><span data-stu-id="2c9dd-122">2</span></span> | <span data-ttu-id="2c9dd-123">Örneği oluşturun.</span><span class="sxs-lookup"><span data-stu-id="2c9dd-123">Create the instance.</span></span> <span data-ttu-id="2c9dd-124">Örneği zaten varsa başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="2c9dd-124">The call fails if the instance already exists.</span></span> |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | <span data-ttu-id="2c9dd-125">0x10</span><span class="sxs-lookup"><span data-stu-id="2c9dd-125">0x10</span></span> | <span data-ttu-id="2c9dd-126">Bayrağı yarı zaman uyumsuz bir çağrı neden olur.</span><span class="sxs-lookup"><span data-stu-id="2c9dd-126">The flag causes a semisynchronous call.</span></span> |

`pCtx`  
<span data-ttu-id="2c9dd-127">[in] Genellikle, bu değer, `null`.</span><span class="sxs-lookup"><span data-stu-id="2c9dd-127">[in] Typically, this value is `null`.</span></span> <span data-ttu-id="2c9dd-128">Aksi takdirde, bir işaretçi olduğu bir [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) istenen sınıfları sağlayan sağlayıcı tarafından kullanılan bir örnek.</span><span class="sxs-lookup"><span data-stu-id="2c9dd-128">Otherwise, it is a pointer to an [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) instance that can be used by the provider that is providing the requested classes.</span></span> 

`ppCallResult`  
<span data-ttu-id="2c9dd-129">[out] Varsa `null`, bu parametre kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="2c9dd-129">[out] If `null`, this parameter is unused.</span></span> <span data-ttu-id="2c9dd-130">Varsa `lFlags` içeren `WBEM_FLAG_RETURN_IMMEDIATELY`, işlev ile hemen döndürür. `WBEM_S_NO_ERROR`.</span><span class="sxs-lookup"><span data-stu-id="2c9dd-130">If `lFlags` contains `WBEM_FLAG_RETURN_IMMEDIATELY`, the function returns immediately with `WBEM_S_NO_ERROR`.</span></span> <span data-ttu-id="2c9dd-131">`ppCallResult` Parametre bir işaretçi yeni bir alan [IWbemCallResult](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcallresult) nesne.</span><span class="sxs-lookup"><span data-stu-id="2c9dd-131">The `ppCallResult` parameter receives a pointer to a new [IWbemCallResult](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcallresult) object.</span></span>

## <a name="return-value"></a><span data-ttu-id="2c9dd-132">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="2c9dd-132">Return value</span></span>

<span data-ttu-id="2c9dd-133">Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üst bilgi dosyası veya tanımlayabilirsiniz bunları sabitleri kodunuzda:</span><span class="sxs-lookup"><span data-stu-id="2c9dd-133">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="2c9dd-134">Sabit</span><span class="sxs-lookup"><span data-stu-id="2c9dd-134">Constant</span></span>  |<span data-ttu-id="2c9dd-135">Değer</span><span class="sxs-lookup"><span data-stu-id="2c9dd-135">Value</span></span>  |<span data-ttu-id="2c9dd-136">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2c9dd-136">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | <span data-ttu-id="2c9dd-137">0x80041003</span><span class="sxs-lookup"><span data-stu-id="2c9dd-137">0x80041003</span></span> | <span data-ttu-id="2c9dd-138">Kullanıcının belirtilen sınıfın bir örneği güncelleştirme izni yok.</span><span class="sxs-lookup"><span data-stu-id="2c9dd-138">The user does not have permission to update an instance of the specified class.</span></span> |
| `WBEM_E_FAILED` | <span data-ttu-id="2c9dd-139">0x80041001</span><span class="sxs-lookup"><span data-stu-id="2c9dd-139">0x80041001</span></span> | <span data-ttu-id="2c9dd-140">Belirtilmeyen bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="2c9dd-140">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_CLASS` | <span data-ttu-id="2c9dd-141">0x80041010</span><span class="sxs-lookup"><span data-stu-id="2c9dd-141">0x80041010</span></span> | <span data-ttu-id="2c9dd-142">Bu örneğinin destekleyen sınıf geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="2c9dd-142">The class supporting this instance is not valid.</span></span> |
| `WBEM_E_ILLEGAL_NULL` | <span data-ttu-id="2c9dd-143">0x80041028</span><span class="sxs-lookup"><span data-stu-id="2c9dd-143">0x80041028</span></span> | <span data-ttu-id="2c9dd-144">bir `null` edilemeyecek bir özelliği için belirtilen `null`, tarafından işaretlenen bir gibi bir **sıralı** veya **Not_Null** niteleyicisi.</span><span class="sxs-lookup"><span data-stu-id="2c9dd-144">a `null` was specified for a property that cannot be `null`, such as one that is marked by an **Indexed** or **Not_Null** qualifier.</span></span> |
| `WBEM_E_INVALID_OBJECT` | <span data-ttu-id="2c9dd-145">0x8004100f</span><span class="sxs-lookup"><span data-stu-id="2c9dd-145">0x8004100f</span></span> | <span data-ttu-id="2c9dd-146">Belirtilen örnek geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="2c9dd-146">The specified instance is not valid.</span></span> <span data-ttu-id="2c9dd-147">(Örneğin, çağırma `PutInstanceWmi` bir sınıf ile bu değeri döndürür.)</span><span class="sxs-lookup"><span data-stu-id="2c9dd-147">(For example, calling `PutInstanceWmi` with a class returns this value.)</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="2c9dd-148">0x80041008</span><span class="sxs-lookup"><span data-stu-id="2c9dd-148">0x80041008</span></span> | <span data-ttu-id="2c9dd-149">Bir parametre geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="2c9dd-149">A parameter is not valid.</span></span> |
| `WBEM_E_ALREADY_EXISTS` | <span data-ttu-id="2c9dd-150">0x80041019</span><span class="sxs-lookup"><span data-stu-id="2c9dd-150">0x80041019</span></span> | <span data-ttu-id="2c9dd-151">`WBEM_FLAG_CREATE_ONLY` Bayrağı belirtildi, ancak örnek zaten mevcut.</span><span class="sxs-lookup"><span data-stu-id="2c9dd-151">The `WBEM_FLAG_CREATE_ONLY` flag was specified, but the instance already exists.</span></span> |
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="2c9dd-152">0x80041002</span><span class="sxs-lookup"><span data-stu-id="2c9dd-152">0x80041002</span></span> | <span data-ttu-id="2c9dd-153">`WBEM_FLAG_UPDATE_ONLY` Belirtilen `lFlags`, ancak örneği yok.</span><span class="sxs-lookup"><span data-stu-id="2c9dd-153">`WBEM_FLAG_UPDATE_ONLY` was specified in `lFlags`, but the instance does not exist.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="2c9dd-154">0x80041006</span><span class="sxs-lookup"><span data-stu-id="2c9dd-154">0x80041006</span></span> | <span data-ttu-id="2c9dd-155">İşlemi tamamlamak yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="2c9dd-155">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_SHUTTING_DOWN` | <span data-ttu-id="2c9dd-156">0x80041033</span><span class="sxs-lookup"><span data-stu-id="2c9dd-156">0x80041033</span></span> | <span data-ttu-id="2c9dd-157">WMI, büyük olasılıkla durdu ve yeniden başlatılıyor.</span><span class="sxs-lookup"><span data-stu-id="2c9dd-157">WMI was probably stopped and restarting.</span></span> <span data-ttu-id="2c9dd-158">Çağrı [ConnectServerWmi](connectserverwmi.md) yeniden.</span><span class="sxs-lookup"><span data-stu-id="2c9dd-158">Call [ConnectServerWmi](connectserverwmi.md) again.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="2c9dd-159">0x80041015</span><span class="sxs-lookup"><span data-stu-id="2c9dd-159">0x80041015</span></span> | <span data-ttu-id="2c9dd-160">Geçerli işlem WMI arasındaki uzak yordam çağrısı (RPC) bağlantı başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="2c9dd-160">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="2c9dd-161">0</span><span class="sxs-lookup"><span data-stu-id="2c9dd-161">0</span></span> | <span data-ttu-id="2c9dd-162">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="2c9dd-162">The function call was successful.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="2c9dd-163">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2c9dd-163">Remarks</span></span>

<span data-ttu-id="2c9dd-164">Bu işlev bir çağrı sarılır [IWbemServices::PutInstance](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-putinstance) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="2c9dd-164">This function wraps a call to the [IWbemServices::PutInstance](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-putinstance) method.</span></span>

<span data-ttu-id="2c9dd-165">`PutInstanceWmi` İşlev örnekleri oluşturma ve güncelleştirme yalnızca mevcut sınıfların örneklerini destekler.</span><span class="sxs-lookup"><span data-stu-id="2c9dd-165">The `PutInstanceWmi` function supports creating instances and updating instances of existing classes only.</span></span>  <span data-ttu-id="2c9dd-166">Bağlı olarak nasıl `pCtx` parametresi olarak ayarlanmışsa, bazı veya tüm özelliklerini örneğinin güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="2c9dd-166">Depending on how the `pCtx` parameter is set, either some or all of the properties of the instance are updated.</span></span> 

<span data-ttu-id="2c9dd-167">Ne zaman örneği tarafından işaret edilen `pInst` bir alt sınıfı için Windows Yönetim alt sınıfın türetildiği sınıfların için sorumlu tüm sağlayıcıları çağrıları ait.</span><span class="sxs-lookup"><span data-stu-id="2c9dd-167">When the instance pointed to by `pInst` belongs to a subclass, Windows Management calls all the providers responsible for the classes from which the subclass derives.</span></span> <span data-ttu-id="2c9dd-168">Tüm bu sağlayıcıları için özgün başarılı olması gerektiği `PutInstanceWmi` başarılı olması için istek.</span><span class="sxs-lookup"><span data-stu-id="2c9dd-168">All of these providers must succeed for the original `PutInstanceWmi` request to succeed.</span></span> <span data-ttu-id="2c9dd-169">Hiyerarşideki en üst sınıf destekleyen sağlayıcı önce çağrılır.</span><span class="sxs-lookup"><span data-stu-id="2c9dd-169">The provider supporting the topmost class in the hierarchy is called first.</span></span> <span data-ttu-id="2c9dd-170">Arama sırası üstteki sınıfının alt ile devam eder ve sağlayıcı işaret ettiği örneğine sahip olan sınıf için Windows Yönetim ulaşana kadar üstten alta geçer `pInst`.</span><span class="sxs-lookup"><span data-stu-id="2c9dd-170">The calling order continues with the subclass of the topmost class and proceeds from top to bottom until Windows Management reaches the provider for the class owning the instance pointed to by `pInst`.</span></span>
<span data-ttu-id="2c9dd-171">Windows yönetimi sağlayıcıları herhangi bir alt sınıfı örneğinin çağırmaz.</span><span class="sxs-lookup"><span data-stu-id="2c9dd-171">Windows Management does not call the providers for any of the child classes of an instance.</span></span> 

<span data-ttu-id="2c9dd-172">Bir sınıf hiyerarşisine ait bir örnek uygulamanın güncelleştirmeniz gerektiğinde `pInst` parametresi değiştirilecek özellikleri içeren örneğine işaret etmelidir.</span><span class="sxs-lookup"><span data-stu-id="2c9dd-172">When an application must update an instance that belongs to a class hierarchy, the `pInst` parameter must point to the instance containing the properties to be modified.</span></span> <span data-ttu-id="2c9dd-173">Diğer bir deyişle, ait bir hedef örneği göz önünde bulundurun **Sınıfb**.</span><span class="sxs-lookup"><span data-stu-id="2c9dd-173">That is, consider a target instance that belongs to **ClassB**.</span></span> <span data-ttu-id="2c9dd-174">**Sınıfb** örneği türetilir **Türetilme**, ve **Türetilme** özelliği tanımlar **PropA**.</span><span class="sxs-lookup"><span data-stu-id="2c9dd-174">The **ClassB** instance derives from **ClassA**, and **ClassA** defines the property **PropA**.</span></span> <span data-ttu-id="2c9dd-175">Bir uygulama değerinde bir değişiklik isteyip istemediği **PropA** içinde **Sınıfb** örneği, onu ayarlamanız gerekir `pInst` örneği yerine bu örneği **Türetilme** .</span><span class="sxs-lookup"><span data-stu-id="2c9dd-175">If an application wants to make a change to the value of **PropA** in the **ClassB** instance, it must set `pInst` to that instance rather than an instance of **ClassA**.</span></span>

<span data-ttu-id="2c9dd-176">Çağırma `PutInstanceWmi` soyut bir sınıf örneği üzerinde izin verilmiyor.</span><span class="sxs-lookup"><span data-stu-id="2c9dd-176">Calling `PutInstanceWmi` on an instance of an abstract class is not allowed.</span></span>

<span data-ttu-id="2c9dd-177">İşlev çağrısı başarısız olursa, ek hata bilgileri çağırarak elde edebileceğiniz [Geterrorınfo](geterrorinfo.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="2c9dd-177">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="2c9dd-178">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2c9dd-178">Requirements</span></span>  
 <span data-ttu-id="2c9dd-179">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2c9dd-179">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c9dd-180">**Başlık:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="2c9dd-180">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="2c9dd-181">**.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="2c9dd-181">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c9dd-182">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2c9dd-182">See also</span></span>  
[<span data-ttu-id="2c9dd-183">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="2c9dd-183">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
