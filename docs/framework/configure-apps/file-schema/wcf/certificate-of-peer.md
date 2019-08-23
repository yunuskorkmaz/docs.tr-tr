---
title: <certificate> / <peer>
ms.date: 03/30/2017
ms.assetid: 48b69142-c957-4305-a042-c9d0c9a55c0e
ms.openlocfilehash: 72128aca1321f3adc4c99ce0e3a47489b1640e31
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919594"
---
# <a name="certificate-of-peer"></a>\<\<eş > sertifika >
Bir eş tarafından kullanılan bir sertifikayı belirtir.  
  
 \<system.ServiceModel>  
\<davranışlar >  
\<serviceBehaviors>  
\<davranış >  
\<serviceCredentials>  
\<eş >  
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
|`findValue`|X. 509.440 sertifika deposunda aranacak değeri içeren bir dize. Özniteliğinde yer alan türün, belirtilen `x509FindType`gereksinimleri karşılaması gerekir. Varsayılan değer boş bir dizedir.|  
|`storeLocation`|İstemcinin eşin sertifikasını doğrulamak için kullandığı X. 509.952 sertifika deposunun konumunu belirtir. Geçerli değerler şunlardır:<br /><br /> -LocalMachine: yerel makineye atanan sertifika depolama alanı.<br />-CurrentUser: geçerli kullanıcıya atanmış sertifika deposu.<br /><br /> Varsayılan değer LocalMachine 'dir.|  
|`storeName`|Açılacak X. 509.440 sertifika deposunun adını belirtir. Geçerli değerler şunlardır:<br /><br /> -AddressBook: Diğer kullanıcılar için sertifika deposu.<br />-AuthRoot: Üçüncü taraf sertifika yetkilileri (CA 'Lar) için sertifika deposu.<br />CertificateAuthority Ara sertifika yetkilileri (CA 'Lar) için sertifika deposu.<br />Veril İptal edilen sertifikalar için sertifika deposu.<br />My Kişisel Sertifikalar için sertifika deposu.<br />Asıl Güvenilen kök sertifika yetkilileri (CA 'Lar) için sertifika deposu.<br />TrustedPeople Doğrudan güvenilen kişiler ve kaynaklar için sertifika deposu.<br />-TrustedPublisher: Doğrudan güvenilen yayımcılar için sertifika deposu.<br /><br /> Varsayılan My.|  
|`X509FindType`|Yürütülecek X. 509.440 aramasının türünü tanımlar. Geçerli değerler şunlardır:<br /><br /> -Findbyparmak Izi<br />-FindBySubjectName<br />- FindBySubjectDistinguishedName<br />-FindByIssuerName<br />- FindByIssuerDistinguishedName<br />-FindBySerialNumber<br />-FindByTimeValid<br />-FindByTimeNotYetValid<br />-FindByTemplateName<br />- FindByApplicationPolicy<br />-FindByCertificatePolicy<br />-FindByExtension<br />-FindByKeyUsage<br />-FindBySubjectKeyIdentifier<br /><br /> `findValue` Özniteliğinde yer alan türün, belirtilen `X509FindType`gereksinimleri karşılaması gerekir.<br /><br /> Varsayılan değer FindBySubjectDistinguishedName ' dir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<eş >](peer-of-servicecredentials.md)|Eş düğüm için geçerli kimlik bilgilerini belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yapılandırma öğesi, eş `X509Certificate2` kafeste komşuları doğrulanırken kullanılan bir örnek içerir.  
  
 Eşler arası programlama hakkında daha fazla bilgi için bkz. eşler [arası ağ iletişimi](../../../wcf/feature-details/peer-to-peer-networking.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.Certificate%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateElement>
- <xref:System.ServiceModel.Security.PeerCredential.Certificate%2A>
- <xref:System.ServiceModel.Security.PeerCredential>
- [Sertifikalarla Çalışma](../../../wcf/feature-details/working-with-certificates.md)
- [Eşler Arası Ağ](../../../wcf/feature-details/peer-to-peer-networking.md)
- [Eş kanal Iletisi kimlik doğrulaması](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))
- [Eş kanal özel kimlik doğrulaması](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))
- [Eş Kanalı Uygulamalarını Güvenli Hale Getirme](../../../wcf/feature-details/securing-peer-channel-applications.md)
- [Hizmet ve İstemcileri Güvenli Hale Getirme](../../../wcf/feature-details/securing-services-and-clients.md)
