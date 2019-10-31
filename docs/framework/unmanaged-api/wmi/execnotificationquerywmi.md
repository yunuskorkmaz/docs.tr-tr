---
title: ExecNotificationQueryWmi işlevi (yönetilmeyen API Başvurusu)
description: ExecNotificationQueryWmi işlevi, olayları almak için bir sorgu yürütür.
ms.date: 11/06/2017
api_name:
- ExecNotificationQueryWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- ExecNotificationQueryWmi
helpviewer_keywords:
- ExecNotificationQueryWmi function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 3d8a7683eef52a5e91bf7aa84d5aa7db7dbdac8d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130447"
---
# <a name="execnotificationquerywmi-function"></a><span data-ttu-id="270e0-103">ExecNotificationQueryWmi işlevi</span><span class="sxs-lookup"><span data-stu-id="270e0-103">ExecNotificationQueryWmi function</span></span>

<span data-ttu-id="270e0-104">Olayları almak için bir sorgu yürütür.</span><span class="sxs-lookup"><span data-stu-id="270e0-104">Executes a query to receive events.</span></span> <span data-ttu-id="270e0-105">Çağrı hemen döndürülür ve çağıran, gelen olaylar için döndürülen numaralandırıcıyı yoklayabilirler.</span><span class="sxs-lookup"><span data-stu-id="270e0-105">The call returns immediately, and the caller can poll the returned enumerator for events as they arrive.</span></span> <span data-ttu-id="270e0-106">Döndürülen Numaralandırıcı serbest bırakıldığında sorgu iptal edilir.</span><span class="sxs-lookup"><span data-stu-id="270e0-106">Releasing the returned enumerator cancels the query.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="270e0-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="270e0-107">Syntax</span></span>

```cpp
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

## <a name="parameters"></a><span data-ttu-id="270e0-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="270e0-108">Parameters</span></span>

`strQueryLanguage`\
<span data-ttu-id="270e0-109">'ndaki Windows yönetimi tarafından desteklenen geçerli sorgu diline sahip bir dize.</span><span class="sxs-lookup"><span data-stu-id="270e0-109">[in] A string with the valid query language supported by Windows Management.</span></span> <span data-ttu-id="270e0-110">WMI Sorgu Dili için kısaltmasının "WQL" olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="270e0-110">It must be "WQL", the acronym for WMI Query Language.</span></span>

`strQuery`\
<span data-ttu-id="270e0-111">'ndaki Sorgunun metni.</span><span class="sxs-lookup"><span data-stu-id="270e0-111">[in] The text of the query.</span></span> <span data-ttu-id="270e0-112">Bu parametre `null`olamaz.</span><span class="sxs-lookup"><span data-stu-id="270e0-112">This parameter cannot be `null`.</span></span>

`lFlags`\
<span data-ttu-id="270e0-113">'ndaki Bu işlevin davranışını etkileyen aşağıdaki iki bayrakların birleşimi.</span><span class="sxs-lookup"><span data-stu-id="270e0-113">[in] A combination of the following two flags that affect the behavior of this function.</span></span> <span data-ttu-id="270e0-114">Bu değerler, *Wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="270e0-114">These values are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span>

| <span data-ttu-id="270e0-115">Sabit</span><span class="sxs-lookup"><span data-stu-id="270e0-115">Constant</span></span> | <span data-ttu-id="270e0-116">Değer</span><span class="sxs-lookup"><span data-stu-id="270e0-116">Value</span></span>  | <span data-ttu-id="270e0-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="270e0-117">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_RETURN_IMMEDIATELY` | <span data-ttu-id="270e0-118">0x10</span><span class="sxs-lookup"><span data-stu-id="270e0-118">0x10</span></span> | <span data-ttu-id="270e0-119">Bayrak, yarı zaman uyumlu bir çağrıya neden olur.</span><span class="sxs-lookup"><span data-stu-id="270e0-119">The flag causes a semisynchronous call.</span></span> <span data-ttu-id="270e0-120">Bu bayrak ayarlanmamışsa, çağrı başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="270e0-120">If this flag is not set, the call fails.</span></span> <span data-ttu-id="270e0-121">Bunun nedeni, olayların sürekli olarak alınması anlamına gelir, yani Kullanıcı Döndürülen numaralandırıcısı yoklamalıdır.</span><span class="sxs-lookup"><span data-stu-id="270e0-121">This is because events are received continuously, which means the user must poll the returned enumerator.</span></span> <span data-ttu-id="270e0-122">Bu çağrıyı süresiz olarak engellemek olanaksız hale getirir.</span><span class="sxs-lookup"><span data-stu-id="270e0-122">Blocking this call indefinitely makes that impossible.</span></span> |
| `WBEM_FLAG_FORWARD_ONLY` | <span data-ttu-id="270e0-123">0x20</span><span class="sxs-lookup"><span data-stu-id="270e0-123">0x20</span></span> | <span data-ttu-id="270e0-124">İşlev, salt ileri bir Numaralandırıcı döndürür.</span><span class="sxs-lookup"><span data-stu-id="270e0-124">The function returns a forward-only enumerator.</span></span> <span data-ttu-id="270e0-125">Genellikle, yalnızca ileri Numaralandırıcılar daha hızlıdır ve geleneksel numaralandırıcılardan daha az bellek kullanır, ancak [kopyalama](clone.md)çağrılarına izin vermez.</span><span class="sxs-lookup"><span data-stu-id="270e0-125">Typically, forward-only enumerators are faster and use less memory than conventional enumerators, but they do not allow calls to [Clone](clone.md).</span></span> |

