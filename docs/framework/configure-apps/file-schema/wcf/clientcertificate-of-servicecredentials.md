---
title: <clientCertificate> / <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 90ad03aa-2317-43dd-8a72-6d24cdcad15c
ms.openlocfilehash: 26ebac6439a90959e3a926e6a36c9044251a4aae
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59107997"
---
# <a name="clientcertificate-of-servicecredentials"></a>\<clientCertificate >, \<issuedTokenAuthentication >
Bir istemci forma bir çift yönlü iletişim deseni hizmetinde, iletileri imzalamak ve şifrelemek için kullanılan bir X.509 sertifikası tanımlar.  
  
 \<system.ServiceModel>  
\<davranışlar >  
\<serviceBehaviors>  
\<serviceBehaviors>  
\<davranışı >  
\<serviceCredentials>  
\<clientCertificate >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<clientCertificate>
  <certificate />
  <authentication />
</clientCertificate>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
 Yok.  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<kimlik doğrulama >](../../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md)|İstemci sertifikası kimlik doğrulaması seçeneklerini belirtir.|  
|[\<Sertifika >](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-of-clientcertificate-element.md)|Kullanılacak sertifikayı belirtir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<serviceCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|Hizmet kimlik doğrulaması olarak kullanılacak kimlik bilgilerini belirtir ve istemci kimlik bilgileri doğrulaması ilgili ayarları.|  
  
## <a name="remarks"></a>Açıklamalar  
 Hizmet istemcisi ile önceden güvenli şekilde iletişim kurması için istemci sertifikasını olmalıdır, bu öğe kullanılır. Bu, çift yönlü iletişim deseni kullanırken gerçekleşir. Daha genel istek/yanıt modelinde istemci sertifikasını hizmetin istemciye yanıtına imzalamak ve şifrelemek için kullandığı isteğinde içerir. Çift yönlü iletişim deseni, ancak hizmetin istemciden gelen istekte yok ve bu nedenle önceden istemciye ileti güvenliğini sağlamak için istemci sertifikasını gerekir. Bu nedenle istemci sertifikasının, bir bant dışı anlaşma edinmek ve bu öğenin kullanarak sertifikayı belirtmeniz gerekir. Çift yönlü hizmetler hakkında daha fazla bilgi için bkz: [nasıl yapılır: Çift yönlü sözleşme oluşturma](../../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).  
  
 Bu öğe kümesindeki sertifika ile yapılandırılmış bağlamalar istemciye iletileri şifrelemek için kullanılan `MutualCertificateDuplex` ileti güvenlik kimlik doğrulama modu.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.ClientCertificate%2A>
- <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>
- <xref:System.ServiceModel.Description.ServiceCredentials.ClientCertificate%2A>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential>
- [Nasıl yapılır: Çift yönlü sözleşme oluşturma](../../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)
- [Güvenlik Davranışları](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [Sertifikalarla Çalışma](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
