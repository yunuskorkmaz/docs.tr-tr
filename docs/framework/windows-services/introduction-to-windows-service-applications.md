---
title: "Windows Hizmet Uygulamalarına Giriş"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ServiceController
helpviewer_keywords:
- Windows Service applications, deploying
- OnStop method
- OnPause method
- services, about services
- Service class, Windows Service applications
- framework services, creating services
- ServiceController components, about Windows services
- Win32OwnProcess service type
- services, lifetime
- OnContinue method
- Windows Service applications, about Windows Service applications
- services, states
- service states
- WaitForStatus method
- Win32ShareProcess service type
- Windows Service applications, lifetime
ms.assetid: 1b1b5e67-3ff3-40c0-8154-322cfd6ef0ae
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 613107a13820ad71b854dcba93f21c41f2a5fa5f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="introduction-to-windows-service-applications"></a>Windows Hizmet Uygulamalarına Giriş
Microsoft Windows Hizmetleri, önceden NT hizmeti olarak bilinen kendi Windows oturumlarında çalışan uzun süre çalışan yürütülebilir uygulamalar oluşturmanıza olanak sağlar. Bilgisayar önyükleme yaptığında, bu hizmetler otomatik olarak yeniden başlatılabilir duraklatıldı ve yeniden başlatılabilir ve herhangi bir kullanıcı arabirimi gösterme. Bu özellikler Hizmetleri sunucusunda veya aynı bilgisayarda çalışan diğer kullanıcılarla etkilemediğinden uzun süre çalışan işlevselliğe gereksinim duyduğunuzda kullanım için ideal hale getirir. Oturum açmış olan kullanıcının farklı belirli bir kullanıcı hesabı veya varsayılan bilgisayar hesabının güvenlik bağlamı hizmetleri de çalıştırabilirsiniz. Hizmetleri ve Windows oturumları hakkında daha fazla bilgi için Windows SDK belgelerine bakın.  
  
 Hizmetleri hizmeti olarak yüklenen bir uygulama oluşturarak kolayca oluşturabilirsiniz. Örneğin, performans sayacı verilerini izleme ve eşik değerlerine tepki istediğinizi varsayalım. Performans sayacı verilerini dinleyen bir Windows hizmet uygulaması yazma, uygulamayı dağıtmak ve verileri toplamaya ve çözümlemeye başlayın.  
  
 Hizmetinizi Microsoft Visual Studio projesi olarak oluşturun, hangi komutları denetleyen kodu tanımlayarak hizmeti ve bu komutları alındığında hangi eylemlerin gerçekleştirilmesi gönderilebilir. Bir hizmete gönderilen komutları başlatma, duraklatma, sürdürme ve hizmetin durdurulması içerir; Ayrıca özel komutlar yürütebilir.  
  
 Oluşturun ve uygulamayı derlediğinizde sonra InstallUtil.exe komut satırı yardımcı programını çalıştırarak ve yolun hizmetin yürütülebilir dosyaya geçirerek yükleyebilirsiniz. Daha sonra **Hizmet Denetim Yöneticisi** başlatmak, durdurmak, duraklatma, sürdürme ve hizmetinizi yapılandırmak için. Ayrıca bu aynı görevlerin çoğunu gerçekleştirebilirsiniz **Hizmetleri** düğümünde **Sunucu Gezgini** veya kullanarak <xref:System.ServiceProcess.ServiceController> sınıfı.  
  
## <a name="service-applications-vs-other-visual-studio-applications"></a>Hizmet uygulamaları vs. Diğer Visual Studio uygulamaları  
 Hizmet uygulamaları işlevinden farklı çeşitli şekillerde diğer birçok proje türleri:  
  
-   Proje anlamlı bir şekilde çalışabilmesi için önce bir hizmet uygulaması projesi oluşturur derlenmiş yürütülebilir dosya sunucusuna yüklenmelidir. Hata ayıklama veya F5 veya F11 tuşuna basarak bir hizmet uygulaması çalıştırın; bir hizmet veya adımı'nı, hemen kodunda çalıştıramazsınız. Bunun yerine, yüklemeniz ve hizmetinizi başlatın ve sonra hizmetin işlemi bir hata ayıklayıcısı eklemeniz gerekir. Daha fazla bilgi için bkz: [nasıl yapılır: Windows hizmet uygulamalarında hata ayıklama](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md).  
  
-   Bazı projeleri türlerinin aksine, hizmet uygulamaları için Yükleme bileşenleri oluşturmanız gerekir. Yükleme bileşenleri yükleyin ve sunucunun hizmet kaydı ve Windows ile hizmetiniz için bir giriş oluşturun **Hizmet Denetim Yöneticisi**. Daha fazla bilgi için bkz: [nasıl yapılır: Hizmet uygulamanız için yükleyiciler ekleme](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).  
  
