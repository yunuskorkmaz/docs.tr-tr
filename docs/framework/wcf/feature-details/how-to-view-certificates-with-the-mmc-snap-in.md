---
title: 'Nasıl yapilir: MMC snap-in ile sertifikaları görüntüleme'
ms.date: 02/25/2019
helpviewer_keywords:
- certificates [WCF], viewing with the MMC snap-in
ms.assetid: 2b8782aa-ebb4-4ee7-974b-90299e356dc5
ms.openlocfilehash: 35048c24e838c513909fae8bedcba287001f5cef
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184779"
---
# <a name="how-to-view-certificates-with-the-mmc-snap-in"></a>Nasıl yapilir: MMC snap-in ile sertifikaları görüntüleme
Güvenli bir istemci veya hizmet oluşturduğunuzda, [sertifikayı](working-with-certificates.md) kimlik bilgisi olarak kullanabilirsiniz. Örneğin, yaygın bir kimlik bilgisi türü, <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A?displayProperty=nameWithType> yöntemle oluşturduğunuz X.509 sertifikasıdır.

Windows sistemlerinde Microsoft Yönetim Konsolu (MMC) ile incelediğiniz üç farklı sertifika deposu türü vardır:

- Yerel bilgisayar: Mağaza aygıtiçin yerel ve aygıttaki tüm kullanıcılar için geneldir.

- Geçerli kullanıcı: Mağaza, aygıttaki geçerli kullanıcı hesabına yereldir.

- Servis hesabı: Mağaza, aygıttaki belirli bir hizmetin yereldir.

## <a name="view-certificates-in-the-mmc-snap-in"></a>MMC snap-in'deki sertifikaları görüntüleme

Aşağıdaki yordam, uygun bir sertifika bulmak için yerel cihazınızdaki mağazaların nasıl incelenir olduğunu gösterir:
  
1. **Başlat** menüsünden **Çalıştır'ı** seçin ve ardından *mmc'yi*girin.

    MMC görünür.
  
2. **Dosya** menüsünden **Ekle/Kaldır'ı**seçin.

    **Eklenti veya Kaldır Snap-ins** penceresi görüntülenir.
  
3. Kullanılabilir **ekler** listesinden **Sertifikalar'ı**seçin ve ardından **Ekle'yi**seçin.  

    ![Sertifika ekleme ekleme](./media/mmc-add-certificate-snap-in.png)
  
4. **Sertifikalar'a giriş** penceresinde **Bilgisayar hesabı'nı**seçin ve sonra **İleri'yi**seçin.
  
    İsteğe bağlı olarak, belirli bir hizmet için geçerli kullanıcı veya **Hizmet hesabı** için kullanıcı **hesabımı** seçebilirsiniz.

    > [!NOTE]
    > Aygıtınızın yöneticisi değilseniz, sertifikaları yalnızca kullanıcı hesabınız için yönetebilirsiniz.
  
5. Bilgisayarı **Seç** penceresinde, **Yerel bilgisayarı** seçili bırakın ve ardından **Bitir'i**seçin.  
  
6. Ekle **veya Kaldır** penceresinde **Tamam'ı**seçin.  
  
    ![Sertifika ekleme ekleme](./media/mmc-certificate-snap-in-selected.png)

7. İsteğe bağlı: **Dosya** menüsünden, MMC konsol dosyasını daha sonra kullanmak üzere kaydetmek için **Kaydet** veya **Kaydet'i** seçin.  

8. Sertifikalarınızı MMC snap-in'de görüntülemek için sol bölmede **Konsol Kökü'nü** seçin ve **ardından Sertifikaları (Yerel Bilgisayar)** genişletin.

    Her sertifika türü için dizin listesi görüntülenir. Her sertifika dizininden, sertifikalarını görüntüleyebilir, dışa aktarabilir, içe aktarabilir ve silebilirsiniz.

## <a name="view-certificates-with-the-certificate-manager-tool"></a>Sertifika Yöneticisi aracıyla sertifikaları görüntüleme

Sertifika Yöneticisi aracını kullanarak sertifikaları görüntüleyebilir, dışa aktarabilir, içe aktarabilir ve silebilirsiniz.

### <a name="to-view-certificates-for-the-local-device"></a>Yerel aygıtın sertifikalarını görüntülemek için

1. **Başlat** menüsünden **Çalıştır'ı** seçin ve *ardından certlm.msc'yi*girin.

    Yerel aygıt için Sertifika Yöneticisi aracı görüntülenir.
  
2. Sertifikalarınızı görüntülemek için, sol bölmedeki **Sertifikalar - Yerel Bilgisayar** altında, görüntülemek istediğiniz sertifika türüiçin dizini genişletin.

### <a name="to-view-certificates-for-the-current-user"></a>Geçerli kullanıcının sertifikalarını görüntülemek için

1. **Başlat** menüsünden **Çalıştır'ı** seçin ve ardından *certmgr.msc'yi*girin.

    Geçerli kullanıcı için Sertifika Yöneticisi aracı görüntülenir.
  
2. Sertifikalarınızı görüntülemek **için, Sertifikalar altında - Sol** bölmedeki Geçerli Kullanıcı, görüntülemek istediğiniz sertifika türüiçin dizini genişletin.

## <a name="see-also"></a>Ayrıca bkz.

- [Sertifikalarla çalışma](working-with-certificates.md)
- [Nasıl kullanılır: Geliştirme sırasında kullanılmak üzere geçici sertifikalar oluşturma](how-to-create-temporary-certificates-for-use-during-development.md)
- [Nasıl yapılır: Sertifikanın parmak izini alma](how-to-retrieve-the-thumbprint-of-a-certificate.md)
