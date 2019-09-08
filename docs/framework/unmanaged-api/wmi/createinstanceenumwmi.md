---
title: Createınstanceenumwmi işlevi (yönetilmeyen API Başvurusu)
description: Createınstanceenumwmi işlevi, seçim ölçütlerine uyan belirli bir sınıfın örneklerini içeren bir Numaralandırıcı döndürür.
ms.date: 11/06/2017
api_name:
- CreateInstanceEnumWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- CreateInstanceEnumWmi
helpviewer_keywords:
- CreateInstanceEnumWmi function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b7709d9c50a494013ece2f91b3acc213278f0e57
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798910"
---
# <a name="createinstanceenumwmi-function"></a><span data-ttu-id="8c8c6-103">Createınstanceenumwmi işlevi</span><span class="sxs-lookup"><span data-stu-id="8c8c6-103">CreateInstanceEnumWmi function</span></span>

<span data-ttu-id="8c8c6-104">Belirtilen seçim ölçütlerine uyan belirli bir sınıfın örneklerini döndüren bir Numaralandırıcı döndürür.</span><span class="sxs-lookup"><span data-stu-id="8c8c6-104">Returns an enumerator that returns the instances of a specified class that meet specified selection criteria.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="8c8c6-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8c8c6-105">Syntax</span></span>

