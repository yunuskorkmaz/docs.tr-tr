---
title: Genişletilmiş Koruma Kimlik Doğrulama için Beni Oku Örnek
ms.date: 03/30/2017
ms.assetid: 80bf2e97-398d-4db5-9040-d96478a2ccab
ms.openlocfilehash: 53592db03c88e673d529ef04f2fbc6e182897457
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59979128"
---
# <a name="readme-for-extended-protection-authentication-sample"></a>Genişletilmiş Koruma Kimlik Doğrulama için Beni Oku Örnek
Genişletilmiş koruma, bir saldırgan ("adam-in--middle") istemci kimlik bilgileri yakalar ve bunları istemcinin hedeflenen sunucusundaki güvenli kaynaklara erişmek için kullandığı adam-de-adam (MITM) saldırılarına karşı korumak için bir güvenlik girişimidir.  
  
 Daha fazla bilgi için [kimlik doğrulamasına genel bakış için genişletilmiş koruma](../../../../docs/framework/wcf/feature-details/extended-protection-for-authentication-overview.md).  
  
> [!NOTE]
>  Bu örnek yalnızca IIS üzerinde barındırıldığında çalışır. HTTPS desteklemediği için Visual Studio geliştirme sunucusu üzerinde çalışmaz.  
  
## <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1. IIS üzerinde Program Ekle/Kaldır makineden yükleme -> Windows özelliklerini.  
  
2. Windows kimlik doğrulamasını Windows özelliklerini aç: Internet Information Services World Wide Web -> hizmetler -> Güvenlik Windows kimlik doğrulaması ->.  
  
3. HTTP etkinleştirmesini Windows özelliklerini aç: Microsoft .NET Framework 3.5.1 -> Windows Communication Foundation HTTP etkinleştirme.  
  
4. İstemcinin sunucuyla güvenli bir kanal oluşturmak için bu örneği gerektirir ve bu nedenle, Internet Information Services (IIS) Yöneticisi'nden yüklenebilecek bir sunucu sertifikası varlığını gerektirir.  
  
    1.  Açık IIS Yöneticisi -> sunucu sertifikaları (sekmesinden özelliği Görünüm).  
  
    2.  Bu örnek sınama amacıyla bir otomatik olarak imzalanan sertifika oluşturabilirsiniz. (Internet Explorer'ı güvenli olmadığı hakkında sertifika istemek için istemiyorsanız, güvenilen kök sertifika yetkilisi depolarında yükleyebilirsiniz).  
  
5. Varsayılan Web sitesi için Eylemler bölmesine gidin. Düzenle düğmesine Site bağlamaları ->. Bir tür olarak HTTPS henüz varsa, bağlantı noktası numarası 443 ve Yukarıdaki adımda oluşturulan SSL sertifika atama ekleyin.  
  
6. Derleme hizmeti. Bu sanal dizini IIS içinde sizin için (post yapı eylemi proje özelliklerinde belirtilen) oluşturur ve barındırılan Web olması için bir hizmet için gerektiği şekilde dll, .svc ve yapılandırma dosyalarını kopyalar.  
  
7. IIS Yöneticisi'ni açın. Önceki adımda oluşturduğunuz sanal dizini (ExtendedProtection) sağ tıklayın ve uygulama Dönüştür'ı seçin.  
  
8. Kimlik doğrulama modülünü, bu sanal dizin için IIS Yöneticisi'nde açın ve Windows kimlik doğrulamasını etkinleştirin.  
  
9. Gelişmiş ayarları için Windows kimlik doğrulaması için bu sanal dizin açın ve aşağıdaki örnekte, her zaman ilgili ExtendedProtection ayarı ayarlandığından, gerekli ayarlayın.  
  
10. Hizmet URL'sini bir tarayıcı penceresinden erişerek test edebilirsiniz. Bu URL'yi bir çapraz makineden erişmek istiyorsanız, güvenlik duvarı tüm gelen HTTP ve HTTPS bağlantıları için açık olduğundan emin olun.  
  
11. İstemci yapılandırma dosyasını açın ve sağlamak için tam makine adı \<istemci >- \<uç noktası >-<< full_machine_name >> değiştirerek, adresi özniteliği.  
  
12. İstemciyi çalıştırın. İstemci hizmete güvenli bir kanal oluşturma ve arka planda altında genişletilmiş koruma kullanarak iletişim kurar.
