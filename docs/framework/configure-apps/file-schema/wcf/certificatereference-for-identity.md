---
title: "&lt;kimlik&gt; için &lt;certificateReference&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ac359c65-c22d-42d2-97de-db53b77cebdb
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e7728f2ffc74462e43de32b07b819cc2371c9bc0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltcertificatereferencegt-for-ltidentitygt"></a>&lt;kimlik&gt; için &lt;certificateReference&gt;
X.509 Sertifika doğrulama ayarlarını belirtir. Güvenli [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] Bu kimliğe sahip bir uç nokta bağlanan istemci doğrular sunucu tarafından sunulan talepler bu kimliği oluşturmak için kullanılan kimlik talebi içerir.  
  
 \<Kimliği >  
\<certificateReference >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<certificateReference   
        findValue="String"   
    isChainIncluded="Boolean"  
    storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"storeName="  
  
    storeLocation="LocalMachine/CurrentUser"  
  
X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"  
</certificateReference>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|findValue|X.509 sertifika deposunda aramak için kullanılacak değeri belirtir. Bu öznitelikte bulunan türü belirtilen gereksinimleri karşılaması gerekir `X509FindType` değeri. Varsayılan boş bir dizedir.|  
|isChainIncluded|Doğrulama atanarak belirten bir Boole değeri kullanarak bir sertifika zinciri.|  
|storeLocation|İstemci, sunucu sertifikasını doğrulamak üzere kullanabilir sertifika depolama konumunu belirtir.<br /><br /> Geçerli değerler şunlardır:<br /><br /> -LocalMachine: sertifika deposu yerel makineye atanmış.<br />-Currentuser'a: sertifika deposu geçerli kullanıcıya atanmış.<br /><br /> Varsayılan, LocalMachine değerdir.<br /><br /> Bu öznitelik türünde <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.|  
|storeName|Açmak için X.509 Sertifika deposu adını belirtir.<br /><br /> Geçerli değerler şunlardır:<br /><br /> -Adres Defteri: Diğer kullanıcılar sertifika deposu.<br />-AuthRoot: sertifika deposunu üçüncü taraf sertifika yetkilileri (CA'lar) için.<br />-CertificateAuthority: Ara CA'lar sertifika deposu.<br />-İzin verilmeyen: mağaza iptal edilen sertifikaları için sertifika.<br />-My: Sertifika deposunda kişisel sertifikalar için.<br />-Kök: Güvenilen kök CA sertifika deposu.<br />-TrustedPeople: Doğrudan güvenilir kişiler ve kaynaklar sertifika deposu.<br />-TrustedPublisher: Doğrudan Güvenilen Yayımcılar sertifika deposu.<br /><br /> Varsayılan değer My.<br /><br /> Bu öznitelik türünde <xref:System.Security.Cryptography.X509Certificates.StoreName>.|  
|X509FindType|Yürütülecek X.509 arama türünü belirtir. İçinde yer alan türü `findValue` özniteliği belirtilen X509FindType gereksinimlerini karşılaması gerekir.<br /><br /> Geçerli değerler şunlardır:<br /><br /> -FindByThumbPrint<br />-FindBySubjectName<br />-FindBySubjectDistinguishedName<br />-FindByIssuerName<br />-FindByIssuerDistinguishedName<br />-FindBySerialNumber<br />-FindByTimeValid<br />-FindByTimeNotYetValid<br />-FindByTemplateName<br />-FindByApplicationPolicy<br />-FindByCertificatePolicy<br />-FindByExtension<br />-FindByKeyUsage<br />-FindBySubjectKeyIdentifier<br /><br /> FindBySubjectDistinguishedName varsayılan değerdir.<br /><br /> Bu öznitelik türünde <xref:System.Security.Cryptography.X509Certificates.X509FindType>.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Kimliği >](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|Bir uç nokta onunla ileti değiş tokuşu diğer uç noktaları tarafından kimlik doğrulaması sağlayan ayarları belirtir.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Configuration.CertificateReferenceElement>  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>
