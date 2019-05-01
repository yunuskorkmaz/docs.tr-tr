---
title: 'Nasıl yapılır: MMC ek bileşeni ile sertifikaları görüntüleme'
ms.date: 02/25/2019
helpviewer_keywords:
- certificates [WCF], viewing with the MMC snap-in
ms.assetid: 2b8782aa-ebb4-4ee7-974b-90299e356dc5
ms.openlocfilehash: 69f79b64250ff46524e7b4720d13351774875a3f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61972737"
---
# <a name="how-to-view-certificates-with-the-mmc-snap-in"></a>Nasıl yapılır: MMC ek bileşeni ile sertifikaları görüntüleme
Güvenli istemci veya hizmet oluştururken kullanabileceğiniz bir [sertifika](working-with-certificates.md) kimlik bilgisi olarak. Örneğin, ortak bir kimlik bilgisi türü ile oluşturduğunuz X.509 sertifikası olan <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A?displayProperty=nameWithType> yöntemi. 

Microsoft Yönetim Konsolu (MMC) ile Windows sistemlerinde inceleyebilirsiniz sertifika depolarını üç farklı türü vardır:

- Yerel bilgisayar: Yerel cihaz ve cihazdaki tüm kullanıcılar için küresel deposudur.

- Geçerli kullanıcı: Cihazdaki geçerli kullanıcı hesabı için yerel deposudur.

- Hizmet hesabı: Belirli bir hizmete cihazdaki yerel deposudur.

## <a name="view-certificates-in-the-mmc-snap-in"></a>MMC ek bileşeninde sertifikaları görüntüle 

Aşağıdaki yordam, uygun bir sertifika bulmak için yerel cihazınıza depoları incelemek nasıl göstermektedir: 
  
1. Seçin **çalıştırma** gelen **Başlat** menüsünde ve enter *mmc*. 

    MMC açılır. 
  
2. Gelen **dosya** menüsünde **Ekle/Kaldır ek bileşen içinde**. 
    
    **Ek bileşenler Ekle / Kaldır** penceresi görüntülenir.
  
3. Gelen **kullanılabilir ek bileşenler** listesinde **sertifikaları**, ardından **Ekle**.  

    ![Sertifika ek bileşenini Ekle](./media/mmc-add-certificate-snap-in.png)
  
4. İçinde **Sertifikalar ek bileşenini** penceresinde **bilgisayar hesabı**ve ardından **sonraki**. 
  
    İsteğe bağlı olarak seçebileceğiniz **kullanıcı hesabım** geçerli kullanıcı için ya da **hizmet hesabı** belirli bir hizmet için. 

    > [!NOTE]
    > Bir yöneticinin Cihazınızda siz değilseniz, yalnızca kullanıcı hesabınız için sertifikaları yönetebilir.
  
5. İçinde **Bilgisayar Seç** penceresinde bırakın **yerel bilgisayar** seçili ve ardından **son**.  
  
6. İçinde **Ekle veya Kaldır ek bileşenini** penceresinde **Tamam**.  
  
    ![Sertifika ek bileşenini Ekle](./media/mmc-certificate-snap-in-selected.png)

7. İsteğe bağlı: Gelen **dosya** menüsünde **Kaydet** veya **Kaydet** daha sonra kullanmak için MMC konsolu dosyasını kaydetmek için.  

8. MMC ek bileşeninde, sertifikaları görüntülemek için seçin **konsol kökü** sol bölmede genişletin **sertifikalar (yerel bilgisayar)**.

    Her sertifika türünün dizinlerinin listesi görüntülenir. Her sertifika dizinden görüntülemek, dışarı aktarma, alma ve sertifikalarını silin.

## <a name="view-certificates-with-the-certificate-manager-tool"></a>Sertifika Yöneticisi Aracı ile sertifikaları görüntüleme

Da görüntüleyebilir, dışarı aktarma almak ve Sertifika Yöneticisi aracı kullanarak sertifikaları silin.

### <a name="to-view-certificates-for-the-local-device"></a>Yerel cihaz sertifikalarını görüntülemek için

1. Seçin **çalıştırma** gelen **Başlat** menüsünde ve enter *certlm.msc*. 

    Sertifika Yöneticisi Aracı için yerel cihaz görünür. 
  
2. Sertifikalarınızı, altında görüntülemek için **sertifikalar - yerel bilgisayar** sol bölmede, görüntülemek istediğiniz sertifika türü için dizine genişletin.

### <a name="to-view-certificates-for-the-current-user"></a>Geçerli kullanıcının sertifikalarını görüntülemek için

1. Seçin **çalıştırma** gelen **Başlat** menüsünde ve enter *certmgr.msc*. 

    Geçerli kullanıcı için Sertifika Yöneticisi Aracı görünür. 
  
2. Sertifikalarınızı, altında görüntülemek için **Sertifikalar - Geçerli kullanıcı** sol bölmede, görüntülemek istediğiniz sertifika türü için dizine genişletin.

## <a name="see-also"></a>Ayrıca bkz.

- [Sertifikalarla çalışma](working-with-certificates.md)
- [Nasıl yapılır: Geliştirme sırasında kullanmak için geçici sertifikalar oluşturma](how-to-create-temporary-certificates-for-use-during-development.md)
- [Nasıl yapılır: Bir sertifikanın parmak izini alma](how-to-retrieve-the-thumbprint-of-a-certificate.md)
