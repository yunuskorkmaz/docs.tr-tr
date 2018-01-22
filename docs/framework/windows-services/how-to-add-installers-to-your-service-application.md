---
title: "Nasıl Yapılır: Hizmet Uygulamasına Yükleyiciler Ekleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Service applications, deploying
- installation components, adding to services
- installers, adding to services
- Windows Service applications, adding installers
- services, adding installers
- ServiceInstaller class, adding installers to services
- ServiceProcessInstaller class, adding installers to services
ms.assetid: 8b698e9a-b88e-4f44-ae45-e0c5ea0ae5a8
caps.latest.revision: "14"
author: ghogen
ms.author: ghogen
manager: douge
ms.workload: dotnet
ms.openlocfilehash: 15487d4311f896aa09c1c7712292058086a49b50
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-add-installers-to-your-service-application"></a>Nasıl Yapılır: Hizmet Uygulamasına Yükleyiciler Ekleme
Visual Studio hizmet uygulamalarınızla ilişkili kaynakları yükleyebilirsiniz Yükleme bileşenleri gelir. Yükleme bileşenleri bireysel bir hizmet olarak yüklendiği ve Hizmet Denetim Yöneticisi'nin hizmetinin var olduğunu bilmek istiyorum sistemdeki kaydedin. Bir hizmet uygulaması ile çalışırken, bağlantı otomatik olarak uygun yükleyicileri projenize eklemek için Özellikler penceresini seçebilirsiniz.  
  
> [!NOTE]
>  Hizmetiniz için özellik değerleri hizmet sınıfından yükleyici sınıfa kopyalanır. Hizmet sınıfı özellik değerlerini güncelleştirirseniz, bunlar otomatik olarak yükleyicisinde güncelleştirilmez.  
  
 Projenize yeni bir sınıf bir yükleyici eklediğinizde (varsayılan olarak adlandırılan, `ProjectInstaller`) proje ve bileşenleri içinde oluşturulur uygun yükleme örnekleri oluşturulur. Bu sınıf davranır tüm yükleme bileşenleri için merkezi bir nokta olarak projenizi gerekir. Örneğin, ikinci bir hizmeti uygulamanıza ekleyin ve Yükleyici Ekle bağlantısına tıklayın, ikinci bir yükleyici sınıfı oluşturulmaz; Bunun yerine, ikinci hizmeti için gerekli ek yükleme bileşen varolan bir sınıfa eklenir.  
  
 Hizmetlerinizin düzgün yüklenmesi yapmak için yükleyiciler içinde özel hiçbir kodlama yapmak gerekmez. Ancak, bazen yükleme işlemine özel işlevsellik eklemeniz gerekiyorsa yükleyicileri içeriğini değiştirmeniz gerekebilir.  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-add-installers-to-your-service-application"></a>Hizmet uygulamasına yükleyiciler eklemek için  
  
1.  İçinde **Çözüm Gezgini**, erişim **tasarım** bir yükleme bileşeni eklemek istediğiniz hizmet için görünümü.  
  
2.  Hizmet seçmek için tasarlayıcı arka planını kendisi yerine İçeriklerinden biri'ı tıklatın.  
  
3.  Odak, sağ tıklatın ve ardından Tasarımcısı ile **Yükleyici Ekle**.  
  
     Yeni bir sınıf `ProjectInstaller`ve iki yükleme bileşenleri <xref:System.ServiceProcess.ServiceProcessInstaller> ve <xref:System.ServiceProcess.ServiceInstaller>, hizmet kopyalanır için bileşenlere, proje ve özellik değerleri için eklenir.  
  
4.  ' I tıklatın <xref:System.ServiceProcess.ServiceInstaller> bileşen doğrulayın değerini <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> özelliği aynı değere ayarlanmış <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> hizmeti özelliği.  
  
5.  Hizmetinizi çalışmaya nasıl belirlemek için tıklatın <xref:System.ServiceProcess.ServiceInstaller> bileşen ve ayarlanmış <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> uygun değere özelliği.  
  
    |Değer|Sonuç|  
    |-----------|------------|  
    |<xref:System.ServiceProcess.ServiceStartMode.Manual>|Hizmeti yüklendikten sonra el ile başlatılması gerekir. Daha fazla bilgi için bkz: [nasıl yapılır: Hizmetleri başlatma](../../../docs/framework/windows-services/how-to-start-services.md).|  
    |<xref:System.ServiceProcess.ServiceStartMode.Automatic>|Bilgisayar yeniden başlatıldığında hizmet kendiliğinden başlar.|  
    |<xref:System.ServiceProcess.ServiceStartMode.Disabled>|Hizmet başlatılamıyor.|  
  
6.  Hizmetinizin çalışacağı güvenlik bağlamı belirlemek için tıklatın <xref:System.ServiceProcess.ServiceProcessInstaller> bileşeni ve uygun özellik değerlerini ayarlayın. Daha fazla bilgi için bkz: [nasıl yapılır: Hizmetleri için güvenlik bağlamı belirtin](../../../docs/framework/windows-services/how-to-specify-the-security-context-for-services.md).  
  
7.  Özel işleme gerçekleştirmek gereken yöntemleri geçersiz kılar.  
  
8.  Projenizdeki ek her hizmet için 1 ile 7 arasındaki adımları gerçekleştirin.  
  
    > [!NOTE]
    >  Projenizdeki her ek hizmet için ek bir eklemelisiniz <xref:System.ServiceProcess.ServiceInstaller> projenin bileşen `ProjectInstaller` sınıfı. <xref:System.ServiceProcess.ServiceProcessInstaller> Üç adımda eklenen bileşeni, bireysel hizmet yükleyicileri projedeki tüm çalışır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Hizmeti Uygulamalarına Giriş](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [Nasıl Yapılır: Hizmetleri Yükleme ve Kaldırma](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)  
 [Nasıl Yapılır: Hizmetleri Başlatma](../../../docs/framework/windows-services/how-to-start-services.md)  
 [Nasıl Yapılır: Hizmetler için Güvenlik İçeriği Belirtme](../../../docs/framework/windows-services/how-to-specify-the-security-context-for-services.md)
