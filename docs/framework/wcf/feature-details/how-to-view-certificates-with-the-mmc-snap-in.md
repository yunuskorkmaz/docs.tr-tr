---
title: 'Nasıl yapılır: MMC ek bileşeni ile sertifikaları görüntüleme'
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], viewing with the MMC snap-in
ms.assetid: 2b8782aa-ebb4-4ee7-974b-90299e356dc5
ms.openlocfilehash: 72fd6a1be2f33e1bfeb08fd43f3436627ee842e5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54521588"
---
# <a name="how-to-view-certificates-with-the-mmc-snap-in"></a>Nasıl yapılır: MMC ek bileşeni ile sertifikaları görüntüleme
Ortak bir kimlik bilgisi türünü X.509 sertifikasıdır. Güvenli Hizmetleri veya istemciler oluştururken, bir sertifika yöntemleri kullanarak istemci veya hizmet kimlik bilgisi olarak kullanılabilir belirtebilirsiniz <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> yöntemi. Yöntemi, sertifikanın depolandığı deponun ve sertifikasını ararken kullanmak için bir değer gibi çeşitli parametreler gerektirir. Aşağıdaki yordam bir bilgisayarda uygun bir sertifika bulmak için depoları incelemek nasıl gösterir. Sertifika parmak izi bulma örneği için bkz: [nasıl yapılır: Bir sertifikanın parmak izini alma](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).  
  
### <a name="to-view-certificates-in-the-mmc-snap-in"></a>Sertifikalar MMC ek bileşeninde görüntülemek için  
  
1.  Bir komut istemi penceresi açın.  
  
2.  Tür `mmc` ve ENTER tuşuna basın. Yerel makine deposuna sertifikaları görüntülemek için yönetici rolünde olması gerektiğini unutmayın.  
  
3.  Üzerinde **dosya** menüsünde tıklatın **Ekle/Kaldır ek bileşen içinde**.  
  
4.  **Ekle**'yi tıklatın.  
  
5.  İçinde **tek başına ek eklentisi** iletişim kutusunda **sertifikaları**.  
  
6.  **Ekle**'yi tıklatın.  
  
7.  İçinde **Sertifikalar ek bileşenini** iletişim kutusunda **bilgisayar hesabı** tıklatıp **sonraki**. İsteğe bağlı olarak seçebileceğiniz **My kullanıcı hesabı** veya **hizmet hesabı**. Bilgisayarın Yönetici değilseniz, yalnızca kullanıcı hesabınız için sertifikaları yönetebilir.  
  
8.  İçinde **Bilgisayar Seç** iletişim kutusu, tıklayın **son**.  
  
9. İçinde **tek başına ek eklentisi** iletişim kutusu, tıklayın **Kapat**.  
  
10. Üzerinde **Ekle/Kaldır ek bileşenini** iletişim kutusu, tıklayın **Tamam**.  
  
11. İçinde **konsol kökü** penceresinde tıklayın **sertifikalar (yerel bilgisayar)** sertifikayı görüntülemek için bilgisayar için depolar.  
  
12. İsteğe bağlı. Hesabınız için sertifikaları görüntülemek için 3-6 adımlarını yineleyin. Yerne 7. adımda **bilgisayar hesabı**, tıklayın **My kullanıcı hesabı** 8-10 adımları yineleyin.  
  
13. İsteğe bağlı. Üzerinde **dosya** menüsünde tıklatın **Kaydet** veya **Kaydet**. Daha sonra yeniden kullanmak için konsol dosyayı kaydedin.  
  
## <a name="viewing-certificates-with-internet-explorer"></a>Internet Explorer ile sertifikaları görüntüleme  
 Da görüntüleyebilir, dışarı aktarma almak ve Internet Explorer'ı kullanarak sertifikaları silin.  
  
#### <a name="to-view-certificates-with-internet-explorer"></a>Internet Explorer ile sertifikaları görüntülemek için  
  
1.  Internet Explorer'ı tıklatın **Araçları**, ardından **Internet Seçenekleri** görüntülenecek **Internet Seçenekleri** iletişim kutusu.  
  
2.  Tıklayın **içerik** sekmesi.  
  
3.  Altında **sertifikaları**, tıklayın **sertifikaları**.  
  
4.  Herhangi bir sertifika ayrıntılarını görüntülemek için sertifikayı seçin ve tıklayın **görünümü**.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Sertifikalarla Çalışma](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [Nasıl yapılır: Geliştirme sırasında kullanmak için geçici sertifikalar oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md)
- [Nasıl yapılır: Bir sertifikanın parmak izini alma](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)
