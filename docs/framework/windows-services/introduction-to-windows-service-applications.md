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
ms.openlocfilehash: 8ff1adaa025dc11417c3dcfdaf42ea203828be57
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053516"
---
# <a name="introduction-to-windows-service-applications"></a>Windows Hizmet Uygulamalarına Giriş
Eski adıyla NT Hizmetleri olarak bilinen Microsoft Windows Hizmetleri, kendi Windows oturumlarında çalışan uzun süreli yürütülebilir uygulamalar oluşturmanıza olanak sağlar. Bilgisayar önyüklendiğinde bu hizmetler otomatik olarak başlatılabilir, duraklatılıp yeniden başlatılabilir ve hiçbir Kullanıcı arabirimini göstermez. Bu özellikler, Hizmetleri bir sunucuda kullanılmak üzere ideal hale getirir veya aynı bilgisayarda çalışan diğer kullanıcılarla karışmayan uzun süre çalışan işlevlere ihtiyacınız olduğunda. Hizmetleri, oturum açmış kullanıcının veya varsayılan bilgisayar hesabından farklı olan belirli bir kullanıcı hesabının güvenlik bağlamında da çalıştırabilirsiniz. Hizmetler ve Windows oturumları hakkında daha fazla bilgi için Windows SDK belgelerine bakın.  
  
 Hizmet olarak yüklenen bir uygulama oluşturarak kolayca hizmet oluşturabilirsiniz. Örneğin, performans sayacı verilerini izlemek ve eşik değerlerine tepki vermek istediğinizi varsayalım. Performans sayacı verilerini dinleyen, uygulamayı dağıtan ve verileri toplamaya ve çözümlemeye başlayabileceğiniz bir Windows hizmeti uygulaması yazabilirsiniz.  
  
 Hizmetinizi, hizmete hangi komutların gönderilebileceklerini ve bu komutlar alındığında hangi eylemlerin alınacağını denetleyen bir Microsoft Visual Studio projesi olarak oluşturursunuz. Hizmeti başlatma, duraklatma, sürdürme ve durdurma dahil olmak üzere bir hizmete gönderilebilecek komutlar; Özel komutları da yürütebilirsiniz.  
  
 Uygulamayı oluşturup oluşturduktan sonra, komut satırı yardımcı programı InstallUtil. exe ' yi çalıştırarak ve yolu hizmetin yürütülebilir dosyasına geçirerek yükleyebilirsiniz. Daha sonra hizmet **Denetimi Yöneticisi 'ni** kullanarak hizmetinizi başlatabilir, durdurabilir, duraklatabilir, sürdürebilir ve yapılandırabilirsiniz. Ayrıca, bu görevlerin birçoğunu **Sunucu Gezgini** <xref:System.ServiceProcess.ServiceController> **Hizmetleri** düğümünde veya sınıfını kullanarak da gerçekleştirebilirsiniz.  
  
## <a name="service-applications-vs-other-visual-studio-applications"></a>Hizmet uygulamaları ile Diğer Visual Studio uygulamaları  
 Hizmet uygulamaları pek çok farklı proje türünden farklı şekilde çalışır:  
  
- Bir hizmet uygulaması projesinin oluşturduğu derlenmiş yürütülebilir dosya, projenin anlamlı bir şekilde çalışması için önce sunucuda yüklü olmalıdır. F5 veya F11 tuşlarına basarak bir hizmet uygulamasını hata ayıklamanıza veya çalıştırmazsınız. bir hizmeti hemen çalıştıramazsınız veya kendi kodunda adımlayın. Bunun yerine, hizmetinizi yükleyip başlatmanız ve sonra hizmetin işlemine bir hata ayıklayıcı eklemeniz gerekir. Daha fazla bilgi için [nasıl yapılır: Windows hizmet uygulamalarında](how-to-debug-windows-service-applications.md)hata ayıklama.  
  
- Bazı proje türlerinden farklı olarak, hizmet uygulamaları için yükleme bileşenleri oluşturmanız gerekir. Yükleme bileşenleri, hizmeti sunucuya yükleyip kaydeder ve Windows **Hizmetleri Denetim Yöneticisi**ile hizmetiniz için bir giriş oluşturur. Daha fazla bilgi için [nasıl yapılır: Hizmet uygulamanıza](how-to-add-installers-to-your-service-application.md)yükleyicileri ekleyin.  
  
