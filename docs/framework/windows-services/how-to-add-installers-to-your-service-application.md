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
ms.openlocfilehash: 335bff660e401d8fbaf531f1c1f3ccc166d1c70a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69952517"
---
# <a name="how-to-add-installers-to-your-service-application"></a>Nasıl yapılır: Hizmet Uygulamasına Yükleyiciler Ekleme
Visual Studio, hizmet uygulamalarınızla ilişkili kaynakları yükleyebilen yükleme bileşenlerini sevk eder. Yükleme bileşenleri, yüklenmekte olan sisteme tek bir hizmeti kaydeder ve hizmetler Denetim Yöneticisi 'nin hizmetin var olduğunu bilmesini sağlar. Bir hizmet uygulamasıyla çalışırken, projenize uygun yükleyicileri otomatik olarak eklemek için Özellikler penceresi bir bağlantı seçebilirsiniz.  
  
> [!NOTE]
> Hizmetinizin özellik değerleri, hizmet sınıfından yükleyici sınıfına kopyalanır. Hizmet sınıfındaki özellik değerlerini güncelleştirirseniz, bunlar yükleyicide otomatik olarak güncellenmez.  
  
 Projenize bir yükleyici eklediğinizde, projede yeni bir sınıf (varsayılan olarak, olarak adlandırılır `ProjectInstaller`) oluşturulur ve ilgili yükleme bileşenlerinin örnekleri içinde oluşturulur. Bu sınıf, projenizin ihtiyaç duyacağı tüm yükleme bileşenlerine yönelik bir merkezi nokta görevi görür. Örneğin, uygulamanıza ikinci bir hizmet ekler ve Yükleyici Ekle bağlantısına tıklarsanız ikinci bir yükleyici sınıfı oluşturulmaz; Bunun yerine, ikinci hizmet için gereken ek yükleme bileşeni mevcut sınıfa eklenir.  
  
 Hizmetlerinizin doğru şekilde yüklenmesini sağlamak için yükleyicilerin içinde herhangi bir özel kodlama yapmanız gerekmez. Ancak, yükleme işlemine özel işlevsellik eklemeniz gerekiyorsa, bazen yükleyicilerin içeriğini değiştirmeniz gerekebilir.  
  
> [!NOTE]
> Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için bkz. [Visual STUDIO IDE 'Yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-add-installers-to-your-service-application"></a>Hizmet uygulamanıza yükleyiciler eklemek için  
  
1. **Çözüm Gezgini**, yükleme bileşeni eklemek Istediğiniz hizmetin **Tasarım** görünümünde erişin.  
  
2. Tüm içerikleri yerine hizmetin kendisini seçmek için tasarımcının arka planına tıklayın.  
  
3. Tasarımcı odaklanarak, öğesine sağ tıklayın ve ardından **Yükleyici Ekle**' ye tıklayın.  
  
     Yeni bir sınıf, `ProjectInstaller`ve iki yükleme <xref:System.ServiceProcess.ServiceProcessInstaller> bileşeni ve <xref:System.ServiceProcess.ServiceInstaller>projenize eklenir ve hizmetin özellik değerleri bileşenlere kopyalanır.  
  
4. Bileşene tıklayın ve <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> özelliğin değerinin hizmetin kendisindeki <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> özellik ile aynı değere ayarlandığını doğrulayın. <xref:System.ServiceProcess.ServiceInstaller>  
  
5. Hizmetinizin nasıl başlatılaceğini öğrenmek için <xref:System.ServiceProcess.ServiceInstaller> bileşene tıklayın ve <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> özelliği uygun değere ayarlayın.  
  
    |Değer|Sonuç|  
    |-----------|------------|  
    |<xref:System.ServiceProcess.ServiceStartMode.Manual>|Hizmetin, yüklemeden sonra el ile başlatılması gerekir. Daha fazla bilgi için [nasıl yapılır: Hizmetleri](../../../docs/framework/windows-services/how-to-start-services.md)başlatın.|  
    |<xref:System.ServiceProcess.ServiceStartMode.Automatic>|Bilgisayar her yeniden başlatıldığında hizmet kendisi tarafından başlatılır.|  
    |<xref:System.ServiceProcess.ServiceStartMode.Disabled>|Hizmet başlatılamıyor.|  
  
6. Hizmetinizin çalışacağı güvenlik bağlamını öğrenmek için <xref:System.ServiceProcess.ServiceProcessInstaller> bileşene tıklayın ve uygun özellik değerlerini ayarlayın. Daha fazla bilgi için [nasıl yapılır: Hizmetler](../../../docs/framework/windows-services/how-to-specify-the-security-context-for-services.md)için güvenlik bağlamını belirtin.  
  
7. Özel işlem gerçekleştirmeniz gereken tüm yöntemleri geçersiz kılın.  
  
8. Projenizdeki her bir ek hizmet için 1 ile 7 arasındaki adımları gerçekleştirin.  
  
    > [!NOTE]
    > Projenizdeki her bir ek hizmet için, <xref:System.ServiceProcess.ServiceInstaller> `ProjectInstaller` projenin sınıfına ek bir bileşen eklemeniz gerekir. Adım 3 ' te eklenen Bileşen,projedekibireyselhizmetyükleyicilerinintümüilebirliktegeçerlidir.<xref:System.ServiceProcess.ServiceProcessInstaller>  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Hizmeti Uygulamalarına Giriş](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
- [Nasıl yapılır: Hizmetleri yükleme ve kaldırma](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)
- [Nasıl yapılır: Hizmetleri Başlat](../../../docs/framework/windows-services/how-to-start-services.md)
- [Nasıl yapılır: Hizmetler için güvenlik bağlamını belirtin](../../../docs/framework/windows-services/how-to-specify-the-security-context-for-services.md)
