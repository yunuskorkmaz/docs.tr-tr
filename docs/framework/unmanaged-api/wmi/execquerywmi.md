---
title: ExecQueryWmi işlevi (yönetilmeyen API Başvurusu)
description: ExecQueryWmi işlevi, nesneleri almak için bir sorgu yürütür.
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
ms.openlocfilehash: 3c6ea58eca5ac635893a24b57ade261e04a69721
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130428"
---
# <a name="execquerywmi-function"></a><span data-ttu-id="32b41-103">ExecQueryWmi işlevi</span><span class="sxs-lookup"><span data-stu-id="32b41-103">ExecQueryWmi function</span></span>

<span data-ttu-id="32b41-104">Nesneleri almak için bir sorgu yürütür.</span><span class="sxs-lookup"><span data-stu-id="32b41-104">Executes a query to retrieve objects.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="32b41-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="32b41-105">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="32b41-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="32b41-106">Parameters</span></span>

`strQueryLanguage`\
<span data-ttu-id="32b41-107">'ndaki Windows yönetimi tarafından desteklenen geçerli sorgu diline sahip bir dize.</span><span class="sxs-lookup"><span data-stu-id="32b41-107">[in] A string with the valid query language supported by Windows Management.</span></span> <span data-ttu-id="32b41-108">WMI Sorgu Dili için kısaltmasının "WQL" olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="32b41-108">It must be "WQL", the acronym for WMI Query Language.</span></span>

`strQuery`\
<span data-ttu-id="32b41-109">'ndaki Sorgunun metni.</span><span class="sxs-lookup"><span data-stu-id="32b41-109">[in] The text of the query.</span></span> <span data-ttu-id="32b41-110">Bu parametre `null`olamaz.</span><span class="sxs-lookup"><span data-stu-id="32b41-110">This parameter cannot be `null`.</span></span>

`lFlags`\
<span data-ttu-id="32b41-111">'ndaki Bu işlevin davranışını etkileyen bayrakların birleşimi.</span><span class="sxs-lookup"><span data-stu-id="32b41-111">[in] A combination of flags that affect the behavior of this function.</span></span> <span data-ttu-id="32b41-112">Aşağıdaki değerler *Wbemcli. h* üstbilgi dosyasında tanımlanmıştır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="32b41-112">The following values are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

