---
title: '&lt;servicePointManager&gt; öğesi (ağ ayarları)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#servicePointManager
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/servicePointManager
helpviewer_keywords:
- servicePointManager element
- <servicePointManager> element
ms.assetid: 6e5def51-3646-4ef6-a7bd-c69151321bec
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 5903174f125938923a63fc031421a8d5a020e56d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltservicepointmanagergt-element-network-settings"></a><span data-ttu-id="b67d8-102">&lt;servicePointManager&gt; öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="b67d8-102">&lt;servicePointManager&gt; Element (Network Settings)</span></span>
<span data-ttu-id="b67d8-103">Ağ kaynaklarına bağlantılarını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="b67d8-103">Configures connections to network resources.</span></span>  
  
 <span data-ttu-id="b67d8-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="b67d8-104">\<configuration></span></span>  
<span data-ttu-id="b67d8-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="b67d8-105">\<system.net></span></span>  
<span data-ttu-id="b67d8-106">\<Ayarlar ></span><span class="sxs-lookup"><span data-stu-id="b67d8-106">\<settings></span></span>  
<span data-ttu-id="b67d8-107">\<servicePointManager ></span><span class="sxs-lookup"><span data-stu-id="b67d8-107">\<servicePointManager></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b67d8-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b67d8-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b67d8-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b67d8-109">Attributes and Elements</span></span>  
 <span data-ttu-id="b67d8-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b67d8-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b67d8-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b67d8-111">Attributes</span></span>  
  
|<span data-ttu-id="b67d8-112">**Özniteliği**</span><span class="sxs-lookup"><span data-stu-id="b67d8-112">**Attribute**</span></span>|<span data-ttu-id="b67d8-113">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="b67d8-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`checkCertificateName`|<span data-ttu-id="b67d8-114">Sistem adı sertifikadaki sertifika kullanmadan önce sunucu ana bilgisayar adıyla eşleşen doğrulamalısınız olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="b67d8-114">Specifies whether the system should verify that the name on the certificate matches the server host name before using the certificate.</span></span> <span data-ttu-id="b67d8-115">Varsayılan değer `true` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="b67d8-115">The default value is `true`.</span></span>|  
|`checkCertificateRevocationList`|<span data-ttu-id="b67d8-116">Sistem sertifika kullanmadan önce sertifikanın iptal edilmediğini denetleyip denetlemeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b67d8-116">Specifies whether the system should check whether the certificate has been revoked before using the certificate.</span></span> <span data-ttu-id="b67d8-117">Varsayılan değer `false` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="b67d8-117">The default value is `false`.</span></span>|  
|`dnsRefreshTimeout`|<span data-ttu-id="b67d8-118">Milisaniye cinsinden DNS hepsini bir kez seçeneğiyle birlikte ne kadar etki alanı adı hizmeti (çözümleri önbelleğe alınan DNS) belirtir.</span><span class="sxs-lookup"><span data-stu-id="b67d8-118">Specifies how long Domain Name Service (DNS) resolutions are cached in conjunction with the DNS Round Robin option, in milliseconds.</span></span> <span data-ttu-id="b67d8-119">Varsayılan değer 120.000 (iki dakika) milisaniyedir.</span><span class="sxs-lookup"><span data-stu-id="b67d8-119">The default value is 120,000 milliseconds (two minutes).</span></span>|  
|`enableDnsRoundRobin`|<span data-ttu-id="b67d8-120">Ana bilgisayarın DNS çözümleri adları olup olmadığını birden çok Internet Protokolü (IP) adreslerini ile dönüş tüm adresleri ya da yalnızca ilk dizine belirtir.</span><span class="sxs-lookup"><span data-stu-id="b67d8-120">Specifies whether DNS resolutions of host names with multiple Internet Protocol (IP) addresses return all the addresses, or just the first one.</span></span> <span data-ttu-id="b67d8-121">Varsayılan değer `false` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="b67d8-121">The default value is `false`.</span></span>|  
|`encryptionPolicy`|<span data-ttu-id="b67d8-122">Bir SSL/TLS oturumu uygulanan şifreleme ilkesi belirtir bir <xref:System.Net.ServicePointManager> örneği.</span><span class="sxs-lookup"><span data-stu-id="b67d8-122">Specifies the encryption policy applied to an SSL/TLS session on a <xref:System.Net.ServicePointManager> instance.</span></span> <span data-ttu-id="b67d8-123">Olası değerler için değerlerine eşdeğer <xref:System.Net.Security.EncryptionPolicy> numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="b67d8-123">The possible values are equivalent to the values for the <xref:System.Net.Security.EncryptionPolicy> enumeration.</span></span> <span data-ttu-id="b67d8-124">Kullanımını <xref:System.Security.Authentication.CipherAlgorithmType.Null> şifreleme ilkesi ayarlandığında gereklidir `NoEncryption`.</span><span class="sxs-lookup"><span data-stu-id="b67d8-124">The use of <xref:System.Security.Authentication.CipherAlgorithmType.Null> is required when the encryption policy is set to `NoEncryption`.</span></span> <span data-ttu-id="b67d8-125">Varsayılan değer `RequireEncryption` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="b67d8-125">The default value is `RequireEncryption`.</span></span>|  
|`expect100Continue`|<span data-ttu-id="b67d8-126">POST yöntemleri almaya beklemelisiniz olup olmadığını belirten bir `100-continue` sunucudan gelen yanıtı.</span><span class="sxs-lookup"><span data-stu-id="b67d8-126">Specifies whether POST methods should expect to receive a `100-continue` response from the server.</span></span> <span data-ttu-id="b67d8-127">Varsayılan değer `true` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="b67d8-127">The default value is `true`.</span></span>|  
|`useNagleAlgorithm`|<span data-ttu-id="b67d8-128">Hizmet Noktası Yöneticisi tarafından denetlenen bağlantıları Nagle algoritması kullanıp kullanmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="b67d8-128">Specifies whether connections controlled by the service point manager use the Nagle algorithm.</span></span> <span data-ttu-id="b67d8-129">Varsayılan değer `true` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="b67d8-129">The default value is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b67d8-130">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b67d8-130">Child Elements</span></span>  
 <span data-ttu-id="b67d8-131">Yok.</span><span class="sxs-lookup"><span data-stu-id="b67d8-131">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b67d8-132">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b67d8-132">Parent Elements</span></span>  
  
|<span data-ttu-id="b67d8-133">**Öğesi**</span><span class="sxs-lookup"><span data-stu-id="b67d8-133">**Element**</span></span>|<span data-ttu-id="b67d8-134">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="b67d8-134">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="b67d8-135">Ayarlar</span><span class="sxs-lookup"><span data-stu-id="b67d8-135">Settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<span data-ttu-id="b67d8-136">Temel ağ seçeneklerini yapılandırır <xref:System.Net> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="b67d8-136">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b67d8-137">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b67d8-137">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="b67d8-138">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="b67d8-138">Configuration Files</span></span>  
 <span data-ttu-id="b67d8-139">Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b67d8-139">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b67d8-140">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b67d8-140">See Also</span></span>  
 <xref:System.Net.ServicePointManager>  
 <xref:System.Net.Security.EncryptionPolicy>  
 [<span data-ttu-id="b67d8-141">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="b67d8-141">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
