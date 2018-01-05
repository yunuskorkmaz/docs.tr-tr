---
title: "ExecNotificationQueryWmi işlevi (yönetilmeyen API Başvurusu)"
description: "ExecNotificationQueryWmi işlevi olaylarını almak için bir sorgu yürütür."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: ExecNotificationQueryWmi
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: ExecNotificationQueryWmi
helpviewer_keywords: ExecNotificationQueryWmi function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d6dd0926d2262f8d0aa125b86755017a65a95a7f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="execnotificationquerywmi-function"></a><span data-ttu-id="c7a0d-103">ExecNotificationQueryWmi işlevi</span><span class="sxs-lookup"><span data-stu-id="c7a0d-103">ExecNotificationQueryWmi function</span></span>
<span data-ttu-id="c7a0d-104">Olaylarını almak için bir sorgu yürütür.</span><span class="sxs-lookup"><span data-stu-id="c7a0d-104">Executes a query to receive events.</span></span> <span data-ttu-id="c7a0d-105">Çağrı hemen döndürür ve geldikçe çağıran olayları için döndürülen Numaralandırıcı yoklaması.</span><span class="sxs-lookup"><span data-stu-id="c7a0d-105">The call returns immediately, and the caller can poll the returned enumerator for events as they arrive.</span></span> <span data-ttu-id="c7a0d-106">Döndürülen Numaralandırıcı serbest sorguyu iptal eder.</span><span class="sxs-lookup"><span data-stu-id="c7a0d-106">Releasing the returned enumerator cancels the query.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="c7a0d-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c7a0d-107">Syntax</span></span>  
  
```  
HRESULT ExecNotificationQueryWmi (
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

## <a name="parameters"></a><span data-ttu-id="c7a0d-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c7a0d-108">Parameters</span></span>

`strQueryLanguage`    
<span data-ttu-id="c7a0d-109">[in] Windows Yönetimi tarafından desteklenen geçerli bir sorgu dili olan bir dize.</span><span class="sxs-lookup"><span data-stu-id="c7a0d-109">[in] A string with the valid query language supported by Windows Management.</span></span> <span data-ttu-id="c7a0d-110">WMI Sorgu Dili kısaltması "WQL" olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c7a0d-110">It must be "WQL", the acronym for WMI Query Language.</span></span>

`strQuery`  
<span data-ttu-id="c7a0d-111">[in] Sorgu metni.</span><span class="sxs-lookup"><span data-stu-id="c7a0d-111">[in] The text of the query.</span></span> <span data-ttu-id="c7a0d-112">Bu parametre olamaz `null`.</span><span class="sxs-lookup"><span data-stu-id="c7a0d-112">This parameter cannot be `null`.</span></span>

`lFlags`   
<span data-ttu-id="c7a0d-113">[in] Bu işlev davranışını etkileyen aşağıdaki iki bayrak birleşimi.</span><span class="sxs-lookup"><span data-stu-id="c7a0d-113">[in] A combination of the following two flags that affect the behavior of this function.</span></span> <span data-ttu-id="c7a0d-114">Bu değerleri tanımlanan *WbemCli.h* üstbilgi dosyası, veya tanımlayabilirsiniz bunları sabitleri kodunuzda.</span><span class="sxs-lookup"><span data-stu-id="c7a0d-114">These values are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span> 

| <span data-ttu-id="c7a0d-115">Sabit</span><span class="sxs-lookup"><span data-stu-id="c7a0d-115">Constant</span></span> | <span data-ttu-id="c7a0d-116">Değer</span><span class="sxs-lookup"><span data-stu-id="c7a0d-116">Value</span></span>  | <span data-ttu-id="c7a0d-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c7a0d-117">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_RETURN_IMMEDIATELY` | <span data-ttu-id="c7a0d-118">0x10</span><span class="sxs-lookup"><span data-stu-id="c7a0d-118">0x10</span></span> | <span data-ttu-id="c7a0d-119">Bayrağı yarı zaman uyumlu bir çağrı neden olur.</span><span class="sxs-lookup"><span data-stu-id="c7a0d-119">The flag causes a semisynchronous call.</span></span> <span data-ttu-id="c7a0d-120">Bu bayrak ayarlanmazsa, çağrı başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="c7a0d-120">If this flag is not set, the call fails.</span></span> <span data-ttu-id="c7a0d-121">Olayları sürekli olarak alınan kullanıcı döndürülen Numaralandırıcı yoklaması gerekir yani olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="c7a0d-121">This is because events are received continuously, which means the user must poll the returned enumerator.</span></span> <span data-ttu-id="c7a0d-122">Bu çağrı süresiz olarak engelleme, mümkün kılar.</span><span class="sxs-lookup"><span data-stu-id="c7a0d-122">Blocking this call indefinitely makes that impossible.</span></span> |
| `WBEM_FLAG_FORWARD_ONLY` | <span data-ttu-id="c7a0d-123">0x20</span><span class="sxs-lookup"><span data-stu-id="c7a0d-123">0x20</span></span> | <span data-ttu-id="c7a0d-124">İşlevi yalnızca ileri bir numaralandırıcı döndürür.</span><span class="sxs-lookup"><span data-stu-id="c7a0d-124">The function returns a forward-only enumerator.</span></span> <span data-ttu-id="c7a0d-125">Genellikle, yalnızca ileri numaralandırıcılar daha hızlı ve geleneksel numaralandırıcılar daha az bellek kullanır, ancak çağrıları izin verme [kopya](clone.md).</span><span class="sxs-lookup"><span data-stu-id="c7a0d-125">Typically, forward-only enumerators are faster and use less memory than conventional enumerators, but they do not allow calls to [Clone](clone.md).</span></span> |

