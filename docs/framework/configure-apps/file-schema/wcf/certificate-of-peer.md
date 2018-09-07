---
title: '&lt;eş&gt; &lt;sertifikası&gt;'
ms.date: 03/30/2017
ms.assetid: 48b69142-c957-4305-a042-c9d0c9a55c0e
ms.openlocfilehash: 59aaee5549aae5df173174651ee3a520a0ac10fb
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44084020"
---
# <a name="ltcertificategt-of-ltpeergt"></a>&lt;eş&gt; &lt;sertifikası&gt;
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
X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`findValue`|X.509 sertifika deposunda aranacak değeri içeren bir dize. Özniteliğinde bulunan türü belirtilen gereksinimleri karşılaması gerekir `x509FindType`. Varsayılan değer boş bir dizedir.|  
|`storeLocation`|Eşin sertifikasını doğrulamak için istemcinin kullandığı X.509 Sertifika deposunun konumunu belirtir. Geçerli değerler şunlardır:<br /><br /> -LocalMachine: yerel makineye atanmış sertifika deposu.<br />-CurrentUser: geçerli kullanıcıya atanmış sertifika deposu.<br /><br /> LocalMachine varsayılandır.|  
|`storeName`|Açılacak X.509 Sertifika deposunun adını belirtir. Geçerli değerler şunlardır:<br /><br /> -Adres Defteri: Diğer kullanıcılar için sertifika deposuna.<br />-AuthRoot: sertifika deposunu için üçüncü taraf sertifika yetkilileri (CA).<br />-CertificateAuthority: Ara sertifika yetkilileri (CA'lar) sertifika deposu.<br />-İzin verilmedi: iptal edilen sertifikalar deposuna sertifika.<br />-My: Kişisel Sertifikalar için sertifika deposu.<br />-Kök: Güvenilen kök sertifika yetkilileri (CA'lar) için sertifika deposu.<br />-TrustedPeople: Sertifika deposu-doğrudan güvenilen kişiler ve kaynaklar.<br />-TrustedPublisher: Doğrudan Güvenilen Yayımcılar sertifika deposuna.<br /><br /> Varsayılan değer benim.|  
|`X509FindType`|Yürütülecek X.509 arama türünü tanımlar. Geçerli değerler şunlardır:<br /><br /> -FindByThumbPrint<br />-FindBySubjectName<br />-FindBySubjectDistinguishedName<br />-FindByIssuerName<br />-FindByIssuerDistinguishedName<br />-FindBySerialNumber<br />-FindByTimeValid<br />-FindByTimeNotYetValid<br />-FindByTemplateName<br />-FindByApplicationPolicy<br />-FindByCertificatePolicy<br />-FindByExtension<br />-FindByKeyUsage<br />-FindBySubjectKeyIdentifier<br /><br /> Bulunan tür `findValue` öznitelik belirtilen gereksinimleri karşılaması gerekir `X509FindType`.<br /><br /> FindBySubjectDistinguishedName varsayılan değerdir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Eş >](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-servicecredentials.md)|Bir eşdüzey düğüm için geçerli kimlik bilgilerini belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yapılandırma öğesi içeren bir `X509Certificate2` Komşuları eş ağ içinde kimlik doğrulaması için kullanılan bir örnek.  
  
 Eşler arası programlama hakkında daha fazla bilgi için bkz. [eşler arası ağ](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement.Certificate%2A>  
 <xref:System.ServiceModel.Configuration.X509PeerCertificateElement>  
 <xref:System.ServiceModel.Security.PeerCredential.Certificate%2A>  
 <xref:System.ServiceModel.Security.PeerCredential>  
 [Sertifikalarla Çalışma](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [Eşler Arası Ağ](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [Eş kanal ileti kimlik doğrulaması](https://msdn.microsoft.com/library/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [Eş kanal özel kimlik doğrulama](https://msdn.microsoft.com/library/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [Eş Kanalı Uygulamalarını Güvenli Hale Getirme](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)  
 [Hizmet ve İstemcileri Güvenli Hale Getirme](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
