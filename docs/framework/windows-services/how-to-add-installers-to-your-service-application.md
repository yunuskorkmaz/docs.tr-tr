---
title: 'Nasıl yapılır: Hizmet Uygulamasına Yükleyiciler Ekleme'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Service applications, deploying
- installation components, adding to services
- installers, adding to services
- Windows Service applications, adding installers
- services, adding installers
- ServiceInstaller class, adding installers to services
- ServiceProcessInstaller class, adding installers to services
ms.assetid: 8b698e9a-b88e-4f44-ae45-e0c5ea0ae5a8
author: ghogen
ms.openlocfilehash: af56e01c1c8c1e23bb80413ce6f52a5f6d467b4b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61914127"
---
# <a name="how-to-add-installers-to-your-service-application"></a>Nasıl yapılır: Hizmet Uygulamasına Yükleyiciler Ekleme
Visual Studio hizmet uygulamalarınızla ilişkili kaynakları yükleyebilmek için Yükleme bileşenleri ile birlikte gelir. Yükleme bileşenleri olarak yüklendiği ve Hizmet Denetim Yöneticisi hizmetinin var olduğunu bilmek istiyorum sistemdeki tek tek bir hizmeti kaydedin. Bir hizmet uygulaması ile çalışırken, Özellikler penceresinde otomatik olarak uygun yükleyicileri projenize eklemek için bağlantıyı seçebilirsiniz.  
  
> [!NOTE]
>  Hizmetiniz için özellik değerleri hizmet sınıfından yükleyici dosyasına kopyalanır. Özellik değerlerine göre hizmet sınıfı güncelleştirirseniz, bunlar otomatik olarak yükleyicide güncelleştirilmez.  
  
 Projenize yeni bir sınıf bir yükleyici eklediğinizde, (varsayılan olarak adlandırılan, `ProjectInstaller`) örneklerini uygun yükleme bileşenleri içinde oluşturulur ve Proje oluşturulur. Bu sınıf davranır tüm yükleme bileşenleri için merkezi bir nokta olarak projenize gerekir. Örneğin, ikinci bir hizmet uygulamanıza ekleyin ve Yükleyici Ekle bağlantısına tıklayın, ikinci bir yükleyici sınıfı oluşturulmaz; Bunun yerine, ikinci hizmeti için gerekli ek yükleme bileşeni varolan bir sınıfa eklenir.  
  
 Tüm özel hizmetlerinizin doğru bir biçimde yüklenmesi için yükleyicileri içinde kodlama yapmanız gerekmez. Ancak, bazen özel İşlevler'i yükleme işlemine eklemeniz gerekiyorsa yükleyicileri içeriğini değiştirmeniz gerekebilir.  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-add-installers-to-your-service-application"></a>Hizmet uygulamasına yükleyiciler ekleme  
  
1. İçinde **Çözüm Gezgini**, erişim **tasarım** görünümü için bir yükleme bileşeni eklemek istediğiniz hizmet.  
  
2. Hizmet seçmek için tasarımcının arka planını kendisi yerine herhangi bir içeriğini tıklayın.  
  
3. Odak, sağ tıklayın ve ardından Tasarımcısı ile **Yükleyici Ekle**.  
  
     Yeni bir sınıf `ProjectInstaller`ve iki yükleme bileşenleri <xref:System.ServiceProcess.ServiceProcessInstaller> ve <xref:System.ServiceProcess.ServiceInstaller>, hizmet kopyalanır için bileşenleri, proje ve özellik değerlerine eklenir.  
  
4. Tıklayın <xref:System.ServiceProcess.ServiceInstaller> bileşeni doğrulayın değerini <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> özelliği aynı değere ayarlanır <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> hizmet özelliği.  
  
5. Hizmetinizi kullanmaya nasıl belirlemek için tıklatın <xref:System.ServiceProcess.ServiceInstaller> bileşen ve ayarlanmış <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> özelliğini uygun değer.  
  
    |Değer|Sonuç|  
    |-----------|------------|  
    |<xref:System.ServiceProcess.ServiceStartMode.Manual>|Hizmeti el ile yükleme sonrasında başlatılması gerekir. Daha fazla bilgi için [nasıl yapılır: Hizmetleri başlatmak](../../../docs/framework/windows-services/how-to-start-services.md).|  
    |<xref:System.ServiceProcess.ServiceStartMode.Automatic>|Bilgisayar yeniden başlatıldığında hizmet kendi kendine başlar.|  
    |<xref:System.ServiceProcess.ServiceStartMode.Disabled>|Hizmet başlatılamıyor.|  
  
6. Hizmetinizi çalışacağı güvenlik bağlamı belirlemek için tıklatın <xref:System.ServiceProcess.ServiceProcessInstaller> bileşen ve uygun özellik değerlerini ayarlayın. Daha fazla bilgi için [nasıl yapılır: Hizmetler için güvenlik içeriği belirtme](../../../docs/framework/windows-services/how-to-specify-the-security-context-for-services.md).  
  
7. Özel işleme gerçekleştirmek ihtiyaç duyduğunuz herhangi bir yöntemi geçersiz kılın.  
  
8. Projenizdeki her bir ek hizmet için 1 ile 7 arasındaki adımları gerçekleştirin.  
  
    > [!NOTE]
    >  Projenizdeki her ek hizmet için ek bir eklemelisiniz <xref:System.ServiceProcess.ServiceInstaller> projenin bileşen `ProjectInstaller` sınıfı. <xref:System.ServiceProcess.ServiceProcessInstaller> Üç adımda eklediğiniz bileşen bireysel hizmet yükleyiciler projedeki tüm ile birlikte çalışır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Hizmeti Uygulamalarına Giriş](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
- [Nasıl yapılır: Hizmetleri Yükleme ve kaldırma](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)
- [Nasıl yapılır: Başlangıç Hizmetleri](../../../docs/framework/windows-services/how-to-start-services.md)
- [Nasıl yapılır: Hizmetler için güvenlik içeriği belirtme](../../../docs/framework/windows-services/how-to-specify-the-security-context-for-services.md)