| <span data-ttu-id="32b41-113">Sabit</span><span class="sxs-lookup"><span data-stu-id="32b41-113">Constant</span></span> | <span data-ttu-id="32b41-114">Değer</span><span class="sxs-lookup"><span data-stu-id="32b41-114">Value</span></span>  | <span data-ttu-id="32b41-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="32b41-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | <span data-ttu-id="32b41-116">0x20000</span><span class="sxs-lookup"><span data-stu-id="32b41-116">0x20000</span></span> | <span data-ttu-id="32b41-117">Ayarlanırsa, işlev geçerli bağlantının yerel ayarında yerelleştirilmiş ad alanında depolanan değiştirilmiş niteleyicileri alır.</span><span class="sxs-lookup"><span data-stu-id="32b41-117">If set, the function retrieves the amended qualifiers stored in the localized namespace of the current connection's locale.</span></span> <br/> <span data-ttu-id="32b41-118">Ayarlanmamışsa, işlev yalnızca anında ad alanında depolanan niteleyicileri alır.</span><span class="sxs-lookup"><span data-stu-id="32b41-118">If not set, the function retrieves only the qualifiers stored in the immediate namespace.</span></span> |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | <span data-ttu-id="32b41-119">0x10</span><span class="sxs-lookup"><span data-stu-id="32b41-119">0x10</span></span> | <span data-ttu-id="32b41-120">Bayrak, yarı zaman uyumlu bir çağrıya neden olur.</span><span class="sxs-lookup"><span data-stu-id="32b41-120">The flag causes a semisynchronous call.</span></span> |
| `WBEM_FLAG_FORWARD_ONLY` | <span data-ttu-id="32b41-121">0x20</span><span class="sxs-lookup"><span data-stu-id="32b41-121">0x20</span></span> | <span data-ttu-id="32b41-122">İşlev, salt ileri bir Numaralandırıcı döndürür.</span><span class="sxs-lookup"><span data-stu-id="32b41-122">The function returns a forward-only enumerator.</span></span> <span data-ttu-id="32b41-123">Genellikle, yalnızca ileri Numaralandırıcılar daha hızlıdır ve geleneksel numaralandırıcılardan daha az bellek kullanır, ancak [kopyalama](clone.md)çağrılarına izin vermez.</span><span class="sxs-lookup"><span data-stu-id="32b41-123">Typically, forward-only enumerators are faster and use less memory than conventional enumerators, but they do not allow calls to [Clone](clone.md).</span></span> |
| `WBEM_FLAG_BIDIRECTIONAL` | <span data-ttu-id="32b41-124">0</span><span class="sxs-lookup"><span data-stu-id="32b41-124">0</span></span> | <span data-ttu-id="32b41-125">WMI, serbest bırakılana kadar Numaralandırmadaki nesnelere işaretçiler tutar.</span><span class="sxs-lookup"><span data-stu-id="32b41-125">WMI retains pointers to objects in the enumeration until they are released.</span></span> |
| `WBEM_FLAG_ENSURE_LOCATABLE` | <span data-ttu-id="32b41-126">0x100</span><span class="sxs-lookup"><span data-stu-id="32b41-126">0x100</span></span> | <span data-ttu-id="32b41-127">Döndürülen tüm nesnelerin, **__Path**, **__Relpath**ve **__server**gibi sistem özelliklerinin `null`olmamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="32b41-127">Ensures that any returned objects have enough information in them so that system properties, such as **__PATH**, **__RELPATH**, and **__SERVER**, are not `null`.</span></span> |
| `WBEM_FLAG_PROTOTYPE` | <span data-ttu-id="32b41-128">2</span><span class="sxs-lookup"><span data-stu-id="32b41-128">2</span></span> | <span data-ttu-id="32b41-129">Bu bayrak prototipleme için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="32b41-129">This flag is used for prototyping.</span></span> <span data-ttu-id="32b41-130">Sorguyu yürütmez ve bunun yerine tipik bir sonuç nesnesi gibi görünen bir nesne döndürür.</span><span class="sxs-lookup"><span data-stu-id="32b41-130">It does not execute the query and instead returns an object that looks like a typical result object.</span></span> |
| `WBEM_FLAG_DIRECT_READ` | <span data-ttu-id="32b41-131">0x200</span><span class="sxs-lookup"><span data-stu-id="32b41-131">0x200</span></span> | <span data-ttu-id="32b41-132">, Kendi üst sınıfı veya alt sınıflarından bağımsız kalmadan belirtilen sınıf için sağlayıcıya doğrudan erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="32b41-132">Causes direct access to the provider for the class specified without regard to its parent class or any subclasses.</span></span> |

<span data-ttu-id="32b41-133">Önerilen bayraklar `WBEM_FLAG_RETURN_IMMEDIATELY` ve en iyi performans için `WBEM_FLAG_FORWARD_ONLY`.</span><span class="sxs-lookup"><span data-stu-id="32b41-133">The recommended flags are `WBEM_FLAG_RETURN_IMMEDIATELY` and `WBEM_FLAG_FORWARD_ONLY` for best performance.</span></span>

`pCtx`\
<span data-ttu-id="32b41-134">'ndaki Genellikle, bu değer `null`.</span><span class="sxs-lookup"><span data-stu-id="32b41-134">[in] Typically, this value is `null`.</span></span> <span data-ttu-id="32b41-135">Aksi takdirde, istenen sınıfları sağlayan sağlayıcı tarafından kullanılabilen bir [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) örneğine yönelik bir işaretçidir.</span><span class="sxs-lookup"><span data-stu-id="32b41-135">Otherwise, it is a pointer to an [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) instance that can be used by the provider that is providing the requested classes.</span></span>

`ppEnum`\
<span data-ttu-id="32b41-136">dışı Herhangi bir hata oluşursa, çağıranın sorgunun sonuç kümesindeki örnekleri almasına izin veren Numaralandırıcı için işaretçiyi alır.</span><span class="sxs-lookup"><span data-stu-id="32b41-136">[out] If no error occurs, receives the pointer to the enumerator that allows the caller to retrieve the instances in the query's result set.</span></span> <span data-ttu-id="32b41-137">Sorgu sıfır örnek içeren bir sonuç kümesine sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="32b41-137">The query can have a result set with zero instances.</span></span> <span data-ttu-id="32b41-138">Daha fazla bilgi için [açıklamalar](#remarks) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="32b41-138">See the [Remarks](#remarks) section for more information.</span></span>

`authLevel`\
<span data-ttu-id="32b41-139">'ndaki Yetkilendirme düzeyi.</span><span class="sxs-lookup"><span data-stu-id="32b41-139">[in] The authorization level.</span></span>

