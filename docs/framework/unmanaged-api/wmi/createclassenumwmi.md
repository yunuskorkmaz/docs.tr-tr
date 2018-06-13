---
title: CreateClassEnumWmi işlevi (yönetilmeyen API Başvurusu)
description: CreateClassEnumWmi işlevi belirtilen ölçütleri karşılayan tüm sınıflar için bir numaralandırıcı döndürür.
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
ms.openlocfilehash: 3f84902586a2b940d52eb6365a141af61af802dd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33461460"
---
# <a name="createclassenumwmi-function"></a><span data-ttu-id="5d69c-103">CreateClassEnumWmi işlevi</span><span class="sxs-lookup"><span data-stu-id="5d69c-103">CreateClassEnumWmi function</span></span>
<span data-ttu-id="5d69c-104">Belirtilen seçim ölçütü karşılayan tüm sınıflar için bir numaralandırıcı döndürür.</span><span class="sxs-lookup"><span data-stu-id="5d69c-104">Returns an enumerator for all classes that satisfy the specified selection criteria.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="5d69c-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5d69c-105">Syntax</span></span>  
  
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

## <a name="parameters"></a><span data-ttu-id="5d69c-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5d69c-106">Parameters</span></span>

`strSuperclass`    
<span data-ttu-id="5d69c-107">[in] Aksi takdirde `null` veya boş, bir üst sınıf; adını belirtir, bu sınıfın yalnızca alt sınıfların Numaralandırıcı döndürür.</span><span class="sxs-lookup"><span data-stu-id="5d69c-107">[in] If not `null` or blank, specifies the name of a parent class; the enumerator returns only subclasses of this class.</span></span> <span data-ttu-id="5d69c-108">Eğer öyleyse `null` ya da boş ve `lFlags` WBEM_FLAG_SHALLOW ise, yalnızca üst düzey sınıflar (hiçbir üst sınıf sınıflarıyla) döndürür.</span><span class="sxs-lookup"><span data-stu-id="5d69c-108">If it is `null` or blank and `lFlags` is WBEM_FLAG_SHALLOW, returns only top-level classes (classes with no parent class).</span></span> <span data-ttu-id="5d69c-109">Eğer öyleyse `null` ya da boş ve `lFlags` olan `WBEM_FLAG_DEEP`, ad alanındaki tüm sınıfları döndürür.</span><span class="sxs-lookup"><span data-stu-id="5d69c-109">If it is `null` or blank and `lFlags` is `WBEM_FLAG_DEEP`, returns all classes in the namespace.</span></span>

`lFlags`   
<span data-ttu-id="5d69c-110">[in] Bu işlev davranışını etkileyen bayrak birleşimi.</span><span class="sxs-lookup"><span data-stu-id="5d69c-110">[in] A combination of flags that affect the behavior of this function.</span></span> <span data-ttu-id="5d69c-111">Aşağıdaki değerleri tanımlanan *WbemCli.h* üstbilgi dosyası, veya tanımlayabilirsiniz bunları sabitleri kodunuzda:</span><span class="sxs-lookup"><span data-stu-id="5d69c-111">The following values are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span> 

