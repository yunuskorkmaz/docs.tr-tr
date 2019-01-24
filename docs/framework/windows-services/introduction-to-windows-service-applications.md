---
title: Windows Hizmet Uygulamalarına Giriş
ms.date: 03/30/2017
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
author: ghogen
ms.openlocfilehash: b26186ccf4a773297db89026797e89f194db2aa4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54614426"
---
# <a name="introduction-to-windows-service-applications"></a>Windows Hizmet Uygulamalarına Giriş
Eski adıyla NT Hizmetleri olarak bilinen Microsoft Windows Hizmetleri kendi Windows oturumlarında çalışan uzun süreli yürütülebilir uygulamalar oluşturmanıza olanak sağlar. Bu hizmetler, bilgisayar önyükleme yaptığında, otomatik olarak başlatılabilir duraklatılabilir ve yeniden başlatılabilir ve herhangi bir kullanıcı arabirimi gösterme. Bu özellikler Hizmetleri sunucusunda veya aynı bilgisayarda çalışan diğer kullanıcılarla engellemeyen uzun süreli işlevselliğe gereksinim duyduğunuzda kullanım için ideal hale getirir. Ayrıca, hizmetleri veya varsayılan bilgisayar hesabından oturum açan kullanıcıdan farklı bir belirli kullanıcı hesabının güvenlik bağlamında da çalıştırabilirsiniz. Hizmetleri ve Windows oturumları hakkında daha fazla bilgi için Windows SDK belgelerine bakın.  
  
 Hizmetleri, hizmet olarak yüklenen bir uygulama oluşturarak kolayca oluşturabilirsiniz. Örneğin, performans sayacını izlemeyi ve eşik değerlerine tepki vermeyi istediğinizi varsayın. Performans sayacı verilerini dinleyen bir Windows hizmeti uygulaması yazabilirsiniz, uygulamayı dağıtmak ve verileri toplamaya ve çözümlemeye başlayın.  
  
 Hizmetiniz bir Microsoft Visual Studio projesi olarak oluşturduğunuz hangi komutları denetleyen kodu tanımlayarak hizmeti ve bu komutlar alındığında hangi eylemlerin yapılması gerektiğini gönderilebilir. Bir hizmete gönderilebilen komutlar, başlatma, duraklatma, sürdürme ve hizmetin durdurulması içerir. özel komutlar da yürütebilirsiniz.  
  
 Uygulaması oluşturmayı ve sonra komut satırı yardımcı programını InstallUtil.exe ve hizmetin yürütülebilir dosyaya yolunu geçirerek yükleyebilirsiniz. Ardından **Hizmet Denetim Yöneticisi** Başlat, Durdur, duraklatma, sürdürme ve hizmetinizi yapılandırmak için. Ayrıca bu görevlerin çoğunu gerçekleştirebilirsiniz **Hizmetleri** düğümünde **Sunucu Gezgini** kullanarak veya <xref:System.ServiceProcess.ServiceController> sınıfı.  
  
## <a name="service-applications-vs-other-visual-studio-applications"></a>Hizmet uygulamaları vs. Diğer Visual Studio uygulamalarını  
 Hizmet uygulamaları işlevinden farklı çeşitli şekillerde birçok diğer proje türleri:  
  
-   Projenin anlamlı bir şekilde çalışabilmesi için önce bir hizmet uygulama projesinin oluşturduğu derlenmiş yürütülebilir dosya sunucuya yüklenmelidir. Hata ayıklama yapılamıyor veya F5 veya F11 tuşuna basarak bir hizmet uygulaması çalıştırın; kodunda bir hizmet veya adımı hemen çalıştıramazsınız. Bunun yerine, yüklemeniz gerekir ve hizmetinizi başlatın ve ardından hizmetin işlemine bir hata ayıklayıcı ekleyin. Daha fazla bilgi için [nasıl yapılır: Windows hizmet uygulamalarında hata ayıklama](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md).  
  
-   Bazı proje türlerinden farklı olarak, hizmet uygulamaları için Yükleme bileşenleri oluşturmanız gerekir. Yükleme bileşenleri yüklemek ve sunucunun hizmet kaydı ve Windows ile hizmetiniz için bir giriş oluşturmak **Hizmet Denetim Yöneticisi**. Daha fazla bilgi için [nasıl yapılır: Hizmet uygulamasına yükleyiciler ekleme](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).  
  
