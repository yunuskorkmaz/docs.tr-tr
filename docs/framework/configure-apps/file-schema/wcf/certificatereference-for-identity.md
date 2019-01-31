---
title: <certificateReference> için <identity>
ms.date: 03/30/2017
ms.assetid: ac359c65-c22d-42d2-97de-db53b77cebdb
ms.openlocfilehash: 44bfb2fd77c4f4db6f7fede296b1cdb74e8d5e7c
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55254840"
---
# <a name="certificatereference-for-identity"></a>\<certificateReference > için \<kimliği >
X.509 Sertifika doğrulama ayarlarını belirtir. Bu kimlik ile bir uç noktayı bağlayan güvenli bir Windows Communication Foundation (WCF) istemci, sunucu tarafından sunulan istemlerin, bu kimliği oluşturmak için kullanılan kimlik talebi içerdiğini doğrular.  
  
 \<Kimliği >  
\<certificateReference >  
  
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
|findValue|X.509 sertifika deposunda aranacak değerini belirtir. Bu öznitelikte yer alan türü belirtilen gereksinimleri karşılaması gerekir `X509FindType` değeri. Varsayılan değer boş bir dizedir.|  
|isChainIncluded|Doğrulama yapıldığını belirten bir Boole değeri bir sertifika zinciri.|  
|storeLocation|İstemcinin sunucu sertifikasını doğrulamak için kullanabileceği sertifika deposunun konumunu belirtir.<br /><br /> Geçerli değerler şunlardır:<br /><br /> -LocalMachine: Yerel makineye atanmış sertifika deposu.<br />-   CurrentUser: Geçerli kullanıcıya atanmış sertifika deposu.<br /><br /> LocalMachine varsayılan değerdir.<br /><br /> Bu öznitelik türünde <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.|  
|storeName|Açılacak X.509 Sertifika deposunun adını belirtir.<br /><br /> Geçerli değerler şunlardır:<br /><br /> -Adres Defteri: Diğer kullanıcılar için sertifika deposu.<br />-AuthRoot: Üçüncü taraf sertifika yetkilileri (CA'lar) için sertifika deposu.<br />-CertificateAuthority: Ara CA'lar için sertifika deposu.<br />-İzin verilmedi: İptal edilen sertifikalar için sertifika deposu.<br />-My: Kişisel Sertifikalar için sertifika deposu.<br />-Kök: Güvenilen kök CA'lar için sertifika deposu.<br />-TrustedPeople: Doğrudan güvenilen kişiler ve kaynaklar için sertifika deposu.<br />-TrustedPublisher: Doğrudan Güvenilen Yayımcılar sertifika deposu.<br /><br /> Varsayılan değer benim.<br /><br /> Bu öznitelik türünde <xref:System.Security.Cryptography.X509Certificates.StoreName>.|  
|X509FindType|Yürütülecek X.509 arama türünü belirtir. Bulunan tür `findValue` öznitelik belirtilen X509FindType gereksinimlerini karşılaması gerekir.<br /><br /> Geçerli değerler şunlardır:<br /><br /> -FindByThumbPrint<br />-FindBySubjectName<br />-FindBySubjectDistinguishedName<br />-FindByIssuerName<br />-FindByIssuerDistinguishedName<br />-FindBySerialNumber<br />-FindByTimeValid<br />-FindByTimeNotYetValid<br />-   FindByTemplateName<br />-FindByApplicationPolicy<br />-FindByCertificatePolicy<br />-FindByExtension<br />-   FindByKeyUsage<br />-FindBySubjectKeyIdentifier<br /><br /> FindBySubjectDistinguishedName varsayılan değerdir.<br /><br /> Bu öznitelik türünde <xref:System.Security.Cryptography.X509Certificates.X509FindType>.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Kimliği >](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|Onunla mesaj alışverişleri diğer uç noktalar tarafından bir uç nokta kimlik doğrulaması etkinleştiren ayarları belirtir.|  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.ServiceModel.Configuration.CertificateReferenceElement>
- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
