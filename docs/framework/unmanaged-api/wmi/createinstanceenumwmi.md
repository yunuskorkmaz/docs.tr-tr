---
title: CreateInstanceEnumWmi işlevi (yönetilmeyen API Başvurusu)
description: CreateInstanceEnumWmi işlev seçim ölçütleri karşılayan belirli bir sınıf örneklerini içeren bir numaralandırıcı döndürür.
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
ms.openlocfilehash: db325296d85dc6d4780583731a6cab10fb884fd1
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65636473"
---
# <a name="createinstanceenumwmi-function"></a><span data-ttu-id="5c5c1-103">CreateInstanceEnumWmi işlevi</span><span class="sxs-lookup"><span data-stu-id="5c5c1-103">CreateInstanceEnumWmi function</span></span>

<span data-ttu-id="5c5c1-104">Belirtilen seçim ölçütlerine belirli bir sınıf örneğini döndüren bir numaralandırıcı döndürür.</span><span class="sxs-lookup"><span data-stu-id="5c5c1-104">Returns an enumerator that returns the instances of a specified class that meet specified selection criteria.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="5c5c1-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5c5c1-105">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="5c5c1-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5c5c1-106">Parameters</span></span>

`strFilter`\
<span data-ttu-id="5c5c1-107">[in] Kendisi için örnekleri istenen sınıfı adı.</span><span class="sxs-lookup"><span data-stu-id="5c5c1-107">[in] The name of the class for which instances are desired.</span></span> <span data-ttu-id="5c5c1-108">Bu parametre olamaz `null`.</span><span class="sxs-lookup"><span data-stu-id="5c5c1-108">This parameter cannot be `null`.</span></span>

`lFlags`\
<span data-ttu-id="5c5c1-109">[in] Bu işlevin davranışını etkileyen bayrakların birleşimi.</span><span class="sxs-lookup"><span data-stu-id="5c5c1-109">[in] A combination of flags that affect the behavior of this function.</span></span> <span data-ttu-id="5c5c1-110">Aşağıdaki değerleri tanımlanan *WbemCli.h* üst bilgi dosyası veya tanımlayabilirsiniz bunları sabitleri kodunuzda:</span><span class="sxs-lookup"><span data-stu-id="5c5c1-110">The following values are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="5c5c1-111">Sabit</span><span class="sxs-lookup"><span data-stu-id="5c5c1-111">Constant</span></span>  |<span data-ttu-id="5c5c1-112">Değer</span><span class="sxs-lookup"><span data-stu-id="5c5c1-112">Value</span></span>  |<span data-ttu-id="5c5c1-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5c5c1-113">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | <span data-ttu-id="5c5c1-114">0x20000</span><span class="sxs-lookup"><span data-stu-id="5c5c1-114">0x20000</span></span> | <span data-ttu-id="5c5c1-115">Geçerli bağlantının yerel yerelleştirilmiş ad alanında depolanan değiştirilen niteleyicileri işlev kümesini alır</span><span class="sxs-lookup"><span data-stu-id="5c5c1-115">If set, the function retrieves the amended qualifiers stored in the localized namespace of the current connection's locale.</span></span> <br/> <span data-ttu-id="5c5c1-116">Aksi durumda, küme yalnızca anında ad alanında depolanan niteleyicileri işlevi alır.</span><span class="sxs-lookup"><span data-stu-id="5c5c1-116">If not set, the function retrieves only the qualifiers stored in the immediate namespace.</span></span> |
| `WBEM_FLAG_DEEP` | <span data-ttu-id="5c5c1-117">0</span><span class="sxs-lookup"><span data-stu-id="5c5c1-117">0</span></span> | <span data-ttu-id="5c5c1-118">Numaralandırma hiyerarşi içinde bu ve tüm alt sınıflar içerir.</span><span class="sxs-lookup"><span data-stu-id="5c5c1-118">The enumeration includes this and all subclasses in the hierarchy.</span></span> |
| `WBEM_FLAG_SHALLOW` | <span data-ttu-id="5c5c1-119">1.</span><span class="sxs-lookup"><span data-stu-id="5c5c1-119">1</span></span> | <span data-ttu-id="5c5c1-120">Bu sınıfın yalnızca saf örneklerini içerir ve bu sınıfında bulunmayan özellikleri tedarik alt sınıfların tüm örneklerini dahil değildir.</span><span class="sxs-lookup"><span data-stu-id="5c5c1-120">The enumeration includes only pure instances of this class and excludes all instances of subclasses that supply properties not found in this class.</span></span> |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | <span data-ttu-id="5c5c1-121">0x10</span><span class="sxs-lookup"><span data-stu-id="5c5c1-121">0x10</span></span> | <span data-ttu-id="5c5c1-122">Bayrağı yarı zaman uyumsuz bir çağrı neden olur.</span><span class="sxs-lookup"><span data-stu-id="5c5c1-122">The flag causes a semisynchronous call.</span></span> |
| `WBEM_FLAG_FORWARD_ONLY` | <span data-ttu-id="5c5c1-123">0x20</span><span class="sxs-lookup"><span data-stu-id="5c5c1-123">0x20</span></span> | <span data-ttu-id="5c5c1-124">İşlev yalnızca iletme bir numaralandırıcı döndürür.</span><span class="sxs-lookup"><span data-stu-id="5c5c1-124">The function returns a forward-only enumerator.</span></span> <span data-ttu-id="5c5c1-125">Genellikle, yalnızca iletme numaralandırıcılar daha hızlıdır ve geleneksel numaralandırıcılar daha az bellek kullanır, ancak çağrısına izin verme [kopya](clone.md).</span><span class="sxs-lookup"><span data-stu-id="5c5c1-125">Typically, forward-only enumerators are faster and use less memory than conventional enumerators, but they do not allow calls to [Clone](clone.md).</span></span> |
| `WBEM_FLAG_BIDIRECTIONAL` | <span data-ttu-id="5c5c1-126">0</span><span class="sxs-lookup"><span data-stu-id="5c5c1-126">0</span></span> | <span data-ttu-id="5c5c1-127">Serbest bırakılana kadar WMI numaralandırmada nesnelerine işaretçiler korur.</span><span class="sxs-lookup"><span data-stu-id="5c5c1-127">WMI retains pointers to objects in the enumeration until they are released.</span></span> |