`impLevel`\
<span data-ttu-id="32b41-140">'ndaki Kimliğe bürünme düzeyi.</span><span class="sxs-lookup"><span data-stu-id="32b41-140">[in] The impersonation level.</span></span>

`pCurrentNamespace`\
<span data-ttu-id="32b41-141">'ndaki Geçerli ad alanını temsil eden bir [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="32b41-141">[in] A pointer to an [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) object that represents the current namespace.</span></span>

`strUser`\
<span data-ttu-id="32b41-142">'ndaki Kullanıcı adı.</span><span class="sxs-lookup"><span data-stu-id="32b41-142">[in] The user name.</span></span> <span data-ttu-id="32b41-143">Daha fazla bilgi için bkz. [Connectserverwmi](connectserverwmi.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="32b41-143">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strPassword`\
<span data-ttu-id="32b41-144">'ndaki Parola.</span><span class="sxs-lookup"><span data-stu-id="32b41-144">[in] The password.</span></span> <span data-ttu-id="32b41-145">Daha fazla bilgi için bkz. [Connectserverwmi](connectserverwmi.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="32b41-145">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strAuthority`\
<span data-ttu-id="32b41-146">'ndaki Kullanıcının etki alanı adı.</span><span class="sxs-lookup"><span data-stu-id="32b41-146">[in] The domain name of the user.</span></span> <span data-ttu-id="32b41-147">Daha fazla bilgi için bkz. [Connectserverwmi](connectserverwmi.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="32b41-147">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="32b41-148">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="32b41-148">Return value</span></span>

<span data-ttu-id="32b41-149">Bu işlev tarafından döndürülen aşağıdaki değerler, *Wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="32b41-149">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="32b41-150">Sabit</span><span class="sxs-lookup"><span data-stu-id="32b41-150">Constant</span></span>  |<span data-ttu-id="32b41-151">Değer</span><span class="sxs-lookup"><span data-stu-id="32b41-151">Value</span></span>  |<span data-ttu-id="32b41-152">Açıklama</span><span class="sxs-lookup"><span data-stu-id="32b41-152">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | <span data-ttu-id="32b41-153">0x80041003</span><span class="sxs-lookup"><span data-stu-id="32b41-153">0x80041003</span></span> | <span data-ttu-id="32b41-154">Kullanıcının işlevin döndüregörüntüleyebileceği bir veya daha fazla sınıfı görüntüleme izni yok.</span><span class="sxs-lookup"><span data-stu-id="32b41-154">The user does not have permission to view one or more of the classes that the function can return.</span></span> |
| `WBEM_E_FAILED` | <span data-ttu-id="32b41-155">0x80041001</span><span class="sxs-lookup"><span data-stu-id="32b41-155">0x80041001</span></span> | <span data-ttu-id="32b41-156">Belirtilmeyen bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="32b41-156">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="32b41-157">0x80041008</span><span class="sxs-lookup"><span data-stu-id="32b41-157">0x80041008</span></span> | <span data-ttu-id="32b41-158">Parametre geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="32b41-158">A parameter is not valid.</span></span> |
| `WBEM_E_INVALID_QUERY` | <span data-ttu-id="32b41-159">0x80041017</span><span class="sxs-lookup"><span data-stu-id="32b41-159">0x80041017</span></span> | <span data-ttu-id="32b41-160">Sorguda sözdizimi hatası vardı.</span><span class="sxs-lookup"><span data-stu-id="32b41-160">The query had a syntax error.</span></span> |
| `WBEM_E_INVALID_QUERY_TYPE` | <span data-ttu-id="32b41-161">0x80041018</span><span class="sxs-lookup"><span data-stu-id="32b41-161">0x80041018</span></span> | <span data-ttu-id="32b41-162">İstenen sorgu dili desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="32b41-162">The requested query language is not supported.</span></span> |
| `WBEM_E_QUOTA_VIOLATION` | <span data-ttu-id="32b41-163">0x8004106c</span><span class="sxs-lookup"><span data-stu-id="32b41-163">0x8004106c</span></span> | <span data-ttu-id="32b41-164">Sorgu çok karmaşık.</span><span class="sxs-lookup"><span data-stu-id="32b41-164">The query is too complex.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="32b41-165">0x80041006</span><span class="sxs-lookup"><span data-stu-id="32b41-165">0x80041006</span></span> | <span data-ttu-id="32b41-166">İşlemi gerçekleştirmek için yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="32b41-166">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_SHUTTING_DOWN` | <span data-ttu-id="32b41-167">0x80041033</span><span class="sxs-lookup"><span data-stu-id="32b41-167">0x80041033</span></span> | <span data-ttu-id="32b41-168">WMI, büyük olasılıkla durmuş ve yeniden başlatılıyor.</span><span class="sxs-lookup"><span data-stu-id="32b41-168">WMI was probably stopped and restarting.</span></span> <span data-ttu-id="32b41-169">[Connectserverwmi](connectserverwmi.md) ' i yeniden çağırın.</span><span class="sxs-lookup"><span data-stu-id="32b41-169">Call [ConnectServerWmi](connectserverwmi.md) again.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="32b41-170">0x80041015</span><span class="sxs-lookup"><span data-stu-id="32b41-170">0x80041015</span></span> | <span data-ttu-id="32b41-171">Geçerli işlem ve WMI arasındaki uzak yordam çağrısı (RPC) bağlantısı başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="32b41-171">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="32b41-172">0x80041002</span><span class="sxs-lookup"><span data-stu-id="32b41-172">0x80041002</span></span> | <span data-ttu-id="32b41-173">Sorgu var olmayan bir sınıfı belirtiyor.</span><span class="sxs-lookup"><span data-stu-id="32b41-173">The query specifies a class that does not exist.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="32b41-174">0</span><span class="sxs-lookup"><span data-stu-id="32b41-174">0</span></span> | <span data-ttu-id="32b41-175">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="32b41-175">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="32b41-176">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="32b41-176">Remarks</span></span>

<span data-ttu-id="32b41-177">Bu işlev, [IWbemServices:: ExecQuery](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-execquery) yöntemine bir çağrı kaydırır.</span><span class="sxs-lookup"><span data-stu-id="32b41-177">This function wraps a call to the [IWbemServices::ExecQuery](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-execquery) method.</span></span>

<span data-ttu-id="32b41-178">Bu işlev `strQuery` parametresinde belirtilen sorguyu işler ve çağıranın sorgu sonuçlarına erişebileceği bir Numaralandırıcı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="32b41-178">This function processes the query specified in the `strQuery` parameter and creates an enumerator through which the caller can access the query results.</span></span> <span data-ttu-id="32b41-179">Numaralandırıcı bir [ıenumwbemclassobject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject) arabirimine yönelik bir işaretçidir; sorgu sonuçları, [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) arabirimi aracılığıyla kullanılabilir hale getirilen sınıf nesnelerinin örnekleridir.</span><span class="sxs-lookup"><span data-stu-id="32b41-179">The enumerator is a pointer to an [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject) interface; the query results are instances of class objects made available through the [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) interface.</span></span>

<span data-ttu-id="32b41-180">WQL sorgularında kullanılabilecek `AND` sayısı ve `OR` anahtar kelimeleriyle ilgili sınırlar vardır.</span><span class="sxs-lookup"><span data-stu-id="32b41-180">There are limits to the number of `AND` and `OR` keywords that can be used in WQL queries.</span></span> <span data-ttu-id="32b41-181">Karmaşık bir sorguda kullanılan çok sayıda WQL anahtar sözcüğü, WMI 'nin `WBEM_E_QUOTA_VIOLATION` (veya 0x8004106c) hata kodunu `HRESULT` değeri olarak döndürmesini sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="32b41-181">Large numbers of WQL keywords used in a complex query can cause WMI to return the `WBEM_E_QUOTA_VIOLATION` (or 0x8004106c) error code as an `HRESULT` value.</span></span> <span data-ttu-id="32b41-182">WQL anahtar kelimesinin sınırı, sorgunun ne kadar karmaşık olduğuna bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="32b41-182">The limit of WQL keywords depends on how complex the query is.</span></span>

<span data-ttu-id="32b41-183">İşlev çağrısı başarısız olursa, [GetErrorInfo](geterrorinfo.md) işlevini çağırarak ek hata bilgileri alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="32b41-183">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="32b41-184">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="32b41-184">Requirements</span></span>

<span data-ttu-id="32b41-185">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="32b41-185">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="32b41-186">**Üst bilgi:** WMINet_Utils. IDL</span><span class="sxs-lookup"><span data-stu-id="32b41-186">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="32b41-187">**.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="32b41-187">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="32b41-188">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="32b41-188">See also</span></span>

- [<span data-ttu-id="32b41-189">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="32b41-189">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