|<span data-ttu-id="5d69c-112">Sabit</span><span class="sxs-lookup"><span data-stu-id="5d69c-112">Constant</span></span>  |<span data-ttu-id="5d69c-113">Değer</span><span class="sxs-lookup"><span data-stu-id="5d69c-113">Value</span></span>  |<span data-ttu-id="5d69c-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5d69c-114">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | <span data-ttu-id="5d69c-115">0x20000</span><span class="sxs-lookup"><span data-stu-id="5d69c-115">0x20000</span></span> | <span data-ttu-id="5d69c-116">Geçerli bağlantının yerel yerelleştirilmiş ad alanında depolanan değiştirilen niteleyicileri kümesi, işlevi alır</span><span class="sxs-lookup"><span data-stu-id="5d69c-116">If set, the function retrieves the amended qualifiers stored in the localized namespace of the current connection's locale.</span></span> <br/> <span data-ttu-id="5d69c-117">Aksi durumda kümesi işlevi yalnızca hemen ad alanında depolanan niteleyicileri alır.</span><span class="sxs-lookup"><span data-stu-id="5d69c-117">If not set, the function retrieves only the qualifiers stored in the immediate namespace.</span></span> |
| `WBEM_FLAG_DEEP` | <span data-ttu-id="5d69c-118">0</span><span class="sxs-lookup"><span data-stu-id="5d69c-118">0</span></span> | <span data-ttu-id="5d69c-119">Numaralandırma, hiyerarşi, ancak bu sınıfın tüm alt sınıflar içerir.</span><span class="sxs-lookup"><span data-stu-id="5d69c-119">The enumeration includes all subclasses in the hierarchy, but not this class.</span></span> |
| `WBEM_FLAG_SHALLOW` | <span data-ttu-id="5d69c-120">1.</span><span class="sxs-lookup"><span data-stu-id="5d69c-120">1</span></span> | <span data-ttu-id="5d69c-121">Numaralandırma yalnızca saf bu sınıfın örnekleri içerir ve bu sınıfında bulunmayan özellikleri tedarik alt sınıfların tüm örneklerini dışlar.</span><span class="sxs-lookup"><span data-stu-id="5d69c-121">The enumeration includes only pure instances of this class and excludes all instances of subclasses that supply properties not found in this class.</span></span> |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | <span data-ttu-id="5d69c-122">0x10</span><span class="sxs-lookup"><span data-stu-id="5d69c-122">0x10</span></span> | <span data-ttu-id="5d69c-123">Bayrağı yarı zaman uyumlu bir çağrı neden olur.</span><span class="sxs-lookup"><span data-stu-id="5d69c-123">The flag causes a semisynchronous call.</span></span> |
| `WBEM_FLAG_FORWARD_ONLY` | <span data-ttu-id="5d69c-124">0x20</span><span class="sxs-lookup"><span data-stu-id="5d69c-124">0x20</span></span> | <span data-ttu-id="5d69c-125">İşlevi yalnızca ileri bir numaralandırıcı döndürür.</span><span class="sxs-lookup"><span data-stu-id="5d69c-125">The function returns a forward-only enumerator.</span></span> <span data-ttu-id="5d69c-126">Genellikle, yalnızca ileri numaralandırıcılar daha hızlı ve geleneksel numaralandırıcılar daha az bellek kullanır, ancak çağrıları izin verme [kopya](clone.md).</span><span class="sxs-lookup"><span data-stu-id="5d69c-126">Typically, forward-only enumerators are faster and use less memory than conventional enumerators, but they do not allow calls to [Clone](clone.md).</span></span> |
| `WBEM_FLAG_BIDIRECTIONAL` | <span data-ttu-id="5d69c-127">0</span><span class="sxs-lookup"><span data-stu-id="5d69c-127">0</span></span> | <span data-ttu-id="5d69c-128">Serbest bırakılana kadar WMI enumration nesnelerine işaretçiler korur.</span><span class="sxs-lookup"><span data-stu-id="5d69c-128">WMI retains pointers to objects in the enumration until they are released.</span></span> | 

<span data-ttu-id="5d69c-129">Önerilen bayraklar `WBEM_FLAG_RETURN_IMMEDIATELY` ve `WBEM_FLAG_FORWARD_ONLY` en iyi performans için.</span><span class="sxs-lookup"><span data-stu-id="5d69c-129">The recommended flags are `WBEM_FLAG_RETURN_IMMEDIATELY` and `WBEM_FLAG_FORWARD_ONLY` for best performance.</span></span>