`pCtx`\
<span data-ttu-id="270e0-126">'ndaki Genellikle, bu değer `null`.</span><span class="sxs-lookup"><span data-stu-id="270e0-126">[in] Typically, this value is `null`.</span></span> <span data-ttu-id="270e0-127">Aksi takdirde, istenen olayları sağlayan sağlayıcı tarafından kullanılabilen bir [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) örneğine yönelik bir işaretçidir.</span><span class="sxs-lookup"><span data-stu-id="270e0-127">Otherwise, it is a pointer to an [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) instance that can be used by the provider that is providing the requested events.</span></span>

`ppEnum`\
<span data-ttu-id="270e0-128">dışı Herhangi bir hata oluşursa, çağıranın sorgunun sonuç kümesindeki örnekleri almasına izin veren Numaralandırıcı için işaretçiyi alır.</span><span class="sxs-lookup"><span data-stu-id="270e0-128">[out] If no error occurs, receives the pointer to the enumerator that allows the caller to retrieve the instances in the query's result set.</span></span> <span data-ttu-id="270e0-129">Daha fazla bilgi için [açıklamalar](#remarks) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="270e0-129">See the [Remarks](#remarks) section for more information.</span></span>

`authLevel`\
<span data-ttu-id="270e0-130">'ndaki Yetkilendirme düzeyi.</span><span class="sxs-lookup"><span data-stu-id="270e0-130">[in] The authorization level.</span></span>

`impLevel`\
<span data-ttu-id="270e0-131">'ndaki Kimliğe bürünme düzeyi.</span><span class="sxs-lookup"><span data-stu-id="270e0-131">[in] The impersonation level.</span></span>

`pCurrentNamespace`\
<span data-ttu-id="270e0-132">'ndaki Geçerli ad alanını temsil eden bir [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="270e0-132">[in] A pointer to an [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) object that represents the current namespace.</span></span>

