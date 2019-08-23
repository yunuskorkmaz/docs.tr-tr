---
title: <serviceCertificate>
ms.date: 03/30/2017
ms.assetid: 42c7f291-2ec3-43c5-8872-35897ff3c660
author: BrucePerlerMS
ms.openlocfilehash: a3aba5618855f7225dc8a427516eaa72b45f6e8b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942405"
---
# <a name="servicecertificate"></a>\<serviceCertificate >
Belirteçleri şifrelemek ve şifrelerini çözmek için kullanılan X. 509.440 sertifikasını yapılandırır.  
  
 \<System. IdentityModel. Services >  
\<federationConfiguration >  
\<serviceCertificate >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <serviceCertificate>  
    </serviceCertificate>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
 Yok.  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<certificateReference >](certificatereference.md)|Bir sertifika deposundaki bir X. 509.440 sertifikasını bulmak ve doğrulamak için kullanılan ayarları belirtir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<federationConfiguration >](federationconfiguration.md)|<xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (Wsfab) <xref:System.IdentityModel.Services.SessionAuthenticationModule> ve (Sam) yapılandırma ayarlarını içerir.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki XML, \<ServiceCertificate > öğesinin kullanımını gösterir. XML `CustomToken` örnekten alınır.  
  
```xml  
<serviceCertificate>  
  <certificateReference x509FindType="FindBySubjectName" findValue="localhost" storeLocation="LocalMachine" storeName="My"/>  
</serviceCertificate>  
```
