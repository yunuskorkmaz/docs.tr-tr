---
title: HTTPS, TCP üzerinden SSL ve SOAP Güvenliği Arasındaki Sertifika Doğrulama Farkları
description: WCF 'nin HTTPS veya TCP 'ye ek olarak sunduğu ileti katmanı (SOAP) güvenliğine sahip sertifikalar hakkında bilgi edinin ve WCF 'nin bu sertifikaları nasıl doğrulayacağını öğrenin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- certificates [WCF], validation differences
ms.assetid: 953a219f-4745-4019-9894-c70704f352e6
ms.openlocfilehash: 97d51e5b65ebf20e80a69512370b68a51eeb28a7
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245277"
---
# <a name="certificate-validation-differences-between-https-ssl-over-tcp-and-soap-security"></a>HTTPS, TCP üzerinden SSL ve SOAP Güvenliği Arasındaki Sertifika Doğrulama Farkları
HTTP (HTTPS) veya TCP üzerinden Aktarım Katmanı Güvenliği (TLS) ek olarak, ileti katmanı (SOAP) güvenliği ile Windows Communication Foundation (WCF) içindeki sertifikaları kullanabilirsiniz. Bu konu, bu tür sertifikaların doğrulanması için farkları açıklar.  
  
## <a name="validation-of-https-client-certificates"></a>HTTPS Istemci sertifikalarının doğrulanması  
 İstemci ile bir hizmet arasında iletişim kurmak için HTTPS kullanılırken, istemcinin hizmette kimlik doğrulamak için kullandığı sertifikanın zincir güvenini desteklemesi gerekir. Diğer bir deyişle, güvenilen bir kök sertifika yetkilisine zincirlenmelidir. Aksi takdirde, HTTP katmanı bir <xref:System.Net.WebException> "uzak sunucu bir hata döndürdü: (403) yasak iletisi ile bir oluşturur. WCF bu özel durumu bir olarak gösterir <xref:System.ServiceModel.Security.MessageSecurityException> .  
  
## <a name="validation-of-https-service-certificates"></a>HTTPS hizmet sertifikalarının doğrulanması  
 İstemci ile bir hizmet arasında iletişim kurmak için HTTPS kullanılırken, sunucunun kimlik doğrulaması yaptığı sertifikanın varsayılan olarak zincir güvenini desteklemesi gerekir. Diğer bir deyişle, güvenilen bir kök sertifika yetkilisine zincirlenmelidir. Sertifikanın iptal edilip edilmediğini görmek için çevrimiçi denetim gerçekleştirilmez. <xref:System.Net.Security.RemoteCertificateValidationCallback>Aşağıdaki kodda gösterildiği gibi, bir geri çağırma kaydederek bu davranışı geçersiz kılabilirsiniz.  
  
 [!code-csharp[c_CertificateValidationDifferences#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#1)]
 [!code-vb[c_CertificateValidationDifferences#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#1)]  
  
 imzası `ValidateServerCertificate` aşağıdaki gibidir:  
  
 [!code-csharp[c_CertificateValidationDifferences#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#2)]
 [!code-vb[c_CertificateValidationDifferences#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#2)]  
  
 Uygulama, `ValidateServerCertificate` istemci uygulama geliştiricisi tarafından hizmet sertifikasını doğrulamak için gerekli olan tüm denetimleri gerçekleştirebilir.  
  
## <a name="validation-of-client-certificates-in-ssl-over-tcp-or-soap-security"></a>TCP veya SOAP Güvenliği üzerinden SSL 'de Istemci sertifikalarının doğrulanması  
 TCP veya ileti (SOAP) güvenliği üzerinden Güvenli Yuva Katmanı (SSL) kullanırken, istemci sertifikaları, <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A> sınıfının özellik değerine göre onaylanır <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> . Özelliği değerlerden birine ayarlanır <xref:System.ServiceModel.Security.X509CertificateValidationMode> . İptal denetimi, <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.RevocationMode%2A> sınıfının özellik değerinin değerlerine göre gerçekleştirilir <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> . Özelliği değerlerden birine ayarlanır <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> .  
  
 [!code-csharp[c_CertificateValidationDifferences#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#3)]
 [!code-vb[c_CertificateValidationDifferences#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#3)]  
  
## <a name="validation-of-service-certificate-in-ssl-over-tcp-and-soap-security"></a>TCP ve SOAP Güvenliği üzerinden SSL 'de hizmet sertifikası doğrulaması  
 TCP veya (SOAP) ileti güvenliği üzerinden SSL kullanırken, hizmet sertifikaları, <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> sınıfının özellik değerine göre onaylanır <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication> . Özelliği değerlerden birine ayarlanır <xref:System.ServiceModel.Security.X509CertificateValidationMode> .  
  
 İptal denetimi, <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.RevocationMode%2A> sınıfının özellik değerinin değerlerine göre gerçekleştirilir <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication> . Özelliği değerlerden birine ayarlanır <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> .  
  
 [!code-csharp[c_CertificateValidationDifferences#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#4)]
 [!code-vb[c_CertificateValidationDifferences#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#4)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Net.Security.RemoteCertificateValidationCallback>
- [Sertifikalarla Çalışma](working-with-certificates.md)