<span data-ttu-id="5c5c1-128">Önerilen bayraklar `WBEM_FLAG_RETURN_IMMEDIATELY` ve `WBEM_FLAG_FORWARD_ONLY` en iyi performans için.</span><span class="sxs-lookup"><span data-stu-id="5c5c1-128">The recommended flags are `WBEM_FLAG_RETURN_IMMEDIATELY` and `WBEM_FLAG_FORWARD_ONLY` for best performance.</span></span>

`pCtx`\
<span data-ttu-id="5c5c1-129">[in] Genellikle, bu değer, `null`.</span><span class="sxs-lookup"><span data-stu-id="5c5c1-129">[in] Typically, this value is `null`.</span></span> <span data-ttu-id="5c5c1-130">Aksi takdirde, bir işaretçi olduğu bir [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) istenen örnekleri sağlayan sağlayıcı tarafından kullanılan bir örnek.</span><span class="sxs-lookup"><span data-stu-id="5c5c1-130">Otherwise, it is a pointer to an [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) instance that may be used by the provider that is providing the requested instances.</span></span>

`ppEnum`\
<span data-ttu-id="5c5c1-131">[out] İşaretçi numaralandırıcıyı alır.</span><span class="sxs-lookup"><span data-stu-id="5c5c1-131">[out] Receives the pointer to the enumerator.</span></span>

`authLevel`\
<span data-ttu-id="5c5c1-132">[in] Yetkilendirme düzeyi.</span><span class="sxs-lookup"><span data-stu-id="5c5c1-132">[in] The authorization level.</span></span>

`impLevel`\
<span data-ttu-id="5c5c1-133">[in] Kimliğe bürünme düzeyi.</span><span class="sxs-lookup"><span data-stu-id="5c5c1-133">[in] The impersonation level.</span></span>

`pCurrentNamespace`\
<span data-ttu-id="5c5c1-134">[in] Bir işaretçi bir [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) geçerli ad alanını temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="5c5c1-134">[in] A pointer to an [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) object that represents the current namespace.</span></span>

`strUser`\
<span data-ttu-id="5c5c1-135">[in] Kullanıcı adı.</span><span class="sxs-lookup"><span data-stu-id="5c5c1-135">[in] The user name.</span></span> <span data-ttu-id="5c5c1-136">Bkz: [ConnectServerWmi](connectserverwmi.md) işlevi daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="5c5c1-136">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strPassword`\
<span data-ttu-id="5c5c1-137">[in] Parola.</span><span class="sxs-lookup"><span data-stu-id="5c5c1-137">[in] The password.</span></span> <span data-ttu-id="5c5c1-138">Bkz: [ConnectServerWmi](connectserverwmi.md) işlevi daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="5c5c1-138">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strAuthority`\
<span data-ttu-id="5c5c1-139">[in] Kullanıcı etki alanı adı.</span><span class="sxs-lookup"><span data-stu-id="5c5c1-139">[in] The domain name of the user.</span></span> <span data-ttu-id="5c5c1-140">Bkz: [ConnectServerWmi](connectserverwmi.md) işlevi daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="5c5c1-140">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="5c5c1-141">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="5c5c1-141">Return value</span></span>

