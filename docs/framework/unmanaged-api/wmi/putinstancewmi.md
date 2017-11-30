---
title: "PutInstanceWmi işlevi (yönetilmeyen API Başvurusu)"
description: "PutInstanceWmi işlevi oluşturur veya mevcut bir sınıfın bir örneğini güncelleştirir."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: PutInstanceWmi
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: PutInstanceWmi
helpviewer_keywords: PutInstanceWmi function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b7a4ffce4789fb59d84778d02b41910c974216bd
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/15/2017
---
# <a name="putinstancewmi-function"></a><span data-ttu-id="61166-103">PutInstanceWmi işlevi</span><span class="sxs-lookup"><span data-stu-id="61166-103">PutInstanceWmi function</span></span>
<span data-ttu-id="61166-104">Oluşturur veya mevcut bir sınıfın bir örneğini güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="61166-104">Creates or updates an instance of an existing class.</span></span> <span data-ttu-id="61166-105">Örnek için WMI deposunun yazılır.</span><span class="sxs-lookup"><span data-stu-id="61166-105">The instance is written to the WMI repository.</span></span> 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="61166-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="61166-106">Syntax</span></span>  
  
```  
HRESULT PutInstanceWmi (
   [in] IWbemClassObject*    pInst,
   [in] long                 lFlags,
   [in] IWbemContext*        pCtx,
   [out] IWbemCallResult**   ppCallResult
); 
```  

## <a name="parameters"></a><span data-ttu-id="61166-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="61166-107">Parameters</span></span>

`pInst`    
<span data-ttu-id="61166-108">[in] Writen olmasını örneği için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="61166-108">[in] A pointer to the instance to be writen.</span></span>

`lFlags`   
<span data-ttu-id="61166-109">[in] Bu işlev davranışını etkileyen bayrak birleşimi.</span><span class="sxs-lookup"><span data-stu-id="61166-109">[in] A combination of flags that affect the behavior of this function.</span></span> <span data-ttu-id="61166-110">Aşağıdaki değerleri tanımlanan *WbemCli.h* üstbilgi dosyası, veya tanımlayabilirsiniz bunları sabitleri kodunuzda:</span><span class="sxs-lookup"><span data-stu-id="61166-110">The following values are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span> 

|<span data-ttu-id="61166-111">Sabit</span><span class="sxs-lookup"><span data-stu-id="61166-111">Constant</span></span>  |<span data-ttu-id="61166-112">Değer</span><span class="sxs-lookup"><span data-stu-id="61166-112">Value</span></span>  |<span data-ttu-id="61166-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="61166-113">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | <span data-ttu-id="61166-114">0x20000</span><span class="sxs-lookup"><span data-stu-id="61166-114">0x20000</span></span> | <span data-ttu-id="61166-115">Ayarlama, WMI ile tüm niteleyicileri depolamaz, **Amended** çeşidi.</span><span class="sxs-lookup"><span data-stu-id="61166-115">If set, WMI does not store any qualifiers with the **Amended** flavor.</span></span> </br> <span data-ttu-id="61166-116">Değilse kümesi varsayılır Bu nesne yerelleştirilmemiş ve tüm niteleyiciler storedwith olduğundan bu örnek.</span><span class="sxs-lookup"><span data-stu-id="61166-116">If not set, it is assumed that this object is not localized, and all qualifiers are storedwith this instance.</span></span> |
| `WBEM_FLAG_CREATE_OR_UPDATE` | <span data-ttu-id="61166-117">0</span><span class="sxs-lookup"><span data-stu-id="61166-117">0</span></span> | <span data-ttu-id="61166-118">Bunu yok, veya zaten varsa üzerine örneği oluşturun.</span><span class="sxs-lookup"><span data-stu-id="61166-118">Create the instance if it does not exist, or overwrite it if it exists already.</span></span> |
| `WBEM_FLAG_UPDATE_ONLY` | <span data-ttu-id="61166-119">1.</span><span class="sxs-lookup"><span data-stu-id="61166-119">1</span></span> | <span data-ttu-id="61166-120">Örnek güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="61166-120">Update the instance.</span></span> <span data-ttu-id="61166-121">Örnek çağrı başarılı olması mevcut olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="61166-121">The instance must exist for the call to be successful.</span></span> |
| `WBEM_FLAG_CREATE_ONLY` | <span data-ttu-id="61166-122">2</span><span class="sxs-lookup"><span data-stu-id="61166-122">2</span></span> | <span data-ttu-id="61166-123">Örneği oluşturun.</span><span class="sxs-lookup"><span data-stu-id="61166-123">Create the instance.</span></span> <span data-ttu-id="61166-124">Örneği zaten varsa çağrı başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="61166-124">The call fails if the instance already exists.</span></span> |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | <span data-ttu-id="61166-125">0x10</span><span class="sxs-lookup"><span data-stu-id="61166-125">0x10</span></span> | <span data-ttu-id="61166-126">Bayrağı yarı zaman uyumlu bir çağrı neden olur.</span><span class="sxs-lookup"><span data-stu-id="61166-126">The flag causes a semisynchronous call.</span></span> |

