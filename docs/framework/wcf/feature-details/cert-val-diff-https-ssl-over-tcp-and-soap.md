---
title: HTTPS, TCP üzerinden SSL ve SOAP Güvenliği Arasındaki Sertifika Doğrulama Farkları
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- certificates [WCF], validation differences
ms.assetid: 953a219f-4745-4019-9894-c70704f352e6
ms.openlocfilehash: 0e82d1898bec7cda474a5a92958b5af1b30c9de7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185401"
---
# <a name="certificate-validation-differences-between-https-ssl-over-tcp-and-soap-security"></a>HTTPS, TCP üzerinden SSL ve SOAP Güvenliği Arasındaki Sertifika Doğrulama Farkları
Windows Communication Foundation'daki (WCF) ileti katmanı (SOAP) güvenliğine sahip sertifikaları, HTTP (HTTPS) veya TCP üzerinden taşıma katmanı güvenliğine (TLS) ek olarak kullanabilirsiniz. Bu konu, bu tür sertifikaların doğrulanma şeklindeki farklılıkları açıklar.  
  
## <a name="validation-of-https-client-certificates"></a>HTTPS İstemci Sertifikalarının Doğrulanması  
 İstemci ve hizmet arasında iletişim kurmak için HTTPS kullanırken, istemcinin hizmete kimlik doğrulamak için kullandığı sertifika zincir güvenini desteklemelidir. Diğer bir süre, güvenilir bir kök sertifika yetkilisine zincirleme olmalıdır. Değilse, HTTP katmanı "Uzak sunucu bir hata döndü: (403) Yasak" iletisi ile yükseltir. <xref:System.Net.WebException> WCF bu istisnayı <xref:System.ServiceModel.Security.MessageSecurityException>bir .  
  
## <a name="validation-of-https-service-certificates"></a>HTTPS Hizmet Sertifikalarının Doğrulanması  
 İstemci ve hizmet arasında iletişim kurmak için HTTPS kullanırken, sunucunun kimlik doğrulaması yaptığı sertifika varsayılan olarak zincir güvenini desteklemelidir. Diğer bir süre, güvenilir bir kök sertifika yetkilisine zincirleme olmalıdır. Sertifikanın iptal edilip edilmediğine dair çevrimiçi denetim yapılmaz. Aşağıdaki kodda gösterildiği gibi bir <xref:System.Net.Security.RemoteCertificateValidationCallback> geri arama kaydederek bu davranışı geçersiz kılabilirsiniz.  
  
 [!code-csharp[c_CertificateValidationDifferences#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#1)]
 [!code-vb[c_CertificateValidationDifferences#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#1)]  
  
 için `ValidateServerCertificate` imza aşağıdaki gibi olduğu yer:  
  
 [!code-csharp[c_CertificateValidationDifferences#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#2)]
 [!code-vb[c_CertificateValidationDifferences#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#2)]  
  
 Uygulama, `ValidateServerCertificate` istemci uygulama geliştiricisinin hizmet sertifikasını doğrulamak için gerekli gördüğü denetimleri gerçekleştirebilir.  
  
## <a name="validation-of-client-certificates-in-ssl-over-tcp-or-soap-security"></a>SSL'deki Müşteri Sertifikalarının TCP veya SOAP Security üzerinden doğrulanması  
 TCP veya ileti (SOAP) güvenliği üzerinden Güvenli Soketkatmanı (SSL) kullanırken, <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A> istemci sertifikaları <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> sınıfın özellik değerine göre doğrulanır. Özellik <xref:System.ServiceModel.Security.X509CertificateValidationMode> değerlerden birine ayarlanır. İptal denetimi <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.RevocationMode%2A> <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> sınıfın özellik değeri değerlerine göre gerçekleştirilir. Özellik <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> değerlerden birine ayarlanır.  
  
 [!code-csharp[c_CertificateValidationDifferences#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#3)]
 [!code-vb[c_CertificateValidationDifferences#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#3)]  
  
## <a name="validation-of-service-certificate-in-ssl-over-tcp-and-soap-security"></a>SSL'de Hizmet Belgesinin TCP ve SOAP Security üzerinden doğrulanması  
 TCP veya (SOAP) ileti güvenliği üzerinden SSL kullanırken, hizmet <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> sertifikaları <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication> sınıfın özellik değerine göre doğrulanır. Özellik <xref:System.ServiceModel.Security.X509CertificateValidationMode> değerlerden birine ayarlanır.  
  
 İptal denetimi <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.RevocationMode%2A> <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication> sınıfın özellik değeri değerlerine göre gerçekleştirilir. Özellik <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> değerlerden birine ayarlanır.  
  
 [!code-csharp[c_CertificateValidationDifferences#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#4)]
 [!code-vb[c_CertificateValidationDifferences#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#4)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Net.Security.RemoteCertificateValidationCallback>
- [Sertifikalarla Çalışma](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
