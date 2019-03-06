---
title: ExecQueryWmi işlevi (yönetilmeyen API Başvurusu)
description: ExecQueryWmi işlevi nesneleri almak için bir sorgu yürütür.
ms.date: 11/06/2017
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
ms.openlocfilehash: 402bbcb9ad5e462a55c5ec2716417f512f03ee19
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57373224"
---
# <a name="execquerywmi-function"></a><span data-ttu-id="90ae1-103">ExecQueryWmi işlevi</span><span class="sxs-lookup"><span data-stu-id="90ae1-103">ExecQueryWmi function</span></span>

<span data-ttu-id="90ae1-104">Nesneleri almak için bir sorgu yürütür.</span><span class="sxs-lookup"><span data-stu-id="90ae1-104">Executes a query to retrieve objects.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="90ae1-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="90ae1-105">Syntax</span></span>

```cpp
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

## <a name="parameters"></a><span data-ttu-id="90ae1-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="90ae1-106">Parameters</span></span>

`strQueryLanguage`\
<span data-ttu-id="90ae1-107">[in] Windows Management tarafından desteklenen geçerli bir sorgu dili olan bir dize.</span><span class="sxs-lookup"><span data-stu-id="90ae1-107">[in] A string with the valid query language supported by Windows Management.</span></span> <span data-ttu-id="90ae1-108">WMI Sorgu Dili kısaltması "WQL" olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="90ae1-108">It must be "WQL", the acronym for WMI Query Language.</span></span>

`strQuery`\
<span data-ttu-id="90ae1-109">[in] Sorgu metni.</span><span class="sxs-lookup"><span data-stu-id="90ae1-109">[in] The text of the query.</span></span> <span data-ttu-id="90ae1-110">Bu parametre olamaz `null`.</span><span class="sxs-lookup"><span data-stu-id="90ae1-110">This parameter cannot be `null`.</span></span>

`lFlags`\
<span data-ttu-id="90ae1-111">[in] Bu işlevin davranışını etkileyen bayrakların birleşimi.</span><span class="sxs-lookup"><span data-stu-id="90ae1-111">[in] A combination of flags that affect the behavior of this function.</span></span> <span data-ttu-id="90ae1-112">Aşağıdaki değerleri tanımlanan *WbemCli.h* üst bilgi dosyası veya tanımlayabilirsiniz bunları sabitleri kodunuzda:</span><span class="sxs-lookup"><span data-stu-id="90ae1-112">The following values are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

| <span data-ttu-id="90ae1-113">Sabit</span><span class="sxs-lookup"><span data-stu-id="90ae1-113">Constant</span></span> | <span data-ttu-id="90ae1-114">Değer</span><span class="sxs-lookup"><span data-stu-id="90ae1-114">Value</span></span>  | <span data-ttu-id="90ae1-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="90ae1-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | <span data-ttu-id="90ae1-116">0x20000</span><span class="sxs-lookup"><span data-stu-id="90ae1-116">0x20000</span></span> | <span data-ttu-id="90ae1-117">Geçerli bağlantının yerel yerelleştirilmiş ad alanında depolanan değiştirilen niteleyicileri işlev kümesini alır</span><span class="sxs-lookup"><span data-stu-id="90ae1-117">If set, the function retrieves the amended qualifiers stored in the localized namespace of the current connection's locale.</span></span> <br/> <span data-ttu-id="90ae1-118">Aksi durumda, küme yalnızca anında ad alanında depolanan niteleyicileri işlevi alır.</span><span class="sxs-lookup"><span data-stu-id="90ae1-118">If not set, the function retrieves only the qualifiers stored in the immediate namespace.</span></span> |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | <span data-ttu-id="90ae1-119">0x10</span><span class="sxs-lookup"><span data-stu-id="90ae1-119">0x10</span></span> | <span data-ttu-id="90ae1-120">Bayrağı yarı zaman uyumsuz bir çağrı neden olur.</span><span class="sxs-lookup"><span data-stu-id="90ae1-120">The flag causes a semisynchronous call.</span></span> |
| `WBEM_FLAG_FORWARD_ONLY` | <span data-ttu-id="90ae1-121">0x20</span><span class="sxs-lookup"><span data-stu-id="90ae1-121">0x20</span></span> | <span data-ttu-id="90ae1-122">İşlev yalnızca iletme bir numaralandırıcı döndürür.</span><span class="sxs-lookup"><span data-stu-id="90ae1-122">The function returns a forward-only enumerator.</span></span> <span data-ttu-id="90ae1-123">Genellikle, yalnızca iletme numaralandırıcılar daha hızlıdır ve geleneksel numaralandırıcılar daha az bellek kullanır, ancak çağrısına izin verme [kopya](clone.md).</span><span class="sxs-lookup"><span data-stu-id="90ae1-123">Typically, forward-only enumerators are faster and use less memory than conventional enumerators, but they do not allow calls to [Clone](clone.md).</span></span> |
| `WBEM_FLAG_BIDIRECTIONAL` | <span data-ttu-id="90ae1-124">0</span><span class="sxs-lookup"><span data-stu-id="90ae1-124">0</span></span> | <span data-ttu-id="90ae1-125">Serbest bırakılana kadar WMI numaralandırmada nesnelerine işaretçiler korur.</span><span class="sxs-lookup"><span data-stu-id="90ae1-125">WMI retains pointers to objects in the enumeration until they are released.</span></span> |
| `WBEM_FLAG_ENSURE_LOCATABLE` | <span data-ttu-id="90ae1-126">0x100</span><span class="sxs-lookup"><span data-stu-id="90ae1-126">0x100</span></span> | <span data-ttu-id="90ae1-127">Döndürülen tüm nesneler sahip yeterli bilgi bunları böylece sağlar, Sistem özellikleri gibi **__PATH**, **__RELPATH**, ve **__SERVER**, olmayan `null`.</span><span class="sxs-lookup"><span data-stu-id="90ae1-127">Ensures that any returned objects have enough information in them so that system properties, such as **__PATH**, **__RELPATH**, and **__SERVER**, are not `null`.</span></span> |
| `WBEM_FLAG_PROTOTYPE` | <span data-ttu-id="90ae1-128">2</span><span class="sxs-lookup"><span data-stu-id="90ae1-128">2</span></span> | <span data-ttu-id="90ae1-129">Bu bayrak, prototip oluşturma için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="90ae1-129">This flag is used for prototyping.</span></span> <span data-ttu-id="90ae1-130">Bu sorgu çalıştırma ve bunun yerine bir normal sonuç nesnesi gibi görünen bir nesne döndürür.</span><span class="sxs-lookup"><span data-stu-id="90ae1-130">It does not execute the query and instead returns an object that looks like a typical result object.</span></span> |
| `WBEM_FLAG_DIRECT_READ` | <span data-ttu-id="90ae1-131">0x200</span><span class="sxs-lookup"><span data-stu-id="90ae1-131">0x200</span></span> | <span data-ttu-id="90ae1-132">Doğrudan sağlayıcı erişim kendi üst sınıfı veya alt sınıfların bakılmaksızın belirtilen sınıf için neden olur.</span><span class="sxs-lookup"><span data-stu-id="90ae1-132">Causes direct access to the provider for the class specified without regard to its parent class or any subclasses.</span></span> |

<span data-ttu-id="90ae1-133">Önerilen bayraklar `WBEM_FLAG_RETURN_IMMEDIATELY` ve `WBEM_FLAG_FORWARD_ONLY` en iyi performans için.</span><span class="sxs-lookup"><span data-stu-id="90ae1-133">The recommended flags are `WBEM_FLAG_RETURN_IMMEDIATELY` and `WBEM_FLAG_FORWARD_ONLY` for best performance.</span></span>

`pCtx`\
<span data-ttu-id="90ae1-134">[in] Genellikle, bu değer, `null`.</span><span class="sxs-lookup"><span data-stu-id="90ae1-134">[in] Typically, this value is `null`.</span></span> <span data-ttu-id="90ae1-135">Aksi takdirde, bir işaretçi olduğu bir [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) istenen sınıfları sağlayan sağlayıcı tarafından kullanılan bir örnek.</span><span class="sxs-lookup"><span data-stu-id="90ae1-135">Otherwise, it is a pointer to an [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) instance that can be used by the provider that is providing the requested classes.</span></span>

`ppEnum`\
<span data-ttu-id="90ae1-136">[out] Eğer hiç Hata oluşmazsa, işaretçi örnekleri sorgunun sonuç kümesinde almak çağırıcı veren numaralandırıcıyı alır.</span><span class="sxs-lookup"><span data-stu-id="90ae1-136">[out] If no error occurs, receives the pointer to the enumerator that allows the caller to retrieve the instances in the query's result set.</span></span> <span data-ttu-id="90ae1-137">Sorgu bir sonuç kümesi sıfır örnekleriyle olabilir.</span><span class="sxs-lookup"><span data-stu-id="90ae1-137">The query can have a result set with zero instances.</span></span> <span data-ttu-id="90ae1-138">Bkz: [açıklamalar](#remarks) bölümünde daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="90ae1-138">See the [Remarks](#remarks) section for more information.</span></span>

`authLevel`\
<span data-ttu-id="90ae1-139">[in] Yetkilendirme düzeyi.</span><span class="sxs-lookup"><span data-stu-id="90ae1-139">[in] The authorization level.</span></span>

`impLevel`\
<span data-ttu-id="90ae1-140">[in] Kimliğe bürünme düzeyi.</span><span class="sxs-lookup"><span data-stu-id="90ae1-140">[in] The impersonation level.</span></span>

`pCurrentNamespace`\
<span data-ttu-id="90ae1-141">[in] Bir işaretçi bir [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) geçerli ad alanını temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="90ae1-141">[in] A pointer to an [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) object that represents the current namespace.</span></span>

`strUser`\
<span data-ttu-id="90ae1-142">[in] Kullanıcı adı.</span><span class="sxs-lookup"><span data-stu-id="90ae1-142">[in] The user name.</span></span> <span data-ttu-id="90ae1-143">Bkz: [ConnectServerWmi](connectserverwmi.md) işlevi daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="90ae1-143">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strPassword`\
<span data-ttu-id="90ae1-144">[in] Parola.</span><span class="sxs-lookup"><span data-stu-id="90ae1-144">[in] The password.</span></span> <span data-ttu-id="90ae1-145">Bkz: [ConnectServerWmi](connectserverwmi.md) işlevi daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="90ae1-145">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strAuthority`\
<span data-ttu-id="90ae1-146">[in] Kullanıcı etki alanı adı.</span><span class="sxs-lookup"><span data-stu-id="90ae1-146">[in] The domain name of the user.</span></span> <span data-ttu-id="90ae1-147">Bkz: [ConnectServerWmi](connectserverwmi.md) işlevi daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="90ae1-147">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="90ae1-148">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="90ae1-148">Return value</span></span>

<span data-ttu-id="90ae1-149">Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üst bilgi dosyası veya tanımlayabilirsiniz bunları sabitleri kodunuzda:</span><span class="sxs-lookup"><span data-stu-id="90ae1-149">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="90ae1-150">Sabit</span><span class="sxs-lookup"><span data-stu-id="90ae1-150">Constant</span></span>  |<span data-ttu-id="90ae1-151">Değer</span><span class="sxs-lookup"><span data-stu-id="90ae1-151">Value</span></span>  |<span data-ttu-id="90ae1-152">Açıklama</span><span class="sxs-lookup"><span data-stu-id="90ae1-152">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | <span data-ttu-id="90ae1-153">0x80041003</span><span class="sxs-lookup"><span data-stu-id="90ae1-153">0x80041003</span></span> | <span data-ttu-id="90ae1-154">Kullanıcı, bir veya daha fazla işlev döndürebilir sınıfları görüntüleme izni yok.</span><span class="sxs-lookup"><span data-stu-id="90ae1-154">The user does not have permission to view one or more of the classes that the function can return.</span></span> |
| `WBEM_E_FAILED` | <span data-ttu-id="90ae1-155">0x80041001</span><span class="sxs-lookup"><span data-stu-id="90ae1-155">0x80041001</span></span> | <span data-ttu-id="90ae1-156">Belirtilmeyen bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="90ae1-156">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="90ae1-157">0x80041008</span><span class="sxs-lookup"><span data-stu-id="90ae1-157">0x80041008</span></span> | <span data-ttu-id="90ae1-158">Bir parametre geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="90ae1-158">A parameter is not valid.</span></span> |
| `WBEM_E_INVALID_QUERY` | <span data-ttu-id="90ae1-159">0x80041017</span><span class="sxs-lookup"><span data-stu-id="90ae1-159">0x80041017</span></span> | <span data-ttu-id="90ae1-160">Sorgu söz dizimi hatası vardı.</span><span class="sxs-lookup"><span data-stu-id="90ae1-160">The query had a syntax error.</span></span> |
| `WBEM_E_INVALID_QUERY_TYPE` | <span data-ttu-id="90ae1-161">0x80041018</span><span class="sxs-lookup"><span data-stu-id="90ae1-161">0x80041018</span></span> | <span data-ttu-id="90ae1-162">İstenen sorgu dili desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="90ae1-162">The requested query language is not supported.</span></span> |
| `WBEM_E_QUOTA_VIOLATION` | <span data-ttu-id="90ae1-163">0x8004106c</span><span class="sxs-lookup"><span data-stu-id="90ae1-163">0x8004106c</span></span> | <span data-ttu-id="90ae1-164">Sorgu çok daha karmaşıktır.</span><span class="sxs-lookup"><span data-stu-id="90ae1-164">The query is too complex.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="90ae1-165">0x80041006</span><span class="sxs-lookup"><span data-stu-id="90ae1-165">0x80041006</span></span> | <span data-ttu-id="90ae1-166">İşlemi tamamlamak yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="90ae1-166">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_SHUTTING_DOWN` | <span data-ttu-id="90ae1-167">0x80041033</span><span class="sxs-lookup"><span data-stu-id="90ae1-167">0x80041033</span></span> | <span data-ttu-id="90ae1-168">WMI, büyük olasılıkla durdu ve yeniden başlatılıyor.</span><span class="sxs-lookup"><span data-stu-id="90ae1-168">WMI was probably stopped and restarting.</span></span> <span data-ttu-id="90ae1-169">Çağrı [ConnectServerWmi](connectserverwmi.md) yeniden.</span><span class="sxs-lookup"><span data-stu-id="90ae1-169">Call [ConnectServerWmi](connectserverwmi.md) again.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="90ae1-170">0x80041015</span><span class="sxs-lookup"><span data-stu-id="90ae1-170">0x80041015</span></span> | <span data-ttu-id="90ae1-171">Geçerli işlem WMI arasındaki uzak yordam çağrısı (RPC) bağlantı başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="90ae1-171">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="90ae1-172">0x80041002</span><span class="sxs-lookup"><span data-stu-id="90ae1-172">0x80041002</span></span> | <span data-ttu-id="90ae1-173">Sorgu var olmayan bir sınıfı belirtiyor.</span><span class="sxs-lookup"><span data-stu-id="90ae1-173">The query specifies a class that does not exist.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="90ae1-174">0</span><span class="sxs-lookup"><span data-stu-id="90ae1-174">0</span></span> | <span data-ttu-id="90ae1-175">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="90ae1-175">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="90ae1-176">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="90ae1-176">Remarks</span></span>

