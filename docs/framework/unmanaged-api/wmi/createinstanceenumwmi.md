---
title: "CreateInstanceEnumWmi işlevi (yönetilmeyen API Başvurusu)"
description: "CreateInstanceEnumWmi işlevi seçim ölçütleri karşılayan belirli bir sınıf örneklerini içeren bir numaralandırıcı döndürür."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: CreateInstanceEnumWmi
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: CreateInstanceEnumWmi
helpviewer_keywords: CreateInstanceEnumWmi function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 19a4102796da7a5692eb5b9b459a6a95ff7409f9
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/15/2017
---
# <a name="createinstanceenumwmi-function"></a><span data-ttu-id="d2fc3-103">CreateInstanceEnumWmi işlevi</span><span class="sxs-lookup"><span data-stu-id="d2fc3-103">CreateInstanceEnumWmi function</span></span>
<span data-ttu-id="d2fc3-104">Belirtilen seçim ölçütleri karşılayan belirli bir sınıf örneklerini döndüren bir numaralandırıcı döndürür.</span><span class="sxs-lookup"><span data-stu-id="d2fc3-104">Returns an enumerator that returns the instances of a specified class that meet specified selection criteria.</span></span> 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="d2fc3-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d2fc3-105">Syntax</span></span>  
  
```  
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

## <a name="parameters"></a><span data-ttu-id="d2fc3-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d2fc3-106">Parameters</span></span>

`strFilter`    
<span data-ttu-id="d2fc3-107">[in] Örnekleri istenen sınıfın adı.</span><span class="sxs-lookup"><span data-stu-id="d2fc3-107">[in] The name of the class for which instances are desired.</span></span> <span data-ttu-id="d2fc3-108">Bu parametre olamaz `null`.</span><span class="sxs-lookup"><span data-stu-id="d2fc3-108">This parameter cannot be `null`.</span></span>

`lFlags`   
<span data-ttu-id="d2fc3-109">[in] Bu işlev davranışını etkileyen bayrak birleşimi.</span><span class="sxs-lookup"><span data-stu-id="d2fc3-109">[in] A combination of flags that affect the behavior of this function.</span></span> <span data-ttu-id="d2fc3-110">Aşağıdaki değerleri tanımlanan *WbemCli.h* üstbilgi dosyası, veya tanımlayabilirsiniz bunları sabitleri kodunuzda:</span><span class="sxs-lookup"><span data-stu-id="d2fc3-110">The following values are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span> 

|<span data-ttu-id="d2fc3-111">Sabit</span><span class="sxs-lookup"><span data-stu-id="d2fc3-111">Constant</span></span>  |<span data-ttu-id="d2fc3-112">Değer</span><span class="sxs-lookup"><span data-stu-id="d2fc3-112">Value</span></span>  |<span data-ttu-id="d2fc3-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d2fc3-113">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | <span data-ttu-id="d2fc3-114">0x20000</span><span class="sxs-lookup"><span data-stu-id="d2fc3-114">0x20000</span></span> | <span data-ttu-id="d2fc3-115">Geçerli bağlantının yerel yerelleştirilmiş ad alanında depolanan değiştirilen niteleyicileri kümesi, işlevi alır</span><span class="sxs-lookup"><span data-stu-id="d2fc3-115">If set, the function retrieves the amended qualifiers stored in the localized namespace of the current connection's locale.</span></span> <br/> <span data-ttu-id="d2fc3-116">Aksi durumda kümesi işlevi yalnızca hemen ad alanında depolanan niteleyicileri alır.</span><span class="sxs-lookup"><span data-stu-id="d2fc3-116">If not set, the function retrieves only the qualifiers stored in the immediate namespace.</span></span> |
| `WBEM_FLAG_DEEP` | <span data-ttu-id="d2fc3-117">0</span><span class="sxs-lookup"><span data-stu-id="d2fc3-117">0</span></span> | <span data-ttu-id="d2fc3-118">Numaralandırma hiyerarşi içinde bu ve tüm alt sınıflar içerir.</span><span class="sxs-lookup"><span data-stu-id="d2fc3-118">The enumeration includes this and all subclasses in the hierarchy.</span></span> |
| `WBEM_FLAG_SHALLOW` | <span data-ttu-id="d2fc3-119">1.</span><span class="sxs-lookup"><span data-stu-id="d2fc3-119">1</span></span> | <span data-ttu-id="d2fc3-120">Numaralandırma yalnızca saf bu sınıfın örnekleri içerir ve bu sınıfında bulunmayan özellikleri tedarik alt sınıfların tüm örneklerini dışlar.</span><span class="sxs-lookup"><span data-stu-id="d2fc3-120">The enumeration includes only pure instances of this class and excludes all instances of subclasses that supply properties not found in this class.</span></span> |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | <span data-ttu-id="d2fc3-121">0x10</span><span class="sxs-lookup"><span data-stu-id="d2fc3-121">0x10</span></span> | <span data-ttu-id="d2fc3-122">Bayrağı yarı zaman uyumlu bir çağrı neden olur.</span><span class="sxs-lookup"><span data-stu-id="d2fc3-122">The flag causes a semisynchronous call.</span></span> |
| `WBEM_FLAG_FORWARD_ONLY` | <span data-ttu-id="d2fc3-123">0x20</span><span class="sxs-lookup"><span data-stu-id="d2fc3-123">0x20</span></span> | <span data-ttu-id="d2fc3-124">İşlevi yalnızca ileri bir numaralandırıcı döndürür.</span><span class="sxs-lookup"><span data-stu-id="d2fc3-124">The function returns a forward-only enumerator.</span></span> <span data-ttu-id="d2fc3-125">Genellikle, yalnızca ileri numaralandırıcılar daha hızlı ve geleneksel numaralandırıcılar daha az bellek kullanır, ancak çağrıları izin verme [kopya](clone.md).</span><span class="sxs-lookup"><span data-stu-id="d2fc3-125">Typically, forward-only enumerators are faster and use less memory than conventional enumerators, but they do not allow calls to [Clone](clone.md).</span></span> |
| `WBEM_FLAG_BIDIRECTIONAL` | <span data-ttu-id="d2fc3-126">0</span><span class="sxs-lookup"><span data-stu-id="d2fc3-126">0</span></span> | <span data-ttu-id="d2fc3-127">Serbest bırakılana kadar WMI enumration nesnelerine işaretçiler korur.</span><span class="sxs-lookup"><span data-stu-id="d2fc3-127">WMI retains pointers to objects in the enumration until they are released.</span></span> | 

<span data-ttu-id="d2fc3-128">Önerilen bayraklar `WBEM_FLAG_RETURN_IMMEDIATELY` ve `WBEM_FLAG_FORWARD_ONLY` en iyi performans için.</span><span class="sxs-lookup"><span data-stu-id="d2fc3-128">The recommended flags are `WBEM_FLAG_RETURN_IMMEDIATELY` and `WBEM_FLAG_FORWARD_ONLY` for best performance.</span></span>

`pCtx`  
<span data-ttu-id="d2fc3-129">[in] Bu değer genellikle `null`.</span><span class="sxs-lookup"><span data-stu-id="d2fc3-129">[in] Typically, this value is `null`.</span></span> <span data-ttu-id="d2fc3-130">Aksi takdirde, gösteren bir işaretçidir bir [IWbemContext](https://msdn.microsoft.com/library/aa391465(v=vs.85).aspx) istenen örnekleri sağlayarak sağlayıcı tarafından kullanılan örnek.</span><span class="sxs-lookup"><span data-stu-id="d2fc3-130">Otherwise, it is a pointer to an [IWbemContext](https://msdn.microsoft.com/library/aa391465(v=vs.85).aspx) instance that may be used by the provider that is providing the requested instances.</span></span>

`ppEnum`  
<span data-ttu-id="d2fc3-131">[out] İşaretçi Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="d2fc3-131">[out] Receives the pointer to the enumerator.</span></span>

`authLevel`  
<span data-ttu-id="d2fc3-132">[in] Kimlik doğrulama düzeyi.</span><span class="sxs-lookup"><span data-stu-id="d2fc3-132">[in] The authorization level.</span></span>

<span data-ttu-id="d2fc3-133">`impLevel`[in] Kimliğe bürünme düzeyi.</span><span class="sxs-lookup"><span data-stu-id="d2fc3-133">`impLevel` [in] The impersonation level.</span></span>

`pCurrentNamespace`   
<span data-ttu-id="d2fc3-134">[in] Bir işaretçi bir [IWbemServices](https://msdn.microsoft.com/library/aa392093(v=vs.85).aspx) geçerli ad alanını temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="d2fc3-134">[in] A pointer to an [IWbemServices](https://msdn.microsoft.com/library/aa392093(v=vs.85).aspx) object that represents the current namespace.</span></span>

`strUser`   
<span data-ttu-id="d2fc3-135">[in] Kullanıcı adı.</span><span class="sxs-lookup"><span data-stu-id="d2fc3-135">[in] The user name.</span></span> <span data-ttu-id="d2fc3-136">Bkz: [ConnectServerWmi](connectserverwmi.md) daha fazla bilgi için işlevi.</span><span class="sxs-lookup"><span data-stu-id="d2fc3-136">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strPassword`   
<span data-ttu-id="d2fc3-137">[in] Parola.</span><span class="sxs-lookup"><span data-stu-id="d2fc3-137">[in] The password.</span></span> <span data-ttu-id="d2fc3-138">Bkz: [ConnectServerWmi](connectserverwmi.md) daha fazla bilgi için işlevi.</span><span class="sxs-lookup"><span data-stu-id="d2fc3-138">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strAuthority`   
<span data-ttu-id="d2fc3-139">[in] Kullanıcının etki alanı adı.</span><span class="sxs-lookup"><span data-stu-id="d2fc3-139">[in] The domain name of the user.</span></span> <span data-ttu-id="d2fc3-140">Bkz: [ConnectServerWmi](connectserverwmi.md) daha fazla bilgi için işlevi.</span><span class="sxs-lookup"><span data-stu-id="d2fc3-140">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="d2fc3-141">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="d2fc3-141">Return value</span></span>

<span data-ttu-id="d2fc3-142">Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üstbilgi dosyası, veya tanımlayabilirsiniz bunları sabitleri kodunuzda:</span><span class="sxs-lookup"><span data-stu-id="d2fc3-142">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="d2fc3-143">Sabit</span><span class="sxs-lookup"><span data-stu-id="d2fc3-143">Constant</span></span>  |<span data-ttu-id="d2fc3-144">Değer</span><span class="sxs-lookup"><span data-stu-id="d2fc3-144">Value</span></span>  |<span data-ttu-id="d2fc3-145">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d2fc3-145">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | <span data-ttu-id="d2fc3-146">0x80041003</span><span class="sxs-lookup"><span data-stu-id="d2fc3-146">0x80041003</span></span> | <span data-ttu-id="d2fc3-147">Kullanıcının belirtilen sınıf örneklerini görüntülemek için izni yok.</span><span class="sxs-lookup"><span data-stu-id="d2fc3-147">The user does not have permission to view instances of the specified class.</span></span> |
| `WBEM_E_FAILED` | <span data-ttu-id="d2fc3-148">0x80041001</span><span class="sxs-lookup"><span data-stu-id="d2fc3-148">0x80041001</span></span> | <span data-ttu-id="d2fc3-149">Belirlenemeyen bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="d2fc3-149">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_CLASS` | <span data-ttu-id="d2fc3-150">0x80041010</span><span class="sxs-lookup"><span data-stu-id="d2fc3-150">0x80041010</span></span> | <span data-ttu-id="d2fc3-151">`strFilter`mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="d2fc3-151">`strFilter` does not exist.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="d2fc3-152">0x80041008</span><span class="sxs-lookup"><span data-stu-id="d2fc3-152">0x80041008</span></span> | <span data-ttu-id="d2fc3-153">Parametre geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="d2fc3-153">A parameter is not valid.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="d2fc3-154">0x80041006</span><span class="sxs-lookup"><span data-stu-id="d2fc3-154">0x80041006</span></span> | <span data-ttu-id="d2fc3-155">İşlemi tamamlamak yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="d2fc3-155">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_SHUTTING_DOWN` | <span data-ttu-id="d2fc3-156">0x80041033</span><span class="sxs-lookup"><span data-stu-id="d2fc3-156">0x80041033</span></span> | <span data-ttu-id="d2fc3-157">WMI, büyük olasılıkla durduruldu ve yeniden başlatma.</span><span class="sxs-lookup"><span data-stu-id="d2fc3-157">WMI was probably stopped and restarting.</span></span> <span data-ttu-id="d2fc3-158">Çağrı [ConnectServerWmi](connectserverwmi.md) yeniden.</span><span class="sxs-lookup"><span data-stu-id="d2fc3-158">Call [ConnectServerWmi](connectserverwmi.md) again.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="d2fc3-159">0x80041015</span><span class="sxs-lookup"><span data-stu-id="d2fc3-159">0x80041015</span></span> | <span data-ttu-id="d2fc3-160">Geçerli işlem ile WMI arasındaki uzak yordam çağrısı (RPC) bağlantı başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="d2fc3-160">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="d2fc3-161">0</span><span class="sxs-lookup"><span data-stu-id="d2fc3-161">0</span></span> | <span data-ttu-id="d2fc3-162">İşlev çağrısı başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="d2fc3-162">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="d2fc3-163">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d2fc3-163">Remarks</span></span>

<span data-ttu-id="d2fc3-164">Bu işlev çağrısı sarmalar [IWbemServices::CreateClassEnum](https://msdn.microsoft.com/library/aa392097(v=vs.85).aspx) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d2fc3-164">This function wraps a call to the [IWbemServices::CreateClassEnum](https://msdn.microsoft.com/library/aa392097(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="d2fc3-165">Döndürülen Numaralandırıcı sıfır öğeleri gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="d2fc3-165">Note that the returned enumerator can have zero elements.</span></span>

<span data-ttu-id="d2fc3-166">İşlev çağrısı başarısız olursa, çağırarak ek hata bilgileri elde edebileceğiniz [Geterrorınfo](geterrorinfo.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="d2fc3-166">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="d2fc3-167">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d2fc3-167">Requirements</span></span>  
 <span data-ttu-id="d2fc3-168">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d2fc3-168">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2fc3-169">**Başlık:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="d2fc3-169">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="d2fc3-170">**.NET framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="d2fc3-170">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2fc3-171">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d2fc3-171">See also</span></span>  
[<span data-ttu-id="d2fc3-172">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="d2fc3-172">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
