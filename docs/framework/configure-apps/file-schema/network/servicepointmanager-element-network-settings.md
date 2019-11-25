---
title: <servicePointManager> Öğesi (Ağ Ayarları)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#servicePointManager
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/servicePointManager
helpviewer_keywords:
- servicePointManager element
- <servicePointManager> element
ms.assetid: 6e5def51-3646-4ef6-a7bd-c69151321bec
ms.openlocfilehash: b7333016fea2d46285d3c98181c0ca4904c376f8
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74089120"
---
# <a name="servicepointmanager-element-network-settings"></a><span data-ttu-id="2714b-102">\<servicePointManager > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="2714b-102">\<servicePointManager> Element (Network Settings)</span></span>
<span data-ttu-id="2714b-103">Ağ kaynaklarına bağlantıları yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="2714b-103">Configures connections to network resources.</span></span>  

<span data-ttu-id="2714b-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="2714b-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="2714b-105">[**System. net >\<** ](system-net-element-network-settings.md) &nbsp;&nbsp;</span><span class="sxs-lookup"><span data-stu-id="2714b-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="2714b-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<ayarları >** ](settings-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="2714b-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)</span></span>\
<span data-ttu-id="2714b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<servicePointManager >**</span><span class="sxs-lookup"><span data-stu-id="2714b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<servicePointManager>**</span></span>

## <a name="syntax"></a><span data-ttu-id="2714b-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2714b-108">Syntax</span></span>  
  
```xml  
<servicePointManager  
  checkCertificateName="true|false"  
  checkCertificateRevocationList="true|false"  
  encryptionPolicy="AllowNoEncryption|NoEncryption|RequireEncryption"  
  expect100Continue="true|false"  
  useNagleAlgorithm="true|false"  
  enableDnsRoundRobin="true|false"  
  dnsRefreshTimeout="time"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2714b-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="2714b-109">Attributes and Elements</span></span>  
 <span data-ttu-id="2714b-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2714b-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2714b-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="2714b-111">Attributes</span></span>  
  
|<span data-ttu-id="2714b-112">**Öznitelik**</span><span class="sxs-lookup"><span data-stu-id="2714b-112">**Attribute**</span></span>|<span data-ttu-id="2714b-113">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="2714b-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`checkCertificateName`|<span data-ttu-id="2714b-114">Sistemin, sertifikayı kullanmadan önce sertifikadaki adın sunucu ana bilgisayar adıyla eşleşip eşleşmediğini doğrulaması gerekip gerekmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="2714b-114">Specifies whether the system should verify that the name on the certificate matches the server host name before using the certificate.</span></span> <span data-ttu-id="2714b-115">Varsayılan değer `true` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="2714b-115">The default value is `true`.</span></span>|  
|`checkCertificateRevocationList`|<span data-ttu-id="2714b-116">Sistemin sertifika kullanılmadan önce sertifikanın iptal edilip edilmediğini denetleyip denetmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="2714b-116">Specifies whether the system should check whether the certificate has been revoked before using the certificate.</span></span> <span data-ttu-id="2714b-117">Varsayılan değer `false` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="2714b-117">The default value is `false`.</span></span>|  
|`dnsRefreshTimeout`|<span data-ttu-id="2714b-118">Etki alanı adı hizmeti (DNS) çözümlerinin, DNS hepsini bir kez deneme seçeneğiyle birlikte ne kadar süreyle önbelleğe alınacağını belirtir (milisaniye cinsinden).</span><span class="sxs-lookup"><span data-stu-id="2714b-118">Specifies how long Domain Name Service (DNS) resolutions are cached in conjunction with the DNS Round Robin option, in milliseconds.</span></span> <span data-ttu-id="2714b-119">Varsayılan değer 120.000 milisaniyedir (iki dakika).</span><span class="sxs-lookup"><span data-stu-id="2714b-119">The default value is 120,000 milliseconds (two minutes).</span></span>|  
|`enableDnsRoundRobin`|<span data-ttu-id="2714b-120">Birden çok Internet Protokolü (IP) adresi olan ana bilgisayar adlarının DNS çözümlerinin, tüm adresleri mi yoksa yalnızca ilk birini mi döndürmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="2714b-120">Specifies whether DNS resolutions of host names with multiple Internet Protocol (IP) addresses return all the addresses, or just the first one.</span></span> <span data-ttu-id="2714b-121">Varsayılan değer `false` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="2714b-121">The default value is `false`.</span></span>|  
|`encryptionPolicy`|<span data-ttu-id="2714b-122">Bir <xref:System.Net.ServicePointManager> örneğindeki SSL/TLS oturumuna uygulanan şifreleme ilkesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="2714b-122">Specifies the encryption policy applied to an SSL/TLS session on a <xref:System.Net.ServicePointManager> instance.</span></span> <span data-ttu-id="2714b-123">Olası değerler <xref:System.Net.Security.EncryptionPolicy> numaralandırması için değerler ile eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="2714b-123">The possible values are equivalent to the values for the <xref:System.Net.Security.EncryptionPolicy> enumeration.</span></span> <span data-ttu-id="2714b-124">Şifreleme ilkesi `NoEncryption`olarak ayarlandığında <xref:System.Security.Authentication.CipherAlgorithmType.Null> kullanılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="2714b-124">The use of <xref:System.Security.Authentication.CipherAlgorithmType.Null> is required when the encryption policy is set to `NoEncryption`.</span></span> <span data-ttu-id="2714b-125">Varsayılan değer `RequireEncryption` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="2714b-125">The default value is `RequireEncryption`.</span></span>|  
|`expect100Continue`|<span data-ttu-id="2714b-126">POST yöntemlerinin sunucudan `100-continue` yanıtı almayı beklemesi gerekip gerekmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="2714b-126">Specifies whether POST methods should expect to receive a `100-continue` response from the server.</span></span> <span data-ttu-id="2714b-127">Varsayılan değer `true` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="2714b-127">The default value is `true`.</span></span>|  
|`useNagleAlgorithm`|<span data-ttu-id="2714b-128">Hizmet noktası Yöneticisi tarafından denetlenen bağlantıların Nagle algoritmasını kullanıp kullanmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="2714b-128">Specifies whether connections controlled by the service point manager use the Nagle algorithm.</span></span> <span data-ttu-id="2714b-129">Varsayılan değer `true` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="2714b-129">The default value is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2714b-130">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="2714b-130">Child Elements</span></span>  
 <span data-ttu-id="2714b-131">Yok.</span><span class="sxs-lookup"><span data-stu-id="2714b-131">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2714b-132">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="2714b-132">Parent Elements</span></span>  
  
|<span data-ttu-id="2714b-133">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="2714b-133">**Element**</span></span>|<span data-ttu-id="2714b-134">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="2714b-134">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="2714b-135">Ayarlar</span><span class="sxs-lookup"><span data-stu-id="2714b-135">Settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="2714b-136"><xref:System.Net> ad alanı için temel ağ seçeneklerini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="2714b-136">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2714b-137">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2714b-137">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="2714b-138">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="2714b-138">Configuration Files</span></span>  
 <span data-ttu-id="2714b-139">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine. config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2714b-139">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2714b-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2714b-140">See also</span></span>

- <xref:System.Net.ServicePointManager>
- <xref:System.Net.Security.EncryptionPolicy>
- [<span data-ttu-id="2714b-141">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="2714b-141">Network Settings Schema</span></span>](index.md)
