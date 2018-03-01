---
title: "Nasıl yapılır: MMC Ek Bileşeni ile Sertifikaları Görüntüleme"
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
- certificates [WCF], viewing with the MMC snap-in
ms.assetid: 2b8782aa-ebb4-4ee7-974b-90299e356dc5
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 582eaef518e10acb4c4c356226ce0be24d1b4c35
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-view-certificates-with-the-mmc-snap-in"></a>Nasıl yapılır: MMC Ek Bileşeni ile Sertifikaları Görüntüleme
Bir ortak kimlik bilgisi X.509 sertifikası türüdür. Güvenli Hizmetleri veya istemcileri oluştururken, bir sertifika, istemci veya hizmet kimlik bilgisi olarak yöntemleri kullanarak kullanılabilir belirtebilirsiniz <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> yöntemi. Yöntemi, sertifikanın depolandığı deposu ve sertifika için ararken kullanmak için bir değer gibi çeşitli parametreleri gerektirir. Aşağıdaki yordam, uygun bir sertifika bulmak için bir bilgisayarda depoları incelemek gösterilmiştir. Sertifika parmak izini bulma örneği için bkz: [nasıl yapılır: bir sertifikanın parmak izini alma](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).  
  
### <a name="to-view-certificates-in-the-mmc-snap-in"></a>MMC ek bileşeninde sertifikaları görüntülemek için  
  
1.  Bir komut istemi penceresi açın.  
  
2.  Tür `mmc` ve ENTER tuşuna basın. Yerel makine deposunda sertifikaları görüntülemek için yönetici rolünde olması gerektiğini unutmayın.  
  
3.  Üzerinde **dosya** menüsünde tıklatın **Ekle/Kaldır ek bileşenini**.  
  
4.  **Ekle**'yi tıklatın.  
  
5.  İçinde **tek başına ek bileşen Ekle alanında** iletişim kutusunda **Sertifikalar**.  
  
6.  **Ekle**'yi tıklatın.  
  
7.  İçinde **Sertifikalar ek bileşenini** iletişim kutusunda **bilgisayar hesabı** tıklatıp **sonraki**. İsteğe bağlı olarak seçebileceğiniz **My kullanıcı hesabı** veya **hizmet hesabı**. Bilgisayarın yöneticisi değilse, yalnızca kullanıcı hesabınız için sertifikaları yönetebilirsiniz.  
  
8.  İçinde **Bilgisayar Seç** iletişim kutusu, tıklatın **son**.  
  
9. İçinde **tek başına ek bileşen Ekle alanında** iletişim kutusu, tıklatın **Kapat**.  
  
10. Üzerinde **Ekle/Kaldır ek bileşenini** iletişim kutusu, tıklatın **Tamam**.  
  
11. İçinde **konsol kökü** penceresinde tıklatın **sertifikalar (yerel bilgisayar)** sertifikayı görüntülemek için bilgisayar için depolar.  
  
12. İsteğe bağlı. Hesabınıza ilişkin sertifikaları görüntülemek için 3-6 adımlarını yineleyin. Seçmek yerine 7. adımda **bilgisayar hesabı**, tıklatın **My kullanıcı hesabı** ve 8-10 adımları yineleyin.  
  
13. İsteğe bağlı. Üzerinde **dosya** menüsünde tıklatın **kaydetmek** veya **Kaydet**. Daha sonra yeniden kullanmak için konsol dosyasına kaydedin.  
  
## <a name="viewing-certificates-with-internet-explorer"></a>Internet Explorer ile sertifikaları görüntüleme  
 Da görüntüleyebilir, dışarı aktarmak ve Internet Explorer kullanarak sertifikaları silmek.  
  
#### <a name="to-view-certificates-with-internet-explorer"></a>Internet Explorer ile sertifikaları görüntülemek için  
  
1.  Internet Explorer'daki **Araçları**, ardından **Internet Seçenekleri** görüntülemek için **Internet Seçenekleri** iletişim kutusu.  
  
2.  Tıklatın **içerik** sekmesi.  
  
3.  Altında **sertifikaları**, tıklatın **Sertifikalar**.  
  
4.  Herhangi bir sertifika ayrıntılarını görüntüleyin, sertifikayı seçin ve ' **Görünüm**.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sertifikalarla Çalışma](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [Nasıl yapılır: Geliştirme Sırasında Kullanmak için Geçici Sertifikalar Oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md)  
 [Nasıl yapılır: Bir Sertifikanın Parmak İzini Alma](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)