-   `Main` Hizmet uygulamanızın projenize Hizmetleri için Çalıştır komutunu vermelidir yöntemi içerir. `Run` Metodunun hizmetlerine **Hizmet Denetim Yöneticisi** uygun sunucuda. Kullanırsanız **Windows Hizmetleri** proje şablonu, bu yöntem yazılmış sizin için otomatik olarak. Bir hizmeti yükleme hizmet başlangıç olarak aynı anlama olmadığını unutmayın. "Hizmet ömrü" aşağıdaki daha fazla bilgi için bkz.  
  
-   Windows hizmet uygulamaları, farklı bir pencere istasyonunda oturum açmış kullanıcının etkileşimli istasyonundan çalıştırın. Pencere istasyonu bir pano, bir grup masaüstü ve genel atom kümesi içeren güvenli bir nesnedir. Windows hizmeti istasyon etkileşimli bir istasyon olmadığı için iletişim kutularını gelen bir Windows hizmeti uygulaması değil görürler ve programınızın yanıt vermemesine neden olabilir içinde oluşturulur. Benzer şekilde, hata iletileri Windows olay günlüğüne yerine kullanıcı arabiriminde gerçekleşti.  
  
     .NET Framework tarafından desteklenen Windows hizmet sınıfları etkileşimli kanallarla diğer bir deyişle, oturum açmış kullanıcı etkileşimi desteklemez. .NET Framework istasyonları ve masaüstlerini temsil eden sınıflar da içermez. Windows hizmetinizin diğer istasyonlar ile etkileşimde olması durumunda, yönetilmeyen Windows API'sine erişmeniz gerekir. Daha fazla bilgi için Windows SDK belgelerine bakın.  
  
     Hizmeti kullanıcı ya da diğer istasyonlar ile oturum açmış kullanıcı yok veya kullanıcının masaüstü nesneleri beklenmeyen bir dizi olması gibi senaryoları beklenmediğini dahil etmek için dikkatle tasarlanmalıdır Windows etkileşimi. Bazı durumlarda, kullanıcı denetimi altında çalışan bir Windows uygulaması yazmak daha uygun olabilir.  
  
-   Windows hizmet uygulamaları, kendi güvenlik bağlamında çalıştırın ve bunlar yüklendiği Windows bilgisayara kullanıcı oturum açmadan önce başlatılır. Hizmet içinde çalıştırmak için hangi kullanıcı hesabının dikkatle planlamanız gereken; Sistem hesabı altında çalışan bir hizmete daha fazla izinler ve bir kullanıcı hesabından ayrıcalıklara sahiptir.  
  
## <a name="service-lifetime"></a>Hizmet ömrü  
 Bir hizmet birçok dahili durumdan ömrü gider. İlk olarak, hizmet üzerinde çalışacağı sisteme yüklenir. Bu işlem hizmet projesi için yükleyicileri yürütür ve hizmete yükler **Hizmet Denetim Yöneticisi** bu bilgisayar için. **Hizmet Denetim Yöneticisi** hizmetleri yönetmek için Windows tarafından sağlanan Merkezi hizmet programıdır.  
  
 Hizmeti yüklendikten sonra başlatılmalıdır. Hizmet başlatma çalışmasını başlamasını sağlar. Bir hizmetinden başlatabilirsiniz **Hizmet Denetim Yöneticisi**, gelen **Sunucu Gezgini**, veya çağırarak koddan <xref:System.ServiceProcess.ServiceController.Start%2A> yöntemi. <xref:System.ServiceProcess.ServiceController.Start%2A> Yöntemi uygulamanın işleme geçirir <xref:System.ServiceProcess.ServiceBase.OnStart%2A> yöntemi ve orada tanımladığınız herhangi bir kod işler.  
  
 Çalışan bir hizmeti süresiz olarak bunu da durduruldu veya duraklatıldı kadar veya bilgisayar kapatılana kadar bu durumda bulunabilir. Bir hizmet üç temel durumdan birinde bulunabilir: <xref:System.ServiceProcess.ServiceControllerStatus.Running>, <xref:System.ServiceProcess.ServiceControllerStatus.Paused>, veya <xref:System.ServiceProcess.ServiceControllerStatus.Stopped>. Hizmetin bekleyen bir komut durumunu rapor edebilirsiniz: <xref:System.ServiceProcess.ServiceControllerStatus.ContinuePending>, <xref:System.ServiceProcess.ServiceControllerStatus.PausePending>, <xref:System.ServiceProcess.ServiceControllerStatus.StartPending>, veya <xref:System.ServiceProcess.ServiceControllerStatus.StopPending>. Bu durumlar, komut, çalışan bir hizmeti duraklatmak için bir komut gibi verilen ancak henüz yapıldığını değil gösterir. Sorgulayabileceğiniz <xref:System.ServiceProcess.ServiceController.Status%2A> ne bir hizmettir durumu belirlemek veya kullanmak için <xref:System.ServiceProcess.ServiceController.WaitForStatus%2A> bu durumların herhangi biri, bir eyleme devam etmek için oluşur.  
  
 Duraklatmak, durdurmak veya bir hizmetinden devam ettirmek **Hizmet Denetim Yöneticisi**, gelen **Sunucu Gezgini**, veya kodda yöntemleri çağırma. Bu eylemlerin her biri bir ilişkili yordama hizmetinde çağırabilirsiniz (<xref:System.ServiceProcess.ServiceBase.OnStop%2A>, <xref:System.ServiceProcess.ServiceBase.OnPause%2A>, veya <xref:System.ServiceProcess.ServiceBase.OnContinue%2A>), hizmet durumu değiştiğinde gerçekleştirilecek ek işleme tanımlayabileceğiniz içinde.  
  