`pCtx`  
<span data-ttu-id="c7a0d-126">[in] Bu değer genellikle `null`.</span><span class="sxs-lookup"><span data-stu-id="c7a0d-126">[in] Typically, this value is `null`.</span></span> <span data-ttu-id="c7a0d-127">Aksi takdirde, gösteren bir işaretçidir bir [IWbemContext](https://msdn.microsoft.com/library/aa391465(v=vs.85).aspx) istenen olaylar sağlayarak sağlayıcı tarafından kullanılan örnek.</span><span class="sxs-lookup"><span data-stu-id="c7a0d-127">Otherwise, it is a pointer to an [IWbemContext](https://msdn.microsoft.com/library/aa391465(v=vs.85).aspx) instance that can be used by the provider that is providing the requested events.</span></span> 

`ppEnum`  
<span data-ttu-id="c7a0d-128">[out] Herhangi bir hata oluşursa, sorgunun sonuç kümesinde örnekleri almak arayan verir Numaralandırıcı işaretçisine alır.</span><span class="sxs-lookup"><span data-stu-id="c7a0d-128">[out] If no error occurs, receives the pointer to the enumerator that allows the caller to retrieve the instances in the query's result set.</span></span> <span data-ttu-id="c7a0d-129">Bkz: [açıklamalar](#remarks) daha fazla bilgi için bölüm.</span><span class="sxs-lookup"><span data-stu-id="c7a0d-129">See the [Remarks](#remarks) section for more information.</span></span>

`authLevel`  
<span data-ttu-id="c7a0d-130">[in] Kimlik doğrulama düzeyi.</span><span class="sxs-lookup"><span data-stu-id="c7a0d-130">[in] The authorization level.</span></span>

<span data-ttu-id="c7a0d-131">`impLevel`[in] Kimliğe bürünme düzeyi.</span><span class="sxs-lookup"><span data-stu-id="c7a0d-131">`impLevel` [in] The impersonation level.</span></span>

`pCurrentNamespace`   
<span data-ttu-id="c7a0d-132">[in] Bir işaretçi bir [IWbemServices](https://msdn.microsoft.com/library/aa392093(v=vs.85).aspx) geçerli ad alanını temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="c7a0d-132">[in] A pointer to an [IWbemServices](https://msdn.microsoft.com/library/aa392093(v=vs.85).aspx) object that represents the current namespace.</span></span>

`strUser`   
<span data-ttu-id="c7a0d-133">[in] Kullanıcı adı.</span><span class="sxs-lookup"><span data-stu-id="c7a0d-133">[in] The user name.</span></span> <span data-ttu-id="c7a0d-134">Bkz: [ConnectServerWmi](connectserverwmi.md) daha fazla bilgi için işlevi.</span><span class="sxs-lookup"><span data-stu-id="c7a0d-134">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strPassword`   
<span data-ttu-id="c7a0d-135">[in] Parola.</span><span class="sxs-lookup"><span data-stu-id="c7a0d-135">[in] The password.</span></span> <span data-ttu-id="c7a0d-136">Bkz: [ConnectServerWmi](connectserverwmi.md) daha fazla bilgi için işlevi.</span><span class="sxs-lookup"><span data-stu-id="c7a0d-136">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strAuthority`   
<span data-ttu-id="c7a0d-137">[in] Kullanıcının etki alanı adı.</span><span class="sxs-lookup"><span data-stu-id="c7a0d-137">[in] The domain name of the user.</span></span> <span data-ttu-id="c7a0d-138">Bkz: [ConnectServerWmi](connectserverwmi.md) daha fazla bilgi için işlevi.</span><span class="sxs-lookup"><span data-stu-id="c7a0d-138">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="c7a0d-139">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="c7a0d-139">Return value</span></span>

<span data-ttu-id="c7a0d-140">Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üstbilgi dosyası, veya tanımlayabilirsiniz bunları sabitleri kodunuzda:</span><span class="sxs-lookup"><span data-stu-id="c7a0d-140">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="c7a0d-141">Sabit</span><span class="sxs-lookup"><span data-stu-id="c7a0d-141">Constant</span></span>  |<span data-ttu-id="c7a0d-142">Değer</span><span class="sxs-lookup"><span data-stu-id="c7a0d-142">Value</span></span>  |<span data-ttu-id="c7a0d-143">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c7a0d-143">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | <span data-ttu-id="c7a0d-144">0x80041003</span><span class="sxs-lookup"><span data-stu-id="c7a0d-144">0x80041003</span></span> | <span data-ttu-id="c7a0d-145">Kullanıcı, bir veya daha fazla işlev döndürebilir sınıfları görüntüleme izni yok.</span><span class="sxs-lookup"><span data-stu-id="c7a0d-145">The user does not have permission to view one or more of the classes that the function can return.</span></span> |
| `WBEM_E_FAILED` | <span data-ttu-id="c7a0d-146">0x80041001</span><span class="sxs-lookup"><span data-stu-id="c7a0d-146">0x80041001</span></span> | <span data-ttu-id="c7a0d-147">Belirlenemeyen bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="c7a0d-147">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="c7a0d-148">0x80041008</span><span class="sxs-lookup"><span data-stu-id="c7a0d-148">0x80041008</span></span> | <span data-ttu-id="c7a0d-149">Parametre geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="c7a0d-149">A parameter is not valid.</span></span> |
| `WBEM_E_INVALID_CLASS` | <span data-ttu-id="c7a0d-150">0x80041010</span><span class="sxs-lookup"><span data-stu-id="c7a0d-150">0x80041010</span></span> | <span data-ttu-id="c7a0d-151">Sorgu var olmayan bir sınıfı belirtiyor.</span><span class="sxs-lookup"><span data-stu-id="c7a0d-151">The query specifies a class that does not exist.</span></span> |
| `WBEMESS_E_REGISTRATION_TOO_PRECISE` | <span data-ttu-id="c7a0d-152">0x80042002</span><span class="sxs-lookup"><span data-stu-id="c7a0d-152">0x80042002</span></span> | <span data-ttu-id="c7a0d-153">Çok fazla kesinlik olayların teslimini istendi.</span><span class="sxs-lookup"><span data-stu-id="c7a0d-153">Too much precision in delivery of events has been requested.</span></span> <span data-ttu-id="c7a0d-154">Daha büyük bir yoklama dayanıklılık belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="c7a0d-154">A larger polling tolerance must be specified.</span></span> |
| `WBEMESS_E_REGISTRATION_TOO_BROAD` | <span data-ttu-id="c7a0d-155">0x80042001</span><span class="sxs-lookup"><span data-stu-id="c7a0d-155">0x80042001</span></span> | <span data-ttu-id="c7a0d-156">Sorgu requess Windows yönetimi daha fazla bilgi sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="c7a0d-156">The query requess more information than Windows Management can provide.</span></span> <span data-ttu-id="c7a0d-157">Bu `HRESULT` bir ad alanındaki tüm nesneleri yoklamak için bir istek bir olay sorgusu sonuçları döndürülür.</span><span class="sxs-lookup"><span data-stu-id="c7a0d-157">This `HRESULT` is returned when an event query results in a request to poll all objects in a namespace.</span></span> |
| `WBEM_E_INVALID_QUERY` | <span data-ttu-id="c7a0d-158">0x80041017</span><span class="sxs-lookup"><span data-stu-id="c7a0d-158">0x80041017</span></span> | <span data-ttu-id="c7a0d-159">Sorgu sözdizimi hatası oluştu.</span><span class="sxs-lookup"><span data-stu-id="c7a0d-159">The query had a syntax error.</span></span> |
| `WBEM_E_INVALID_QUERY_TYPE` | <span data-ttu-id="c7a0d-160">0x80041018</span><span class="sxs-lookup"><span data-stu-id="c7a0d-160">0x80041018</span></span> | <span data-ttu-id="c7a0d-161">İstenen sorgu dili desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="c7a0d-161">The requested query language is not supported.</span></span> |
| `WBEM_E_QUOTA_VIOLATION` | <span data-ttu-id="c7a0d-162">0x8004106c</span><span class="sxs-lookup"><span data-stu-id="c7a0d-162">0x8004106c</span></span> | <span data-ttu-id="c7a0d-163">Sorgu çok karmaşıktır.</span><span class="sxs-lookup"><span data-stu-id="c7a0d-163">The query is too complex.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="c7a0d-164">0x80041006</span><span class="sxs-lookup"><span data-stu-id="c7a0d-164">0x80041006</span></span> | <span data-ttu-id="c7a0d-165">İşlemi tamamlamak yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="c7a0d-165">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_SHUTTING_DOWN` | <span data-ttu-id="c7a0d-166">0x80041033</span><span class="sxs-lookup"><span data-stu-id="c7a0d-166">0x80041033</span></span> | <span data-ttu-id="c7a0d-167">WMI, büyük olasılıkla durduruldu ve yeniden başlatma.</span><span class="sxs-lookup"><span data-stu-id="c7a0d-167">WMI was probably stopped and restarting.</span></span> <span data-ttu-id="c7a0d-168">Çağrı [ConnectServerWmi](connectserverwmi.md) yeniden.</span><span class="sxs-lookup"><span data-stu-id="c7a0d-168">Call [ConnectServerWmi](connectserverwmi.md) again.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="c7a0d-169">0x80041015</span><span class="sxs-lookup"><span data-stu-id="c7a0d-169">0x80041015</span></span> | <span data-ttu-id="c7a0d-170">Geçerli işlem ile WMI arasındaki uzak yordam çağrısı (RPC) bağlantı başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="c7a0d-170">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
| `WBEM_E_UNPARSABLE_QUERY` | <span data-ttu-id="c7a0d-171">0x80041058</span><span class="sxs-lookup"><span data-stu-id="c7a0d-171">0x80041058</span></span> | <span data-ttu-id="c7a0d-172">Sorgu ayrıştırılamıyor.</span><span class="sxs-lookup"><span data-stu-id="c7a0d-172">The query cannot be parsed.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="c7a0d-173">0</span><span class="sxs-lookup"><span data-stu-id="c7a0d-173">0</span></span> | <span data-ttu-id="c7a0d-174">İşlev çağrısı başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="c7a0d-174">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="c7a0d-175">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c7a0d-175">Remarks</span></span>

<span data-ttu-id="c7a0d-176">Bu işlev çağrısı sarmalar [IWbemServices::ExecNotificationQuery](https://msdn.microsoft.com/library/aa392105(v=vs.85).aspx) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c7a0d-176">This function wraps a call to the [IWbemServices::ExecNotificationQuery](https://msdn.microsoft.com/library/aa392105(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="c7a0d-177">Arayan düzenli aralıklarla işlevi döndükten sonra döndürülen geçirir. `ppEnum` nesnesini [sonraki](next.md) herhangi bir olayı kullanılabilir olup olmadığını görmek için işlev.</span><span class="sxs-lookup"><span data-stu-id="c7a0d-177">After the function returns, the caller periodically passes the returned `ppEnum` object to the [Next](next.md) function to see if any events are available.</span></span>

<span data-ttu-id="c7a0d-178">Sayısıyla sınırlar vardır `AND` ve `OR` WQL sorguları kullanılabilir anahtar sözcükler.</span><span class="sxs-lookup"><span data-stu-id="c7a0d-178">There are limits to the number of `AND` and `OR` keywords that can be used in WQL queries.</span></span> <span data-ttu-id="c7a0d-179">Çok sayıda karmaşık bir sorguda kullanılan WQL anahtar sözcükleri döndürmek WMI neden `WBEM_E_QUOTA_VIOLATION` (veya 0x8004106c) hata kodu olarak bir `HRESULT` değeri.</span><span class="sxs-lookup"><span data-stu-id="c7a0d-179">Large numbers of WQL keywords used in a complex query can cause WMI to return the `WBEM_E_QUOTA_VIOLATION` (or 0x8004106c) error code as an `HRESULT` value.</span></span> <span data-ttu-id="c7a0d-180">WQL anahtar sözcükleri sınırını sorgu nasıl karmaşık olduğuna bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="c7a0d-180">The limit of WQL keywords depends on how complex the query is.</span></span>

<span data-ttu-id="c7a0d-181">İşlev çağrısı başarısız olursa, çağırarak ek hata bilgileri elde edebileceğiniz [Geterrorınfo](geterrorinfo.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="c7a0d-181">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="c7a0d-182">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c7a0d-182">Requirements</span></span>  
 <span data-ttu-id="c7a0d-183">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c7a0d-183">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7a0d-184">**Başlık:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="c7a0d-184">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="c7a0d-185">**.NET framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="c7a0d-185">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7a0d-186">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c7a0d-186">See also</span></span>  
[<span data-ttu-id="c7a0d-187">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="c7a0d-187">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