-   `Main` Hizmet uygulamanızı, projenize hizmetler için Çalıştır komutunu vermelidir yöntemi içerir. `Run` Metodunun hizmetlerine **Hizmet Denetim Yöneticisi** uygun sunucuda. Kullanırsanız **Windows Hizmetleri** proje şablonu, bu yöntem yazılmış sizin için otomatik olarak. Hizmet yüklemenin hizmet başlatmayla aynı şey olmadığını unutmayın. "Hizmet ömrü" aşağıda daha fazla bilgi için bkz.  
  
-   Windows hizmet uygulamaları, farklı bir iş istasyonunda oturum açmış kullanıcının etkileşimli istasyonundan çalışır. Pencere istasyonu bir pano, genel Atomlar kümesi ve bir masaüstü nesne grubu içeren güvenli bir nesnedir. Windows hizmetinin istasyonu etkileşimli bir istasyon olmadığı için iletişim kutularını gelen bir Windows hizmeti uygulaması görülmeyecektir ve programınızın yanıt vermeyi durdurmasına neden olabilir içinde oluşturulur. Benzer şekilde, hata iletileri Windows olay günlüğüne yerine kullanıcı arabiriminde oluşturulmak.  
  
     .NET Framework tarafından desteklenen Windows hizmet sınıfları etkileşimli kanallarla etkileşimi, diğer bir deyişle, oturum açan kullanıcının desteklemez. .NET Framework, aynı zamanda istasyonları ve masaüstlerini temsil eden sınıfları içermez. Windows hizmetinizin diğer istasyonlar ile etkileşmesi şartsa, yönetilmeyen Windows API'sine erişmeniz gerekecektir. Daha fazla bilgi için Windows SDK belgelerine bakın.  
  
     Windows hizmetinin kullanıcı ya da diğer istasyonlar ile oturum açan hiçbir kullanıcı ya da kullanıcının beklenmedik bir masaüstü nesne kümesi olması gibi senaryoları beklenmediğini içerecek şekilde dikkatle tasarlanmalıdır etkileşimi. Bazı durumlarda, kullanıcı denetimi altında çalışan bir Windows uygulaması yazmak daha uygun olabilir.  
  
-   Windows hizmet uygulamaları kendi güvenlik bağlamlarında çalışır ve uygulamaların yüklü Windows bilgisayara kullanıcı oturum açmadan önce başlatılır. Ayrıca, hizmet içinde çalıştırmak için hangi kullanıcı hesabı dikkatli bir şekilde planlamanız gerekir; Sistem hesabı altında çalışan bir hizmet, daha fazla izinleri ve bir kullanıcı hesabından ayrıcalıklara sahiptir.  
  
## <a name="service-lifetime"></a>Hizmet ömrü  
 Bir hizmet, ömrü süresince birçok dahili durumdan gider. İlk olarak, hizmet üzerinde çalışacağı sisteme yüklenir. Bu işlem hizmet projesi için yükleyicileri yürütür ve hizmeti yükler **Hizmet Denetim Yöneticisi** o bilgisayar için. **Hizmet Denetim Yöneticisi** hizmetlerini yönetmek için Windows tarafından sağlanan Merkezi hizmet programıdır.  
  
 Hizmet yüklendikten sonra başlatılmalıdır. Hizmetin başlatılması, çalışmasını sağlar. Bir hizmetten başlayabilirsiniz **Hizmet Denetim Yöneticisi**, gelen **Sunucu Gezgini**, veya çağırarak koddan <xref:System.ServiceProcess.ServiceController.Start%2A> yöntemi. <xref:System.ServiceProcess.ServiceController.Start%2A> Yöntemi uygulamanın işleme geçirir <xref:System.ServiceProcess.ServiceBase.OnStart%2A> yöntemi ve orada tanımladığınız tüm kodları işler.  
  
 Çalışan bir hizmete kadar süresiz olarak bunu da durduruldu veya duraklatıldı ya da bilgisayar kapatılana kadar bu durumda bulunabilir. Bir hizmet üç temel durumdan birinde bulunabilir: <xref:System.ServiceProcess.ServiceControllerStatus.Running>, <xref:System.ServiceProcess.ServiceControllerStatus.Paused>, veya <xref:System.ServiceProcess.ServiceControllerStatus.Stopped>. Hizmet ayrıca bekleyen bir komut durumunu raporlayabilirsiniz: <xref:System.ServiceProcess.ServiceControllerStatus.ContinuePending>, <xref:System.ServiceProcess.ServiceControllerStatus.PausePending>, <xref:System.ServiceProcess.ServiceControllerStatus.StartPending>, veya <xref:System.ServiceProcess.ServiceControllerStatus.StopPending>. Bu durumlar, komut, çalıştırılan bir hizmeti duraklatma komutu gibi verildi ancak henüz SCVMM'den gösterir. Sorgulayabilirsiniz <xref:System.ServiceProcess.ServiceController.Status%2A> ne bir hizmetin içinde bulunduğu durumu belirlemek veya bunları kullanmanızı <xref:System.ServiceProcess.ServiceController.WaitForStatus%2A> şu durumlardan birinde olduğunda bir eylem gerçekleştirmek için gerçekleşir.  
  
 Duraklat, Durdur veya hizmetten sürdürme **Hizmet Denetim Yöneticisi**, gelen **Sunucu Gezgini**, veya kod yöntemleri çağırarak. Bu eylemlerin her biri hizmette bir ilişkili yordam çağırabilir (<xref:System.ServiceProcess.ServiceBase.OnStop%2A>, <xref:System.ServiceProcess.ServiceBase.OnPause%2A>, veya <xref:System.ServiceProcess.ServiceBase.OnContinue%2A>), bu, hizmet durum değiştirdiğinde gerçekleştirilecek ilave işlemi tanımlayabileceğiniz içinde.  
  