```cpp
HRESULT CreateInstanceEnumWmi (
   [in] BSTR                    strFilter,
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

## <a name="parameters"></a><span data-ttu-id="8c8c6-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8c8c6-106">Parameters</span></span>

`strFilter`\
<span data-ttu-id="8c8c6-107">'ndaki Örnekleri istenen sınıfın adı.</span><span class="sxs-lookup"><span data-stu-id="8c8c6-107">[in] The name of the class for which instances are desired.</span></span> <span data-ttu-id="8c8c6-108">Bu parametre `null`olamaz.</span><span class="sxs-lookup"><span data-stu-id="8c8c6-108">This parameter cannot be `null`.</span></span>

`lFlags`\
<span data-ttu-id="8c8c6-109">'ndaki Bu işlevin davranışını etkileyen bayrakların birleşimi.</span><span class="sxs-lookup"><span data-stu-id="8c8c6-109">[in] A combination of flags that affect the behavior of this function.</span></span> <span data-ttu-id="8c8c6-110">Aşağıdaki değerler *Wbemcli. h* üstbilgi dosyasında tanımlanmıştır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8c8c6-110">The following values are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="8c8c6-111">Sabit</span><span class="sxs-lookup"><span data-stu-id="8c8c6-111">Constant</span></span>  |<span data-ttu-id="8c8c6-112">Değer</span><span class="sxs-lookup"><span data-stu-id="8c8c6-112">Value</span></span>  |<span data-ttu-id="8c8c6-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8c8c6-113">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | <span data-ttu-id="8c8c6-114">0x20000</span><span class="sxs-lookup"><span data-stu-id="8c8c6-114">0x20000</span></span> | <span data-ttu-id="8c8c6-115">Ayarlanırsa, işlev geçerli bağlantının yerel ayarında yerelleştirilmiş ad alanında depolanan değiştirilmiş niteleyicileri alır.</span><span class="sxs-lookup"><span data-stu-id="8c8c6-115">If set, the function retrieves the amended qualifiers stored in the localized namespace of the current connection's locale.</span></span> <br/> <span data-ttu-id="8c8c6-116">Ayarlanmamışsa, işlev yalnızca anında ad alanında depolanan niteleyicileri alır.</span><span class="sxs-lookup"><span data-stu-id="8c8c6-116">If not set, the function retrieves only the qualifiers stored in the immediate namespace.</span></span> |
| `WBEM_FLAG_DEEP` | <span data-ttu-id="8c8c6-117">0</span><span class="sxs-lookup"><span data-stu-id="8c8c6-117">0</span></span> | <span data-ttu-id="8c8c6-118">Sabit listesi bu ve hiyerarşideki tüm alt sınıfları içerir.</span><span class="sxs-lookup"><span data-stu-id="8c8c6-118">The enumeration includes this and all subclasses in the hierarchy.</span></span> |
| `WBEM_FLAG_SHALLOW` | <span data-ttu-id="8c8c6-119">1\.</span><span class="sxs-lookup"><span data-stu-id="8c8c6-119">1</span></span> | <span data-ttu-id="8c8c6-120">Sabit listesi yalnızca bu sınıfın saf örneklerini içerir ve bu sınıfta bulunmayan özellikleri sağlayan tüm alt sınıfların örneklerini dışlar.</span><span class="sxs-lookup"><span data-stu-id="8c8c6-120">The enumeration includes only pure instances of this class and excludes all instances of subclasses that supply properties not found in this class.</span></span> |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | <span data-ttu-id="8c8c6-121">0x10</span><span class="sxs-lookup"><span data-stu-id="8c8c6-121">0x10</span></span> | <span data-ttu-id="8c8c6-122">Bayrak, yarı zaman uyumlu bir çağrıya neden olur.</span><span class="sxs-lookup"><span data-stu-id="8c8c6-122">The flag causes a semisynchronous call.</span></span> |
| `WBEM_FLAG_FORWARD_ONLY` | <span data-ttu-id="8c8c6-123">0x20</span><span class="sxs-lookup"><span data-stu-id="8c8c6-123">0x20</span></span> | <span data-ttu-id="8c8c6-124">İşlev, salt ileri bir Numaralandırıcı döndürür.</span><span class="sxs-lookup"><span data-stu-id="8c8c6-124">The function returns a forward-only enumerator.</span></span> <span data-ttu-id="8c8c6-125">Genellikle, yalnızca ileri Numaralandırıcılar daha hızlıdır ve geleneksel numaralandırıcılardan daha az bellek kullanır, ancak [kopyalama](clone.md)çağrılarına izin vermez.</span><span class="sxs-lookup"><span data-stu-id="8c8c6-125">Typically, forward-only enumerators are faster and use less memory than conventional enumerators, but they do not allow calls to [Clone](clone.md).</span></span> |
| `WBEM_FLAG_BIDIRECTIONAL` | <span data-ttu-id="8c8c6-126">0</span><span class="sxs-lookup"><span data-stu-id="8c8c6-126">0</span></span> | <span data-ttu-id="8c8c6-127">WMI, serbest bırakılana kadar Numaralandırmadaki nesnelere işaretçiler tutar.</span><span class="sxs-lookup"><span data-stu-id="8c8c6-127">WMI retains pointers to objects in the enumeration until they are released.</span></span> |

<span data-ttu-id="8c8c6-128">Önerilen bayraklar `WBEM_FLAG_RETURN_IMMEDIATELY` ve `WBEM_FLAG_FORWARD_ONLY` en iyi performans için.</span><span class="sxs-lookup"><span data-stu-id="8c8c6-128">The recommended flags are `WBEM_FLAG_RETURN_IMMEDIATELY` and `WBEM_FLAG_FORWARD_ONLY` for best performance.</span></span>

`pCtx`\
<span data-ttu-id="8c8c6-129">'ndaki Genellikle, bu değer `null`.</span><span class="sxs-lookup"><span data-stu-id="8c8c6-129">[in] Typically, this value is `null`.</span></span> <span data-ttu-id="8c8c6-130">Aksi takdirde, istenen örnekleri sağlayan sağlayıcı tarafından kullanılabilecek bir [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) örneğine yönelik bir işaretçidir.</span><span class="sxs-lookup"><span data-stu-id="8c8c6-130">Otherwise, it is a pointer to an [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) instance that may be used by the provider that is providing the requested instances.</span></span>

`ppEnum`\
<span data-ttu-id="8c8c6-131">dışı Numaralandırıcı için işaretçiyi alır.</span><span class="sxs-lookup"><span data-stu-id="8c8c6-131">[out] Receives the pointer to the enumerator.</span></span>

`authLevel`\
<span data-ttu-id="8c8c6-132">'ndaki Yetkilendirme düzeyi.</span><span class="sxs-lookup"><span data-stu-id="8c8c6-132">[in] The authorization level.</span></span>

`impLevel`\
<span data-ttu-id="8c8c6-133">'ndaki Kimliğe bürünme düzeyi.</span><span class="sxs-lookup"><span data-stu-id="8c8c6-133">[in] The impersonation level.</span></span>

`pCurrentNamespace`\
<span data-ttu-id="8c8c6-134">'ndaki Geçerli ad alanını temsil eden bir [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="8c8c6-134">[in] A pointer to an [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) object that represents the current namespace.</span></span>

`strUser`\
<span data-ttu-id="8c8c6-135">'ndaki Kullanıcı adı.</span><span class="sxs-lookup"><span data-stu-id="8c8c6-135">[in] The user name.</span></span> <span data-ttu-id="8c8c6-136">Daha fazla bilgi için bkz. [Connectserverwmi](connectserverwmi.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="8c8c6-136">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strPassword`\
<span data-ttu-id="8c8c6-137">'ndaki Parola.</span><span class="sxs-lookup"><span data-stu-id="8c8c6-137">[in] The password.</span></span> <span data-ttu-id="8c8c6-138">Daha fazla bilgi için bkz. [Connectserverwmi](connectserverwmi.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="8c8c6-138">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strAuthority`\
<span data-ttu-id="8c8c6-139">'ndaki Kullanıcının etki alanı adı.</span><span class="sxs-lookup"><span data-stu-id="8c8c6-139">[in] The domain name of the user.</span></span> <span data-ttu-id="8c8c6-140">Daha fazla bilgi için bkz. [Connectserverwmi](connectserverwmi.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="8c8c6-140">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="8c8c6-141">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="8c8c6-141">Return value</span></span>

<span data-ttu-id="8c8c6-142">Bu işlev tarafından döndürülen aşağıdaki değerler, *Wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8c8c6-142">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="8c8c6-143">Sabit</span><span class="sxs-lookup"><span data-stu-id="8c8c6-143">Constant</span></span>  |<span data-ttu-id="8c8c6-144">Değer</span><span class="sxs-lookup"><span data-stu-id="8c8c6-144">Value</span></span>  |<span data-ttu-id="8c8c6-145">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8c8c6-145">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | <span data-ttu-id="8c8c6-146">0x80041003</span><span class="sxs-lookup"><span data-stu-id="8c8c6-146">0x80041003</span></span> | <span data-ttu-id="8c8c6-147">Kullanıcının belirtilen sınıfın örneklerini görüntüleme izni yok.</span><span class="sxs-lookup"><span data-stu-id="8c8c6-147">The user does not have permission to view instances of the specified class.</span></span> |
| `WBEM_E_FAILED` | <span data-ttu-id="8c8c6-148">0x80041001</span><span class="sxs-lookup"><span data-stu-id="8c8c6-148">0x80041001</span></span> | <span data-ttu-id="8c8c6-149">Belirtilmeyen bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="8c8c6-149">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_CLASS` | <span data-ttu-id="8c8c6-150">0x80041010</span><span class="sxs-lookup"><span data-stu-id="8c8c6-150">0x80041010</span></span> | <span data-ttu-id="8c8c6-151">`strFilter`yok.</span><span class="sxs-lookup"><span data-stu-id="8c8c6-151">`strFilter` does not exist.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="8c8c6-152">0x80041008</span><span class="sxs-lookup"><span data-stu-id="8c8c6-152">0x80041008</span></span> | <span data-ttu-id="8c8c6-153">Parametre geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="8c8c6-153">A parameter is not valid.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="8c8c6-154">0x80041006</span><span class="sxs-lookup"><span data-stu-id="8c8c6-154">0x80041006</span></span> | <span data-ttu-id="8c8c6-155">İşlemi gerçekleştirmek için yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="8c8c6-155">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_SHUTTING_DOWN` | <span data-ttu-id="8c8c6-156">0x80041033</span><span class="sxs-lookup"><span data-stu-id="8c8c6-156">0x80041033</span></span> | <span data-ttu-id="8c8c6-157">WMI, büyük olasılıkla durmuş ve yeniden başlatılıyor.</span><span class="sxs-lookup"><span data-stu-id="8c8c6-157">WMI was probably stopped and restarting.</span></span> <span data-ttu-id="8c8c6-158">[Connectserverwmi](connectserverwmi.md) ' i yeniden çağırın.</span><span class="sxs-lookup"><span data-stu-id="8c8c6-158">Call [ConnectServerWmi](connectserverwmi.md) again.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="8c8c6-159">0x80041015</span><span class="sxs-lookup"><span data-stu-id="8c8c6-159">0x80041015</span></span> | <span data-ttu-id="8c8c6-160">Geçerli işlem ve WMI arasındaki uzak yordam çağrısı (RPC) bağlantısı başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="8c8c6-160">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="8c8c6-161">0</span><span class="sxs-lookup"><span data-stu-id="8c8c6-161">0</span></span> | <span data-ttu-id="8c8c6-162">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="8c8c6-162">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="8c8c6-163">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8c8c6-163">Remarks</span></span>

<span data-ttu-id="8c8c6-164">Bu işlev, [IWbemServices:: CreateClassEnum](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-createinstanceenum) yöntemi çağrısını sarmalanmış.</span><span class="sxs-lookup"><span data-stu-id="8c8c6-164">This function wraps a call to the [IWbemServices::CreateClassEnum](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-createinstanceenum) method.</span></span>

<span data-ttu-id="8c8c6-165">Döndürülen Numaralandırıcı sıfır öğelerine sahip olabileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="8c8c6-165">Note that the returned enumerator can have zero elements.</span></span>

<span data-ttu-id="8c8c6-166">İşlev çağrısı başarısız olursa, [GetErrorInfo](geterrorinfo.md) işlevini çağırarak ek hata bilgileri alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8c8c6-166">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="8c8c6-167">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8c8c6-167">Requirements</span></span>

<span data-ttu-id="8c8c6-168">**Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8c8c6-168">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="8c8c6-169">**Üst bilgi** WMINet_Utils. IDL</span><span class="sxs-lookup"><span data-stu-id="8c8c6-169">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="8c8c6-170">**.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="8c8c6-170">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="8c8c6-171">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8c8c6-171">See also</span></span>

- [<span data-ttu-id="8c8c6-172">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="8c8c6-172">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
