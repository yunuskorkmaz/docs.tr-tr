---
title: "Nasıl yapılır: Bir Sertifikanın Parmak İzini Alma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- certificates [WCF], retrieving thumbprint
ms.assetid: da3101aa-78cd-4c34-9652-d1f24777eeab
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8f6d00d31023aa8d6dbfec4a8306f1cb9da17c74
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-retrieve-the-thumbprint-of-a-certificate"></a>Nasıl yapılır: Bir Sertifikanın Parmak İzini Alma
Yazılırken bir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] kimlik doğrulaması için bir X.509 sertifikası kullanan bir uygulama olmasından genellikle sertifika içinde bulunan talepleri belirtmek gerekli. Örneğin, kullanırken bir parmak izi talep sağlamalısınız <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByThumbprint> numaralandırmada <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> yöntemi. Talep değeri bulma iki adımı gerektirir. İlk olarak, sertifikalar için Microsoft Yönetim Konsolu (MMC) ek bileşenini açın. (Bkz [nasıl yapılır: MMC ek bileşeni ile sertifikaları görüntüle](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).) İkinci olarak, burada açıklandığı gibi uygun bir sertifika Bul ve kendi parmak izi (veya diğer talep değerleri) kopyalayın.  
  
 Hizmet kimlik doğrulaması için bir sertifika kullanıyorsanız, değeri not daha önemlidir **çıkarılan** sütun (ilk sütun konsolunda). Tekdüzen Kaynak Tanımlayıcısı (URI) bir hizmetin temel karşılaştırmak için bir taşıma güvenliği, yapılan ilk denetimleri birini olduğu gibi Güvenli Yuva Katmanı (SSL) kullanarak adres **çıkarılan** değeri. Değerler eşleşmelidir veya kimlik doğrulama işlemi durdu.  
  
 Makecert.exe aracından de kullanabilirsiniz [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] SDK'sını yalnızca geliştirme sırasında kullanmak için geçici sertifikalar oluşturma. Varsayılan olarak, ancak bu tür bir sertifika bir sertifika yetkilisi tarafından verilmemiş ve üretim için kullanılamaz. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Nasıl yapılır: geliştirme sırasında kullanmak için geçici sertifikalar oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md).  
  
### <a name="to-retrieve-a-certificates-thumbprint"></a>Bir sertifikanın parmak izi almak için  
  
1.  Sertifikalar için Microsoft Yönetim Konsolu (MMC) ek bileşenini açın. (Bkz [nasıl yapılır: MMC ek bileşeni ile sertifikaları görüntüle](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).)  
  
2.  İçinde **konsol kökü** penceresinin sol bölmesinde, tıklatın **sertifikalar (yerel bilgisayar)**.  
  
3.  Tıklatın **kişisel** klasörünü genişletin.  
  
4.  Tıklatın **sertifikaları** klasörünü genişletin.  
  
5.  Sertifikaları listesinde Not **Hedeflenen amaçlar** başlığı. Listeleyen bir sertifika bulunamadı **istemci kimlik doğrulaması** hedeflenen amacı olarak.  
  
6.  Sertifikayı çift tıklatın.  
  
7.  İçinde **sertifika** iletişim kutusu, tıklatın **ayrıntıları** sekmesi.  
  
8.  Alanları listede ilerleyin ve tıklayın **parmak izi**.  
  
9. Onaltılık karakterler kutusundan kopyalayın. Bu parmak izi kodu kullanılıyorsa `X509FindType`, onaltılık sayılar arasında boşluk kaldırın. Örneğin, parmak izi "a9 09 50 2B d8 2a e4 14 33 e6 f8 38 86 b0 0d 42 77 a3 2a 7b" Code "a909502dd82ae41433e6f83886b00d4277a32a7b" olarak belirtilmelidir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByThumbprint>  
 <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A>  
 [Nasıl Yapılır: SSL Sertifikası ile Bir Bağlantı Noktasını Yapılandırma](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)  
 [Nasıl yapılır: MMC Ek Bileşeni ile Sertifikaları Görüntüleme](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md)  
 [Nasıl yapılır: Geliştirme Sırasında Kullanmak için Geçici Sertifikalar Oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md)
