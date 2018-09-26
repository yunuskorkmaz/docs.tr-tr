---
title: HTTPS, TCP üzerinden SSL ve SOAP Güvenliği Arasındaki Sertifika Doğrulama Farkları
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- certificates [WCF], validation differences
ms.assetid: 953a219f-4745-4019-9894-c70704f352e6
author: BrucePerlerMS
ms.openlocfilehash: 79b5e86b689da0678b0d949d2a335dbfe3836f0e
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47195335"
---
# <a name="certificate-validation-differences-between-https-ssl-over-tcp-and-soap-security"></a>HTTPS, TCP üzerinden SSL ve SOAP Güvenliği Arasındaki Sertifika Doğrulama Farkları
Sertifikaları Windows Communication Foundation (WCF) Aktarım Katmanı Güvenliği (TLS) yanı sıra ileti düzeyi (SOAP) güvenlik ile HTTP (HTTPS) veya TCP üzerinden kullanabilirsiniz. Bu konuda, bunun gibi sertifikaların doğrulanır farklılıklar açıklanmaktadır.  
  
## <a name="validation-of-https-client-certificates"></a>HTTPS istemci sertifikalarını doğrulama  
 Bir istemci ve hizmet arasında iletişim kurmak için HTTPS kullanırken, istemcinin hizmete kimlik doğrulaması için kullandığı sertifika güven zinciri desteklemesi gerekir. Diğer bir deyişle, güvenilen kök sertifika yetkilisine zincirleme gerekir. Değilse, HTTP katman harekete geçirirse bir <xref:System.Net.WebException> iletisiyle "uzak sunucu bir hata döndürdü: (403) Yasak." WCF olarak bu durum ortaya çıkarır bir <xref:System.ServiceModel.Security.MessageSecurityException>.  
  
## <a name="validation-of-https-service-certificates"></a>HTTPS hizmet sertifika doğrulama  
 Sunucu doğrulamasını sertifika güven zinciri, bir istemci ve hizmet arasında iletişim kurmak için HTTPS kullanarak, varsayılan olarak desteklemesi gerekir. Diğer bir deyişle, güvenilen kök sertifika yetkilisine zincirleme gerekir. Sertifika iptal olup olmadığını görmek için hiçbir çevrimiçi denetimi gerçekleştirilir. Kaydederek bu davranışı geçersiz kılabilirsiniz bir <xref:System.Net.Security.RemoteCertificateValidationCallback> aşağıdaki kodda gösterildiği gibi geri çağırma.  
  
 [!code-csharp[c_CertificateValidationDifferences#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#1)] 
 [!code-vb[c_CertificateValidationDifferences#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#1)]  
  
 Burada imzası `ValidateServerCertificate` aşağıdaki gibidir:  
  
 [!code-csharp[c_CertificateValidationDifferences#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#2)]
 [!code-vb[c_CertificateValidationDifferences#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#2)]  
  
 Uygulama `ValidateServerCertificate` istemci uygulama geliştiricisinin hizmet sertifikasını doğrulamak gerekli kabul ettiği tüm denetimleri gerçekleştirebilirsiniz.  
  
## <a name="validation-of-client-certificates-in-ssl-over-tcp-or-soap-security"></a>İstemci sertifikaları, SSL üzerinden TCP veya SOAP güvenlik doğrulaması  
 Ne zaman Güvenli Yuva Katmanı (SSL) TCP veya (SOAP) ileti güvenliği, istemci sertifikaları kullanarak doğrulanır göre <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A> özelliği değerinin <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> sınıfı. Özelliği, birine ayarlanmış <xref:System.ServiceModel.Security.X509CertificateValidationMode> değerleri. İptal denetimi değerlerine göre gerçekleştirilir <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.RevocationMode%2A> özelliği değerinin <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> sınıfı. Özelliği, birine ayarlanmış <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> değerleri.  
  
 [!code-csharp[c_CertificateValidationDifferences#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#3)]
 [!code-vb[c_CertificateValidationDifferences#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#3)]  
  
## <a name="validation-of-service-certificate-in-ssl-over-tcp-and-soap-security"></a>SSL TCP ve SOAP güvenliği üzerinden hizmet sertifikası doğrulama  
 SSL ileti güvenliği TCP veya (SOAP) kullanırken hizmet sertifikaları göre doğrulanır <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> özelliği değerinin <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication> sınıfı. Özelliği, birine ayarlanmış <xref:System.ServiceModel.Security.X509CertificateValidationMode> değerleri.  
  
 İptal denetimi değerlerine göre gerçekleştirilir <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.RevocationMode%2A> özelliği değerinin <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication> sınıfı. Özelliği, birine ayarlanmış <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> değerleri.  
  
 [!code-csharp[c_CertificateValidationDifferences#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#4)]
 [!code-vb[c_CertificateValidationDifferences#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#4)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Net.Security.RemoteCertificateValidationCallback>  
 [Sertifikalarla Çalışma](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