`pCtx`  
<span data-ttu-id="61166-127">[in] Bu değer genellikle `null`.</span><span class="sxs-lookup"><span data-stu-id="61166-127">[in] Typically, this value is `null`.</span></span> <span data-ttu-id="61166-128">Aksi takdirde, gösteren bir işaretçidir bir [IWbemContext](https://msdn.microsoft.com/library/aa391465(v=vs.85).aspx) istenen sınıfları sağlayarak sağlayıcı tarafından kullanılan örnek.</span><span class="sxs-lookup"><span data-stu-id="61166-128">Otherwise, it is a pointer to an [IWbemContext](https://msdn.microsoft.com/library/aa391465(v=vs.85).aspx) instance that can be used by the provider that is providing the requested classes.</span></span> 

`ppCallResult`  
<span data-ttu-id="61166-129">[out] Varsa `null`, bu parametre kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="61166-129">[out] If `null`, this parameter is unused.</span></span> <span data-ttu-id="61166-130">Varsa `lFlags` içeren `WBEM_FLAG_RETURN_IMMEDIATELY`, işlevi ile hemen döndürür `WBEM_S_NO_ERROR`.</span><span class="sxs-lookup"><span data-stu-id="61166-130">If `lFlags` contains `WBEM_FLAG_RETURN_IMMEDIATELY`, the function returns immediately with `WBEM_S_NO_ERROR`.</span></span> <span data-ttu-id="61166-131">`ppCallResult` Parametre alan yeni bir işaretçi [IWbemCallResult](https://msdn.microsoft.com/library/aa391425(v=vs.85).aspx) nesnesi.</span><span class="sxs-lookup"><span data-stu-id="61166-131">The `ppCallResult` parameter receives a pointer to a new [IWbemCallResult](https://msdn.microsoft.com/library/aa391425(v=vs.85).aspx) object.</span></span>

## <a name="return-value"></a><span data-ttu-id="61166-132">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="61166-132">Return value</span></span>

<span data-ttu-id="61166-133">Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üstbilgi dosyası, veya tanımlayabilirsiniz bunları sabitleri kodunuzda:</span><span class="sxs-lookup"><span data-stu-id="61166-133">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="61166-134">Sabit</span><span class="sxs-lookup"><span data-stu-id="61166-134">Constant</span></span>  |<span data-ttu-id="61166-135">Değer</span><span class="sxs-lookup"><span data-stu-id="61166-135">Value</span></span>  |<span data-ttu-id="61166-136">Açıklama</span><span class="sxs-lookup"><span data-stu-id="61166-136">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | <span data-ttu-id="61166-137">0x80041003</span><span class="sxs-lookup"><span data-stu-id="61166-137">0x80041003</span></span> | <span data-ttu-id="61166-138">Kullanıcının belirtilen sınıfının bir örneği güncelleştirme izni yok.</span><span class="sxs-lookup"><span data-stu-id="61166-138">The user does not have permission to update an instance of the specified class.</span></span> |
| `WBEM_E_FAILED` | <span data-ttu-id="61166-139">0x80041001</span><span class="sxs-lookup"><span data-stu-id="61166-139">0x80041001</span></span> | <span data-ttu-id="61166-140">Belirlenemeyen bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="61166-140">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_CLASS` | <span data-ttu-id="61166-141">0x80041010</span><span class="sxs-lookup"><span data-stu-id="61166-141">0x80041010</span></span> | <span data-ttu-id="61166-142">Bu örneğinin destekleyen sınıfı geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="61166-142">The class supporting this instance is not valid.</span></span> |
| `WBEM_E_ILLEGAL_NULL` | <span data-ttu-id="61166-143">0x80041028</span><span class="sxs-lookup"><span data-stu-id="61166-143">0x80041028</span></span> | <span data-ttu-id="61166-144">bir `null` olamayacak bir özellik için belirtilen `null`, tarafından işaretlenen gibi bir **sıralı** veya **Not_Null** niteleyicisi.</span><span class="sxs-lookup"><span data-stu-id="61166-144">a `null` was specified for a property that cannot be `null`, such as one that is marked by an **Indexed** or **Not_Null** qualifier.</span></span> |
| `WBEM_E_INVALID_OBJECT` | <span data-ttu-id="61166-145">0x8004100f</span><span class="sxs-lookup"><span data-stu-id="61166-145">0x8004100f</span></span> | <span data-ttu-id="61166-146">Belirtilen örnek geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="61166-146">The specified instance is not valid.</span></span> <span data-ttu-id="61166-147">(Örneğin, arama `PutInstanceWmi` sınıf ile bu değeri döndürür.)</span><span class="sxs-lookup"><span data-stu-id="61166-147">(For example, calling `PutInstanceWmi` with a class returns this value.)</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="61166-148">0x80041008</span><span class="sxs-lookup"><span data-stu-id="61166-148">0x80041008</span></span> | <span data-ttu-id="61166-149">Parametre geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="61166-149">A parameter is not valid.</span></span> |
| `WBEM_E_ALREADY_EXISTS` | <span data-ttu-id="61166-150">0x80041019</span><span class="sxs-lookup"><span data-stu-id="61166-150">0x80041019</span></span> | <span data-ttu-id="61166-151">`WBEM_FLAG_CREATE_ONLY` Bayrağı belirtildi, ancak örnek zaten var.</span><span class="sxs-lookup"><span data-stu-id="61166-151">The `WBEM_FLAG_CREATE_ONLY` flag was specified, but the instance already exists.</span></span> |
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="61166-152">0x80041002</span><span class="sxs-lookup"><span data-stu-id="61166-152">0x80041002</span></span> | <span data-ttu-id="61166-153">`WBEM_FLAG_UPDATE_ONLY`Belirtilen `lFlags`, ancak örnek yok.</span><span class="sxs-lookup"><span data-stu-id="61166-153">`WBEM_FLAG_UPDATE_ONLY` was specified in `lFlags`, but the instance does not exist.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="61166-154">0x80041006</span><span class="sxs-lookup"><span data-stu-id="61166-154">0x80041006</span></span> | <span data-ttu-id="61166-155">İşlemi tamamlamak yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="61166-155">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_SHUTTING_DOWN` | <span data-ttu-id="61166-156">0x80041033</span><span class="sxs-lookup"><span data-stu-id="61166-156">0x80041033</span></span> | <span data-ttu-id="61166-157">WMI, büyük olasılıkla durduruldu ve yeniden başlatma.</span><span class="sxs-lookup"><span data-stu-id="61166-157">WMI was probably stopped and restarting.</span></span> <span data-ttu-id="61166-158">Çağrı [ConnectServerWmi](connectserverwmi.md) yeniden.</span><span class="sxs-lookup"><span data-stu-id="61166-158">Call [ConnectServerWmi](connectserverwmi.md) again.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="61166-159">0x80041015</span><span class="sxs-lookup"><span data-stu-id="61166-159">0x80041015</span></span> | <span data-ttu-id="61166-160">Geçerli işlem ile WMI arasındaki uzak yordam çağrısı (RPC) bağlantı başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="61166-160">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="61166-161">0</span><span class="sxs-lookup"><span data-stu-id="61166-161">0</span></span> | <span data-ttu-id="61166-162">İşlev çağrısı başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="61166-162">The function call was successful.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="61166-163">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="61166-163">Remarks</span></span>

<span data-ttu-id="61166-164">Bu işlev çağrısı sarmalar [IWbemServices::PutInstance](https://msdn.microsoft.com/library/aa392115(v=vs.85).aspx) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="61166-164">This function wraps a call to the [IWbemServices::PutInstance](https://msdn.microsoft.com/library/aa392115(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="61166-165">`PutInstanceWmi` İşlev örnekleri oluşturma ve mevcut sınıfların örnekleri güncelleştirme destekler.</span><span class="sxs-lookup"><span data-stu-id="61166-165">The `PutInstanceWmi` function supports creating instances and updating instances of existing classes only.</span></span>  <span data-ttu-id="61166-166">Bağlı olarak nasıl `pCtx` parametre olarak ayarlanmışsa, bazı veya tüm özellikleri örneğinin güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="61166-166">Depending on how the `pCtx` parameter is set, either some or all of the properties of the instance are updated.</span></span> 

<span data-ttu-id="61166-167">Ne zaman örneği işaret için tarafından `pInst` bir alt sınıfı Windows Management çağrıları için bir alt türetilen sınıflar sorumlu tüm sağlayıcıları ait.</span><span class="sxs-lookup"><span data-stu-id="61166-167">When the instance pointed to by `pInst` belongs to a subclass, Windows Management calls all the providers responsible for the classes from which the subclass derives.</span></span> <span data-ttu-id="61166-168">Tüm bu sağlayıcıları için özgün başarılı `PutInstanceWmi` başarılı olması için istek.</span><span class="sxs-lookup"><span data-stu-id="61166-168">All of these providers must succeed for the original `PutInstanceWmi` request to succeed.</span></span> <span data-ttu-id="61166-169">Hiyerarşide en üstteki sınıfı destekleyen sağlayıcı önce çağrılır.</span><span class="sxs-lookup"><span data-stu-id="61166-169">The provider supporting the topmost class in the hierarchy is called first.</span></span> <span data-ttu-id="61166-170">Arama sırası en üstteki sınıfın alt ile devam eder ve sağlayıcı gösterdiği örneği sorumlu sınıfı için Windows Yönetim ulaşana kadar üstten alta devam eder `pInst`.</span><span class="sxs-lookup"><span data-stu-id="61166-170">The calling order continues with the subclass of the topmost class and proceeds from top to bottom until Windows Management reaches the provider for the class owning the instance pointed to by `pInst`.</span></span>
<span data-ttu-id="61166-171">Windows Yönetim sağlayıcıları herhangi bir örneğinin alt sınıfların çağırmaz.</span><span class="sxs-lookup"><span data-stu-id="61166-171">Windows Management does not call the providers for any of the child classes of an instance.</span></span> 

<span data-ttu-id="61166-172">Bir sınıf hiyerarşiye ait bir örnek uygulamanın güncelleştirmeniz gerektiğinde `pInst` parametresi değiştirilecek özelliklerini içeren örneğine işaret etmelidir.</span><span class="sxs-lookup"><span data-stu-id="61166-172">When an application must update an instance that belongs to a class hierarchy, the `pInst` parameter must point to the instance containing the properties to be modified.</span></span> <span data-ttu-id="61166-173">Diğer bir deyişle, ait olduğu bir hedef örneği göz önünde bulundurun **ClassB**.</span><span class="sxs-lookup"><span data-stu-id="61166-173">That is, consider a target instance that belongs to **ClassB**.</span></span> <span data-ttu-id="61166-174">**ClassB** örneği türer **ClassA**, ve **ClassA** özelliği tanımlar **PropA**.</span><span class="sxs-lookup"><span data-stu-id="61166-174">The **ClassB** instance derives from **ClassA**, and **ClassA** defines the property **PropA**.</span></span> <span data-ttu-id="61166-175">Bir uygulama değerine değişiklik yapmak isteyip istemediğini **PropA** içinde **ClassB** örneği, onu ayarlamanız gerekir `pInst` örneği yerine bu örnekte **ClassA** .</span><span class="sxs-lookup"><span data-stu-id="61166-175">If an application wants to make a change to the value of **PropA** in the **ClassB** instance, it must set `pInst` to that instance rather than an instance of **ClassA**.</span></span>

<span data-ttu-id="61166-176">Çağırma `PutInstanceWmi` soyut bir sınıf örneği izin verilmiyor.</span><span class="sxs-lookup"><span data-stu-id="61166-176">Calling `PutInstanceWmi` on an instance of an abstract class is not allowed.</span></span>

<span data-ttu-id="61166-177">İşlev çağrısı başarısız olursa, çağırarak ek hata bilgileri elde edebileceğiniz [Geterrorınfo](geterrorinfo.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="61166-177">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="61166-178">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="61166-178">Requirements</span></span>  
 <span data-ttu-id="61166-179">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="61166-179">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61166-180">**Başlık:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="61166-180">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="61166-181">**.NET framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="61166-181">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61166-182">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="61166-182">See also</span></span>  
[<span data-ttu-id="61166-183">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="61166-183">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