`strUser`\
<span data-ttu-id="270e0-133">'ndaki Kullanıcı adı.</span><span class="sxs-lookup"><span data-stu-id="270e0-133">[in] The user name.</span></span> <span data-ttu-id="270e0-134">Daha fazla bilgi için bkz. [Connectserverwmi](connectserverwmi.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="270e0-134">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strPassword`\
<span data-ttu-id="270e0-135">'ndaki Parola.</span><span class="sxs-lookup"><span data-stu-id="270e0-135">[in] The password.</span></span> <span data-ttu-id="270e0-136">Daha fazla bilgi için bkz. [Connectserverwmi](connectserverwmi.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="270e0-136">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strAuthority`\
<span data-ttu-id="270e0-137">'ndaki Kullanıcının etki alanı adı.</span><span class="sxs-lookup"><span data-stu-id="270e0-137">[in] The domain name of the user.</span></span> <span data-ttu-id="270e0-138">Daha fazla bilgi için bkz. [Connectserverwmi](connectserverwmi.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="270e0-138">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="270e0-139">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="270e0-139">Return value</span></span>

<span data-ttu-id="270e0-140">Bu işlev tarafından döndürülen aşağıdaki değerler, *Wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="270e0-140">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="270e0-141">Sabit</span><span class="sxs-lookup"><span data-stu-id="270e0-141">Constant</span></span>  |<span data-ttu-id="270e0-142">Değer</span><span class="sxs-lookup"><span data-stu-id="270e0-142">Value</span></span>  |<span data-ttu-id="270e0-143">Açıklama</span><span class="sxs-lookup"><span data-stu-id="270e0-143">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | <span data-ttu-id="270e0-144">0x80041003</span><span class="sxs-lookup"><span data-stu-id="270e0-144">0x80041003</span></span> | <span data-ttu-id="270e0-145">Kullanıcının işlevin döndüregörüntüleyebileceği bir veya daha fazla sınıfı görüntüleme izni yok.</span><span class="sxs-lookup"><span data-stu-id="270e0-145">The user does not have permission to view one or more of the classes that the function can return.</span></span> |
| `WBEM_E_FAILED` | <span data-ttu-id="270e0-146">0x80041001</span><span class="sxs-lookup"><span data-stu-id="270e0-146">0x80041001</span></span> | <span data-ttu-id="270e0-147">Belirtilmeyen bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="270e0-147">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="270e0-148">0x80041008</span><span class="sxs-lookup"><span data-stu-id="270e0-148">0x80041008</span></span> | <span data-ttu-id="270e0-149">Parametre geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="270e0-149">A parameter is not valid.</span></span> |
| `WBEM_E_INVALID_CLASS` | <span data-ttu-id="270e0-150">0x80041010</span><span class="sxs-lookup"><span data-stu-id="270e0-150">0x80041010</span></span> | <span data-ttu-id="270e0-151">Sorgu var olmayan bir sınıfı belirtiyor.</span><span class="sxs-lookup"><span data-stu-id="270e0-151">The query specifies a class that does not exist.</span></span> |
| `WBEMESS_E_REGISTRATION_TOO_PRECISE` | <span data-ttu-id="270e0-152">0x80042002</span><span class="sxs-lookup"><span data-stu-id="270e0-152">0x80042002</span></span> | <span data-ttu-id="270e0-153">Olayların tesliminde çok fazla duyarlılık istendi.</span><span class="sxs-lookup"><span data-stu-id="270e0-153">Too much precision in delivery of events has been requested.</span></span> <span data-ttu-id="270e0-154">Daha büyük bir yoklama toleransı belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="270e0-154">A larger polling tolerance must be specified.</span></span> |
| `WBEMESS_E_REGISTRATION_TOO_BROAD` | <span data-ttu-id="270e0-155">0x80042001</span><span class="sxs-lookup"><span data-stu-id="270e0-155">0x80042001</span></span> | <span data-ttu-id="270e0-156">Sorgu Windows yönetiminin sağlayabileceğinden daha fazla bilgi ister.</span><span class="sxs-lookup"><span data-stu-id="270e0-156">The query requests more information than Windows Management can provide.</span></span> <span data-ttu-id="270e0-157">Bu `HRESULT`, bir olay sorgusu bir ad alanındaki tüm nesneleri yoklamaya yönelik bir istek ile sonuçlanırsa döndürülür.</span><span class="sxs-lookup"><span data-stu-id="270e0-157">This `HRESULT` is returned when an event query results in a request to poll all objects in a namespace.</span></span> |
| `WBEM_E_INVALID_QUERY` | <span data-ttu-id="270e0-158">0x80041017</span><span class="sxs-lookup"><span data-stu-id="270e0-158">0x80041017</span></span> | <span data-ttu-id="270e0-159">Sorguda sözdizimi hatası vardı.</span><span class="sxs-lookup"><span data-stu-id="270e0-159">The query had a syntax error.</span></span> |
| `WBEM_E_INVALID_QUERY_TYPE` | <span data-ttu-id="270e0-160">0x80041018</span><span class="sxs-lookup"><span data-stu-id="270e0-160">0x80041018</span></span> | <span data-ttu-id="270e0-161">İstenen sorgu dili desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="270e0-161">The requested query language is not supported.</span></span> |
| `WBEM_E_QUOTA_VIOLATION` | <span data-ttu-id="270e0-162">0x8004106c</span><span class="sxs-lookup"><span data-stu-id="270e0-162">0x8004106c</span></span> | <span data-ttu-id="270e0-163">Sorgu çok karmaşık.</span><span class="sxs-lookup"><span data-stu-id="270e0-163">The query is too complex.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="270e0-164">0x80041006</span><span class="sxs-lookup"><span data-stu-id="270e0-164">0x80041006</span></span> | <span data-ttu-id="270e0-165">İşlemi gerçekleştirmek için yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="270e0-165">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_SHUTTING_DOWN` | <span data-ttu-id="270e0-166">0x80041033</span><span class="sxs-lookup"><span data-stu-id="270e0-166">0x80041033</span></span> | <span data-ttu-id="270e0-167">WMI, büyük olasılıkla durmuş ve yeniden başlatılıyor.</span><span class="sxs-lookup"><span data-stu-id="270e0-167">WMI was probably stopped and restarting.</span></span> <span data-ttu-id="270e0-168">[Connectserverwmi](connectserverwmi.md) ' i yeniden çağırın.</span><span class="sxs-lookup"><span data-stu-id="270e0-168">Call [ConnectServerWmi](connectserverwmi.md) again.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="270e0-169">0x80041015</span><span class="sxs-lookup"><span data-stu-id="270e0-169">0x80041015</span></span> | <span data-ttu-id="270e0-170">Geçerli işlem ve WMI arasındaki uzak yordam çağrısı (RPC) bağlantısı başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="270e0-170">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
| `WBEM_E_UNPARSABLE_QUERY` | <span data-ttu-id="270e0-171">0x80041058</span><span class="sxs-lookup"><span data-stu-id="270e0-171">0x80041058</span></span> | <span data-ttu-id="270e0-172">Sorgu ayrıştırılamıyor.</span><span class="sxs-lookup"><span data-stu-id="270e0-172">The query cannot be parsed.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="270e0-173">0</span><span class="sxs-lookup"><span data-stu-id="270e0-173">0</span></span> | <span data-ttu-id="270e0-174">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="270e0-174">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="270e0-175">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="270e0-175">Remarks</span></span>

<span data-ttu-id="270e0-176">Bu işlev, [IWbemServices:: ExecNotificationQuery](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-execnotificationquery) yöntemine bir çağrı kaydırır.</span><span class="sxs-lookup"><span data-stu-id="270e0-176">This function wraps a call to the [IWbemServices::ExecNotificationQuery](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-execnotificationquery) method.</span></span>

<span data-ttu-id="270e0-177">İşlev çağrıldıktan sonra, çağıran `ppEnum` nesnesini bir [sonraki](next.md) işleve düzenli olarak geçirir ve kullanılabilir herhangi bir olay olup olmadığını görür.</span><span class="sxs-lookup"><span data-stu-id="270e0-177">After the function returns, the caller periodically passes the returned `ppEnum` object to the [Next](next.md) function to see if any events are available.</span></span>

<span data-ttu-id="270e0-178">WQL sorgularında kullanılabilecek `AND` sayısı ve `OR` anahtar kelimeleriyle ilgili sınırlar vardır.</span><span class="sxs-lookup"><span data-stu-id="270e0-178">There are limits to the number of `AND` and `OR` keywords that can be used in WQL queries.</span></span> <span data-ttu-id="270e0-179">Karmaşık bir sorguda kullanılan çok sayıda WQL anahtar sözcüğü, WMI 'nin `WBEM_E_QUOTA_VIOLATION` (veya 0x8004106c) hata kodunu `HRESULT` değeri olarak döndürmesini sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="270e0-179">Large numbers of WQL keywords used in a complex query can cause WMI to return the `WBEM_E_QUOTA_VIOLATION` (or 0x8004106c) error code as an `HRESULT` value.</span></span> <span data-ttu-id="270e0-180">WQL anahtar kelimesinin sınırı, sorgunun ne kadar karmaşık olduğuna bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="270e0-180">The limit of WQL keywords depends on how complex the query is.</span></span>

<span data-ttu-id="270e0-181">İşlev çağrısı başarısız olursa, [GetErrorInfo](geterrorinfo.md) işlevini çağırarak ek hata bilgileri alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="270e0-181">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="270e0-182">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="270e0-182">Requirements</span></span>

<span data-ttu-id="270e0-183">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="270e0-183">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="270e0-184">**Üst bilgi:** WMINet_Utils. IDL</span><span class="sxs-lookup"><span data-stu-id="270e0-184">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="270e0-185">**.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="270e0-185">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="270e0-186">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="270e0-186">See also</span></span>

- [<span data-ttu-id="270e0-187">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="270e0-187">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
