---
title: <certificate> Öğesi
ms.date: 03/30/2017
ms.assetid: 9b3d9233-ef35-477a-bf5d-efd1e80a52f4
ms.openlocfilehash: eea8130911ca3780a6e4e753c17877e58c50b139
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59164274"
---
# <a name="certificate-element"></a>\<Sertifika > öğesi
İmzalama ve eşler arası istemcileri için iletileri şifrelemek için bir X.509 sertifikasını belirtir.  
  
 \<system.ServiceModel>  
\<davranışlar >  
\<endpointBehaviors>  
\<davranışı >  
\<clientCredentials >  
\<Eş >  
\<Sertifika >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<certificate findValue="String"
             storeLocation="LocalMachine/CurrentUser"
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
|[\<Eş >](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-clientcredentials-element.md)|Eşler arası istemcilerin kimlik doğrulaması için kullanılan kimlik bilgilerini belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yapılandırma öğesi içinde Eş Ağ Komşuları kimlik doğrulaması için kullanılan bir X509Certificate2 örneği içerir.  
  
 Eşler arası programlama hakkında daha fazla bilgi için bkz. [eşler arası ağ](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, bir eşler arası senaryosunda kullanılan sertifikanın nasıl belirtir.  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="MyEndpointBehavior">
      <clientCredentials>
        <peer>
          <certificate findValue="www.contoso.com"
                       storeLocation="LocalMachine"
                       x509FindType="FindByIssuerName" />
        </peer>
      </clientCredentials>
    </behavior>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.Certificate%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateElement>
- <xref:System.ServiceModel.Security.PeerCredential.Certificate%2A>
- [Sertifikalarla Çalışma](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [Eşler Arası Ağ](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)
- [Eş kanal ileti kimlik doğrulaması](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))
- [Eş kanal özel kimlik doğrulama](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))
- [Eş Kanalı Uygulamalarını Güvenli Hale Getirme](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
