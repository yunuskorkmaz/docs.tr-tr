---
title: "ExecQueryWmi işlevi (yönetilmeyen API Başvurusu)"
description: "ExecQueryWmi işlevi nesneleri almak için bir sorgu yürütür."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: reference
api_name:
- ExecQueryWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- ExecQueryWmi
helpviewer_keywords:
- ExecQueryWmi function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 872109cb0472a8404c492c2867429fe783f898eb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="execquerywmi-function"></a><span data-ttu-id="b7680-103">ExecQueryWmi işlevi</span><span class="sxs-lookup"><span data-stu-id="b7680-103">ExecQueryWmi function</span></span>
<span data-ttu-id="b7680-104">Nesneleri almak için bir sorgu yürütür.</span><span class="sxs-lookup"><span data-stu-id="b7680-104">Executes a query to retrieve objects.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="b7680-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b7680-105">Syntax</span></span>  
  
```  
HRESULT ExecQueryWmi (
   [in] BSTR                    strQueryLanguage,
   [in] BSTR                    strQuery,
   [in] long                    lFlags,
   [in] IWbemContext*           pCtx,
   [out] IEnumWbemClassObject** ppEnum,
   [in] DWORD                   authLevel,
   [in] DWORD                   impLevel,
   [in] IWbemServices*          pCurrentNamespace,
   [in] BSTR                    strUser,
   [in] BSTR                    strPassword,
   [in] BSTR                    strAuthority
); 
```  

## <a name="parameters"></a><span data-ttu-id="b7680-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b7680-106">Parameters</span></span>

`strQueryLanguage`    
<span data-ttu-id="b7680-107">[in] Windows Yönetimi tarafından desteklenen geçerli bir sorgu dili olan bir dize.</span><span class="sxs-lookup"><span data-stu-id="b7680-107">[in] A string with the valid query language supported by Windows Management.</span></span> <span data-ttu-id="b7680-108">WMI Sorgu Dili kısaltması "WQL" olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b7680-108">It must be "WQL", the acronym for WMI Query Language.</span></span>

`strQuery`  
<span data-ttu-id="b7680-109">[in] Sorgu metni.</span><span class="sxs-lookup"><span data-stu-id="b7680-109">[in] The text of the query.</span></span> <span data-ttu-id="b7680-110">Bu parametre olamaz `null`.</span><span class="sxs-lookup"><span data-stu-id="b7680-110">This parameter cannot be `null`.</span></span>

`lFlags`   
<span data-ttu-id="b7680-111">[in] Bu işlev davranışını etkileyen bayrak birleşimi.</span><span class="sxs-lookup"><span data-stu-id="b7680-111">[in] A combination of flags that affect the behavior of this function.</span></span> <span data-ttu-id="b7680-112">Aşağıdaki değerleri tanımlanan *WbemCli.h* üstbilgi dosyası, veya tanımlayabilirsiniz bunları sabitleri kodunuzda:</span><span class="sxs-lookup"><span data-stu-id="b7680-112">The following values are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span> 