## <a name="types-of-services"></a>Hizmet türleri  
 Hizmetleri .NET Framework kullanarak Visual Studio'da oluşturabileceğiniz iki tür vardır. Bir işlemde yalnızca hizmet Hizmetleri türü atanmıştır <xref:System.ServiceProcess.ServiceType.Win32OwnProcess>. Bir işlem başka bir hizmetle paylaşan Hizmetleri türü atanmıştır <xref:System.ServiceProcess.ServiceType.Win32ShareProcess>. Hizmet türü sorgulayarak alabilirsiniz <xref:System.ServiceProcess.ServiceController.ServiceType%2A> özelliği.  
  
 Visual Studio'da oluşturulmayan varolan Hizmetleri sorgu diğer hizmet türleri bazen görebilirsiniz. Bunlar hakkında daha fazla bilgi için bkz: <xref:System.ServiceProcess.ServiceType>.  
  
## <a name="services-and-the-servicecontroller-component"></a>Hizmetler ve ServiceController Bileşeni  
 <xref:System.ServiceProcess.ServiceController> Bileşenidir yüklenen bir hizmete bağlanmak ve durumu işlemek için kullanılan; kullanarak bir <xref:System.ServiceProcess.ServiceController> bileşen, başlatmak ve bir hizmeti durdurmak, duraklatmak, devam ettirebilir ve bir hizmete özel komut gönderme. Ancak, kullanmak gerekmez bir <xref:System.ServiceProcess.ServiceController> bir hizmet uygulaması oluşturduğunuzda bileşeni. Aslında, çoğu durumda, <xref:System.ServiceProcess.ServiceController> bileşen hizmetinizi tanımlayan Windows hizmet uygulamasından farklı bir uygulamada var.  
  
 Daha fazla bilgi için bkz. <xref:System.ServiceProcess.ServiceController>.  
  
## <a name="requirements"></a>Gereksinimler  
  
-   Hizmetleri oluşturulan, içinde bir **Windows hizmeti** uygulama veya yapılandırıldığında bir .exe dosyası oluşturur ve devraldığı başka bir ve .NET Framework etkinleştirilmiş projesi <xref:System.ServiceProcess.ServiceBase> sınıfı.  
  
-   Windows Hizmetleri içeren projeler proje ve Hizmetleri için Yükleme bileşenleri olması gerekir. Bu gelen kolayca gerçekleştirilebilir **özellikleri** penceresi. Daha fazla bilgi için bkz: [nasıl yapılır: Hizmet uygulamanız için yükleyiciler ekleme](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Hizmeti Uygulamaları](../../../docs/framework/windows-services/index.md)  
 [Hizmet Uygulaması Programlama Mimarisi](../../../docs/framework/windows-services/service-application-programming-architecture.md)  
 [Nasıl Yapılır: Windows Hizmetleri Oluşturma](../../../docs/framework/windows-services/how-to-create-windows-services.md)  
 [Nasıl Yapılır: Hizmetleri Yükleme ve Kaldırma](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)  
 [Nasıl Yapılır: Hizmetleri Başlatma](../../../docs/framework/windows-services/how-to-start-services.md)  
 [Nasıl Yapılır: Windows Hizmet Uygulamalarında Hata Ayıklama](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md)  
 [İzlenecek Yol: Bileşen Tasarımcısında Windows Hizmeti Uygulaması Oluşturma](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)  
 [Nasıl Yapılır: Hizmet Uygulamasına Yükleyiciler Ekleme](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)