- Hizmet `Main` uygulamanız için yönteminin, projenizin içerdiği hizmetler için Run komutunu vermesi gerekir. Yöntemi, hizmetleri uygun sunucuda **Hizmetleri denetim yöneticisine** yükler. `Run` **Windows Hizmetleri** proje şablonunu kullanıyorsanız, bu yöntem sizin için otomatik olarak yazılır. Hizmeti yüklemenin hizmeti başlatmasıyla aynı şey olmadığına unutmayın. Daha fazla bilgi için aşağıdaki "hizmet yaşam süresi" başlığına bakın.  
  
- Windows hizmeti uygulamaları, oturum açmış kullanıcının etkileşimli istasyonundan farklı bir pencere istasyonunda çalışır. Pencere istasyonu, pano, genel bir grup kümesi ve bir masaüstü nesneleri grubunu içeren güvenli bir nesnedir. Windows hizmeti İstasyonu etkileşimli bir istasyon olmadığından, bir Windows hizmeti uygulaması içinden oluşturulan iletişim kutuları görünmez ve programınızın yanıt vermeyi durdurmasına neden olabilir. Benzer şekilde, hata iletileri Kullanıcı arabiriminde tetiklenir yerine Windows olay günlüğü 'ne kaydedilir.  
  
     .NET Framework tarafından desteklenen Windows hizmeti sınıfları, oturum açmış olan kullanıcının etkileşimli istasyonlarla etkileşimi desteklemez. .NET Framework Ayrıca istasyonların ve masaüstlerini temsil eden sınıfları içermez. Windows hizmetinizin diğer istasyonlarla etkileşim kurması gerekiyorsa, yönetilmeyen Windows API 'sine erişmeniz gerekir. Daha fazla bilgi için Windows SDK belgelerine bakın.  
  
     Windows hizmetinin Kullanıcı veya diğer istasyonlarla etkileşimi, oturum açmış kullanıcı veya kullanıcının beklenmedik bir masaüstü nesneleri kümesine sahip olmadığı gibi senaryoları içerecek şekilde dikkatle tasarlanmalıdır. Bazı durumlarda, Kullanıcı denetimi altında çalışan bir Windows uygulaması yazmak daha uygun olabilir.  
  
- Windows hizmeti uygulamaları kendi güvenlik bağlamında çalışır ve Kullanıcı, yüklendiği Windows bilgisayarında oturum açmadan önce başlatılır. Hizmetin hangi kullanıcı hesabı içinde çalıştırılacağını dikkatle planlamanız gerekir; Sistem hesabı altında çalışan bir hizmetin, bir kullanıcı hesabından daha fazla izni ve ayrıcalıkları vardır.  
  
## <a name="service-lifetime"></a>Hizmet ömrü  
 Bir hizmet, ömrü boyunca birkaç iç durumdan geçer. İlk olarak, hizmet üzerinde çalışacağı sisteme yüklenir. Bu işlem, hizmet projesi için yükleyicileri yürütür ve hizmeti o bilgisayar için **Hizmetler denetim yöneticisine** yükler. **Hizmetler Denetim Yöneticisi** , Windows 'un hizmetleri yönetmek için sunduğu merkezi bir yardımcı programdır.  
  
 Hizmet yüklendikten sonra başlatılmış olması gerekir. Hizmeti başlatmak, BT 'nin çalışmaya başlamasını sağlar. Service **Control Manager**'dan, **Sunucu Gezgini**'den veya <xref:System.ServiceProcess.ServiceController.Start%2A> yöntemi çağırarak koddan bir hizmet başlatabilirsiniz. <xref:System.ServiceProcess.ServiceController.Start%2A> Yöntemi<xref:System.ServiceProcess.ServiceBase.OnStart%2A> uygulama yöntemine işleme geçirir ve burada tanımladığınız kodu işler.  
  
 Çalışan bir hizmet, durdurulduğu veya duraklatıldığı ya da bilgisayar kapanana kadar süresiz olarak bu durumda bulunabilir. Bir hizmet üç temel durumdan birinde bulunabilir: <xref:System.ServiceProcess.ServiceControllerStatus.Running>, <xref:System.ServiceProcess.ServiceControllerStatus.Paused>, veya <xref:System.ServiceProcess.ServiceControllerStatus.Stopped>. Hizmet ayrıca bekleyen bir komutun durumunu rapor edebilir <xref:System.ServiceProcess.ServiceControllerStatus.ContinuePending>:, <xref:System.ServiceProcess.ServiceControllerStatus.PausePending>, <xref:System.ServiceProcess.ServiceControllerStatus.StartPending>veya <xref:System.ServiceProcess.ServiceControllerStatus.StopPending>. Bu durumlar, çalışan bir hizmeti duraklatmaya yönelik bir komut gibi bir komutun verildiğini, ancak henüz gerçekleştirilmeyeceğini gösterir. Bir hizmetin hangi duruma <xref:System.ServiceProcess.ServiceController.Status%2A> olduğunu belirlemek için ' i sorgulayabilir veya bu durumların herhangi biri gerçekleştiğinde <xref:System.ServiceProcess.ServiceController.WaitForStatus%2A> bir eylem gerçekleştirmek için öğesini kullanabilirsiniz.  
  
 Service **Control Manager**'dan, **Sunucu Gezgini**'den veya koddaki yöntemleri çağırarak bir hizmeti duraklatabilir, durdurabilir veya devam ettirebilirsiniz. Bu eylemlerin her biri, hizmette bir ilişkili yordam çağırabilir (<xref:System.ServiceProcess.ServiceBase.OnStop%2A>, <xref:System.ServiceProcess.ServiceBase.OnPause%2A>veya <xref:System.ServiceProcess.ServiceBase.OnContinue%2A>), bu, hizmet durumunu değiştirdiğinde gerçekleştirilecek ek işleme tanımlayabilmeniz için kullanabilirsiniz.  
  
