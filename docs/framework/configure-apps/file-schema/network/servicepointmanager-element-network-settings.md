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
# <a name="servicepointmanager-element-network-settings"></a>\<servicePointManager> Öğesi (Ağ Ayarları)
Ağ kaynaklarına bağlantıları yapılandırır.  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<servicePointManager>**

## <a name="syntax"></a>Sözdizimi  
  
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
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|**Öznitelik**|**Açıklama**|  
|-------------------|---------------------|  
|`checkCertificateName`|Sistemin, sertifikayı kullanmadan önce sertifikadaki adın sunucu ana bilgisayar adıyla eşleşip eşleşmediğini doğrulaması gerekip gerekmediğini belirtir. Varsayılan değer: `true`.|  
|`checkCertificateRevocationList`|Sistemin sertifika kullanılmadan önce sertifikanın iptal edilip edilmediğini denetleyip denetmeyeceğini belirtir. Varsayılan değer: `false`.|  
|`dnsRefreshTimeout`|Etki alanı adı hizmeti (DNS) çözümlerinin, DNS hepsini bir kez deneme seçeneğiyle birlikte ne kadar süreyle önbelleğe alınacağını belirtir (milisaniye cinsinden). Varsayılan değer 120.000 milisaniyedir (iki dakika).|  
|`enableDnsRoundRobin`|Birden çok Internet Protokolü (IP) adresi olan ana bilgisayar adlarının DNS çözümlerinin, tüm adresleri mi yoksa yalnızca ilk birini mi döndürmediğini belirtir. Varsayılan değer: `false`.|  
|`encryptionPolicy`|Bir örnekteki SSL/TLS oturumuna uygulanan şifreleme ilkesini belirtir <xref:System.Net.ServicePointManager> . Olası değerler, <xref:System.Net.Security.EncryptionPolicy> sabit listesinin değerlerine eşdeğerdir. <xref:System.Security.Authentication.CipherAlgorithmType.Null>Şifreleme ilkesi olarak ayarlandığında kullanılması gerekir `NoEncryption` . Varsayılan değer: `RequireEncryption`.|  
|`expect100Continue`|POST yöntemlerinin sunucudan bir yanıt almayı beklemesi gerekip gerekmediğini belirtir `100-continue` . Varsayılan değer: `true`.|  
|`useNagleAlgorithm`|Hizmet noktası Yöneticisi tarafından denetlenen bağlantıların Nagle algoritmasını kullanıp kullanmadığını belirtir. Varsayılan değer: `true`.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|**Dosyalarında**|**Açıklama**|  
|-----------------|---------------------|  
|[Ayarlar](settings-element-network-settings.md)|Ad alanı için temel ağ seçeneklerini yapılandırır <xref:System.Net> .|  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="configuration-files"></a>Yapılandırma Dosyaları  
 Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine. config) kullanılabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Net.ServicePointManager>
- <xref:System.Net.Security.EncryptionPolicy>
- [Ağ Ayarları Şeması](index.md)
