---
title: <certificate> ' ın <clientCertificate> öğesi
ms.date: 03/30/2017
ms.assetid: 00297efb-a7f2-4e03-bc2b-943d545610fc
ms.openlocfilehash: 94241d022e8a97253100a67e2a779593861c093c
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57366523"
---
# <a name="certificate-of-clientcertificate-element"></a>\<Sertifika >, \<clientCertificate > öğesi
Bir X.509 belirtir iletileri imzalamak ve şifrelemek için kullanılan sertifika.  
  
 \<system.ServiceModel>  
\<davranışlar >  
\<serviceBehaviors>  
\<davranışı >  
\<serviceCredentials>  
\<clientCertificate >  
\<Sertifika >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<certificate findValue="String"
             storeLocation = "CurrentUser/LocalMachine"
             storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
             X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`findValue`|X.509 sertifika deposunda aranacak değeri içeren bir dize. Özniteliğinde bulunan türü belirtilen X509FindType gereksinimlerini karşılaması gerekir. Varsayılan değer boş bir dizedir.|  
|`storeLocation`|İstemcinin sunucu sertifikasını doğrulamak için kullandığı X.509 Sertifika deposunun konumunu belirtir. Geçerli değerler şunlardır:<br /><br /> -LocalMachine: yerel makineye atanmış sertifika deposu.<br />-CurrentUser: geçerli kullanıcıya atanmış sertifika deposu.<br /><br /> LocalMachine varsayılandır.|  
|`storeName`|Açılacak X.509 Sertifika deposunun adını belirtir. Geçerli değerler şunlardır:<br /><br /> -Adres Defteri: Diğer kullanıcılar için sertifika deposu.<br />-AuthRoot: Üçüncü taraf sertifika yetkilileri (CA'lar) için sertifika deposu.<br />-CertificationAuthority: Ara Sertifika yetkilileri (CA'lar) için sertifika deposu.<br />-İzin verilmedi: İptal edilen sertifikalar için sertifika deposu.<br />-My: Kişisel Sertifikalar için sertifika deposu.<br />-Kök: Güvenilen kök sertifika yetkilileri (CA'lar) için sertifika deposu.<br />-TrustedPeople: Doğrudan güvenilen kişiler ve kaynaklar için sertifika deposu.<br />-TrustedPublisher: Doğrudan Güvenilen Yayımcılar sertifika deposu.<br /><br /> Varsayılan değer benim.|  
|`X509FindType`|Yürütülecek X.509 arama türünü tanımlar. Geçerli değerler şunlardır:<br /><br /> -FindByThumbPrint<br />-FindBySubjectName<br />-FindBySubjectDistinguishedName<br />-FindByIssuerName<br />-FindByIssuerDistinguishedName<br />-FindBySerialNumber<br />-FindByTimeValid<br />-FindByTimeNotYetValid<br />-   FindByTemplateName<br />-FindByApplicationPolicy<br />-FindByCertificatePolicy<br />-FindByExtension<br />-   FindByKeyUsage<br />-FindBySubjectKeyIdentifier<br /><br /> Bulunan tür `findValue` öznitelik belirtilen X509FindType gereksinimlerini karşılaması gerekir.<br /><br /> FindBySubjectDistinguishedName varsayılan değerdir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<clientCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)||  
  
## <a name="remarks"></a>Açıklamalar  
 `<certificate>` Hizmet istemcisi ile önceden güvenli şekilde iletişim kurması için istemci sertifikasını olmalıdır, öğe kullanılır. Bu, çift yönlü iletişim deseni kullanırken gerçekleşir. Daha genel istek/yanıt modelinde istemci sertifikasını hizmetin istemciye yanıtına imzalamak ve şifrelemek için kullandığı isteğinde içerir. Çift yönlü iletişim deseni, ancak hizmetin istemciden gelen istekte yok ve bu nedenle önceden istemciye ileti güvenliğini sağlamak için istemci sertifikasını gerekir. Bu nedenle istemci sertifikasının, bir bant dışı anlaşma edinmek ve bu öğenin kullanarak sertifikayı belirtmeniz gerekir. Çift yönlü hizmetler hakkında daha fazla bilgi için bkz: [nasıl yapılır: Çift yönlü sözleşme oluşturma](../../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod uygun bir bulmak nasıl belirtir X.509 sertifikası ve özel doğrulama yazın `<authentication>` öğesi.  
  
```xml  
<serviceBehaviors>
  <behavior name="myServiceBehavior">
    <clientCertificate>
      <certificate findValue="www.cohowinery.com"
                   storeLocation="CurrentUser"
                   storeName="TrustedPeople"
                   x509FindType="FindByIssuerName" />
      <authentication customCertificateValidatorType="MyTypes.Coho"
                      certificateValidationMode="Custom"
                      revocationMode="Offline"
                      includeWindowsGroups="false"
                      mapClientCertificateToWindowsAccount="true" />
    </clientCertificate>
  </behavior>
</serviceBehaviors>
```  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential.Certificate%2A>
- <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement.Certificate%2A>
- <xref:System.ServiceModel.Configuration.X509ClientCertificateCredentialsElement>
- [Güvenlik Davranışları](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [Nasıl yapılır: Özel bir sertifika Doğrulayıcı kullanan bir hizmet oluşturma](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)
- [Sertifikalarla Çalışma](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
