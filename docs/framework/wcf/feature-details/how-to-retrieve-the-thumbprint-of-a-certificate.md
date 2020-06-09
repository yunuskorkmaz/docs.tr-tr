---
title: 'Nasıl yapılır: Bir Sertifikanın Parmak İzini Alma'
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], retrieving thumbprint
ms.assetid: da3101aa-78cd-4c34-9652-d1f24777eeab
ms.openlocfilehash: f59fad86287e89b0a573a6e3ee8420f384b0bc3b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601211"
---
# <a name="how-to-retrieve-the-thumbprint-of-a-certificate"></a>Nasıl yapılır: Bir Sertifikanın Parmak İzini Alma
Kimlik doğrulaması için bir X. 509.440 sertifikası kullanan bir Windows Communication Foundation (WCF) uygulaması yazarken, genellikle sertifikada bulunan taleplerin belirtilmesi gerekir. Örneğin, yönteminde sabit listesini kullanırken bir parmak izi talebi sağlamalısınız <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByThumbprint> <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> . Talep değerini bulmak için iki adım gerekir. İlk olarak, sertifikalar için Microsoft Yönetim Konsolu (MMC) ek bileşenini açın. (Bkz. [nasıl yapılır: MMC ek bileşeni Ile sertifikaları görüntüleme](how-to-view-certificates-with-the-mmc-snap-in.md).) İkincisi, burada açıklandığı gibi uygun bir sertifika bulun ve parmak izini (veya diğer talep değerlerini) kopyalayın.  
  
 Hizmet kimlik doğrulaması için bir sertifika kullanıyorsanız, **çıkarılan** sütunun değerini (konsolundaki ilk sütun) dikkat etmeniz önemlidir. Taşıma güvenliği olarak Güvenli Yuva Katmanı (SSL) kullanırken, yapılan ilk denetim, bir hizmetin temel adres Tekdüzen Kaynak tanımlayıcısı 'nı (URI) **verilen** değere karşılaştırmaktır. Değerler eşleşmelidir veya kimlik doğrulama işlemi durdurulur.  
  
 Yalnızca geliştirme sırasında kullanılmak üzere geçici sertifikalar oluşturmak için PowerShell New-SelfSignedCertificate cmdlet 'ini de kullanabilirsiniz. Ancak, bu tür bir sertifika bir sertifika yetkilisi tarafından verilmez ve üretim amacıyla kullanılamaz. Daha fazla bilgi için bkz. [nasıl yapılır: geliştirme sırasında kullanılmak üzere geçici sertifikalar oluşturma](how-to-create-temporary-certificates-for-use-during-development.md).  
  
### <a name="to-retrieve-a-certificates-thumbprint"></a>Bir sertifikanın parmak izini almak için  
  
1. Sertifikalar için Microsoft Yönetim Konsolu (MMC) ek bileşenini açın. (Bkz. [nasıl yapılır: MMC ek bileşeni Ile sertifikaları görüntüleme](how-to-view-certificates-with-the-mmc-snap-in.md).)  
  
2. **Konsol kökü** penceresinin sol bölmesinde, **Sertifikalar (yerel bilgisayar)** öğesine tıklayın.  
  
3. **Kişisel** klasöre tıklayarak genişletin.  
  
4. **Sertifikalar** klasörüne tıklayarak genişletin.  
  
5. Sertifika listesinde, **Hedeflenen amaçlar** başlığına göz önünde. **Istemci kimlik doğrulamasını** amaçlanan bir amaç olarak listeleyen bir sertifika bulun.  
  
6. Sertifikaya çift tıklayın.  
  
7. **Sertifika** Iletişim kutusunda **Ayrıntılar** sekmesine tıklayın.  
  
8. Alan listesinde ilerleyin ve **parmak izi**' ne tıklayın.  
  
9. Kutuya onaltılık karakterleri kopyalayın. Bu parmak izi kodda kullanılıyorsa, `X509FindType` onaltılık sayılar arasındaki boşlukları kaldırın. Örneğin, "a9 09 50 2D D8 2a e4 14 33 e6 f8 38 86 B0 0d 42 77 a3 2a 7b" parmak izi kodda "a909502dd82ae41433e6f83886b00d4277a32a7b" olarak belirtilmelidir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByThumbprint>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A>
- [Nasıl Yapılır: SSL Sertifikası ile Bir Bağlantı Noktasını Yapılandırma](how-to-configure-a-port-with-an-ssl-certificate.md)
- [Nasıl yapılır: MMC Ek Bileşeni ile Sertifikaları Görüntüleme](how-to-view-certificates-with-the-mmc-snap-in.md)
- [Nasıl yapılır: Geliştirme Sırasında Kullanmak için Geçici Sertifikalar Oluşturma](how-to-create-temporary-certificates-for-use-during-development.md)
