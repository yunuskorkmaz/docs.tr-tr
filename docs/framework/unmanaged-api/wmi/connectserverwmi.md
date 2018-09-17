---
title: ConnectServerWmi işlevi (yönetilmeyen API Başvurusu)
description: ConnectServerWmi işlev bir WMI ad alanı için bir bağlantı oluşturmak için DCOM kullanır.
ms.date: 11/06/2017
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
ms.openlocfilehash: 163e61eef8a753b5b6470285e5e3ce63789e25a4
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/16/2018
ms.locfileid: "45675762"
---
# <a name="connectserverwmi-function"></a><span data-ttu-id="53751-103">ConnectServerWmi işlevi</span><span class="sxs-lookup"><span data-stu-id="53751-103">ConnectServerWmi function</span></span>
<span data-ttu-id="53751-104">Belirtilen bir bilgisayardaki bir WMI ad alanına DCOM aracılığıyla yapılan bağlantı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="53751-104">Creates a connection through DCOM to a WMI namespace on a specified computer.</span></span>  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="53751-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="53751-105">Syntax</span></span>  
  
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
## <a name="parameters"></a><span data-ttu-id="53751-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="53751-106">Parameters</span></span>

<span data-ttu-id="53751-107">`strNetworkResource` [in] Geçerli bir işaretçi `BSTR` , doğru WMI ad alanının nesne yolu içerir.</span><span class="sxs-lookup"><span data-stu-id="53751-107">`strNetworkResource` [in] Pointer to a valid `BSTR` that contains the object path of the correct WMI namespace.</span></span> <span data-ttu-id="53751-108">Bkz: [açıklamalar](#remarks) bölümünde daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="53751-108">See the [Remarks](#remarks) section for more information.</span></span>

<span data-ttu-id="53751-109">`strUser` [in] Geçerli bir işaretçi `BSTR` , kullanıcı adını içerir.</span><span class="sxs-lookup"><span data-stu-id="53751-109">`strUser` [in] A pointer to a valid `BSTR` that contains the user name.</span></span> <span data-ttu-id="53751-110">A `null` değeri, geçerli güvenlik bağlamı gösterir.</span><span class="sxs-lookup"><span data-stu-id="53751-110">A `null` value indicates the current security context.</span></span> <span data-ttu-id="53751-111">Kullanıcı geçerli olandan farklı bir etki alanından ise `strUser` ters eğik çizgiyle bölünerek etki alanı ve kullanıcı adı da içerebilir.</span><span class="sxs-lookup"><span data-stu-id="53751-111">If the user is from a different domain than the current one, `strUser` can also contain the domain and user name separated by a backslash.</span></span> <span data-ttu-id="53751-112">`strUser` Ayrıca olması kullanıcı asıl adı (UPN) biçimlendirebilir, suhc olarak *userName@domainName*.</span><span class="sxs-lookup"><span data-stu-id="53751-112">`strUser` can also be in user principal name (UPN) format, suhc as *userName@domainName*.</span></span> <span data-ttu-id="53751-113">Bkz: [açıklamalar](#remarks) bölümünde daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="53751-113">See the [Remarks](#remarks) section for more information.</span></span>

<span data-ttu-id="53751-114">`strPassword` [in] Geçerli bir işaretçi `BSTR` , parola içeriyor.</span><span class="sxs-lookup"><span data-stu-id="53751-114">`strPassword` [in] A pointer to a valid `BSTR` that contains the password.</span></span> <span data-ttu-id="53751-115">A `null` geçerli güvenlik bağlamı gösterir.</span><span class="sxs-lookup"><span data-stu-id="53751-115">A `null` indicates the current security context.</span></span> <span data-ttu-id="53751-116">Boş bir dize ("") geçerli sıfır uzunlukta bir parola belirtir.</span><span class="sxs-lookup"><span data-stu-id="53751-116">An empty string ("") indicates a valid zero-length password.</span></span>

<span data-ttu-id="53751-117">`strLocale` [in] Geçerli bir işaretçi `BSTR` bilgi almak için doğru yerel gösterir.</span><span class="sxs-lookup"><span data-stu-id="53751-117">`strLocale` [in] A pointer to a valid `BSTR` that indicates the correct locale for information retrieval.</span></span> <span data-ttu-id="53751-118">Microsoft yerel ayar tanımlayıcılarını için dize biçimindedir "MS\_*xxx*" burada *xxx* yerel ayar tanıtıcısı (LCID) gösteren onaltılık biçimde bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="53751-118">For Microsoft locale identifiers, the format of the string is "MS\_*xxx*", where *xxx* is a string in hexadecimal form that indicates the locale identifier (LCID).</span></span> <span data-ttu-id="53751-119">Geçersiz bir yerel ayar belirtilmezse yöntem döndürür `WBEM_E_INVALID_PARAMETER` hariç Windows 7 varsayılan yerel ayar sunucusunun kullanıldığı bunun yerine,.</span><span class="sxs-lookup"><span data-stu-id="53751-119">If an invalid locale is specified, the method returns `WBEM_E_INVALID_PARAMETER` except on Windows 7, where the default locale of the server is used instead.</span></span> <span data-ttu-id="53751-120">Varsa ' null1, geçerli yerel ayarı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="53751-120">If \`null1, the current locale is used.</span></span> 
 
<span data-ttu-id="53751-121">`lSecurityFlags` [in] Geçirilecek bayrakları `ConnectServerWmi` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="53751-121">`lSecurityFlags` [in] Flags to pass to the `ConnectServerWmi` method.</span></span> <span data-ttu-id="53751-122">Bu parametre için sıfır (0) değerini sonuçları çağrısında `ConnectServerWmi` yalnızca bir sunucu bağlantısı kurulduktan sonra döndürüyor.</span><span class="sxs-lookup"><span data-stu-id="53751-122">A value of zero (0) for this parameter results in the call to `ConnectServerWmi` returning only after a connection to the server is established.</span></span> <span data-ttu-id="53751-123">Bu uygulamada süresiz olarak sunucunun bozuk olup olmadığını yanıt vermiyorsa sonuçlanabilir.</span><span class="sxs-lookup"><span data-stu-id="53751-123">This could result in an application not responding indefinitely if the server is broken.</span></span> <span data-ttu-id="53751-124">Geçerli bir değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="53751-124">The other valid values are:</span></span>

| <span data-ttu-id="53751-125">Sabit</span><span class="sxs-lookup"><span data-stu-id="53751-125">Constant</span></span>  | <span data-ttu-id="53751-126">Değer</span><span class="sxs-lookup"><span data-stu-id="53751-126">Value</span></span>  | <span data-ttu-id="53751-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="53751-127">Description</span></span>  |
|---------|---------|---------|
| `CONNECT_REPOSITORY_ONLY` | <span data-ttu-id="53751-128">0x40</span><span class="sxs-lookup"><span data-stu-id="53751-128">0x40</span></span> | <span data-ttu-id="53751-129">İç kullanım için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="53751-129">Reserved for internal use.</span></span> <span data-ttu-id="53751-130">Kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="53751-130">Do not use.</span></span> |
| `WBEM_FLAG_CONNECT_USE_MAX_WAIT` | <span data-ttu-id="53751-131">0x80</span><span class="sxs-lookup"><span data-stu-id="53751-131">0x80</span></span> | <span data-ttu-id="53751-132">`ConnectServerWmi` iki dakika içinde ya da daha az döndürür.</span><span class="sxs-lookup"><span data-stu-id="53751-132">`ConnectServerWmi` returns in two minutes or less.</span></span> |

<span data-ttu-id="53751-133">`strAuthority` [in] Kullanıcı etki alanı adı.</span><span class="sxs-lookup"><span data-stu-id="53751-133">`strAuthority` [in] The domain name of the user.</span></span> <span data-ttu-id="53751-134">Aşağıdaki değerlere sahip olabilir:</span><span class="sxs-lookup"><span data-stu-id="53751-134">It can have the following values:</span></span>

| <span data-ttu-id="53751-135">Değer</span><span class="sxs-lookup"><span data-stu-id="53751-135">Value</span></span> | <span data-ttu-id="53751-136">Açıklama</span><span class="sxs-lookup"><span data-stu-id="53751-136">Description</span></span> |
|---------|---------|
| <span data-ttu-id="53751-137">Boş</span><span class="sxs-lookup"><span data-stu-id="53751-137">blank</span></span> | <span data-ttu-id="53751-138">NTLM kimlik doğrulaması kullanılır ve geçerli kullanıcının NTLM etki alanı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="53751-138">NTLM authentication is used, and the NTLM domain of the current user is used.</span></span> <span data-ttu-id="53751-139">Varsa `strUser` belirtir (önerilen konum) buraya belirtilmemelidir.</span><span class="sxs-lookup"><span data-stu-id="53751-139">If `strUser` specifies the domain (the recommended location), it must not be specified here.</span></span> <span data-ttu-id="53751-140">İşlev döndürür `WBEM_E_INVALID_PARAMETER` iki parametrede de etki alanı belirtirseniz.</span><span class="sxs-lookup"><span data-stu-id="53751-140">The function returns `WBEM_E_INVALID_PARAMETER` if you specify the domain in both parameters.</span></span> |
| <span data-ttu-id="53751-141">Kerberos:*asıl adı*</span><span class="sxs-lookup"><span data-stu-id="53751-141">Kerberos:*principal name*</span></span> | <span data-ttu-id="53751-142">Kerberos kimlik doğrulaması kullanılır ve bu parametre bir Kerberos asıl adı içerir.</span><span class="sxs-lookup"><span data-stu-id="53751-142">Kerberos authentication is used, and this parameter contains a Kerberos principal name.</span></span> |
| <span data-ttu-id="53751-143">NTLMDOMAIN:*etki alanı adı*</span><span class="sxs-lookup"><span data-stu-id="53751-143">NTLMDOMAIN:*domain name*</span></span> | <span data-ttu-id="53751-144">NT LAN Manager kimlik doğrulaması kullanılır ve bu parametre bir NTLM etki alanı adı içerir.</span><span class="sxs-lookup"><span data-stu-id="53751-144">NT LAN Manager authentication is used, and this parameter contains an NTLM domain name.</span></span> |

`pCtx`   
<span data-ttu-id="53751-145">[in] Bu parametre genelde `null`.</span><span class="sxs-lookup"><span data-stu-id="53751-145">[in] Typically, this parameter is is `null`.</span></span> <span data-ttu-id="53751-146">Aksi takdirde, bir işaretçi olduğu bir [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) nesnesi bir veya daha fazla dinamik sınıfı sağlayıcıları tarafından gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="53751-146">Otherwise, it is a pointer to an [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) object required by one or more dynamic class providers.</span></span> 

`ppNamespace`  
<span data-ttu-id="53751-147">[out] İşlevi döndüğünde, bir işaretçi alır bir [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) nesne belirtilen ad alanına bağlı.</span><span class="sxs-lookup"><span data-stu-id="53751-147">[out] When the function returns, receives a pointer to an [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) object bound to the specified namespace.</span></span> <span data-ttu-id="53751-148">İşaret edecek şekilde ayarlanmış `null` bir hata olduğunda.</span><span class="sxs-lookup"><span data-stu-id="53751-148">It is set to point to `null` when there is an error.</span></span>

`impLevel`  
<span data-ttu-id="53751-149">[in] Kimliğe bürünme düzeyi.</span><span class="sxs-lookup"><span data-stu-id="53751-149">[in] The impersonation level.</span></span>

`authLevel`  
<span data-ttu-id="53751-150">[in] Yetkilendirme düzeyi.</span><span class="sxs-lookup"><span data-stu-id="53751-150">[in] The authorization level.</span></span>

## <a name="return-value"></a><span data-ttu-id="53751-151">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="53751-151">Return value</span></span>

<span data-ttu-id="53751-152">Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üst bilgi dosyası veya tanımlayabilirsiniz bunları sabitleri kodunuzda:</span><span class="sxs-lookup"><span data-stu-id="53751-152">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="53751-153">Sabit</span><span class="sxs-lookup"><span data-stu-id="53751-153">Constant</span></span>  |<span data-ttu-id="53751-154">Değer</span><span class="sxs-lookup"><span data-stu-id="53751-154">Value</span></span>  |<span data-ttu-id="53751-155">Açıklama</span><span class="sxs-lookup"><span data-stu-id="53751-155">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="53751-156">0x80041001</span><span class="sxs-lookup"><span data-stu-id="53751-156">0x80041001</span></span> | <span data-ttu-id="53751-157">Genel bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="53751-157">There has been a general failure.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="53751-158">0x80041008</span><span class="sxs-lookup"><span data-stu-id="53751-158">0x80041008</span></span> | <span data-ttu-id="53751-159">Bir parametre geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="53751-159">A parameter is not valid.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="53751-160">0x80041006</span><span class="sxs-lookup"><span data-stu-id="53751-160">0x80041006</span></span> | <span data-ttu-id="53751-161">İşlemi tamamlamak yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="53751-161">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="53751-162">0</span><span class="sxs-lookup"><span data-stu-id="53751-162">0</span></span> | <span data-ttu-id="53751-163">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="53751-163">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="53751-164">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="53751-164">Remarks</span></span>

<span data-ttu-id="53751-165">Bu işlev bir çağrı sarılır [IWbemLocator::ConnectServer](https://msdn.microsoft.com/libraryaa391769%28v=vs.85%29.aspx) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="53751-165">This function wraps a call to the [IWbemLocator::ConnectServer](https://msdn.microsoft.com/libraryaa391769%28v=vs.85%29.aspx) method.</span></span>

 <span data-ttu-id="53751-166">Yerel erişim için varsayılan ad alanı `strNetworkResource` basit nesne yolu olabilir: "kök\varsayılan" veya "\\.\root\default".</span><span class="sxs-lookup"><span data-stu-id="53751-166">For local access to the default namespace, `strNetworkResource` can be a simple object path: "root\default" or "\\.\root\default".</span></span> <span data-ttu-id="53751-167">Uzak bir bilgisayarda varsayılan ad alanı erişimi için COM veya Microsoft ile uyumlu ağ kullanarak dahil bilgisayar adı: "\\myserver\root\default".</span><span class="sxs-lookup"><span data-stu-id="53751-167">For access to the default namespace on a remote computer using COM or Microsoft-compatible networking, include the computer name: "\\myserver\root\default".</span></span> <span data-ttu-id="53751-168">Bilgisayar adı, ayrıca bir DNS adı veya IP adresi olabilir.</span><span class="sxs-lookup"><span data-stu-id="53751-168">The computer name also can be a DNS name or IP address.</span></span> <span data-ttu-id="53751-169">`ConnectServerWmi` İşlevi IPv6 çalıştıran bilgisayarlarla da bağlanabilir bir IPv6 adresi kullanarak.</span><span class="sxs-lookup"><span data-stu-id="53751-169">The `ConnectServerWmi` function can also connect with computers running IPv6 using an IPv6 address.</span></span>

<span data-ttu-id="53751-170">`strUser` Boş bir dize olamaz.</span><span class="sxs-lookup"><span data-stu-id="53751-170">`strUser` cannot be an empty string.</span></span> <span data-ttu-id="53751-171">Etki alanı belirtilirse `strAuthority`, bu da de dahil edilmemesi gerekir `strUser`, ya da bir işlev döndürür `WBEM_E_INVALID_PARAMETER`.</span><span class="sxs-lookup"><span data-stu-id="53751-171">If the domain is specified in `strAuthority`, it must not also be included in `strUser`, or the function returns `WBEM_E_INVALID_PARAMETER`.</span></span>


## <a name="requirements"></a><span data-ttu-id="53751-172">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="53751-172">Requirements</span></span>  
 <span data-ttu-id="53751-173">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="53751-173">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53751-174">**Başlık:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="53751-174">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="53751-175">**.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="53751-175">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53751-176">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="53751-176">See also</span></span>  
[<span data-ttu-id="53751-177">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="53751-177">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