## <a name="types-of-services"></a>Hizmet türleri  
 .NET Framework kullanarak, Visual Studio 'da oluşturabileceğiniz iki tür hizmet vardır. Bir işlemdeki tek hizmet olan hizmetlere tür <xref:System.ServiceProcess.ServiceType.Win32OwnProcess>atanır. Başka bir hizmetle bir işlem paylaşan hizmetlere bu tür <xref:System.ServiceProcess.ServiceType.Win32ShareProcess>atanır. <xref:System.ServiceProcess.ServiceController.ServiceType%2A> Özelliği sorgulayarak hizmet türünü alabilirsiniz.  
  
 Visual Studio 'da oluşturulmamış Hizmetleri sorgulayıp diğer hizmet türlerini görebilirsiniz. Bunlar hakkında daha fazla bilgi için bkz <xref:System.ServiceProcess.ServiceType>.  
  
## <a name="services-and-the-servicecontroller-component"></a>Hizmetler ve ServiceController bileşeni  
 Bileşen yüklü bir hizmete bağlanmak ve durumunu işlemek için kullanılır; bir <xref:System.ServiceProcess.ServiceController> bileşeni kullanarak bir hizmeti başlatıp durdurabilir, çalışmasını duraklatabilir, devam edebilir ve bir hizmete özel komutlar gönderebilirsiniz. <xref:System.ServiceProcess.ServiceController> Ancak, bir hizmet uygulaması oluşturduğunuzda bir <xref:System.ServiceProcess.ServiceController> bileşeni kullanmanız gerekmez. Aslında, çoğu durumda <xref:System.ServiceProcess.ServiceController> bileşeninizin, hizmetinizi tanımlayan Windows hizmeti uygulamasından ayrı bir uygulamada bulunması gerekir.  
  
 Daha fazla bilgi için bkz. <xref:System.ServiceProcess.ServiceController>.  
  
## <a name="requirements"></a>Gereksinimler  
  
- Hizmetler, <xref:System.ServiceProcess.ServiceBase> sınıftan oluşturulup devralındığında bir. exe dosyası oluşturan bir **Windows hizmet** uygulaması projesinde veya başka bir .NET Framework etkinleştirilmiş projede oluşturulmalıdır.  
  
- Windows Hizmetleri içeren projelerin, proje ve hizmetleri için yükleme bileşenleri olmalıdır. Bu, **Özellikler** penceresinden kolayca gerçekleştirilebilir. Daha fazla bilgi için [nasıl yapılır: Hizmet uygulamanıza](how-to-add-installers-to-your-service-application.md)yükleyicileri ekleyin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Hizmeti Uygulamaları](index.md)
- [Hizmet Uygulaması Programlama Mimarisi](service-application-programming-architecture.md)
- [Nasıl yapılır: Windows Hizmetleri oluşturma](how-to-create-windows-services.md)
- [Nasıl yapılır: Hizmetleri yükleme ve kaldırma](how-to-install-and-uninstall-services.md)
- [Nasıl yapılır: Hizmetleri Başlat](how-to-start-services.md)
- [Nasıl yapılır: Windows hizmet uygulamalarında hata ayıklama](how-to-debug-windows-service-applications.md)
- [İzlenecek yol: Bileşen tasarımcısında bir Windows hizmeti uygulaması oluşturma](walkthrough-creating-a-windows-service-application-in-the-component-designer.md)
- [Nasıl yapılır: Hizmet uygulamanıza yükleyiciler ekleme](how-to-add-installers-to-your-service-application.md)