| <span data-ttu-id="b7680-113">Sabit</span><span class="sxs-lookup"><span data-stu-id="b7680-113">Constant</span></span> | <span data-ttu-id="b7680-114">Değer</span><span class="sxs-lookup"><span data-stu-id="b7680-114">Value</span></span>  | <span data-ttu-id="b7680-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b7680-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | <span data-ttu-id="b7680-116">0x20000</span><span class="sxs-lookup"><span data-stu-id="b7680-116">0x20000</span></span> | <span data-ttu-id="b7680-117">Geçerli bağlantının yerel yerelleştirilmiş ad alanında depolanan değiştirilen niteleyicileri kümesi, işlevi alır</span><span class="sxs-lookup"><span data-stu-id="b7680-117">If set, the function retrieves the amended qualifiers stored in the localized namespace of the current connection's locale.</span></span> <br/> <span data-ttu-id="b7680-118">Aksi durumda kümesi işlevi yalnızca hemen ad alanında depolanan niteleyicileri alır.</span><span class="sxs-lookup"><span data-stu-id="b7680-118">If not set, the function retrieves only the qualifiers stored in the immediate namespace.</span></span> |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | <span data-ttu-id="b7680-119">0x10</span><span class="sxs-lookup"><span data-stu-id="b7680-119">0x10</span></span> | <span data-ttu-id="b7680-120">Bayrağı yarı zaman uyumlu bir çağrı neden olur.</span><span class="sxs-lookup"><span data-stu-id="b7680-120">The flag causes a semisynchronous call.</span></span> |
| `WBEM_FLAG_FORWARD_ONLY` | <span data-ttu-id="b7680-121">0x20</span><span class="sxs-lookup"><span data-stu-id="b7680-121">0x20</span></span> | <span data-ttu-id="b7680-122">İşlevi yalnızca ileri bir numaralandırıcı döndürür.</span><span class="sxs-lookup"><span data-stu-id="b7680-122">The function returns a forward-only enumerator.</span></span> <span data-ttu-id="b7680-123">Genellikle, yalnızca ileri numaralandırıcılar daha hızlı ve geleneksel numaralandırıcılar daha az bellek kullanır, ancak çağrıları izin verme [kopya](clone.md).</span><span class="sxs-lookup"><span data-stu-id="b7680-123">Typically, forward-only enumerators are faster and use less memory than conventional enumerators, but they do not allow calls to [Clone](clone.md).</span></span> |
| `WBEM_FLAG_BIDIRECTIONAL` | <span data-ttu-id="b7680-124">0</span><span class="sxs-lookup"><span data-stu-id="b7680-124">0</span></span> | <span data-ttu-id="b7680-125">Serbest bırakılana kadar WMI enumration nesnelerine işaretçiler korur.</span><span class="sxs-lookup"><span data-stu-id="b7680-125">WMI retains pointers to objects in the enumration until they are released.</span></span> | 
| `WBEM_FLAG_ENSURE_LOCATABLE` | <span data-ttu-id="b7680-126">0x100</span><span class="sxs-lookup"><span data-stu-id="b7680-126">0x100</span></span> | <span data-ttu-id="b7680-127">Döndürülen herhangi nesneler sahip yeterli bilgi bunları böylece sağlar, Sistem özellikleri gibi **__PATH**, **__RELPATH**, ve **__SERVER**, değil `null`.</span><span class="sxs-lookup"><span data-stu-id="b7680-127">Ensures that any returned objects have enough information in them so that system properties, such as **__PATH**, **__RELPATH**, and **__SERVER**, are not `null`.</span></span> |
| `WBEM_FLAG_PROTOTYPE` | <span data-ttu-id="b7680-128">2</span><span class="sxs-lookup"><span data-stu-id="b7680-128">2</span></span> | <span data-ttu-id="b7680-129">Bu bayrak için prototipi oluşturulurken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b7680-129">This flag is used for prototyping.</span></span> <span data-ttu-id="b7680-130">Sorgu çalıştırma ve bunun yerine normal sonuç nesnesi gibi görünen bir nesne döndürür.</span><span class="sxs-lookup"><span data-stu-id="b7680-130">It does not execute the query and instead returns an object that looks like a typical result object.</span></span> |
| `WBEM_FLAG_DIRECT_READ` | <span data-ttu-id="b7680-131">0x200</span><span class="sxs-lookup"><span data-stu-id="b7680-131">0x200</span></span> | <span data-ttu-id="b7680-132">Nedenler sağlayıcısına erişim kendi üst sınıfı veya alt sınıfların bakılmaksızın belirtilen sınıfı için doğrudan.</span><span class="sxs-lookup"><span data-stu-id="b7680-132">Causes direct access to the provider for the class specified without regard to its parent class or any subclasses.</span></span> |

