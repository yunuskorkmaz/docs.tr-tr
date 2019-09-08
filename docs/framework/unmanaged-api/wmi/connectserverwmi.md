---
title: ConnectServerWmi işlevi (yönetilmeyen API Başvurusu)
description: ConnectServerWmi işlevi, bir WMI ad alanına bağlantı oluşturmak için DCOM kullanır.
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
ms.openlocfilehash: 2ebb268dcee877f4e9aea0c88852333897030dd1
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798745"
---
# <a name="connectserverwmi-function"></a><span data-ttu-id="63740-103">ConnectServerWmi işlevi</span><span class="sxs-lookup"><span data-stu-id="63740-103">ConnectServerWmi function</span></span>

<span data-ttu-id="63740-104">Belirtilen bir bilgisayardaki WMI ad alanına DCOM aracılığıyla bir bağlantı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="63740-104">Creates a connection through DCOM to a WMI namespace on a specified computer.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="63740-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="63740-105">Syntax</span></span>

```cpp
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

## <a name="parameters"></a><span data-ttu-id="63740-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="63740-106">Parameters</span></span>

`strNetworkResource`\
<span data-ttu-id="63740-107">'ndaki Doğru WMI ad alanının `BSTR` nesne yolunu içeren geçerli bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="63740-107">[in] Pointer to a valid `BSTR` that contains the object path of the correct WMI namespace.</span></span> <span data-ttu-id="63740-108">Daha fazla bilgi için [açıklamalar](#remarks) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="63740-108">See the [Remarks](#remarks) section for more information.</span></span>

`strUser`\
<span data-ttu-id="63740-109">'ndaki Kullanıcı adını içeren geçerli `BSTR` bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="63740-109">[in] A pointer to a valid `BSTR` that contains the user name.</span></span> <span data-ttu-id="63740-110">Bir `null` değer geçerli güvenlik bağlamını gösterir.</span><span class="sxs-lookup"><span data-stu-id="63740-110">A `null` value indicates the current security context.</span></span> <span data-ttu-id="63740-111">Kullanıcı geçerli olandan farklı bir etki alanından farklıysa, `strUser` bir ters eğik çizgiyle ayrılmış etki alanını ve Kullanıcı adını da içerebilir.</span><span class="sxs-lookup"><span data-stu-id="63740-111">If the user is from a different domain than the current one, `strUser` can also contain the domain and user name separated by a backslash.</span></span> <span data-ttu-id="63740-112">`strUser`, gibi Kullanıcı asıl adı (UPN) biçiminde de olabilir `userName@domainName`.</span><span class="sxs-lookup"><span data-stu-id="63740-112">`strUser` can also be in user principal name (UPN) format, such as `userName@domainName`.</span></span> <span data-ttu-id="63740-113">Daha fazla bilgi için [açıklamalar](#remarks) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="63740-113">See the [Remarks](#remarks) section for more information.</span></span>

`strPassword`\
<span data-ttu-id="63740-114">'ndaki Parolayı içeren geçerli `BSTR` bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="63740-114">[in] A pointer to a valid `BSTR` that contains the password.</span></span> <span data-ttu-id="63740-115">Geçerli güvenlik bağlamını gösterir. `null`</span><span class="sxs-lookup"><span data-stu-id="63740-115">A `null` indicates the current security context.</span></span> <span data-ttu-id="63740-116">Boş bir dize ("") geçerli bir sıfır uzunlukta parolayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="63740-116">An empty string ("") indicates a valid zero-length password.</span></span>

`strLocale`\
<span data-ttu-id="63740-117">'ndaki Bilgi alımı için doğru yerel `BSTR` ayarı gösteren geçerli bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="63740-117">[in] A pointer to a valid `BSTR` that indicates the correct locale for information retrieval.</span></span> <span data-ttu-id="63740-118">Microsoft yerel ayar tanımlayıcıları için, dizenin biçimi "MS\_*XXX*", burada *XXX* , yerel ayar tanımlayıcısını (LCID) gösteren onaltılık biçimli bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="63740-118">For Microsoft locale identifiers, the format of the string is "MS\_*xxx*", where *xxx* is a string in hexadecimal form that indicates the locale identifier (LCID).</span></span> <span data-ttu-id="63740-119">Geçersiz bir yerel ayar belirtilmişse, yöntem bunun yerine sunucunun `WBEM_E_INVALID_PARAMETER` varsayılan yerel ayarının kullanıldığı Windows 7 hariç döndürülür.</span><span class="sxs-lookup"><span data-stu-id="63740-119">If an invalid locale is specified, the method returns `WBEM_E_INVALID_PARAMETER` except on Windows 7, where the default locale of the server is used instead.</span></span> <span data-ttu-id="63740-120">Eğer ' null1, geçerli yerel ayar kullanılır.</span><span class="sxs-lookup"><span data-stu-id="63740-120">If \`null1, the current locale is used.</span></span>

`lSecurityFlags`\
<span data-ttu-id="63740-121">'ndaki `ConnectServerWmi` Yönteme geçirilecek bayraklar.</span><span class="sxs-lookup"><span data-stu-id="63740-121">[in] Flags to pass to the `ConnectServerWmi` method.</span></span> <span data-ttu-id="63740-122">Bu parametre için sıfır (0) değeri, yalnızca sunucuya bağlantı kurulduktan sonra `ConnectServerWmi` döndürme çağrısına neden olur.</span><span class="sxs-lookup"><span data-stu-id="63740-122">A value of zero (0) for this parameter results in the call to `ConnectServerWmi` returning only after a connection to the server is established.</span></span> <span data-ttu-id="63740-123">Bu, sunucu bozulur bir uygulamanın süresiz olarak yanıt vermemesine neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="63740-123">This could result in an application not responding indefinitely if the server is broken.</span></span> <span data-ttu-id="63740-124">Diğer geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="63740-124">The other valid values are:</span></span>

| <span data-ttu-id="63740-125">Sabit</span><span class="sxs-lookup"><span data-stu-id="63740-125">Constant</span></span>  | <span data-ttu-id="63740-126">Değer</span><span class="sxs-lookup"><span data-stu-id="63740-126">Value</span></span>  | <span data-ttu-id="63740-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="63740-127">Description</span></span>  |
|---------|---------|---------|
| `CONNECT_REPOSITORY_ONLY` | <span data-ttu-id="63740-128">0x40</span><span class="sxs-lookup"><span data-stu-id="63740-128">0x40</span></span> | <span data-ttu-id="63740-129">Dahili kullanım için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="63740-129">Reserved for internal use.</span></span> <span data-ttu-id="63740-130">Kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="63740-130">Do not use.</span></span> |
| `WBEM_FLAG_CONNECT_USE_MAX_WAIT` | <span data-ttu-id="63740-131">0x80</span><span class="sxs-lookup"><span data-stu-id="63740-131">0x80</span></span> | <span data-ttu-id="63740-132">`ConnectServerWmi`iki dakika veya daha kısa bir süre döndürür.</span><span class="sxs-lookup"><span data-stu-id="63740-132">`ConnectServerWmi` returns in two minutes or less.</span></span> |

`strAuthority`\
<span data-ttu-id="63740-133">'ndaki Kullanıcının etki alanı adı.</span><span class="sxs-lookup"><span data-stu-id="63740-133">[in] The domain name of the user.</span></span> <span data-ttu-id="63740-134">Aşağıdaki değerlere sahip olabilir:</span><span class="sxs-lookup"><span data-stu-id="63740-134">It can have the following values:</span></span>

| <span data-ttu-id="63740-135">Değer</span><span class="sxs-lookup"><span data-stu-id="63740-135">Value</span></span> | <span data-ttu-id="63740-136">Açıklama</span><span class="sxs-lookup"><span data-stu-id="63740-136">Description</span></span> |
|---------|---------|
| <span data-ttu-id="63740-137">adet</span><span class="sxs-lookup"><span data-stu-id="63740-137">blank</span></span> | <span data-ttu-id="63740-138">NTLM kimlik doğrulaması kullanılır ve geçerli kullanıcının NTLM etki alanı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="63740-138">NTLM authentication is used, and the NTLM domain of the current user is used.</span></span> <span data-ttu-id="63740-139">Etki alanını (önerilen konum) belirtiyorsa,buradabelirtilmemelidir.`strUser`</span><span class="sxs-lookup"><span data-stu-id="63740-139">If `strUser` specifies the domain (the recommended location), it must not be specified here.</span></span> <span data-ttu-id="63740-140">İşlevi, etki `WBEM_E_INVALID_PARAMETER` alanını her iki parametrede de belirtirseniz döndürür.</span><span class="sxs-lookup"><span data-stu-id="63740-140">The function returns `WBEM_E_INVALID_PARAMETER` if you specify the domain in both parameters.</span></span> |
| <span data-ttu-id="63740-141">Kerberos:*asıl ad*</span><span class="sxs-lookup"><span data-stu-id="63740-141">Kerberos:*principal name*</span></span> | <span data-ttu-id="63740-142">Kerberos kimlik doğrulaması kullanılır ve bu parametre bir Kerberos asıl adı içerir.</span><span class="sxs-lookup"><span data-stu-id="63740-142">Kerberos authentication is used, and this parameter contains a Kerberos principal name.</span></span> |
| <span data-ttu-id="63740-143">NTLMDOMAIN:*etki alanı adı*</span><span class="sxs-lookup"><span data-stu-id="63740-143">NTLMDOMAIN:*domain name*</span></span> | <span data-ttu-id="63740-144">NT LAN Manager kimlik doğrulaması kullanılır ve bu parametre bir NTLM etki alanı adı içerir.</span><span class="sxs-lookup"><span data-stu-id="63740-144">NT LAN Manager authentication is used, and this parameter contains an NTLM domain name.</span></span> |

`pCtx`\
<span data-ttu-id="63740-145">'ndaki Genellikle, bu parametre `null`.</span><span class="sxs-lookup"><span data-stu-id="63740-145">[in] Typically, this parameter is `null`.</span></span> <span data-ttu-id="63740-146">Aksi takdirde, bir veya daha fazla dinamik sınıf sağlayıcısı için gereken bir [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) nesnesine yönelik bir işaretçidir.</span><span class="sxs-lookup"><span data-stu-id="63740-146">Otherwise, it is a pointer to an [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) object required by one or more dynamic class providers.</span></span>

`ppNamespace`\
<span data-ttu-id="63740-147">dışı İşlev döndüğünde, belirtilen ad alanına göre bir [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) nesnesine bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="63740-147">[out] When the function returns, receives a pointer to an [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) object bound to the specified namespace.</span></span> <span data-ttu-id="63740-148">Bir hata olduğunda ' ı işaret `null` etmek üzere ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="63740-148">It is set to point to `null` when there is an error.</span></span>

`impLevel`\
<span data-ttu-id="63740-149">'ndaki Kimliğe bürünme düzeyi.</span><span class="sxs-lookup"><span data-stu-id="63740-149">[in] The impersonation level.</span></span>

`authLevel`\
<span data-ttu-id="63740-150">'ndaki Yetkilendirme düzeyi.</span><span class="sxs-lookup"><span data-stu-id="63740-150">[in] The authorization level.</span></span>

## <a name="return-value"></a><span data-ttu-id="63740-151">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="63740-151">Return value</span></span>

<span data-ttu-id="63740-152">Bu işlev tarafından döndürülen aşağıdaki değerler, *Wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="63740-152">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="63740-153">Sabit</span><span class="sxs-lookup"><span data-stu-id="63740-153">Constant</span></span>  |<span data-ttu-id="63740-154">Değer</span><span class="sxs-lookup"><span data-stu-id="63740-154">Value</span></span>  |<span data-ttu-id="63740-155">Açıklama</span><span class="sxs-lookup"><span data-stu-id="63740-155">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="63740-156">0x80041001</span><span class="sxs-lookup"><span data-stu-id="63740-156">0x80041001</span></span> | <span data-ttu-id="63740-157">Genel bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="63740-157">There has been a general failure.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="63740-158">0x80041008</span><span class="sxs-lookup"><span data-stu-id="63740-158">0x80041008</span></span> | <span data-ttu-id="63740-159">Parametre geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="63740-159">A parameter is not valid.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="63740-160">0x80041006</span><span class="sxs-lookup"><span data-stu-id="63740-160">0x80041006</span></span> | <span data-ttu-id="63740-161">İşlemi gerçekleştirmek için yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="63740-161">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="63740-162">0</span><span class="sxs-lookup"><span data-stu-id="63740-162">0</span></span> | <span data-ttu-id="63740-163">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="63740-163">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="63740-164">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="63740-164">Remarks</span></span>

<span data-ttu-id="63740-165">Bu işlev, [IWbemLocator:: ConnectServer](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemlocator-connectserver) yöntemine bir çağrı kaydırır.</span><span class="sxs-lookup"><span data-stu-id="63740-165">This function wraps a call to the [IWbemLocator::ConnectServer](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemlocator-connectserver) method.</span></span>

<span data-ttu-id="63740-166">Varsayılan ad alanına `strNetworkResource` yerel erişim için basit bir nesne yolu olabilir: "root\default" veya "\\.\root\default".</span><span class="sxs-lookup"><span data-stu-id="63740-166">For local access to the default namespace, `strNetworkResource` can be a simple object path: "root\default" or "\\.\root\default".</span></span> <span data-ttu-id="63740-167">COM veya Microsoft uyumlu ağ kullanarak uzak bir bilgisayardaki varsayılan ad alanına erişim için, bilgisayar adı: "\\myserver\root\default" ifadesini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="63740-167">For access to the default namespace on a remote computer using COM or Microsoft-compatible networking, include the computer name: "\\myserver\root\default".</span></span> <span data-ttu-id="63740-168">Bilgisayar adı da bir DNS adı veya IP adresi olabilir.</span><span class="sxs-lookup"><span data-stu-id="63740-168">The computer name also can be a DNS name or IP address.</span></span> <span data-ttu-id="63740-169">`ConnectServerWmi` İşlevi IPv6 adresini kullanarak IPv6 çalıştıran bilgisayarlarla da bağlanabilir.</span><span class="sxs-lookup"><span data-stu-id="63740-169">The `ConnectServerWmi` function can also connect with computers running IPv6 using an IPv6 address.</span></span>

<span data-ttu-id="63740-170">`strUser`boş bir dize olamaz.</span><span class="sxs-lookup"><span data-stu-id="63740-170">`strUser` cannot be an empty string.</span></span> <span data-ttu-id="63740-171">Etki alanı içinde `strAuthority`belirtilmişse, ' de `strUser`dahil edilmemelidir ya da işlev döndürülür `WBEM_E_INVALID_PARAMETER`.</span><span class="sxs-lookup"><span data-stu-id="63740-171">If the domain is specified in `strAuthority`, it must not also be included in `strUser`, or the function returns `WBEM_E_INVALID_PARAMETER`.</span></span>

## <a name="requirements"></a><span data-ttu-id="63740-172">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="63740-172">Requirements</span></span>

 <span data-ttu-id="63740-173">**Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="63740-173">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

 <span data-ttu-id="63740-174">**Üst bilgi** WMINet_Utils. IDL</span><span class="sxs-lookup"><span data-stu-id="63740-174">**Header:** WMINet_Utils.idl</span></span>

 <span data-ttu-id="63740-175">**.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="63740-175">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="63740-176">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="63740-176">See also</span></span>

- [<span data-ttu-id="63740-177">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="63740-177">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
