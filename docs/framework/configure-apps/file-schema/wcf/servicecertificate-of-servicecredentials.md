---
title: "&lt;serviceCredentials&gt; için &lt;serviceCertificate&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 597ae6d5-4938-4950-9f5e-b2280e816182
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e5b6baca250e4fadc2a66bb0fe83b076522f82ee
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltservicecertificategt-of-ltservicecredentialsgt"></a>&lt;serviceCredentials&gt; için &lt;serviceCertificate&gt;
İleti güvenlik modunu kullanarak istemcilere hizmet kimliğini doğrulamak için kullanılan bir X.509 sertifikası belirtin.  
  
 \<Sistem. ServiceModel >  
\<davranışları >  
\<serviceBehaviors >  
\<davranışı >  
\<serviceCredentials >  
\<serviceCertificate >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<serviceCertificate findValue="String"   
    storeLocation="LocalMachine/CurrentUser"  
    storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"  
x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`findValue`|X.509 sertifika deposunda arama için değer içeren bir dize. Özniteliğinde bulunan türü belirtilen X509FindType gereksinimlerini karşılaması gerekir. Varsayılan boş bir dizedir.|  
|`storeLocation`|Sunucu sertifikasının karşı doğrulamak için istemcinin kullandığı X.509 sertifika depolama konumunu belirtir. Geçerli değerler şunlardır:<br /><br /> -LocalMachine: Yerel Makine sertifika deposuna.<br />-Currentuser'a: sertifika deposuna geçerli kullanıcıya atanmış.<br /><br /> LocalMachine varsayılandır.|  
|`storeName`|Açmak için X.509 Sertifika deposu adını belirtir. Geçerli değerler şunlardır:<br /><br /> -Adres Defteri: Diğer kullanıcılar sertifika deposu.<br />-AuthRoot: sertifika deposunu üçüncü taraf sertifika yetkilileri (CA'lar) için.<br />-CertificatAuthority: Ara sertifika yetkilileri (CA'lar) sertifika deposu.<br />-İzin verilmeyen: mağaza iptal edilen sertifikaları için sertifika.<br />-My: Sertifika deposunda kişisel sertifikalar için.<br />-Kök: Güvenilen kök sertifika yetkilileri (CA'lar) sertifika deposu.<br />-TrustedPeople: Doğrudan güvenilir kişiler ve kaynaklar sertifika deposu.<br />-TrustedPublisher: Doğrudan Güvenilen Yayımcılar sertifika deposu.<br /><br /> Varsayılan değer My.|  
|`x509FindType`|Yürütülecek X.509 arama türünü tanımlar. Geçerli değerler şunlardır:<br /><br /> -FindByThumbprint<br />-FindBySubjectName<br />-FindBySubjectDistinguishedName<br />-FindByIssuerName<br />-FindByIssuerDistinguishedName<br />-FindBySerialNumber<br />-FindByTimeValid<br />-FindByTimeNotYetValid<br />-FindByTemplateName<br />-FindByApplicationPolicy<br />-FindByCertificatePolicy<br />-FindByExtension<br />-FindByKeyUsage<br />-FindBySubjectKeyIdentifier<br /><br /> İçinde yer alan türü `findValue` özniteliği belirtilen X509FindType gereksinimlerini karşılaması gerekir.<br /><br /> FindBySubjectDistinguishedName varsayılan değerdir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<serviceCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|Hizmet kimlik doğrulaması kullanmak için kimlik bilgilerini belirtir ve istemci kimlik doğrulaması ilgili ayarları.|  
  
## <a name="remarks"></a>Açıklamalar  
 İleti güvenlik modunu kullanarak istemcilere hizmet kimliğini doğrulamak için kullanılan bir X.509 sertifikasını belirtmek için bu öğeyi kullanın. Düzenli aralıklarla yenilenmesi bir sertifika kullanıyorsanız, parmak izi değiştirir. Bu durumda konu adı olarak kullanın `x509FindType` sertifika ile aynı konu adı verilmesi için.  
  
 [!INCLUDE[crabout](../../../../../includes/crabout-md.md)]öğesini kullanarak bkz [nasıl yapılır: istemci kimlik bilgileri değerlerini belirtme](../../../../../docs/framework/wcf/how-to-specify-client-credential-values.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.ServiceCertificate%2A>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential>  
 <xref:System.ServiceModel.Description.ServiceCredentials.ServiceCertificate%2A>  
 [Nasıl yapılır: İstemci Kimlik Bilgileri Değerlerini Belirtme](../../../../../docs/framework/wcf/how-to-specify-client-credential-values.md)  
 [Güvenlik Davranışları](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
