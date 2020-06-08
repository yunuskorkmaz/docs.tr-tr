---
title: <servicePointManager> Öğesi (Ağ Ayarları)
description: <servicePointManager>Ağ ayarları öğesi .NET Framework ağ kaynakları seçeneklerine yönelik bağlantıları yapılandırır.
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#servicePointManager
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/servicePointManager
helpviewer_keywords:
- servicePointManager element
- <servicePointManager> element
ms.assetid: 6e5def51-3646-4ef6-a7bd-c69151321bec
ms.openlocfilehash: eb27716ec7c2936f32a7e4d4c983d1e175c4d044
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504530"
---
# <a name="servicepointmanager-element-network-settings"></a><span data-ttu-id="8146e-103">\<servicePointManager> Öğesi (Ağ Ayarları)</span><span class="sxs-lookup"><span data-stu-id="8146e-103">\<servicePointManager> Element (Network Settings)</span></span>
<span data-ttu-id="8146e-104">Ağ kaynaklarına bağlantıları yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="8146e-104">Configures connections to network resources.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<servicePointManager>**

## <a name="syntax"></a><span data-ttu-id="8146e-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8146e-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8146e-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="8146e-106">Attributes and Elements</span></span>  
 <span data-ttu-id="8146e-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8146e-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8146e-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="8146e-108">Attributes</span></span>  
  
|<span data-ttu-id="8146e-109">**Öznitelik**</span><span class="sxs-lookup"><span data-stu-id="8146e-109">**Attribute**</span></span>|<span data-ttu-id="8146e-110">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="8146e-110">**Description**</span></span>|  
|-------------------|---------------------|  
|`checkCertificateName`|<span data-ttu-id="8146e-111">Sistemin, sertifikayı kullanmadan önce sertifikadaki adın sunucu ana bilgisayar adıyla eşleşip eşleşmediğini doğrulaması gerekip gerekmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="8146e-111">Specifies whether the system should verify that the name on the certificate matches the server host name before using the certificate.</span></span> <span data-ttu-id="8146e-112">Varsayılan değer: `true`.</span><span class="sxs-lookup"><span data-stu-id="8146e-112">The default value is `true`.</span></span>|  
|`checkCertificateRevocationList`|<span data-ttu-id="8146e-113">Sistemin sertifika kullanılmadan önce sertifikanın iptal edilip edilmediğini denetleyip denetmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="8146e-113">Specifies whether the system should check whether the certificate has been revoked before using the certificate.</span></span> <span data-ttu-id="8146e-114">Varsayılan değer: `false`.</span><span class="sxs-lookup"><span data-stu-id="8146e-114">The default value is `false`.</span></span>|  
|`dnsRefreshTimeout`|<span data-ttu-id="8146e-115">Etki alanı adı hizmeti (DNS) çözümlerinin, DNS hepsini bir kez deneme seçeneğiyle birlikte ne kadar süreyle önbelleğe alınacağını belirtir (milisaniye cinsinden).</span><span class="sxs-lookup"><span data-stu-id="8146e-115">Specifies how long Domain Name Service (DNS) resolutions are cached in conjunction with the DNS Round Robin option, in milliseconds.</span></span> <span data-ttu-id="8146e-116">Varsayılan değer 120.000 milisaniyedir (iki dakika).</span><span class="sxs-lookup"><span data-stu-id="8146e-116">The default value is 120,000 milliseconds (two minutes).</span></span>|  
|`enableDnsRoundRobin`|<span data-ttu-id="8146e-117">Birden çok Internet Protokolü (IP) adresi olan ana bilgisayar adlarının DNS çözümlerinin, tüm adresleri mi yoksa yalnızca ilk birini mi döndürmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="8146e-117">Specifies whether DNS resolutions of host names with multiple Internet Protocol (IP) addresses return all the addresses, or just the first one.</span></span> <span data-ttu-id="8146e-118">Varsayılan değer: `false`.</span><span class="sxs-lookup"><span data-stu-id="8146e-118">The default value is `false`.</span></span>|  
|`encryptionPolicy`|<span data-ttu-id="8146e-119">Bir örnekteki SSL/TLS oturumuna uygulanan şifreleme ilkesini belirtir <xref:System.Net.ServicePointManager> .</span><span class="sxs-lookup"><span data-stu-id="8146e-119">Specifies the encryption policy applied to an SSL/TLS session on a <xref:System.Net.ServicePointManager> instance.</span></span> <span data-ttu-id="8146e-120">Olası değerler, <xref:System.Net.Security.EncryptionPolicy> sabit listesinin değerlerine eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="8146e-120">The possible values are equivalent to the values for the <xref:System.Net.Security.EncryptionPolicy> enumeration.</span></span> <span data-ttu-id="8146e-121"><xref:System.Security.Authentication.CipherAlgorithmType.Null>Şifreleme ilkesi olarak ayarlandığında kullanılması gerekir `NoEncryption` .</span><span class="sxs-lookup"><span data-stu-id="8146e-121">The use of <xref:System.Security.Authentication.CipherAlgorithmType.Null> is required when the encryption policy is set to `NoEncryption`.</span></span> <span data-ttu-id="8146e-122">Varsayılan değer: `RequireEncryption`.</span><span class="sxs-lookup"><span data-stu-id="8146e-122">The default value is `RequireEncryption`.</span></span>|  
|`expect100Continue`|<span data-ttu-id="8146e-123">POST yöntemlerinin sunucudan bir yanıt almayı beklemesi gerekip gerekmediğini belirtir `100-continue` .</span><span class="sxs-lookup"><span data-stu-id="8146e-123">Specifies whether POST methods should expect to receive a `100-continue` response from the server.</span></span> <span data-ttu-id="8146e-124">Varsayılan değer: `true`.</span><span class="sxs-lookup"><span data-stu-id="8146e-124">The default value is `true`.</span></span>|  
|`useNagleAlgorithm`|<span data-ttu-id="8146e-125">Hizmet noktası Yöneticisi tarafından denetlenen bağlantıların Nagle algoritmasını kullanıp kullanmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="8146e-125">Specifies whether connections controlled by the service point manager use the Nagle algorithm.</span></span> <span data-ttu-id="8146e-126">Varsayılan değer: `true`.</span><span class="sxs-lookup"><span data-stu-id="8146e-126">The default value is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8146e-127">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="8146e-127">Child Elements</span></span>  
 <span data-ttu-id="8146e-128">Yok.</span><span class="sxs-lookup"><span data-stu-id="8146e-128">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8146e-129">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="8146e-129">Parent Elements</span></span>  
  
|<span data-ttu-id="8146e-130">**Dosyalarında**</span><span class="sxs-lookup"><span data-stu-id="8146e-130">**Element**</span></span>|<span data-ttu-id="8146e-131">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="8146e-131">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="8146e-132">Ayarlar</span><span class="sxs-lookup"><span data-stu-id="8146e-132">Settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="8146e-133">Ad alanı için temel ağ seçeneklerini yapılandırır <xref:System.Net> .</span><span class="sxs-lookup"><span data-stu-id="8146e-133">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8146e-134">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8146e-134">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="8146e-135">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="8146e-135">Configuration Files</span></span>  
 <span data-ttu-id="8146e-136">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine. config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8146e-136">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8146e-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8146e-137">See also</span></span>

- <xref:System.Net.ServicePointManager>
- <xref:System.Net.Security.EncryptionPolicy>
- [<span data-ttu-id="8146e-138">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="8146e-138">Network Settings Schema</span></span>](index.md)
