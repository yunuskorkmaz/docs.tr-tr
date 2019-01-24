---
title: CreateClassEnumWmi işlevi (yönetilmeyen API Başvurusu)
description: CreateClassEnumWmi işlevi, belirtilen ölçütleri karşılayan tüm sınıflar için bir numaralandırıcı döndürür.
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2fc8b25465657ba41220d4a19e10aa06b0e30e86
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54733044"
---
# <a name="createclassenumwmi-function"></a><span data-ttu-id="d9c02-103">CreateClassEnumWmi işlevi</span><span class="sxs-lookup"><span data-stu-id="d9c02-103">CreateClassEnumWmi function</span></span>
<span data-ttu-id="d9c02-104">Belirtilen seçim kriterleri karşılayan tüm sınıflar için bir numaralandırıcı döndürür.</span><span class="sxs-lookup"><span data-stu-id="d9c02-104">Returns an enumerator for all classes that satisfy the specified selection criteria.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="d9c02-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d9c02-105">Syntax</span></span>  
  
```  
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

## <a name="parameters"></a><span data-ttu-id="d9c02-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d9c02-106">Parameters</span></span>

`strSuperclass`    
<span data-ttu-id="d9c02-107">[in] Aksi takdirde `null` veya boş, bir üst sınıf; adını belirtir. yalnızca alt sınıfları bu sınıftan bir numaralandırıcı döndürür.</span><span class="sxs-lookup"><span data-stu-id="d9c02-107">[in] If not `null` or blank, specifies the name of a parent class; the enumerator returns only subclasses of this class.</span></span> <span data-ttu-id="d9c02-108">Eğer öyleyse `null` veya boş ve `lFlags` WBEM_FLAG_SHALLOW ise, yalnızca üst düzey sınıflar (hiçbir üst sınıf ile sınıflar) döndürür.</span><span class="sxs-lookup"><span data-stu-id="d9c02-108">If it is `null` or blank and `lFlags` is WBEM_FLAG_SHALLOW, returns only top-level classes (classes with no parent class).</span></span> <span data-ttu-id="d9c02-109">Eğer öyleyse `null` veya boş ve `lFlags` olduğu `WBEM_FLAG_DEEP`, ad alanındaki tüm sınıfları döndürür.</span><span class="sxs-lookup"><span data-stu-id="d9c02-109">If it is `null` or blank and `lFlags` is `WBEM_FLAG_DEEP`, returns all classes in the namespace.</span></span>

`lFlags`   
<span data-ttu-id="d9c02-110">[in] Bu işlevin davranışını etkileyen bayrakların birleşimi.</span><span class="sxs-lookup"><span data-stu-id="d9c02-110">[in] A combination of flags that affect the behavior of this function.</span></span> <span data-ttu-id="d9c02-111">Aşağıdaki değerleri tanımlanan *WbemCli.h* üst bilgi dosyası veya tanımlayabilirsiniz bunları sabitleri kodunuzda:</span><span class="sxs-lookup"><span data-stu-id="d9c02-111">The following values are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span> 

|<span data-ttu-id="d9c02-112">Sabit</span><span class="sxs-lookup"><span data-stu-id="d9c02-112">Constant</span></span>  |<span data-ttu-id="d9c02-113">Değer</span><span class="sxs-lookup"><span data-stu-id="d9c02-113">Value</span></span>  |<span data-ttu-id="d9c02-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d9c02-114">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | <span data-ttu-id="d9c02-115">0x20000</span><span class="sxs-lookup"><span data-stu-id="d9c02-115">0x20000</span></span> | <span data-ttu-id="d9c02-116">Geçerli bağlantının yerel yerelleştirilmiş ad alanında depolanan değiştirilen niteleyicileri işlev kümesini alır</span><span class="sxs-lookup"><span data-stu-id="d9c02-116">If set, the function retrieves the amended qualifiers stored in the localized namespace of the current connection's locale.</span></span> <br/> <span data-ttu-id="d9c02-117">Aksi durumda, küme yalnızca anında ad alanında depolanan niteleyicileri işlevi alır.</span><span class="sxs-lookup"><span data-stu-id="d9c02-117">If not set, the function retrieves only the qualifiers stored in the immediate namespace.</span></span> |
| `WBEM_FLAG_DEEP` | <span data-ttu-id="d9c02-118">0</span><span class="sxs-lookup"><span data-stu-id="d9c02-118">0</span></span> | <span data-ttu-id="d9c02-119">Numaralandırma, hiyerarşi, ancak bu sınıfın tüm alt sınıflar içerir.</span><span class="sxs-lookup"><span data-stu-id="d9c02-119">The enumeration includes all subclasses in the hierarchy, but not this class.</span></span> |
| `WBEM_FLAG_SHALLOW` | <span data-ttu-id="d9c02-120">1.</span><span class="sxs-lookup"><span data-stu-id="d9c02-120">1</span></span> | <span data-ttu-id="d9c02-121">Bu sınıfın yalnızca saf örneklerini içerir ve bu sınıfında bulunmayan özellikleri tedarik alt sınıfların tüm örneklerini dahil değildir.</span><span class="sxs-lookup"><span data-stu-id="d9c02-121">The enumeration includes only pure instances of this class and excludes all instances of subclasses that supply properties not found in this class.</span></span> |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | <span data-ttu-id="d9c02-122">0x10</span><span class="sxs-lookup"><span data-stu-id="d9c02-122">0x10</span></span> | <span data-ttu-id="d9c02-123">Bayrağı yarı zaman uyumsuz bir çağrı neden olur.</span><span class="sxs-lookup"><span data-stu-id="d9c02-123">The flag causes a semisynchronous call.</span></span> |
| `WBEM_FLAG_FORWARD_ONLY` | <span data-ttu-id="d9c02-124">0x20</span><span class="sxs-lookup"><span data-stu-id="d9c02-124">0x20</span></span> | <span data-ttu-id="d9c02-125">İşlev yalnızca iletme bir numaralandırıcı döndürür.</span><span class="sxs-lookup"><span data-stu-id="d9c02-125">The function returns a forward-only enumerator.</span></span> <span data-ttu-id="d9c02-126">Genellikle, yalnızca iletme numaralandırıcılar daha hızlıdır ve geleneksel numaralandırıcılar daha az bellek kullanır, ancak çağrısına izin verme [kopya](clone.md).</span><span class="sxs-lookup"><span data-stu-id="d9c02-126">Typically, forward-only enumerators are faster and use less memory than conventional enumerators, but they do not allow calls to [Clone](clone.md).</span></span> |
| `WBEM_FLAG_BIDIRECTIONAL` | <span data-ttu-id="d9c02-127">0</span><span class="sxs-lookup"><span data-stu-id="d9c02-127">0</span></span> | <span data-ttu-id="d9c02-128">Serbest bırakılana kadar WMI enumration nesnelerine işaretçiler korur.</span><span class="sxs-lookup"><span data-stu-id="d9c02-128">WMI retains pointers to objects in the enumration until they are released.</span></span> | 

<span data-ttu-id="d9c02-129">Önerilen bayraklar `WBEM_FLAG_RETURN_IMMEDIATELY` ve `WBEM_FLAG_FORWARD_ONLY` en iyi performans için.</span><span class="sxs-lookup"><span data-stu-id="d9c02-129">The recommended flags are `WBEM_FLAG_RETURN_IMMEDIATELY` and `WBEM_FLAG_FORWARD_ONLY` for best performance.</span></span>

`pCtx`  
<span data-ttu-id="d9c02-130">[in] Genellikle, bu değer, `null`.</span><span class="sxs-lookup"><span data-stu-id="d9c02-130">[in] Typically, this value is `null`.</span></span> <span data-ttu-id="d9c02-131">Aksi takdirde, bir işaretçi olduğu bir [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) istenen sınıfları sağlayan sağlayıcı tarafından kullanılan bir örnek.</span><span class="sxs-lookup"><span data-stu-id="d9c02-131">Otherwise, it is a pointer to an [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) instance that can be used by the provider that is providing the requested classes.</span></span> 

`ppEnum`  
<span data-ttu-id="d9c02-132">[out] İşaretçi numaralandırıcıyı alır.</span><span class="sxs-lookup"><span data-stu-id="d9c02-132">[out] Receives the pointer to the enumerator.</span></span>

`authLevel`  
<span data-ttu-id="d9c02-133">[in] Yetkilendirme düzeyi.</span><span class="sxs-lookup"><span data-stu-id="d9c02-133">[in] The authorization level.</span></span>

<span data-ttu-id="d9c02-134">`impLevel` [in] Kimliğe bürünme düzeyi.</span><span class="sxs-lookup"><span data-stu-id="d9c02-134">`impLevel` [in] The impersonation level.</span></span>

`pCurrentNamespace`   
<span data-ttu-id="d9c02-135">[in] Bir işaretçi bir [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) geçerli ad alanını temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="d9c02-135">[in] A pointer to an [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) object that represents the current namespace.</span></span>

`strUser`   
<span data-ttu-id="d9c02-136">[in] Kullanıcı adı.</span><span class="sxs-lookup"><span data-stu-id="d9c02-136">[in] The user name.</span></span> <span data-ttu-id="d9c02-137">Bkz: [ConnectServerWmi](connectserverwmi.md) işlevi daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="d9c02-137">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strPassword`   
<span data-ttu-id="d9c02-138">[in] Parola.</span><span class="sxs-lookup"><span data-stu-id="d9c02-138">[in] The password.</span></span> <span data-ttu-id="d9c02-139">Bkz: [ConnectServerWmi](connectserverwmi.md) işlevi daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="d9c02-139">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strAuthority`   
<span data-ttu-id="d9c02-140">[in] Kullanıcı etki alanı adı.</span><span class="sxs-lookup"><span data-stu-id="d9c02-140">[in] The domain name of the user.</span></span> <span data-ttu-id="d9c02-141">Bkz: [ConnectServerWmi](connectserverwmi.md) işlevi daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="d9c02-141">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="d9c02-142">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="d9c02-142">Return value</span></span>

<span data-ttu-id="d9c02-143">Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üst bilgi dosyası veya tanımlayabilirsiniz bunları sabitleri kodunuzda:</span><span class="sxs-lookup"><span data-stu-id="d9c02-143">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="d9c02-144">Sabit</span><span class="sxs-lookup"><span data-stu-id="d9c02-144">Constant</span></span>  |<span data-ttu-id="d9c02-145">Değer</span><span class="sxs-lookup"><span data-stu-id="d9c02-145">Value</span></span>  |<span data-ttu-id="d9c02-146">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d9c02-146">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | <span data-ttu-id="d9c02-147">0x80041003</span><span class="sxs-lookup"><span data-stu-id="d9c02-147">0x80041003</span></span> | <span data-ttu-id="d9c02-148">Kullanıcı, bir veya daha fazla işlev döndürebilir sınıfları görüntüleme izni yok.</span><span class="sxs-lookup"><span data-stu-id="d9c02-148">The user does not have permission to view one or more of the classes that the function can return.</span></span> |
| `WBEM_E_FAILED` | <span data-ttu-id="d9c02-149">0x80041001</span><span class="sxs-lookup"><span data-stu-id="d9c02-149">0x80041001</span></span> | <span data-ttu-id="d9c02-150">Belirtilmeyen bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="d9c02-150">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_CLASS` | <span data-ttu-id="d9c02-151">0x80041010</span><span class="sxs-lookup"><span data-stu-id="d9c02-151">0x80041010</span></span> | <span data-ttu-id="d9c02-152">`strSuperClass` mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="d9c02-152">`strSuperClass` does not exist.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="d9c02-153">0x80041008</span><span class="sxs-lookup"><span data-stu-id="d9c02-153">0x80041008</span></span> | <span data-ttu-id="d9c02-154">Bir parametre geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="d9c02-154">A parameter is not valid.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="d9c02-155">0x80041006</span><span class="sxs-lookup"><span data-stu-id="d9c02-155">0x80041006</span></span> | <span data-ttu-id="d9c02-156">İşlemi tamamlamak yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="d9c02-156">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_SHUTTING_DOWN` | <span data-ttu-id="d9c02-157">0x80041033</span><span class="sxs-lookup"><span data-stu-id="d9c02-157">0x80041033</span></span> | <span data-ttu-id="d9c02-158">WMI, büyük olasılıkla durdu ve yeniden başlatılıyor.</span><span class="sxs-lookup"><span data-stu-id="d9c02-158">WMI was probably stopped and restarting.</span></span> <span data-ttu-id="d9c02-159">Çağrı [ConnectServerWmi](connectserverwmi.md) yeniden.</span><span class="sxs-lookup"><span data-stu-id="d9c02-159">Call [ConnectServerWmi](connectserverwmi.md) again.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="d9c02-160">0x80041015</span><span class="sxs-lookup"><span data-stu-id="d9c02-160">0x80041015</span></span> | <span data-ttu-id="d9c02-161">Geçerli işlem WMI arasındaki uzak yordam çağrısı (RPC) bağlantı başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="d9c02-161">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="d9c02-162">0</span><span class="sxs-lookup"><span data-stu-id="d9c02-162">0</span></span> | <span data-ttu-id="d9c02-163">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="d9c02-163">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="d9c02-164">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d9c02-164">Remarks</span></span>

<span data-ttu-id="d9c02-165">Bu işlev bir çağrı sarılır [IWbemServices::CreateClassEnum](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-createclassenum) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d9c02-165">This function wraps a call to the [IWbemServices::CreateClassEnum](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-createclassenum) method.</span></span>

<span data-ttu-id="d9c02-166">İşlev çağrısı başarısız olursa, ek hata bilgileri çağırarak elde edebileceğiniz [Geterrorınfo](geterrorinfo.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="d9c02-166">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="d9c02-167">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d9c02-167">Requirements</span></span>  
 <span data-ttu-id="d9c02-168">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d9c02-168">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9c02-169">**Üst bilgi:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="d9c02-169">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="d9c02-170">**.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="d9c02-170">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9c02-171">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d9c02-171">See also</span></span>
- [<span data-ttu-id="d9c02-172">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="d9c02-172">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