<span data-ttu-id="5c5c1-142">Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üst bilgi dosyası veya tanımlayabilirsiniz bunları sabitleri kodunuzda:</span><span class="sxs-lookup"><span data-stu-id="5c5c1-142">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="5c5c1-143">Sabit</span><span class="sxs-lookup"><span data-stu-id="5c5c1-143">Constant</span></span>  |<span data-ttu-id="5c5c1-144">Değer</span><span class="sxs-lookup"><span data-stu-id="5c5c1-144">Value</span></span>  |<span data-ttu-id="5c5c1-145">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5c5c1-145">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | <span data-ttu-id="5c5c1-146">0x80041003</span><span class="sxs-lookup"><span data-stu-id="5c5c1-146">0x80041003</span></span> | <span data-ttu-id="5c5c1-147">Kullanıcının belirtilen sınıf örneklerini görüntüleme izni yok.</span><span class="sxs-lookup"><span data-stu-id="5c5c1-147">The user does not have permission to view instances of the specified class.</span></span> |
| `WBEM_E_FAILED` | <span data-ttu-id="5c5c1-148">0x80041001</span><span class="sxs-lookup"><span data-stu-id="5c5c1-148">0x80041001</span></span> | <span data-ttu-id="5c5c1-149">Belirtilmeyen bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="5c5c1-149">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_CLASS` | <span data-ttu-id="5c5c1-150">0x80041010</span><span class="sxs-lookup"><span data-stu-id="5c5c1-150">0x80041010</span></span> | <span data-ttu-id="5c5c1-151">`strFilter` mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="5c5c1-151">`strFilter` does not exist.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="5c5c1-152">0x80041008</span><span class="sxs-lookup"><span data-stu-id="5c5c1-152">0x80041008</span></span> | <span data-ttu-id="5c5c1-153">Bir parametre geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="5c5c1-153">A parameter is not valid.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="5c5c1-154">0x80041006</span><span class="sxs-lookup"><span data-stu-id="5c5c1-154">0x80041006</span></span> | <span data-ttu-id="5c5c1-155">İşlemi tamamlamak yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="5c5c1-155">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_SHUTTING_DOWN` | <span data-ttu-id="5c5c1-156">0x80041033</span><span class="sxs-lookup"><span data-stu-id="5c5c1-156">0x80041033</span></span> | <span data-ttu-id="5c5c1-157">WMI, büyük olasılıkla durdu ve yeniden başlatılıyor.</span><span class="sxs-lookup"><span data-stu-id="5c5c1-157">WMI was probably stopped and restarting.</span></span> <span data-ttu-id="5c5c1-158">Çağrı [ConnectServerWmi](connectserverwmi.md) yeniden.</span><span class="sxs-lookup"><span data-stu-id="5c5c1-158">Call [ConnectServerWmi](connectserverwmi.md) again.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="5c5c1-159">0x80041015</span><span class="sxs-lookup"><span data-stu-id="5c5c1-159">0x80041015</span></span> | <span data-ttu-id="5c5c1-160">Geçerli işlem WMI arasındaki uzak yordam çağrısı (RPC) bağlantı başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="5c5c1-160">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="5c5c1-161">0</span><span class="sxs-lookup"><span data-stu-id="5c5c1-161">0</span></span> | <span data-ttu-id="5c5c1-162">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="5c5c1-162">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="5c5c1-163">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5c5c1-163">Remarks</span></span>

<span data-ttu-id="5c5c1-164">Bu işlev bir çağrı sarılır [IWbemServices::CreateClassEnum](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-createinstanceenum) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5c5c1-164">This function wraps a call to the [IWbemServices::CreateClassEnum](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-createinstanceenum) method.</span></span>

<span data-ttu-id="5c5c1-165">Döndürülen Numaralandırıcı sıfır öğeleri sahip olabileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="5c5c1-165">Note that the returned enumerator can have zero elements.</span></span>

<span data-ttu-id="5c5c1-166">İşlev çağrısı başarısız olursa, ek hata bilgileri çağırarak elde edebileceğiniz [Geterrorınfo](geterrorinfo.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="5c5c1-166">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="5c5c1-167">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5c5c1-167">Requirements</span></span>

<span data-ttu-id="5c5c1-168">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5c5c1-168">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="5c5c1-169">**Üst bilgi:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="5c5c1-169">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="5c5c1-170">**.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="5c5c1-170">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="5c5c1-171">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5c5c1-171">See also</span></span>

- [<span data-ttu-id="5c5c1-172">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="5c5c1-172">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
