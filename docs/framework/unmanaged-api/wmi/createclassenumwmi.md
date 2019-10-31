---
title: CreateClassEnumWmi işlevi (yönetilmeyen API Başvurusu)
description: CreateClassEnumWmi işlevi, belirtilen ölçütlere uyan tüm sınıflar için bir Numaralandırıcı döndürür.
ms.date: 11/06/2017
api_name:
- CreateClassEnumWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- CreateClassEnumWmi
helpviewer_keywords:
- CreateClassEnumWmi function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 1d637479bd140e635ee647a1e30d03343d8b0dcd
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73107528"
---
# <a name="createclassenumwmi-function"></a><span data-ttu-id="0f315-103">CreateClassEnumWmi işlevi</span><span class="sxs-lookup"><span data-stu-id="0f315-103">CreateClassEnumWmi function</span></span>
<span data-ttu-id="0f315-104">Belirtilen seçim ölçütlerini karşılayan tüm sınıflar için bir Numaralandırıcı döndürür.</span><span class="sxs-lookup"><span data-stu-id="0f315-104">Returns an enumerator for all classes that satisfy the specified selection criteria.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="0f315-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0f315-105">Syntax</span></span>

```cpp
HRESULT CreateClassEnumWmi (
   [in] BSTR                    strSuperclass,
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

## <a name="parameters"></a><span data-ttu-id="0f315-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0f315-106">Parameters</span></span>

`strSuperclass`\
<span data-ttu-id="0f315-107">'ndaki `null` veya boş değilse, bir üst sınıfın adını belirtir; Numaralandırıcı bu sınıfın yalnızca alt sınıflarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="0f315-107">[in] If not `null` or blank, specifies the name of a parent class; the enumerator returns only subclasses of this class.</span></span> <span data-ttu-id="0f315-108">`null` veya boş ise ve `lFlags` WBEM_FLAG_SHALLOW ise, yalnızca üst düzey sınıfları (üst sınıfı olmayan sınıflar) döndürür.</span><span class="sxs-lookup"><span data-stu-id="0f315-108">If it is `null` or blank and `lFlags` is WBEM_FLAG_SHALLOW, returns only top-level classes (classes with no parent class).</span></span> <span data-ttu-id="0f315-109">`null` veya boş ise ve `lFlags` `WBEM_FLAG_DEEP`, ad alanındaki tüm sınıfları döndürür.</span><span class="sxs-lookup"><span data-stu-id="0f315-109">If it is `null` or blank and `lFlags` is `WBEM_FLAG_DEEP`, returns all classes in the namespace.</span></span>

`lFlags`\
<span data-ttu-id="0f315-110">'ndaki Bu işlevin davranışını etkileyen bayrakların birleşimi.</span><span class="sxs-lookup"><span data-stu-id="0f315-110">[in] A combination of flags that affect the behavior of this function.</span></span> <span data-ttu-id="0f315-111">Aşağıdaki değerler *Wbemcli. h* üstbilgi dosyasında tanımlanmıştır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="0f315-111">The following values are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="0f315-112">Sabit</span><span class="sxs-lookup"><span data-stu-id="0f315-112">Constant</span></span>  |<span data-ttu-id="0f315-113">Değer</span><span class="sxs-lookup"><span data-stu-id="0f315-113">Value</span></span>  |<span data-ttu-id="0f315-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0f315-114">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | <span data-ttu-id="0f315-115">0x20000</span><span class="sxs-lookup"><span data-stu-id="0f315-115">0x20000</span></span> | <span data-ttu-id="0f315-116">Ayarlanırsa, işlev geçerli bağlantının yerel ayarında yerelleştirilmiş ad alanında depolanan değiştirilmiş niteleyicileri alır.</span><span class="sxs-lookup"><span data-stu-id="0f315-116">If set, the function retrieves the amended qualifiers stored in the localized namespace of the current connection's locale.</span></span> <br/> <span data-ttu-id="0f315-117">Ayarlanmamışsa, işlev yalnızca anında ad alanında depolanan niteleyicileri alır.</span><span class="sxs-lookup"><span data-stu-id="0f315-117">If not set, the function retrieves only the qualifiers stored in the immediate namespace.</span></span> |
| `WBEM_FLAG_DEEP` | <span data-ttu-id="0f315-118">0</span><span class="sxs-lookup"><span data-stu-id="0f315-118">0</span></span> | <span data-ttu-id="0f315-119">Sabit Listesi hiyerarşideki tüm alt sınıfları içerir, ancak bu sınıf değildir.</span><span class="sxs-lookup"><span data-stu-id="0f315-119">The enumeration includes all subclasses in the hierarchy, but not this class.</span></span> |
| `WBEM_FLAG_SHALLOW` | <span data-ttu-id="0f315-120">1\.</span><span class="sxs-lookup"><span data-stu-id="0f315-120">1</span></span> | <span data-ttu-id="0f315-121">Sabit listesi yalnızca bu sınıfın saf örneklerini içerir ve bu sınıfta bulunmayan özellikleri sağlayan tüm alt sınıfların örneklerini dışlar.</span><span class="sxs-lookup"><span data-stu-id="0f315-121">The enumeration includes only pure instances of this class and excludes all instances of subclasses that supply properties not found in this class.</span></span> |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | <span data-ttu-id="0f315-122">0x10</span><span class="sxs-lookup"><span data-stu-id="0f315-122">0x10</span></span> | <span data-ttu-id="0f315-123">Bayrak, yarı zaman uyumlu bir çağrıya neden olur.</span><span class="sxs-lookup"><span data-stu-id="0f315-123">The flag causes a semisynchronous call.</span></span> |
| `WBEM_FLAG_FORWARD_ONLY` | <span data-ttu-id="0f315-124">0x20</span><span class="sxs-lookup"><span data-stu-id="0f315-124">0x20</span></span> | <span data-ttu-id="0f315-125">İşlev, salt ileri bir Numaralandırıcı döndürür.</span><span class="sxs-lookup"><span data-stu-id="0f315-125">The function returns a forward-only enumerator.</span></span> <span data-ttu-id="0f315-126">Genellikle, yalnızca ileri Numaralandırıcılar daha hızlıdır ve geleneksel numaralandırıcılardan daha az bellek kullanır, ancak [kopyalama](clone.md)çağrılarına izin vermez.</span><span class="sxs-lookup"><span data-stu-id="0f315-126">Typically, forward-only enumerators are faster and use less memory than conventional enumerators, but they do not allow calls to [Clone](clone.md).</span></span> |
| `WBEM_FLAG_BIDIRECTIONAL` | <span data-ttu-id="0f315-127">0</span><span class="sxs-lookup"><span data-stu-id="0f315-127">0</span></span> | <span data-ttu-id="0f315-128">WMI, serbest bırakılana kadar Numaralandırmadaki nesnelere işaretçiler tutar.</span><span class="sxs-lookup"><span data-stu-id="0f315-128">WMI retains pointers to objects in the enumeration until they are released.</span></span> |

<span data-ttu-id="0f315-129">Önerilen bayraklar `WBEM_FLAG_RETURN_IMMEDIATELY` ve en iyi performans için `WBEM_FLAG_FORWARD_ONLY`.</span><span class="sxs-lookup"><span data-stu-id="0f315-129">The recommended flags are `WBEM_FLAG_RETURN_IMMEDIATELY` and `WBEM_FLAG_FORWARD_ONLY` for best performance.</span></span>

`pCtx`\
<span data-ttu-id="0f315-130">'ndaki Genellikle, bu değer `null`.</span><span class="sxs-lookup"><span data-stu-id="0f315-130">[in] Typically, this value is `null`.</span></span> <span data-ttu-id="0f315-131">Aksi takdirde, istenen sınıfları sağlayan sağlayıcı tarafından kullanılabilen bir [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) örneğine yönelik bir işaretçidir.</span><span class="sxs-lookup"><span data-stu-id="0f315-131">Otherwise, it is a pointer to an [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) instance that can be used by the provider that is providing the requested classes.</span></span>

`ppEnum`\
<span data-ttu-id="0f315-132">dışı Numaralandırıcı için işaretçiyi alır.</span><span class="sxs-lookup"><span data-stu-id="0f315-132">[out] Receives the pointer to the enumerator.</span></span>

`authLevel`\
<span data-ttu-id="0f315-133">'ndaki Yetkilendirme düzeyi.</span><span class="sxs-lookup"><span data-stu-id="0f315-133">[in] The authorization level.</span></span>

`impLevel`\
<span data-ttu-id="0f315-134">'ndaki Kimliğe bürünme düzeyi.</span><span class="sxs-lookup"><span data-stu-id="0f315-134">[in] The impersonation level.</span></span>

`pCurrentNamespace`\
<span data-ttu-id="0f315-135">'ndaki Geçerli ad alanını temsil eden bir [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0f315-135">[in] A pointer to an [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) object that represents the current namespace.</span></span>

`strUser`\
<span data-ttu-id="0f315-136">'ndaki Kullanıcı adı.</span><span class="sxs-lookup"><span data-stu-id="0f315-136">[in] The user name.</span></span> <span data-ttu-id="0f315-137">Daha fazla bilgi için bkz. [Connectserverwmi](connectserverwmi.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="0f315-137">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strPassword`\
<span data-ttu-id="0f315-138">'ndaki Parola.</span><span class="sxs-lookup"><span data-stu-id="0f315-138">[in] The password.</span></span> <span data-ttu-id="0f315-139">Daha fazla bilgi için bkz. [Connectserverwmi](connectserverwmi.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="0f315-139">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strAuthority`\
<span data-ttu-id="0f315-140">'ndaki Kullanıcının etki alanı adı.</span><span class="sxs-lookup"><span data-stu-id="0f315-140">[in] The domain name of the user.</span></span> <span data-ttu-id="0f315-141">Daha fazla bilgi için bkz. [Connectserverwmi](connectserverwmi.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="0f315-141">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="0f315-142">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="0f315-142">Return value</span></span>

<span data-ttu-id="0f315-143">Bu işlev tarafından döndürülen aşağıdaki değerler, *Wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="0f315-143">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="0f315-144">Sabit</span><span class="sxs-lookup"><span data-stu-id="0f315-144">Constant</span></span>  |<span data-ttu-id="0f315-145">Değer</span><span class="sxs-lookup"><span data-stu-id="0f315-145">Value</span></span>  |<span data-ttu-id="0f315-146">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0f315-146">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | <span data-ttu-id="0f315-147">0x80041003</span><span class="sxs-lookup"><span data-stu-id="0f315-147">0x80041003</span></span> | <span data-ttu-id="0f315-148">Kullanıcının işlevin döndüregörüntüleyebileceği bir veya daha fazla sınıfı görüntüleme izni yok.</span><span class="sxs-lookup"><span data-stu-id="0f315-148">The user does not have permission to view one or more of the classes that the function can return.</span></span> |
| `WBEM_E_FAILED` | <span data-ttu-id="0f315-149">0x80041001</span><span class="sxs-lookup"><span data-stu-id="0f315-149">0x80041001</span></span> | <span data-ttu-id="0f315-150">Belirtilmeyen bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="0f315-150">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_CLASS` | <span data-ttu-id="0f315-151">0x80041010</span><span class="sxs-lookup"><span data-stu-id="0f315-151">0x80041010</span></span> | <span data-ttu-id="0f315-152">`strSuperClass` yok.</span><span class="sxs-lookup"><span data-stu-id="0f315-152">`strSuperClass` does not exist.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="0f315-153">0x80041008</span><span class="sxs-lookup"><span data-stu-id="0f315-153">0x80041008</span></span> | <span data-ttu-id="0f315-154">Parametre geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="0f315-154">A parameter is not valid.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="0f315-155">0x80041006</span><span class="sxs-lookup"><span data-stu-id="0f315-155">0x80041006</span></span> | <span data-ttu-id="0f315-156">İşlemi gerçekleştirmek için yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="0f315-156">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_SHUTTING_DOWN` | <span data-ttu-id="0f315-157">0x80041033</span><span class="sxs-lookup"><span data-stu-id="0f315-157">0x80041033</span></span> | <span data-ttu-id="0f315-158">WMI, büyük olasılıkla durmuş ve yeniden başlatılıyor.</span><span class="sxs-lookup"><span data-stu-id="0f315-158">WMI was probably stopped and restarting.</span></span> <span data-ttu-id="0f315-159">[Connectserverwmi](connectserverwmi.md) ' i yeniden çağırın.</span><span class="sxs-lookup"><span data-stu-id="0f315-159">Call [ConnectServerWmi](connectserverwmi.md) again.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="0f315-160">0x80041015</span><span class="sxs-lookup"><span data-stu-id="0f315-160">0x80041015</span></span> | <span data-ttu-id="0f315-161">Geçerli işlem ve WMI arasındaki uzak yordam çağrısı (RPC) bağlantısı başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="0f315-161">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="0f315-162">0</span><span class="sxs-lookup"><span data-stu-id="0f315-162">0</span></span> | <span data-ttu-id="0f315-163">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="0f315-163">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="0f315-164">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0f315-164">Remarks</span></span>

<span data-ttu-id="0f315-165">Bu işlev, [IWbemServices:: CreateClassEnum](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-createclassenum) yöntemi çağrısını sarmalanmış.</span><span class="sxs-lookup"><span data-stu-id="0f315-165">This function wraps a call to the [IWbemServices::CreateClassEnum](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-createclassenum) method.</span></span>

<span data-ttu-id="0f315-166">İşlev çağrısı başarısız olursa, [GetErrorInfo](geterrorinfo.md) işlevini çağırarak ek hata bilgileri alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0f315-166">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="0f315-167">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0f315-167">Requirements</span></span>

<span data-ttu-id="0f315-168">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0f315-168">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="0f315-169">**Üst bilgi:** WMINet_Utils. IDL</span><span class="sxs-lookup"><span data-stu-id="0f315-169">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="0f315-170">**.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="0f315-170">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="0f315-171">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0f315-171">See also</span></span>

- [<span data-ttu-id="0f315-172">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="0f315-172">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