## <a name="types-of-services"></a>Hizmet türleri  
 Hizmetleri .NET Framework kullanarak Visual Studio'da oluşturabileceğiniz iki tür vardır. Bir işlemdeki tek hizmet, hizmetler, türü atanmıştır <xref:System.ServiceProcess.ServiceType.Win32OwnProcess>. Bir işlem başka bir hizmetle paylaşan hizmetlere türü atanmıştır <xref:System.ServiceProcess.ServiceType.Win32ShareProcess>. Sorgulayarak hizmet türünü alabilirsiniz <xref:System.ServiceProcess.ServiceController.ServiceType%2A> özelliği.  
  
 Mevcut Visual Studio'da oluşturulmamış Hizmetleri sorgularsanız, bazen diğer hizmet türlerini görebilirsiniz. Bunlar hakkında daha fazla bilgi için bkz: <xref:System.ServiceProcess.ServiceType>.  
  
## <a name="services-and-the-servicecontroller-component"></a>Hizmetler ve ServiceController Bileşeni  
 <xref:System.ServiceProcess.ServiceController> Bileşeni yüklenen bir hizmete bağlanmak ve durumunu değiştirmek için kullanılır; kullanarak bir <xref:System.ServiceProcess.ServiceController> bileşeni, başlatın ve bir hizmet durdurun, duraklatabilir ve devam ettirebilir ve bir hizmete özel komutlar gönderebilirsiniz. Ancak, kullanın gerekmez bir <xref:System.ServiceProcess.ServiceController> bir hizmet uygulaması oluşturduğunuzda bileşeni. Aslında, çoğu durumda, <xref:System.ServiceProcess.ServiceController> bileşeni hizmetinizi tanımlayan Windows hizmet uygulamasından farklı bir uygulamada bulunmalıdır.  
  
 Daha fazla bilgi için bkz. <xref:System.ServiceProcess.ServiceController>.  
  
## <a name="requirements"></a>Gereksinimler  
  
-   Hizmetlerini oluşturdunuz, içinde bir **Windows hizmeti** uygulama projesi veya devralındığında .exe dosyası oluşturan ve devralınan bir.NET Framework kullanan başka bir proje <xref:System.ServiceProcess.ServiceBase> sınıfı.  
  
-   Windows Hizmetleri içeren projeler, proje ve Hizmetleri için yükleme bileşenlerine sahip olmalıdır. Bu kolayca gerçekleştirilebilir **özellikleri** penceresi. Daha fazla bilgi için [nasıl yapılır: Hizmet uygulamasına yükleyiciler ekleme](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Windows Hizmeti Uygulamaları](../../../docs/framework/windows-services/index.md)
- [Hizmet Uygulaması Programlama Mimarisi](../../../docs/framework/windows-services/service-application-programming-architecture.md)
- [Nasıl yapılır: Windows Hizmetleri oluşturma](../../../docs/framework/windows-services/how-to-create-windows-services.md)
- [Nasıl yapılır: Hizmetleri Yükleme ve kaldırma](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)
- [Nasıl yapılır: Başlangıç Hizmetleri](../../../docs/framework/windows-services/how-to-start-services.md)
- [Nasıl yapılır: Windows hizmet uygulamalarında hata ayıklama](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md)
- [İzlenecek yol: Bileşen tasarımcısında Windows hizmeti uygulaması oluşturma](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)
- [Nasıl yapılır: Hizmet uygulamasına yükleyiciler ekleme](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)