<span data-ttu-id="b7680-133">Önerilen bayraklar `WBEM_FLAG_RETURN_IMMEDIATELY` ve `WBEM_FLAG_FORWARD_ONLY` en iyi performans için.</span><span class="sxs-lookup"><span data-stu-id="b7680-133">The recommended flags are `WBEM_FLAG_RETURN_IMMEDIATELY` and `WBEM_FLAG_FORWARD_ONLY` for best performance.</span></span>

`pCtx`  
<span data-ttu-id="b7680-134">[in] Bu değer genellikle `null`.</span><span class="sxs-lookup"><span data-stu-id="b7680-134">[in] Typically, this value is `null`.</span></span> <span data-ttu-id="b7680-135">Aksi takdirde, gösteren bir işaretçidir bir [IWbemContext](https://msdn.microsoft.com/library/aa391465(v=vs.85).aspx) istenen sınıfları sağlayarak sağlayıcı tarafından kullanılan örnek.</span><span class="sxs-lookup"><span data-stu-id="b7680-135">Otherwise, it is a pointer to an [IWbemContext](https://msdn.microsoft.com/library/aa391465(v=vs.85).aspx) instance that can be used by the provider that is providing the requested classes.</span></span> 

`ppEnum`  
<span data-ttu-id="b7680-136">[out] Herhangi bir hata oluşursa, sorgunun sonuç kümesinde örnekleri almak arayan verir Numaralandırıcı işaretçisine alır.</span><span class="sxs-lookup"><span data-stu-id="b7680-136">[out] If no error occurs, receives the pointer to the enumerator that allows the caller to retrieve the instances in the query's result set.</span></span> <span data-ttu-id="b7680-137">Sorgu bir sonuç sıfır örnekleriyle kümesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="b7680-137">The query can have a result set with zero instances.</span></span> <span data-ttu-id="b7680-138">Bkz: [açıklamalar](#remarks) daha fazla bilgi için bölüm.</span><span class="sxs-lookup"><span data-stu-id="b7680-138">See the [Remarks](#remarks) section for more information.</span></span>

`authLevel`  
<span data-ttu-id="b7680-139">[in] Kimlik doğrulama düzeyi.</span><span class="sxs-lookup"><span data-stu-id="b7680-139">[in] The authorization level.</span></span>

<span data-ttu-id="b7680-140">`impLevel`[in] Kimliğe bürünme düzeyi.</span><span class="sxs-lookup"><span data-stu-id="b7680-140">`impLevel` [in] The impersonation level.</span></span>

`pCurrentNamespace`   
<span data-ttu-id="b7680-141">[in] Bir işaretçi bir [IWbemServices](https://msdn.microsoft.com/library/aa392093(v=vs.85).aspx) geçerli ad alanını temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="b7680-141">[in] A pointer to an [IWbemServices](https://msdn.microsoft.com/library/aa392093(v=vs.85).aspx) object that represents the current namespace.</span></span>

`strUser`   
<span data-ttu-id="b7680-142">[in] Kullanıcı adı.</span><span class="sxs-lookup"><span data-stu-id="b7680-142">[in] The user name.</span></span> <span data-ttu-id="b7680-143">Bkz: [ConnectServerWmi](connectserverwmi.md) daha fazla bilgi için işlevi.</span><span class="sxs-lookup"><span data-stu-id="b7680-143">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strPassword`   
<span data-ttu-id="b7680-144">[in] Parola.</span><span class="sxs-lookup"><span data-stu-id="b7680-144">[in] The password.</span></span> <span data-ttu-id="b7680-145">Bkz: [ConnectServerWmi](connectserverwmi.md) daha fazla bilgi için işlevi.</span><span class="sxs-lookup"><span data-stu-id="b7680-145">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strAuthority`   
<span data-ttu-id="b7680-146">[in] Kullanıcının etki alanı adı.</span><span class="sxs-lookup"><span data-stu-id="b7680-146">[in] The domain name of the user.</span></span> <span data-ttu-id="b7680-147">Bkz: [ConnectServerWmi](connectserverwmi.md) daha fazla bilgi için işlevi.</span><span class="sxs-lookup"><span data-stu-id="b7680-147">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="b7680-148">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="b7680-148">Return value</span></span>

<span data-ttu-id="b7680-149">Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üstbilgi dosyası, veya tanımlayabilirsiniz bunları sabitleri kodunuzda:</span><span class="sxs-lookup"><span data-stu-id="b7680-149">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="b7680-150">Sabit</span><span class="sxs-lookup"><span data-stu-id="b7680-150">Constant</span></span>  |<span data-ttu-id="b7680-151">Değer</span><span class="sxs-lookup"><span data-stu-id="b7680-151">Value</span></span>  |<span data-ttu-id="b7680-152">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b7680-152">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | <span data-ttu-id="b7680-153">0x80041003</span><span class="sxs-lookup"><span data-stu-id="b7680-153">0x80041003</span></span> | <span data-ttu-id="b7680-154">Kullanıcı, bir veya daha fazla işlev döndürebilir sınıfları görüntüleme izni yok.</span><span class="sxs-lookup"><span data-stu-id="b7680-154">The user does not have permission to view one or more of the classes that the function can return.</span></span> |
| `WBEM_E_FAILED` | <span data-ttu-id="b7680-155">0x80041001</span><span class="sxs-lookup"><span data-stu-id="b7680-155">0x80041001</span></span> | <span data-ttu-id="b7680-156">Belirlenemeyen bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="b7680-156">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="b7680-157">0x80041008</span><span class="sxs-lookup"><span data-stu-id="b7680-157">0x80041008</span></span> | <span data-ttu-id="b7680-158">Parametre geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="b7680-158">A parameter is not valid.</span></span> |
| `WBEM_E_INVALID_QUERY` | <span data-ttu-id="b7680-159">0x80041017</span><span class="sxs-lookup"><span data-stu-id="b7680-159">0x80041017</span></span> | <span data-ttu-id="b7680-160">Sorgu sözdizimi hatası oluştu.</span><span class="sxs-lookup"><span data-stu-id="b7680-160">The query had a syntax error.</span></span> |
| `WBEM_E_INVALID_QUERY_TYPE` | <span data-ttu-id="b7680-161">0x80041018</span><span class="sxs-lookup"><span data-stu-id="b7680-161">0x80041018</span></span> | <span data-ttu-id="b7680-162">İstenen sorgu dili desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="b7680-162">The requested query language is not supported.</span></span> |
| `WBEM_E_QUOTA_VIOLATION` | <span data-ttu-id="b7680-163">0x8004106c</span><span class="sxs-lookup"><span data-stu-id="b7680-163">0x8004106c</span></span> | <span data-ttu-id="b7680-164">Sorgu çok karmaşıktır.</span><span class="sxs-lookup"><span data-stu-id="b7680-164">The query is too complex.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="b7680-165">0x80041006</span><span class="sxs-lookup"><span data-stu-id="b7680-165">0x80041006</span></span> | <span data-ttu-id="b7680-166">İşlemi tamamlamak yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="b7680-166">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_SHUTTING_DOWN` | <span data-ttu-id="b7680-167">0x80041033</span><span class="sxs-lookup"><span data-stu-id="b7680-167">0x80041033</span></span> | <span data-ttu-id="b7680-168">WMI, büyük olasılıkla durduruldu ve yeniden başlatma.</span><span class="sxs-lookup"><span data-stu-id="b7680-168">WMI was probably stopped and restarting.</span></span> <span data-ttu-id="b7680-169">Çağrı [ConnectServerWmi](connectserverwmi.md) yeniden.</span><span class="sxs-lookup"><span data-stu-id="b7680-169">Call [ConnectServerWmi](connectserverwmi.md) again.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="b7680-170">0x80041015</span><span class="sxs-lookup"><span data-stu-id="b7680-170">0x80041015</span></span> | <span data-ttu-id="b7680-171">Geçerli işlem ile WMI arasındaki uzak yordam çağrısı (RPC) bağlantı başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="b7680-171">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="b7680-172">0x80041002</span><span class="sxs-lookup"><span data-stu-id="b7680-172">0x80041002</span></span> | <span data-ttu-id="b7680-173">Sorgu var olmayan bir sınıfı belirtiyor.</span><span class="sxs-lookup"><span data-stu-id="b7680-173">The query specifies a class that does not exist.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="b7680-174">0</span><span class="sxs-lookup"><span data-stu-id="b7680-174">0</span></span> | <span data-ttu-id="b7680-175">İşlev çağrısı başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="b7680-175">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="b7680-176">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b7680-176">Remarks</span></span>

<span data-ttu-id="b7680-177">Bu işlev çağrısı sarmalar [IWbemServices::ExecQuery](https://msdn.microsoft.com/library/aa392107(v=vs.85).aspx) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b7680-177">This function wraps a call to the [IWbemServices::ExecQuery](https://msdn.microsoft.com/library/aa392107(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="b7680-178">Bu işlev belirtilen sorgu işlemleri `strQuery` parametre ve üzerinden çağıran sorgu sonuçlarını erişebileceği bir numaralandırıcı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b7680-178">This function processes the query specified in the `strQuery` parameter and creates an enumerator through which the caller can access the query results.</span></span> <span data-ttu-id="b7680-179">Numaralayıcı gösteren bir işaretçidir bir [IEnumWbemClassObject](https://msdn.microsoft.com/library/aa390857(v=vs.85).aspx) arabirimi; sorgu sonucu olan kullanılabilir hale sınıfı nesnelerinin örneklerini [IWbemClassObject](https://msdn.microsoft.com/library/aa391433(v=vs.85).aspx) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="b7680-179">The enumerator is a pointer to an [IEnumWbemClassObject](https://msdn.microsoft.com/library/aa390857(v=vs.85).aspx) interface; the query results are instances of class objects made available through the [IWbemClassObject](https://msdn.microsoft.com/library/aa391433(v=vs.85).aspx) interface.</span></span>

<span data-ttu-id="b7680-180">Sayısıyla sınırlar vardır `AND` ve `OR` WQL sorguları kullanılabilir anahtar sözcükler.</span><span class="sxs-lookup"><span data-stu-id="b7680-180">There are limits to the number of `AND` and `OR` keywords that can be used in WQL queries.</span></span> <span data-ttu-id="b7680-181">Çok sayıda karmaşık bir sorguda kullanılan WQL anahtar sözcükleri döndürmek WMI neden `WBEM_E_QUOTA_VIOLATION` (veya 0x8004106c) hata kodu olarak bir `HRESULT` değeri.</span><span class="sxs-lookup"><span data-stu-id="b7680-181">Large numbers of WQL keywords used in a complex query can cause WMI to return the `WBEM_E_QUOTA_VIOLATION` (or 0x8004106c) error code as an `HRESULT` value.</span></span> <span data-ttu-id="b7680-182">WQL anahtar sözcükleri sınırını sorgu nasıl karmaşık olduğuna bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="b7680-182">The limit of WQL keywords depends on how complex the query is.</span></span>

<span data-ttu-id="b7680-183">İşlev çağrısı başarısız olursa, çağırarak ek hata bilgileri elde edebileceğiniz [Geterrorınfo](geterrorinfo.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="b7680-183">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="b7680-184">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b7680-184">Requirements</span></span>  
 <span data-ttu-id="b7680-185">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b7680-185">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7680-186">**Başlık:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="b7680-186">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="b7680-187">**.NET framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="b7680-187">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7680-188">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b7680-188">See also</span></span>  
[<span data-ttu-id="b7680-189">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="b7680-189">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
