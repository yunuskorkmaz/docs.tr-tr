---
title: "Nasıl yapılır: Bir Sertifikanın Parmak İzini Alma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: certificates [WCF], retrieving thumbprint
ms.assetid: da3101aa-78cd-4c34-9652-d1f24777eeab
caps.latest.revision: "15"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4719be3d4e98407062bd246df4f14b9cbf452c74
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
 [Nasıl yapılır: bir SSL sertifikası ile bir bağlantı noktası yapılandırın](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)  
 [Nasıl yapılır: MMC ek bileşeni ile sertifikaları görüntüle](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md)  
 [Nasıl yapılır: geliştirme sırasında kullanmak için geçici sertifikalar oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md)