`pCtx`  
<span data-ttu-id="5d69c-130">[in] Bu değer genellikle `null`.</span><span class="sxs-lookup"><span data-stu-id="5d69c-130">[in] Typically, this value is `null`.</span></span> <span data-ttu-id="5d69c-131">Aksi takdirde, gösteren bir işaretçidir bir [IWbemContext](https://msdn.microsoft.com/library/aa391465(v=vs.85).aspx) istenen sınıfları sağlayarak sağlayıcı tarafından kullanılan örnek.</span><span class="sxs-lookup"><span data-stu-id="5d69c-131">Otherwise, it is a pointer to an [IWbemContext](https://msdn.microsoft.com/library/aa391465(v=vs.85).aspx) instance that can be used by the provider that is providing the requested classes.</span></span> 

`ppEnum`  
<span data-ttu-id="5d69c-132">[out] İşaretçi Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="5d69c-132">[out] Receives the pointer to the enumerator.</span></span>

`authLevel`  
<span data-ttu-id="5d69c-133">[in] Kimlik doğrulama düzeyi.</span><span class="sxs-lookup"><span data-stu-id="5d69c-133">[in] The authorization level.</span></span>

<span data-ttu-id="5d69c-134">`impLevel` [in] Kimliğe bürünme düzeyi.</span><span class="sxs-lookup"><span data-stu-id="5d69c-134">`impLevel` [in] The impersonation level.</span></span>

`pCurrentNamespace`   
<span data-ttu-id="5d69c-135">[in] Bir işaretçi bir [IWbemServices](https://msdn.microsoft.com/library/aa392093(v=vs.85).aspx) geçerli ad alanını temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="5d69c-135">[in] A pointer to an [IWbemServices](https://msdn.microsoft.com/library/aa392093(v=vs.85).aspx) object that represents the current namespace.</span></span>

`strUser`   
<span data-ttu-id="5d69c-136">[in] Kullanıcı adı.</span><span class="sxs-lookup"><span data-stu-id="5d69c-136">[in] The user name.</span></span> <span data-ttu-id="5d69c-137">Bkz: [ConnectServerWmi](connectserverwmi.md) daha fazla bilgi için işlevi.</span><span class="sxs-lookup"><span data-stu-id="5d69c-137">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strPassword`   
<span data-ttu-id="5d69c-138">[in] Parola.</span><span class="sxs-lookup"><span data-stu-id="5d69c-138">[in] The password.</span></span> <span data-ttu-id="5d69c-139">Bkz: [ConnectServerWmi](connectserverwmi.md) daha fazla bilgi için işlevi.</span><span class="sxs-lookup"><span data-stu-id="5d69c-139">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strAuthority`   
<span data-ttu-id="5d69c-140">[in] Kullanıcının etki alanı adı.</span><span class="sxs-lookup"><span data-stu-id="5d69c-140">[in] The domain name of the user.</span></span> <span data-ttu-id="5d69c-141">Bkz: [ConnectServerWmi](connectserverwmi.md) daha fazla bilgi için işlevi.</span><span class="sxs-lookup"><span data-stu-id="5d69c-141">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="5d69c-142">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="5d69c-142">Return value</span></span>

<span data-ttu-id="5d69c-143">Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üstbilgi dosyası, veya tanımlayabilirsiniz bunları sabitleri kodunuzda:</span><span class="sxs-lookup"><span data-stu-id="5d69c-143">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="5d69c-144">Sabit</span><span class="sxs-lookup"><span data-stu-id="5d69c-144">Constant</span></span>  |<span data-ttu-id="5d69c-145">Değer</span><span class="sxs-lookup"><span data-stu-id="5d69c-145">Value</span></span>  |<span data-ttu-id="5d69c-146">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5d69c-146">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | <span data-ttu-id="5d69c-147">0x80041003</span><span class="sxs-lookup"><span data-stu-id="5d69c-147">0x80041003</span></span> | <span data-ttu-id="5d69c-148">Kullanıcı, bir veya daha fazla işlev döndürebilir sınıfları görüntüleme izni yok.</span><span class="sxs-lookup"><span data-stu-id="5d69c-148">The user does not have permission to view one or more of the classes that the function can return.</span></span> |
| `WBEM_E_FAILED` | <span data-ttu-id="5d69c-149">0x80041001</span><span class="sxs-lookup"><span data-stu-id="5d69c-149">0x80041001</span></span> | <span data-ttu-id="5d69c-150">Belirlenemeyen bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="5d69c-150">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_CLASS` | <span data-ttu-id="5d69c-151">0x80041010</span><span class="sxs-lookup"><span data-stu-id="5d69c-151">0x80041010</span></span> | <span data-ttu-id="5d69c-152">`strSuperClass` mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="5d69c-152">`strSuperClass` does not exist.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="5d69c-153">0x80041008</span><span class="sxs-lookup"><span data-stu-id="5d69c-153">0x80041008</span></span> | <span data-ttu-id="5d69c-154">Parametre geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="5d69c-154">A parameter is not valid.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="5d69c-155">0x80041006</span><span class="sxs-lookup"><span data-stu-id="5d69c-155">0x80041006</span></span> | <span data-ttu-id="5d69c-156">İşlemi tamamlamak yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="5d69c-156">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_SHUTTING_DOWN` | <span data-ttu-id="5d69c-157">0x80041033</span><span class="sxs-lookup"><span data-stu-id="5d69c-157">0x80041033</span></span> | <span data-ttu-id="5d69c-158">WMI, büyük olasılıkla durduruldu ve yeniden başlatma.</span><span class="sxs-lookup"><span data-stu-id="5d69c-158">WMI was probably stopped and restarting.</span></span> <span data-ttu-id="5d69c-159">Çağrı [ConnectServerWmi](connectserverwmi.md) yeniden.</span><span class="sxs-lookup"><span data-stu-id="5d69c-159">Call [ConnectServerWmi](connectserverwmi.md) again.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="5d69c-160">0x80041015</span><span class="sxs-lookup"><span data-stu-id="5d69c-160">0x80041015</span></span> | <span data-ttu-id="5d69c-161">Geçerli işlem ile WMI arasındaki uzak yordam çağrısı (RPC) bağlantı başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="5d69c-161">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="5d69c-162">0</span><span class="sxs-lookup"><span data-stu-id="5d69c-162">0</span></span> | <span data-ttu-id="5d69c-163">İşlev çağrısı başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="5d69c-163">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="5d69c-164">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5d69c-164">Remarks</span></span>

<span data-ttu-id="5d69c-165">Bu işlev çağrısı sarmalar [IWbemServices::CreateClassEnum](https://msdn.microsoft.com/library/aa392095(v=vs.85).aspx) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5d69c-165">This function wraps a call to the [IWbemServices::CreateClassEnum](https://msdn.microsoft.com/library/aa392095(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="5d69c-166">İşlev çağrısı başarısız olursa, çağırarak ek hata bilgileri elde edebileceğiniz [Geterrorınfo](geterrorinfo.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="5d69c-166">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="5d69c-167">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5d69c-167">Requirements</span></span>  
 <span data-ttu-id="5d69c-168">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5d69c-168">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d69c-169">**Başlık:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="5d69c-169">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="5d69c-170">**.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="5d69c-170">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d69c-171">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5d69c-171">See also</span></span>  
[<span data-ttu-id="5d69c-172">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="5d69c-172">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
