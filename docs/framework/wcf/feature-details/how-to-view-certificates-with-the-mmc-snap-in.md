---
title: 'Nasıl yapılır: MMC ek bileşeni ile sertifikaları görüntüleme'
description: Güvenli bir WCF istemcisi veya hizmeti bir sertifikayı kimlik bilgisi olarak kullanabilir. MMC eklentisini kullanarak inceleyebileceğiniz sertifika depolarının türleri hakkında bilgi edinin.
ms.date: 02/25/2019
helpviewer_keywords:
- certificates [WCF], viewing with the MMC snap-in
ms.assetid: 2b8782aa-ebb4-4ee7-974b-90299e356dc5
ms.openlocfilehash: e63034e48ae836f67f89b454829f7196c94610cd
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246681"
---
# <a name="how-to-view-certificates-with-the-mmc-snap-in"></a>Nasıl yapılır: MMC ek bileşeni ile sertifikaları görüntüleme
Güvenli bir istemci veya hizmet oluşturduğunuzda kimlik bilgisi olarak bir [sertifika](working-with-certificates.md) kullanabilirsiniz. Örneğin, ortak bir kimlik bilgisi türü, yöntemiyle oluşturduğunuz X. 509.952 sertifikasıdır <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A?displayProperty=nameWithType> .

Windows sistemlerinde Microsoft Yönetim Konsolu (MMC) ile inceleyebileceğiniz üç farklı türde sertifika deposu vardır:

- Yerel bilgisayar: mağaza cihaz için yereldir ve cihazdaki tüm kullanıcılar için geneldir.

- Geçerli Kullanıcı: mağaza, cihazdaki geçerli kullanıcı hesabına yereldir.

- Hizmet hesabı: mağaza, cihazdaki belirli bir hizmette yereldir.

## <a name="view-certificates-in-the-mmc-snap-in"></a>MMC ek bileşenindeki sertifikaları görüntüleme

Aşağıdaki yordam, uygun bir sertifikayı bulmak için yerel cihazınızdaki mağazaların nasıl inceleneceğini göstermektedir:
  
1. **Başlat** menüsünden **Çalıştır** ' ı seçin ve ardından *MMC*' yi girin.

    MMC görüntülenir.
  
2. **Dosya** menüsünde, **ek bileşen Ekle/Kaldır**' ı seçin.

    **Ek bileşenleri Ekle veya Kaldır** penceresi görüntülenir.
  
3. **Kullanılabilir ek bileşenler** listesinden **Sertifikalar**' ı seçin ve **Ekle**' yi seçin.  

    ![Sertifika ek bileşeni ekleme](./media/mmc-add-certificate-snap-in.png)
  
4. **Sertifikalar ek bileşeni** penceresinde **bilgisayar hesabı**' nı seçin ve ardından **İleri**' yi seçin.
  
    İsteğe bağlı olarak, belirli bir hizmet için geçerli kullanıcı veya **hizmet hesabı** için **Kullanıcı hesabımı** seçebilirsiniz.

    > [!NOTE]
    > Cihazınız için yönetici değilseniz yalnızca Kullanıcı hesabınız için sertifikaları yönetebilirsiniz.
  
5. **Bilgisayar Seç** penceresinde, **Yerel bilgisayar** seçili bırakın ve **son**' u seçin.  
  
6. **Ek bileşen Ekle veya Kaldır** penceresinde **Tamam**' ı seçin.  
  
    ![Sertifika ek bileşeni ekleme](./media/mmc-certificate-snap-in-selected.png)

7. İsteğe bağlı: **Dosya** menüsünde, daha sonra kullanmak üzere MMC konsol dosyasını kaydetmek için **Kaydet** veya **farklı kaydet** ' i seçin.  

8. MMC ek bileşeninde sertifikalarınızı görüntülemek için sol bölmedeki **konsol kökü** ' nü seçin ve ardından **Sertifikalar (yerel bilgisayar)**' ı genişletin.

    Her sertifika türü için dizinlerin listesi görüntülenir. Her bir sertifika dizininden sertifikalarını görüntüleyebilir, dışarı aktarabilir, içeri aktarabilir ve silebilirsiniz.

## <a name="view-certificates-with-the-certificate-manager-tool"></a>Sertifika Yöneticisi aracı ile sertifikaları görüntüleme

Sertifikaları, Sertifika Yöneticisi aracını kullanarak da görüntüleyebilir, dışarı aktarabilir, içeri aktarabilir ve silebilirsiniz.

### <a name="to-view-certificates-for-the-local-device"></a>Yerel cihaz için sertifikaları görüntülemek için

1. **Başlat** menüsünden **Çalıştır** ' ı seçin ve ardından *Certlm. msc*yazın.

    Yerel cihaz için Sertifika Yöneticisi aracı görünür.
  
2. Sertifikalarınızı görüntülemek için, sol bölmedeki **Sertifikalar-Yerel bilgisayar** altında, görüntülemek istediğiniz sertifika türü için dizini genişletin.

### <a name="to-view-certificates-for-the-current-user"></a>Geçerli kullanıcının sertifikalarını görüntülemek için

1. **Başlat** menüsünden **Çalıştır** ' ı seçin ve ardından *certmgr. msc*yazın.

    Geçerli Kullanıcı için Sertifika Yöneticisi aracı görünür.
  
2. Sertifikalarınızı görüntülemek için Sertifikalar ' ın altında, sol bölmedeki **Geçerli Kullanıcı** ' nın altında, görüntülemek istediğiniz sertifika türü için dizini genişletin.

## <a name="see-also"></a>Ayrıca bkz.

- [Sertifikalarla çalışma](working-with-certificates.md)
- [Nasıl yapılır: geliştirme sırasında kullanılmak üzere geçici sertifikalar oluşturma](how-to-create-temporary-certificates-for-use-during-development.md)
- [Nasıl yapılır: bir sertifikanın parmak izini alma](how-to-retrieve-the-thumbprint-of-a-certificate.md)
