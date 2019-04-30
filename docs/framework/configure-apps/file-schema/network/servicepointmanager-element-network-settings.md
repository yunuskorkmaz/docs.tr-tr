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
ms.openlocfilehash: 407ed85de109a671030eccff8ddd92af91628014
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704992"
---
# <a name="servicepointmanager-element-network-settings"></a><span data-ttu-id="1f766-102">\<servicePointManager > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="1f766-102">\<servicePointManager> Element (Network Settings)</span></span>
<span data-ttu-id="1f766-103">Ağ kaynaklarına bağlantılarını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="1f766-103">Configures connections to network resources.</span></span>  
  
 <span data-ttu-id="1f766-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="1f766-104">\<configuration></span></span>  
<span data-ttu-id="1f766-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="1f766-105">\<system.net></span></span>  
<span data-ttu-id="1f766-106">\<Ayarlar ></span><span class="sxs-lookup"><span data-stu-id="1f766-106">\<settings></span></span>  
<span data-ttu-id="1f766-107">\<servicePointManager ></span><span class="sxs-lookup"><span data-stu-id="1f766-107">\<servicePointManager></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f766-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1f766-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1f766-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="1f766-109">Attributes and Elements</span></span>  
 <span data-ttu-id="1f766-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1f766-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1f766-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="1f766-111">Attributes</span></span>  
  
|<span data-ttu-id="1f766-112">**Öznitelik**</span><span class="sxs-lookup"><span data-stu-id="1f766-112">**Attribute**</span></span>|<span data-ttu-id="1f766-113">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="1f766-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`checkCertificateName`|<span data-ttu-id="1f766-114">Sistem sertifika kullanmadan önce sertifikasındaki ad sunucusu konak adı eşleştiğini doğrulayın olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="1f766-114">Specifies whether the system should verify that the name on the certificate matches the server host name before using the certificate.</span></span> <span data-ttu-id="1f766-115">Varsayılan değer `true` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="1f766-115">The default value is `true`.</span></span>|  
|`checkCertificateRevocationList`|<span data-ttu-id="1f766-116">Sistem sertifika kullanmadan önce sertifika iptal olup olmadığını denetleyip denetlemeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="1f766-116">Specifies whether the system should check whether the certificate has been revoked before using the certificate.</span></span> <span data-ttu-id="1f766-117">Varsayılan değer `false` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="1f766-117">The default value is `false`.</span></span>|  
|`dnsRefreshTimeout`|<span data-ttu-id="1f766-118">Milisaniye cinsinden DNS hepsini bir kez deneme seçeneği ile birlikte ne kadar etki alanı adı hizmeti (çözümleri önbelleğe alınan DNS) belirtir.</span><span class="sxs-lookup"><span data-stu-id="1f766-118">Specifies how long Domain Name Service (DNS) resolutions are cached in conjunction with the DNS Round Robin option, in milliseconds.</span></span> <span data-ttu-id="1f766-119">Varsayılan değer 120.000 (iki dakika) milisaniyedir.</span><span class="sxs-lookup"><span data-stu-id="1f766-119">The default value is 120,000 milliseconds (two minutes).</span></span>|  
|`enableDnsRoundRobin`|<span data-ttu-id="1f766-120">Ana bilgisayarın DNS çözümleri adları olup olmadığını birden çok Internet Protokolü (IP) adresi ile dönüş tüm adresleri ya da yalnızca ilk eşleşmenin belirtir.</span><span class="sxs-lookup"><span data-stu-id="1f766-120">Specifies whether DNS resolutions of host names with multiple Internet Protocol (IP) addresses return all the addresses, or just the first one.</span></span> <span data-ttu-id="1f766-121">Varsayılan değer `false` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="1f766-121">The default value is `false`.</span></span>|  
|`encryptionPolicy`|<span data-ttu-id="1f766-122">Bir SSL/TLS oturumuna uygulanan şifreleme ilkesi belirtir bir <xref:System.Net.ServicePointManager> örneği.</span><span class="sxs-lookup"><span data-stu-id="1f766-122">Specifies the encryption policy applied to an SSL/TLS session on a <xref:System.Net.ServicePointManager> instance.</span></span> <span data-ttu-id="1f766-123">Olası değerler şunlardır: değerlerini eşdeğer <xref:System.Net.Security.EncryptionPolicy> sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="1f766-123">The possible values are equivalent to the values for the <xref:System.Net.Security.EncryptionPolicy> enumeration.</span></span> <span data-ttu-id="1f766-124">Kullanımını <xref:System.Security.Authentication.CipherAlgorithmType.Null> şifreleme ilkesi ayarlandığında gereklidir `NoEncryption`.</span><span class="sxs-lookup"><span data-stu-id="1f766-124">The use of <xref:System.Security.Authentication.CipherAlgorithmType.Null> is required when the encryption policy is set to `NoEncryption`.</span></span> <span data-ttu-id="1f766-125">Varsayılan değer `RequireEncryption` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="1f766-125">The default value is `RequireEncryption`.</span></span>|  
|`expect100Continue`|<span data-ttu-id="1f766-126">POST yöntemleri almayı beklemelisiniz olup olmadığını belirten bir `100-continue` sunucu yanıtı.</span><span class="sxs-lookup"><span data-stu-id="1f766-126">Specifies whether POST methods should expect to receive a `100-continue` response from the server.</span></span> <span data-ttu-id="1f766-127">Varsayılan değer `true` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="1f766-127">The default value is `true`.</span></span>|  
|`useNagleAlgorithm`|<span data-ttu-id="1f766-128">Hizmet Noktası Yöneticisi tarafından denetlenen bağlantıları Nagle algoritma kullanıp kullanmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="1f766-128">Specifies whether connections controlled by the service point manager use the Nagle algorithm.</span></span> <span data-ttu-id="1f766-129">Varsayılan değer `true` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="1f766-129">The default value is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1f766-130">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="1f766-130">Child Elements</span></span>  
 <span data-ttu-id="1f766-131">Yok.</span><span class="sxs-lookup"><span data-stu-id="1f766-131">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1f766-132">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="1f766-132">Parent Elements</span></span>  
  
|<span data-ttu-id="1f766-133">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="1f766-133">**Element**</span></span>|<span data-ttu-id="1f766-134">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="1f766-134">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="1f766-135">Ayarlar</span><span class="sxs-lookup"><span data-stu-id="1f766-135">Settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<span data-ttu-id="1f766-136">Temel ağ seçeneklerini yapılandırır <xref:System.Net> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="1f766-136">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1f766-137">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1f766-137">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="1f766-138">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="1f766-138">Configuration Files</span></span>  
 <span data-ttu-id="1f766-139">Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1f766-139">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f766-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1f766-140">See also</span></span>

- <xref:System.Net.ServicePointManager>
- <xref:System.Net.Security.EncryptionPolicy>
- [<span data-ttu-id="1f766-141">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="1f766-141">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
