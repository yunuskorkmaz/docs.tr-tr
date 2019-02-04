---
title: <certificate> , <peer>
ms.date: 03/30/2017
ms.assetid: 48b69142-c957-4305-a042-c9d0c9a55c0e
ms.openlocfilehash: 57f011bd0d6311c71871773ea866ef4c52513b17
ms.sourcegitcommit: b8ace47d839f943f785b89e2fff8092b0bf8f565
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55674613"
---
# <a name="certificate-of-peer"></a>\<Sertifika >, \<eş >
Bir eşin kullandığı sertifikayı belirtir.  
  
 \<system.ServiceModel>  
\<davranışlar >  
\<serviceBehaviors>  
\<davranışı >  
\<serviceCredentials>  
\<Eş >  
\<Sertifika >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<certificate findValue = "String"
             storeLocation = "CurrentUser/LocalMachine"
             storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
             X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`findValue`|X.509 sertifika deposunda aranacak değeri içeren bir dize. Özniteliğinde bulunan türü belirtilen gereksinimleri karşılaması gerekir `x509FindType`. Varsayılan değer boş bir dizedir.|  
|`storeLocation`|Eşin sertifikasını doğrulamak için istemcinin kullandığı X.509 Sertifika deposunun konumunu belirtir. Geçerli değerler şunlardır:<br /><br /> -LocalMachine: yerel makineye atanmış sertifika deposu.<br />-CurrentUser: geçerli kullanıcıya atanmış sertifika deposu.<br /><br /> LocalMachine varsayılandır.|  
|`storeName`|Açılacak X.509 Sertifika deposunun adını belirtir. Geçerli değerler şunlardır:<br /><br /> -Adres Defteri: Diğer kullanıcılar için sertifika deposu.<br />-AuthRoot: Üçüncü taraf sertifika yetkilileri (CA'lar) için sertifika deposu.<br />-CertificateAuthority: Ara Sertifika yetkilileri (CA'lar) için sertifika deposu.<br />-İzin verilmedi: İptal edilen sertifikalar için sertifika deposu.<br />-My: Kişisel Sertifikalar için sertifika deposu.<br />-Kök: Güvenilen kök sertifika yetkilileri (CA'lar) için sertifika deposu.<br />-TrustedPeople: Sertifika deposu-doğrudan güvenilen kişiler ve kaynaklar.<br />-TrustedPublisher: Doğrudan Güvenilen Yayımcılar sertifika deposu.<br /><br /> Varsayılan değer benim.|  
|`X509FindType`|Yürütülecek X.509 arama türünü tanımlar. Geçerli değerler şunlardır:<br /><br /> -FindByThumbPrint<br />-FindBySubjectName<br />-FindBySubjectDistinguishedName<br />-FindByIssuerName<br />-FindByIssuerDistinguishedName<br />-FindBySerialNumber<br />-FindByTimeValid<br />-FindByTimeNotYetValid<br />-   FindByTemplateName<br />-FindByApplicationPolicy<br />-FindByCertificatePolicy<br />-FindByExtension<br />-   FindByKeyUsage<br />-FindBySubjectKeyIdentifier<br /><br /> Bulunan tür `findValue` öznitelik belirtilen gereksinimleri karşılaması gerekir `X509FindType`.<br /><br /> FindBySubjectDistinguishedName varsayılan değerdir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Eş >](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-servicecredentials.md)|Bir eşdüzey düğüm için geçerli kimlik bilgilerini belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yapılandırma öğesi içeren bir `X509Certificate2` Komşuları eş ağ içinde kimlik doğrulaması için kullanılan bir örnek.  
  
 Eşler arası programlama hakkında daha fazla bilgi için bkz. [eşler arası ağ](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.Certificate%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateElement>
- <xref:System.ServiceModel.Security.PeerCredential.Certificate%2A>
- <xref:System.ServiceModel.Security.PeerCredential>
- [Sertifikalarla Çalışma](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [Eşler Arası Ağ](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)
- [Eş kanal ileti kimlik doğrulaması](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))
- [Eş kanal özel kimlik doğrulama](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))
- [Eş Kanalı Uygulamalarını Güvenli Hale Getirme](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
- [Hizmet ve İstemcileri Güvenli Hale Getirme](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
