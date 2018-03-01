---
title: "ConnectServerWmi işlevi (yönetilmeyen API Başvurusu)"
description: "ConnectServerWmi işlevi bir WMI ad alanı için bir bağlantı oluşturmak için DCOM kullanır."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: reference
api_name:
- ConnectServerWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- ConnectServerWmi
helpviewer_keywords:
- ConnectServerWmi function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: dc821bddf1d33ea1144fef0821b81cf027d8f92f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="connectserverwmi-function"></a><span data-ttu-id="b96ec-103">ConnectServerWmi işlevi</span><span class="sxs-lookup"><span data-stu-id="b96ec-103">ConnectServerWmi function</span></span>
<span data-ttu-id="b96ec-104">Belirtilen bir bilgisayardaki bir WMI ad alanı için DCOM aracılığıyla yapılan bağlantı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b96ec-104">Creates a connection through DCOM to a WMI namespace on a specified computer.</span></span>  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="b96ec-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b96ec-105">Syntax</span></span>  
  
```  
HRESULT ConnectServerWmi (
   [in] BSTR               strNetworkResource,
   [in] BSTR               strUser,
   [in] BSTR               strPassword,
   [in] BSTR               strLocale,
   [in] long               lSecurityFlags,
   [in] BSTR               strAuthority,
   [in] IWbemContext*      pCtx,
   [out] IWbemServices**   ppNamespace,
   [in] DWORD              impLevel, 
   [in] DWORD              authLevel
);
```  
## <a name="parameters"></a><span data-ttu-id="b96ec-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b96ec-106">Parameters</span></span>