<span data-ttu-id="90ae1-177">Bu işlev bir çağrı sarılır [IWbemServices::ExecQuery](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-execquery) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="90ae1-177">This function wraps a call to the [IWbemServices::ExecQuery](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-execquery) method.</span></span>

<span data-ttu-id="90ae1-178">Bu işlev, belirtilen sorgu işlemleri `strQuery` parametresi üzerinden çağıran sorgu sonuçları erişebilir bir numaralandırıcı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="90ae1-178">This function processes the query specified in the `strQuery` parameter and creates an enumerator through which the caller can access the query results.</span></span> <span data-ttu-id="90ae1-179">Numaralandırıcı işaretçisidir bir [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject) arabirimi; sorgu sonuçları olan kullanılabilir hale sınıf nesnelerin örneklerini [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="90ae1-179">The enumerator is a pointer to an [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject) interface; the query results are instances of class objects made available through the [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) interface.</span></span>

<span data-ttu-id="90ae1-180">Bununla ilgili sınırlamalar sayısını `AND` ve `OR` WQL sorguları kullanılabilir anahtar sözcükler.</span><span class="sxs-lookup"><span data-stu-id="90ae1-180">There are limits to the number of `AND` and `OR` keywords that can be used in WQL queries.</span></span> <span data-ttu-id="90ae1-181">Çok sayıda karmaşık bir sorguda kullanılan WQL anahtar sözcükleri döndürmek WMI neden olabilecek `WBEM_E_QUOTA_VIOLATION` (veya 0x8004106c) hata kodunu bir `HRESULT` değeri.</span><span class="sxs-lookup"><span data-stu-id="90ae1-181">Large numbers of WQL keywords used in a complex query can cause WMI to return the `WBEM_E_QUOTA_VIOLATION` (or 0x8004106c) error code as an `HRESULT` value.</span></span> <span data-ttu-id="90ae1-182">WQL anahtar sözcük sınırını nasıl karmaşık sorgu olduğuna bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="90ae1-182">The limit of WQL keywords depends on how complex the query is.</span></span>

<span data-ttu-id="90ae1-183">İşlev çağrısı başarısız olursa, ek hata bilgileri çağırarak elde edebileceğiniz [Geterrorınfo](geterrorinfo.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="90ae1-183">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="90ae1-184">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="90ae1-184">Requirements</span></span>

<span data-ttu-id="90ae1-185">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="90ae1-185">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="90ae1-186">**Üst bilgi:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="90ae1-186">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="90ae1-187">**.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="90ae1-187">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="90ae1-188">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="90ae1-188">See also</span></span>

- [<span data-ttu-id="90ae1-189">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="90ae1-189">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)