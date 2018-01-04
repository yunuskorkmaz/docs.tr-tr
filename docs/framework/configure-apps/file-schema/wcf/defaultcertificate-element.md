---
title: "&lt;defaultCertificate&gt; Öğesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f1ddf364-9a00-45d3-b989-ff381c154ce6
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: eeb4c1b010e2d446303e780966668fc8a6f5ddb7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltdefaultcertificategt-element"></a>&lt;defaultCertificate&gt; Öğesi
Kullanılacak bir X.509 sertifikası belirtir ne zaman bir hizmeti veya STS sağlamaz anlaşması protokolü aracılığıyla bir.  
  
 \<Sistem. ServiceModel >  
\<davranışları >  
endpointBehaviors bölümü  
\<davranışı >  
\<clientCredentials >  
\<serviceCertificate >  
\<defaultCertificate >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<defaultCertificate findValue="String"   
storeLocation=" CurrentUser/LocalMachine"  
storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"   
x509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialiNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt öğelerini ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|findValue|Dize. Aranacak değer.|  
|X509FindType|Sabit listesi. Aranacak sertifika alanlardan biri.|  
|storeLocation|Sabit listesi. İki sistem birini aramak için konuma depolayın.|  
|storeName|Sabit listesi. Sistem aramak için depolar.|  
  
## <a name="findvalue-attribute"></a>findValue özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|Dize|Değer (X509FindType özniteliği tarafından belirtilen) alan bağlıdır Aranmakta. Örneğin, bir parmak izi için arama değeri bir onaltılık sayı dizesi olması gerekir.|  
  
## <a name="x509findtype-attribute"></a>x509FindType özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|Sabit Listesi|Değerler şunlardır: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.|  
  
## <a name="storelocation-attribute"></a>storeLocation özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|Sabit Listesi|Currentuser'a veya LocalMachine.|  
  
## <a name="storename-attribute"></a>storeName özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|Sabit Listesi|Değerler: adres defteri, AuthRoot, sertifika yetkilisi, izin verilmeyen, My, kök, TrustedPeople ve TrustedPublisher.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<serviceCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md)|İstemci bir hizmete kimlik doğrulanırken kullanılacak bir sertifika belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Sertifika tabanlı ileti güvenliği kullanan bağlamaları için bu yapılandırma öğesi tarafından belirtilen sertifika hizmet iletileri şifrelemek için kullanılır ve istemciye yanıt imzalama hizmeti tarafından kullanılacak beklenmektedir. Sertifika bir hizmet tarafından belirtildiğinde kullanılacak tek bir sertifika depolar.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, URI http://www.contoso.com ile başlayan uç noktalar için kullanılacak bir sertifika ve sertifika anlaşmasını gerçekleştiren değil tüm diğer uç noktalar için kullanılacak bir sertifika belirtir.  
  
```xml  
<serviceCertificate>  
  <defaultCertificate findValue="www.contoso.com"   
                      storeLocation="LocalMachine"  
                      storeName="TrustedPeople"   
                      x509FindType="FindByIssuerDistinguishedName" />  
  <scopedCertificates>  
     <add targetUri="http://www.contoso.com"   
          findValue="www.contoso.com" storeLocation="LocalMachine"  
                  storeName="Root" x509FindType="FindByIssuerName" />  
  </scopedCertificates>  
  <authentication revocationMode="Online"   
   trustedStoreLocation="LocalMachine" />  
</serviceCertificate>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Configuration.X509DefaultServiceCertificateElement>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.DefaultCertificate%2A>  
 [Sertifikalarla Çalışma](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [\<kimlik doğrulama >](../../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md)  
 [İstemcileri Güvenli Hale Getirme](../../../../../docs/framework/wcf/securing-clients.md)  
 [Hizmet ve İstemcileri Güvenli Hale Getirme](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
