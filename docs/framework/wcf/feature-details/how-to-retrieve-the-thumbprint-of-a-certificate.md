---
title: 'Nasıl yapılır: Bir Sertifikanın Parmak İzini Alma'
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], retrieving thumbprint
ms.assetid: da3101aa-78cd-4c34-9652-d1f24777eeab
ms.openlocfilehash: 51debbbcfec2fd5b82460e1dd1d6ece8e77bfc13
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62000785"
---
# <a name="how-to-retrieve-the-thumbprint-of-a-certificate"></a>Nasıl yapılır: Bir Sertifikanın Parmak İzini Alma
Kimlik doğrulaması için bir X.509 sertifikası kullanan bir Windows Communication Foundation (WCF) uygulaması yazarken genellikle talep sertifika içinde bulunan belirtmek gereklidir. Örneğin, kullanırken bir parmak izi talep sağlamalısınız <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByThumbprint> numaralandırmada <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> yöntemi. Talep değeri bulmak için iki adım gerekir. İlk olarak, sertifikalar Microsoft Yönetim Konsolu (MMC) ek bileşenini açın. (Bkz [nasıl yapılır: MMC ek bileşeni ile sertifikaları görüntüleme](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).) İkinci olarak, aşağıda açıklandığı gibi uygun bir sertifikayı bulun ve parmak izi (veya diğer talep değerleri) kopyalayın.  
  
 Hizmet kimlik doğrulaması için bir sertifika kullanıyorsanız, değerini not edin önemlidir **çıkarılan** sütun (konsolda ilk sütun). Tekdüzen Kaynak Tanımlayıcısı (URI) bir hizmet için bir aktarım güvenliği, yapılan ilk denetimler birini temel karşılaştırmak için olduğu gibi Güvenli Yuva Katmanı (SSL) kullanarak adres **çıkarılan** değeri. Değerlerin eşleşmesi gerekir ya da kimlik doğrulama işlemi durdurulur.  
  
 Yalnızca geliştirme sırasında kullanmak için geçici sertifikalar oluşturmak için New-SelfSignedCertificate Powershell cmdlet'ini de kullanabilirsiniz. Varsayılan olarak, ancak bu tür bir sertifika bir sertifika yetkilisi tarafından verilmemiş ve üretim için kullanılamaz. Daha fazla bilgi için [nasıl yapılır: Geliştirme sırasında kullanmak için geçici sertifikalar oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md).  
  
### <a name="to-retrieve-a-certificates-thumbprint"></a>Bir sertifikanın parmak izi alınamadı  
  
1. Sertifikalar Microsoft Yönetim Konsolu (MMC) ek bileşenini açın. (Bkz [nasıl yapılır: MMC ek bileşeni ile sertifikaları görüntüleme](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).)  
  
2. İçinde **konsol kökü** penceresinin sol bölmesinde, tıklayın **sertifikalar (yerel bilgisayar)**.  
  
3. Tıklayın **kişisel** klasörünü genişletin.  
  
4. Tıklayın **sertifikaları** klasörünü genişletin.  
  
5. Sertifikaları listesinde Not **Hedeflenen amaçlar** başlığı. Listeleyen bir sertifikayı bulma **istemci kimlik doğrulaması** bir amacı olarak.  
  
6. Sertifikaya çift tıklayın.  
  
7. İçinde **sertifika** iletişim kutusu, tıklayın **ayrıntıları** sekmesi.  
  
8. Alanlar listesi boyunca kaydırın ve tıklayın **parmak izi**.  
  
9. Onaltılık karakter kutusundan kopyalayın. Bu parmak izi kodu kullanılırsa `X509FindType`, onaltılık sayı arasındaki boşlukları Kaldır. Örneğin, parmak izi "a9 09 50 2B d8 2a e4 14 33 e6 f8 38 86 b0 0d 42 77 a3 2a 7b" code "a909502dd82ae41433e6f83886b00d4277a32a7b" olarak belirtilmelidir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByThumbprint>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A>
- [Nasıl yapılır: Bir SSL sertifikası ile bir bağlantı noktası yapılandırma](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)
- [Nasıl yapılır: MMC ek bileşeni ile sertifikaları görüntüleme](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md)
- [Nasıl yapılır: Geliştirme sırasında kullanmak için geçici sertifikalar oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md)
