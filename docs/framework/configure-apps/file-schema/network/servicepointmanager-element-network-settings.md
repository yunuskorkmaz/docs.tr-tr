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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "74089120"
---
# <a name="servicepointmanager-element-network-settings"></a><span data-ttu-id="a8559-102">\<servicePointManager> Öğesi (Ağ Ayarları)</span><span class="sxs-lookup"><span data-stu-id="a8559-102">\<servicePointManager> Element (Network Settings)</span></span>
<span data-ttu-id="a8559-103">Ağ kaynaklarına bağlantıları yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="a8559-103">Configures connections to network resources.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<servicePointManager>**

## <a name="syntax"></a><span data-ttu-id="a8559-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a8559-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a8559-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a8559-105">Attributes and Elements</span></span>  
 <span data-ttu-id="a8559-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a8559-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a8559-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a8559-107">Attributes</span></span>  
  
|<span data-ttu-id="a8559-108">**Öznitelik**</span><span class="sxs-lookup"><span data-stu-id="a8559-108">**Attribute**</span></span>|<span data-ttu-id="a8559-109">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="a8559-109">**Description**</span></span>|  
|-------------------|---------------------|  
|`checkCertificateName`|<span data-ttu-id="a8559-110">Sistemin, sertifikayı kullanmadan önce sertifikadaki adın sunucu ana bilgisayar adıyla eşleşip eşleşmediğini doğrulaması gerekip gerekmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a8559-110">Specifies whether the system should verify that the name on the certificate matches the server host name before using the certificate.</span></span> <span data-ttu-id="a8559-111">Varsayılan değer: `true`.</span><span class="sxs-lookup"><span data-stu-id="a8559-111">The default value is `true`.</span></span>|  
|`checkCertificateRevocationList`|<span data-ttu-id="a8559-112">Sistemin sertifika kullanılmadan önce sertifikanın iptal edilip edilmediğini denetleyip denetmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a8559-112">Specifies whether the system should check whether the certificate has been revoked before using the certificate.</span></span> <span data-ttu-id="a8559-113">Varsayılan değer: `false`.</span><span class="sxs-lookup"><span data-stu-id="a8559-113">The default value is `false`.</span></span>|  
|`dnsRefreshTimeout`|<span data-ttu-id="a8559-114">Etki alanı adı hizmeti (DNS) çözümlerinin, DNS hepsini bir kez deneme seçeneğiyle birlikte ne kadar süreyle önbelleğe alınacağını belirtir (milisaniye cinsinden).</span><span class="sxs-lookup"><span data-stu-id="a8559-114">Specifies how long Domain Name Service (DNS) resolutions are cached in conjunction with the DNS Round Robin option, in milliseconds.</span></span> <span data-ttu-id="a8559-115">Varsayılan değer 120.000 milisaniyedir (iki dakika).</span><span class="sxs-lookup"><span data-stu-id="a8559-115">The default value is 120,000 milliseconds (two minutes).</span></span>|  
|`enableDnsRoundRobin`|<span data-ttu-id="a8559-116">Birden çok Internet Protokolü (IP) adresi olan ana bilgisayar adlarının DNS çözümlerinin, tüm adresleri mi yoksa yalnızca ilk birini mi döndürmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a8559-116">Specifies whether DNS resolutions of host names with multiple Internet Protocol (IP) addresses return all the addresses, or just the first one.</span></span> <span data-ttu-id="a8559-117">Varsayılan değer: `false`.</span><span class="sxs-lookup"><span data-stu-id="a8559-117">The default value is `false`.</span></span>|  
|`encryptionPolicy`|<span data-ttu-id="a8559-118">Bir örnekteki SSL/TLS oturumuna uygulanan şifreleme ilkesini belirtir <xref:System.Net.ServicePointManager> .</span><span class="sxs-lookup"><span data-stu-id="a8559-118">Specifies the encryption policy applied to an SSL/TLS session on a <xref:System.Net.ServicePointManager> instance.</span></span> <span data-ttu-id="a8559-119">Olası değerler, <xref:System.Net.Security.EncryptionPolicy> sabit listesinin değerlerine eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="a8559-119">The possible values are equivalent to the values for the <xref:System.Net.Security.EncryptionPolicy> enumeration.</span></span> <span data-ttu-id="a8559-120"><xref:System.Security.Authentication.CipherAlgorithmType.Null>Şifreleme ilkesi olarak ayarlandığında kullanılması gerekir `NoEncryption` .</span><span class="sxs-lookup"><span data-stu-id="a8559-120">The use of <xref:System.Security.Authentication.CipherAlgorithmType.Null> is required when the encryption policy is set to `NoEncryption`.</span></span> <span data-ttu-id="a8559-121">Varsayılan değer: `RequireEncryption`.</span><span class="sxs-lookup"><span data-stu-id="a8559-121">The default value is `RequireEncryption`.</span></span>|  
|`expect100Continue`|<span data-ttu-id="a8559-122">POST yöntemlerinin sunucudan bir yanıt almayı beklemesi gerekip gerekmediğini belirtir `100-continue` .</span><span class="sxs-lookup"><span data-stu-id="a8559-122">Specifies whether POST methods should expect to receive a `100-continue` response from the server.</span></span> <span data-ttu-id="a8559-123">Varsayılan değer: `true`.</span><span class="sxs-lookup"><span data-stu-id="a8559-123">The default value is `true`.</span></span>|  
|`useNagleAlgorithm`|<span data-ttu-id="a8559-124">Hizmet noktası Yöneticisi tarafından denetlenen bağlantıların Nagle algoritmasını kullanıp kullanmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a8559-124">Specifies whether connections controlled by the service point manager use the Nagle algorithm.</span></span> <span data-ttu-id="a8559-125">Varsayılan değer: `true`.</span><span class="sxs-lookup"><span data-stu-id="a8559-125">The default value is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a8559-126">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a8559-126">Child Elements</span></span>  
 <span data-ttu-id="a8559-127">Yok.</span><span class="sxs-lookup"><span data-stu-id="a8559-127">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a8559-128">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a8559-128">Parent Elements</span></span>  
  
|<span data-ttu-id="a8559-129">**Dosyalarında**</span><span class="sxs-lookup"><span data-stu-id="a8559-129">**Element**</span></span>|<span data-ttu-id="a8559-130">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="a8559-130">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="a8559-131">Ayarlar</span><span class="sxs-lookup"><span data-stu-id="a8559-131">Settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="a8559-132">Ad alanı için temel ağ seçeneklerini yapılandırır <xref:System.Net> .</span><span class="sxs-lookup"><span data-stu-id="a8559-132">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a8559-133">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a8559-133">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="a8559-134">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="a8559-134">Configuration Files</span></span>  
 <span data-ttu-id="a8559-135">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine. config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a8559-135">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8559-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a8559-136">See also</span></span>

- <xref:System.Net.ServicePointManager>
- <xref:System.Net.Security.EncryptionPolicy>
- [<span data-ttu-id="a8559-137">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="a8559-137">Network Settings Schema</span></span>](index.md)
