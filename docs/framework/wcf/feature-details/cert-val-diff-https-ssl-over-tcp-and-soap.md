---
title: "HTTPS, TCP üzerinden SSL ve SOAP Güvenliği Arasındaki Sertifika Doğrulama Farkları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: certificates [WCF], validation differences
ms.assetid: 953a219f-4745-4019-9894-c70704f352e6
caps.latest.revision: "14"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 34be2fbc5b8148d7bfdeb5e5d07e5b73ac89a97e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="certificate-validation-differences-between-https-ssl-over-tcp-and-soap-security"></a>HTTPS, TCP üzerinden SSL ve SOAP Güvenliği Arasındaki Sertifika Doğrulama Farkları
Sertifikaları kullanabilirsiniz [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] HTTP (HTTPS) veya TCP üzerinden Aktarım Katmanı Güvenliği (TLS) yanı sıra ileti katmanlı (SOAP) güvenlik ile. Bu konuda bu tür sertifikalar doğrulanır farklılıklar açıklanmaktadır.  
  
## <a name="validation-of-https-client-certificates"></a>HTTPS istemci sertifikalarının doğrulama  
 Bir istemci ve hizmet arasında iletişim kurmak için HTTPS kullanırken, bir hizmetin kimliğini istemcinin kullandığı sertifika zinciri güven desteklemesi gerekir. Diğer bir deyişle, güvenilen kök sertifika yetkilisine zincirleme gerekir. Değilse, HTTP katman geçirirse bir <xref:System.Net.WebException> iletiyle "uzak sunucusu bir hata döndürdü: (403) Yasak." [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Bu özel durum olarak ortaya çıkarır bir <xref:System.ServiceModel.Security.MessageSecurityException>.  
  
## <a name="validation-of-https-service-certificates"></a>HTTPS hizmet sertifika doğrulama  
 Bir istemci ve hizmet arasında iletişim kurmak için HTTPS kullanırken, sunucu kimlik doğrulamasını sertifika zinciri güven varsayılan olarak desteklemesi gerekir. Diğer bir deyişle, güvenilen kök sertifika yetkilisine zincirleme gerekir. Çevrimiçi Denetimsiz sertifikanın iptal edilmediğini görmek için gerçekleştirilir. Kaydederek bu davranışı geçersiz kılabilirsiniz bir <xref:System.Net.Security.RemoteCertificateValidationCallback> aşağıdaki kodda gösterildiği gibi geri çağırma.  
  
 [!code-csharp[c_CertificateValidationDifferences#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#1)] 
 [!code-vb[c_CertificateValidationDifferences#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#1)]  
  
 Burada imza için `ValidateServerCertificate` aşağıdaki gibidir:  
  
 [!code-csharp[c_CertificateValidationDifferences#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#2)]
 [!code-vb[c_CertificateValidationDifferences#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#2)]  
  
 Uygulama `ValidateServerCertificate` istemci uygulama geliştiricisi hizmet sertifikasını doğrulamak üzere gerekli uymak açısından gerekli olduğunu, denetimleri gerçekleştirebilirsiniz.  
  
## <a name="validation-of-client-certificates-in-ssl-over-tcp-or-soap-security"></a>TCP veya SOAP güvenliği üzerinden SSL istemci sertifikalarının doğrulama  
 Ne zaman Güvenli Yuva Katmanı (SSL) kullanarak TCP veya (SOAP) ileti güvenliği, istemci sertifikalarını doğrulanma göre <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A> özellik değerinin <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> sınıfı. Özellik biri olarak ayarlanmışsa <xref:System.ServiceModel.Security.X509CertificateValidationMode> değerleri. İptal denetimi değerlerini göre gerçekleştirilir <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.RevocationMode%2A> özellik değerinin <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> sınıfı. Özellik biri olarak ayarlanmışsa <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> değerleri.  
  
 [!code-csharp[c_CertificateValidationDifferences#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#3)]
 [!code-vb[c_CertificateValidationDifferences#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#3)]  
  
## <a name="validation-of-service-certificate-in-ssl-over-tcp-and-soap-security"></a>SSL TCP ve SOAP güvenliği üzerinden hizmet sertifikasında doğrulanması  
 SSL TCP veya (SOAP) ileti güvenliği kullanırken, hizmet sertifikaları göre doğrulanır <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> özellik değerinin <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication> sınıfı. Özellik biri olarak ayarlanmışsa <xref:System.ServiceModel.Security.X509CertificateValidationMode> değerleri.  
  
 İptal denetimi değerlerini göre gerçekleştirilir <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.RevocationMode%2A> özellik değerinin <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication> sınıfı. Özellik biri olarak ayarlanmışsa <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> değerleri.  
  
 [!code-csharp[c_CertificateValidationDifferences#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#4)]
 [!code-vb[c_CertificateValidationDifferences#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#4)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Net.Security.RemoteCertificateValidationCallback>  
 [Sertifikalarla Çalışma](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
