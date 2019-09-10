---
title: <certificateReference> için <identity>
ms.date: 03/30/2017
ms.assetid: ac359c65-c22d-42d2-97de-db53b77cebdb
ms.openlocfilehash: 93a6290d780ff61756f7315cd0c32f0e199ca00f
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70849991"
---
# <a name="certificatereference-for-identity"></a>\<kimlik > için \<CertificateReference >
X. 509.440 sertifika doğrulamasının ayarlarını belirtir. Bu kimlikle bir uç noktaya bağlanan bir güvenli Windows Communication Foundation (WCF) istemcisi, sunucu tarafından sunulan taleplerin bu kimliği oluşturmak için kullanılan kimlik talebini içerdiğini doğrular.  
  
[ **\<Yapılandırma >** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<İstemci >** ](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<uç nokta >** ](endpoint-of-client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<kimlik >** ](identity.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<certificateReference >**  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<certificateReference findValue="String"
                      isChainIncluded="Boolean"
                      storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                      storeLocation="LocalMachine/CurrentUser"
                      X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier">
</certificateReference>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|findValue|X. 509.440 sertifika deposunda aranacak değeri belirtir. Bu öznitelikte yer alan türün, belirtilen `X509FindType` değerin gereksinimlerini karşılaması gerekir. Varsayılan değer boş bir dizedir.|  
|Ischaindahil|Doğrulamanın bir sertifika zinciri kullanılarak gerçekleştirilip yapılmadığını belirten bir Boole değeri.|  
|storeLocation|İstemcinin, sunucunun sertifikasını doğrulamak için kullanabileceği sertifika deposunun konumunu belirtir.<br /><br /> Geçerli değerler şunlardır:<br /><br /> LocalMachine Yerel makineye atanmış sertifika deposu.<br />CurrentUser Geçerli kullanıcıya atanmış sertifika deposu.<br /><br /> Varsayılan değer LocalMachine 'dir.<br /><br /> Bu öznitelik türü <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.|  
|storeName|Açılacak X. 509.440 sertifika deposunun adını belirtir.<br /><br /> Geçerli değerler şunlardır:<br /><br /> -AddressBook: Diğer kullanıcılar için sertifika deposu.<br />-AuthRoot: Üçüncü taraf sertifika yetkilileri (CA 'Lar) için sertifika deposu.<br />CertificateAuthority Ara CA 'Lar için sertifika deposu.<br />Veril İptal edilen sertifikalar için sertifika deposu.<br />My Kişisel Sertifikalar için sertifika deposu.<br />Asıl Güvenilen kök CA 'Lar için sertifika deposu.<br />TrustedPeople Doğrudan güvenilen kişiler ve kaynaklar için sertifika deposu.<br />-TrustedPublisher: Doğrudan güvenilen yayımcılar için sertifika deposu.<br /><br /> Varsayılan değer My.<br /><br /> Bu öznitelik türü <xref:System.Security.Cryptography.X509Certificates.StoreName>.|  
|X509FindType|Yürütülecek X. 509.952 aramasının türünü belirtir. `findValue` Özniteliğinde yer alan türün belirtilen X509FindType gereksinimlerini karşılaması gerekir.<br /><br /> Geçerli değerler şunlardır:<br /><br /> -Findbyparmak Izi<br />-FindBySubjectName<br />- FindBySubjectDistinguishedName<br />-FindByIssuerName<br />- FindByIssuerDistinguishedName<br />-FindBySerialNumber<br />-FindByTimeValid<br />-FindByTimeNotYetValid<br />-FindByTemplateName<br />- FindByApplicationPolicy<br />-FindByCertificatePolicy<br />-FindByExtension<br />-FindByKeyUsage<br />-FindBySubjectKeyIdentifier<br /><br /> Varsayılan değer FindBySubjectDistinguishedName ' dir.<br /><br /> Bu öznitelik türü <xref:System.Security.Cryptography.X509Certificates.X509FindType>.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<kimlik >](identity.md)|Bir uç noktanın kimlik doğrulamasını diğer uç noktalara sahip iletileri değiş tokuş eden ayarları belirtir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.CertificateReferenceElement>
- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