<span data-ttu-id="b96ec-107">`strNetworkResource`[in] Geçerli bir işaretçi `BSTR` doğru WMI ad alanının nesne yolu içerir.</span><span class="sxs-lookup"><span data-stu-id="b96ec-107">`strNetworkResource` [in] Pointer to a valid `BSTR` that contains the object path of the correct WMI namespace.</span></span> <span data-ttu-id="b96ec-108">Bkz: [açıklamalar](#remarks) daha fazla bilgi için bölüm.</span><span class="sxs-lookup"><span data-stu-id="b96ec-108">See the [Remarks](#remarks) section for more information.</span></span>

<span data-ttu-id="b96ec-109">`strUser`[in] Geçerli bir işaretçi `BSTR` kullanıcı adını içerir.</span><span class="sxs-lookup"><span data-stu-id="b96ec-109">`strUser` [in] A pointer to a valid `BSTR` that contains the user name.</span></span> <span data-ttu-id="b96ec-110">A `null` değeri geçerli güvenlik bağlamı gösterir.</span><span class="sxs-lookup"><span data-stu-id="b96ec-110">A `null` value indicates the current security context.</span></span> <span data-ttu-id="b96ec-111">Kullanıcı mevcut olandan farklı bir etki alanından ise `strUser` ters eğik çizgi ile ayrılmış etki alanı ve kullanıcı adı da içerebilir.</span><span class="sxs-lookup"><span data-stu-id="b96ec-111">If the user is from a different domain than the current one, `strUser` can also contain the domain and user name separated by a backslash.</span></span> <span data-ttu-id="b96ec-112">`strUser`Ayrıca olması kullanıcı asıl adı (UPN) biçimlendirebilir, suhc olarak  *userName@domainName* .</span><span class="sxs-lookup"><span data-stu-id="b96ec-112">`strUser` can also be in user principal name (UPN) format, suhc as *userName@domainName*.</span></span> <span data-ttu-id="b96ec-113">Bkz: [açıklamalar](#remarks) daha fazla bilgi için bölüm.</span><span class="sxs-lookup"><span data-stu-id="b96ec-113">See the [Remarks](#remarks) section for more information.</span></span>

<span data-ttu-id="b96ec-114">`strPassword`[in] Geçerli bir işaretçi `BSTR` parola içeriyor.</span><span class="sxs-lookup"><span data-stu-id="b96ec-114">`strPassword` [in] A pointer to a valid `BSTR` that contains the password.</span></span> <span data-ttu-id="b96ec-115">A `null` geçerli güvenlik bağlamı gösterir.</span><span class="sxs-lookup"><span data-stu-id="b96ec-115">A `null` indicates the current security context.</span></span> <span data-ttu-id="b96ec-116">Boş bir dize ("") geçerli sıfır uzunlukta bir parola belirtir.</span><span class="sxs-lookup"><span data-stu-id="b96ec-116">An empty string ("") indicates a valid zero-length password.</span></span>

<span data-ttu-id="b96ec-117">`strLocale`[in] Geçerli bir işaretçi `BSTR` bilgileri alma doğru yerel gösterir.</span><span class="sxs-lookup"><span data-stu-id="b96ec-117">`strLocale` [in] A pointer to a valid `BSTR` that indicates the correct locale for information retrieval.</span></span> <span data-ttu-id="b96ec-118">Microsoft yerel ayar tanımlayıcılarını için dizesinin biçimi olan "MS\_*xxx*", burada *xxx* yerel ayar kimliği (LCID) gösteren onaltılık biçimde bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="b96ec-118">For Microsoft locale identifiers, the format of the string is "MS\_*xxx*", where *xxx* is a string in hexadecimal form that indicates the locale identifier (LCID).</span></span> <span data-ttu-id="b96ec-119">Bu yöntem geçersiz bir yerel belirtilmiş olup olmadığını döndürür `WBEM_E_INVALID_PARAMETER` dışındaki Windows 7 sunucusunun varsayılan yerel ayar kullanıldığı bunun yerine,.</span><span class="sxs-lookup"><span data-stu-id="b96ec-119">If an invalid locale is specified, the method returns `WBEM_E_INVALID_PARAMETER` except on Windows 7, where the default locale of the server is used instead.</span></span> <span data-ttu-id="b96ec-120">Varsa ' null1, geçerli yerel ayar kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b96ec-120">If \`null1, the current locale is used.</span></span> 
 
<span data-ttu-id="b96ec-121">`lSecurityFlags`[in] Geçirilecek bayrakları `ConnectServerWmi` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b96ec-121">`lSecurityFlags` [in] Flags to pass to the `ConnectServerWmi` method.</span></span> <span data-ttu-id="b96ec-122">Bu parametre için sıfır (0) değeri sonuçları çağrısında `ConnectServerWmi` yalnızca bir sunucu bağlantısı kurulduktan sonra döndürüyor.</span><span class="sxs-lookup"><span data-stu-id="b96ec-122">A value of zero (0) for this parameter results in the call to `ConnectServerWmi` returning only after a connection to the server is established.</span></span> <span data-ttu-id="b96ec-123">Bu süresiz olarak sunucunun bozuk olup olmadığını yanıt vermeyen bir uygulamada neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="b96ec-123">This could result in an application not responding indefinitely if the server is broken.</span></span> <span data-ttu-id="b96ec-124">Diğer geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="b96ec-124">The other valid values are:</span></span>

| <span data-ttu-id="b96ec-125">Sabit</span><span class="sxs-lookup"><span data-stu-id="b96ec-125">Constant</span></span>  | <span data-ttu-id="b96ec-126">Değer</span><span class="sxs-lookup"><span data-stu-id="b96ec-126">Value</span></span>  | <span data-ttu-id="b96ec-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b96ec-127">Description</span></span>  |
|---------|---------|---------|
| `CONNECT_REPOSITORY_ONLY` | <span data-ttu-id="b96ec-128">0x40</span><span class="sxs-lookup"><span data-stu-id="b96ec-128">0x40</span></span> | <span data-ttu-id="b96ec-129">İç kullanım için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="b96ec-129">Reserved for internal use.</span></span> <span data-ttu-id="b96ec-130">Kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="b96ec-130">Do not use.</span></span> |
| `WBEM_FLAG_CONNECT_USE_MAX_WAIT` | <span data-ttu-id="b96ec-131">0x80</span><span class="sxs-lookup"><span data-stu-id="b96ec-131">0x80</span></span> | <span data-ttu-id="b96ec-132">`ConnectServerWmi`iki dakika veya daha az döndürür.</span><span class="sxs-lookup"><span data-stu-id="b96ec-132">`ConnectServerWmi` returns in two minutes or less.</span></span> |

<span data-ttu-id="b96ec-133">`strAuthority`[in] Kullanıcının etki alanı adı.</span><span class="sxs-lookup"><span data-stu-id="b96ec-133">`strAuthority` [in] The domain name of the user.</span></span> <span data-ttu-id="b96ec-134">Aşağıdaki değerlere sahip olabilir:</span><span class="sxs-lookup"><span data-stu-id="b96ec-134">It can have the following values:</span></span>

| <span data-ttu-id="b96ec-135">Değer</span><span class="sxs-lookup"><span data-stu-id="b96ec-135">Value</span></span> | <span data-ttu-id="b96ec-136">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b96ec-136">Description</span></span> |
|---------|---------|
| <span data-ttu-id="b96ec-137">Boş</span><span class="sxs-lookup"><span data-stu-id="b96ec-137">blank</span></span> | <span data-ttu-id="b96ec-138">NTLM kimlik doğrulaması kullanılır ve geçerli kullanıcının NTLM etki alanı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b96ec-138">NTLM authentication is used, and the NTLM domain of the current user is used.</span></span> <span data-ttu-id="b96ec-139">Varsa `strUser` (önerilen konum) etki alanını belirtir burada belirtilmemelidir.</span><span class="sxs-lookup"><span data-stu-id="b96ec-139">If `strUser` specifies the domain (the recommended location), it must not be specified here.</span></span> <span data-ttu-id="b96ec-140">İşlevi döndürür `WBEM_E_INVALID_PARAMETER` parametrelerinin her ikisini de etki alanı belirtirseniz.</span><span class="sxs-lookup"><span data-stu-id="b96ec-140">The function returns `WBEM_E_INVALID_PARAMETER` if you specify the domain in both parameters.</span></span> |
| <span data-ttu-id="b96ec-141">Kerberos:*asıl adı*</span><span class="sxs-lookup"><span data-stu-id="b96ec-141">Kerberos:*principal name*</span></span> | <span data-ttu-id="b96ec-142">Kerberos kimlik doğrulaması kullanılır ve bu parametre bir Kerberos asıl adı içerir.</span><span class="sxs-lookup"><span data-stu-id="b96ec-142">Kerberos authentication is used, and this parameter contains a Kerberos principal name.</span></span> |
| <span data-ttu-id="b96ec-143">NTLMDOMAIN:*etki alanı adı*</span><span class="sxs-lookup"><span data-stu-id="b96ec-143">NTLMDOMAIN:*domain name*</span></span> | <span data-ttu-id="b96ec-144">NT LAN Manager kimlik doğrulaması kullanılır ve bu parametre bir NTLM etki alanı adını içerir.</span><span class="sxs-lookup"><span data-stu-id="b96ec-144">NT LAN Manager authentication is used, and this parameter contains an NTLM domain name.</span></span> |

`pCtx`   
<span data-ttu-id="b96ec-145">[in] Genellikle, bu parametre olan `null`.</span><span class="sxs-lookup"><span data-stu-id="b96ec-145">[in] Typically, this parameter is is `null`.</span></span> <span data-ttu-id="b96ec-146">Aksi takdirde, gösteren bir işaretçidir bir [IWbemContext](https://msdn.microsoft.com/library/aa391465%28v=vs.85%29.aspx) bir veya daha fazla dinamik sınıf sağlayıcıları tarafından gerekli nesne.</span><span class="sxs-lookup"><span data-stu-id="b96ec-146">Otherwise, it is a pointer to an [IWbemContext](https://msdn.microsoft.com/library/aa391465%28v=vs.85%29.aspx) object required by one or more dynamic class providers.</span></span> 

`ppNamespace`  
<span data-ttu-id="b96ec-147">[out] İşlevi döndüğünde gösteren bir işaretçi alan bir [IWbemServices](https://msdn.microsoft.com/library/aa392093(v=vs.85).aspx) nesnesi belirtilen ad alanına bağlı.</span><span class="sxs-lookup"><span data-stu-id="b96ec-147">[out] When the function returns, receives a pointer to an [IWbemServices](https://msdn.microsoft.com/library/aa392093(v=vs.85).aspx) object bound to the specified namespace.</span></span> <span data-ttu-id="b96ec-148">İşaret edecek şekilde ayarlanmış `null` hata olduğunda.</span><span class="sxs-lookup"><span data-stu-id="b96ec-148">It is set to point to `null` when there is an error.</span></span>

`impLevel`  
<span data-ttu-id="b96ec-149">[in] Kimliğe bürünme düzeyi.</span><span class="sxs-lookup"><span data-stu-id="b96ec-149">[in] The impersonation level.</span></span>

`authLevel`  
<span data-ttu-id="b96ec-150">[in] Kimlik doğrulama düzeyi.</span><span class="sxs-lookup"><span data-stu-id="b96ec-150">[in] The authorization level.</span></span>

## <a name="return-value"></a><span data-ttu-id="b96ec-151">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="b96ec-151">Return value</span></span>

<span data-ttu-id="b96ec-152">Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üstbilgi dosyası, veya tanımlayabilirsiniz bunları sabitleri kodunuzda:</span><span class="sxs-lookup"><span data-stu-id="b96ec-152">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="b96ec-153">Sabit</span><span class="sxs-lookup"><span data-stu-id="b96ec-153">Constant</span></span>  |<span data-ttu-id="b96ec-154">Değer</span><span class="sxs-lookup"><span data-stu-id="b96ec-154">Value</span></span>  |<span data-ttu-id="b96ec-155">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b96ec-155">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="b96ec-156">0x80041001</span><span class="sxs-lookup"><span data-stu-id="b96ec-156">0x80041001</span></span> | <span data-ttu-id="b96ec-157">Genel bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="b96ec-157">There has been a general failure.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="b96ec-158">0x80041008</span><span class="sxs-lookup"><span data-stu-id="b96ec-158">0x80041008</span></span> | <span data-ttu-id="b96ec-159">Parametre geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="b96ec-159">A parameter is not valid.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="b96ec-160">0x80041006</span><span class="sxs-lookup"><span data-stu-id="b96ec-160">0x80041006</span></span> | <span data-ttu-id="b96ec-161">İşlemi tamamlamak yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="b96ec-161">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="b96ec-162">0</span><span class="sxs-lookup"><span data-stu-id="b96ec-162">0</span></span> | <span data-ttu-id="b96ec-163">İşlev çağrısı başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="b96ec-163">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="b96ec-164">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b96ec-164">Remarks</span></span>

<span data-ttu-id="b96ec-165">Bu işlev çağrısı sarmalar [IWbemLocator::ConnectServer](https://msdn.microsoft.com/libraryaa391769%28v=vs.85%29.aspx) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b96ec-165">This function wraps a call to the [IWbemLocator::ConnectServer](https://msdn.microsoft.com/libraryaa391769%28v=vs.85%29.aspx) method.</span></span>

 <span data-ttu-id="b96ec-166">Varsayılan ad alanı yerel erişimi için `strNetworkResource` basit bir nesne yolu: "kök\varsayılan" veya "\\.\root\default".</span><span class="sxs-lookup"><span data-stu-id="b96ec-166">For local access to the default namespace, `strNetworkResource` can be a simple object path: "root\default" or "\\.\root\default".</span></span> <span data-ttu-id="b96ec-167">İçin uzak bir bilgisayarda varsayılan ad alanına erişimi COM veya Microsoft uyumlu ağ kullanarak içerecek bilgisayar adı: "\\myserver\root\default".</span><span class="sxs-lookup"><span data-stu-id="b96ec-167">For access to the default namespace on a remote computer using COM or Microsoft-compatible networking, include the computer name: "\\myserver\root\default".</span></span> <span data-ttu-id="b96ec-168">Bilgisayar adı, ayrıca bir DNS adı veya IP adresi olabilir.</span><span class="sxs-lookup"><span data-stu-id="b96ec-168">The computer name also can be a DNS name or IP address.</span></span> <span data-ttu-id="b96ec-169">`ConnectServerWmi` İşlevi IPv6 çalıştıran bilgisayarlarla da bağlanabileceği bir IPv6 adresi kullanarak.</span><span class="sxs-lookup"><span data-stu-id="b96ec-169">The `ConnectServerWmi` function can also connect with computers running IPv6 using an IPv6 address.</span></span>

<span data-ttu-id="b96ec-170">`strUser`boş bir dize olamaz.</span><span class="sxs-lookup"><span data-stu-id="b96ec-170">`strUser` cannot be an empty string.</span></span> <span data-ttu-id="b96ec-171">Etki alanında belirtilmişse, `strAuthority`, ayrıca dahil gerekir değil `strUser`, veya işlevi döndürür `WBEM_E_INVALID_PARAMETER`.</span><span class="sxs-lookup"><span data-stu-id="b96ec-171">If the domain is specified in `strAuthority`, it must not also be included in `strUser`, or the function returns `WBEM_E_INVALID_PARAMETER`.</span></span>


## <a name="requirements"></a><span data-ttu-id="b96ec-172">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b96ec-172">Requirements</span></span>  
 <span data-ttu-id="b96ec-173">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b96ec-173">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b96ec-174">**Başlık:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="b96ec-174">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="b96ec-175">**.NET framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="b96ec-175">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b96ec-176">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b96ec-176">See also</span></span>  
[<span data-ttu-id="b96ec-177">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="b96ec-177">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
