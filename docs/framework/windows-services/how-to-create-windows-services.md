---
title: 'Nasıl Yapılır: Windows Hizmetleri Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Service applications, creating
- templates, Windows Service
ms.assetid: 0f5e2cbb-d95d-477c-b2b5-4b990e6b86ff
author: ghogen
ms.openlocfilehash: 7a529a94edf3a4cf71150c04994d82b8f21eb996
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47170957"
---
# <a name="how-to-create-windows-services"></a>Nasıl Yapılır: Windows Hizmetleri Oluşturma
Bir hizmet oluşturduğu zaman, adlı bir Visual Studio Proje şablonu kullanabilirsiniz **Windows hizmeti**. Bu şablon otomatik olarak işin çoğunu sizin için uygun sınıf ve ad alanları, hizmetler için bir temel sınıftan devralmayı ayarlama başvurarak yapar ve birkaç yöntemleri geçersiz kılan, geçersiz kılmak istediğiniz kullanılma olasılığı.  
  
> [!WARNING]
>  Windows Hizmetleri Proje şablonu Visual Studio'nun Express sürümünde kullanılabilir değil.  
  
 En azından, işlevsel bir hizmet oluşturmak için şunları yapmalısınız:  
  
-   Ayarlama <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> özelliği.  
  
-   Hizmet uygulamanız için gerekli yükleyicileri oluşturun.  
  
-   Geçersiz kılmak ve belirtmek için kod <xref:System.ServiceProcess.ServiceBase.OnStart%2A> ve <xref:System.ServiceProcess.ServiceBase.OnStop%2A> , hizmetinizin davranış yöntemlerini özelleştirmek için yöntemleri.  
  
### <a name="to-create-a-windows-service-application"></a>Bir Windows hizmet uygulaması oluşturmak için  
  
1.  Oluşturma bir **Windows hizmeti** proje.  
  
    > [!NOTE]
    >  Şablon kullanmadan hizmet yazma ile ilgili yönergeler için bkz: [nasıl yapılır: Hizmetleri programlamayla yazma](../../../docs/framework/windows-services/how-to-write-services-programmatically.md).  
  
2.  İçinde **özellikleri** penceresinde <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> hizmetiniz için özellik.  
  
     ![ServiceName özelliğini ayarlayın. ](../../../docs/framework/windows-services/media/windowsservice-servicename.PNG "WindowsService_ServiceName")  
  
    > [!NOTE]
    >  Değerini <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> özelliği her zaman yükleyici sınıflarda kayıtlı adla eşleşmelidir. Bu özelliği değiştirirseniz güncelleştirmelisiniz <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> yükleyici sınıflarının özelliği.  
  
3.  Hizmetinizin nasıl çalışacağını belirlemek için aşağıdaki özellikleri ayarlayın.  
  
    |Özellik|Ayar|  
    |--------------|-------------|  
    |<xref:System.ServiceProcess.ServiceBase.CanStop%2A>|`True` hizmetin çalışmayı durdurmak için istekleri kabul edeceğini belirtmek için; `false` hizmetin durdurulmasını önlemek için.|  
    |<xref:System.ServiceProcess.ServiceBase.CanShutdown%2A>|`True` Hizmet çağıracak şekilde etkinleştirme aşağı üzerinde yaşadığı bilgisayar kapatıldığında bildirim almak istediğini belirten <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> yordamı.|  
    |<xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A>|`True` Hizmeti duraklatmak veya devam ettirmek için istekleri kabul edeceğini belirtmek için çalışan; `false` hizmetinin duraklatılmasını ve devam ettirilmesini önlemek için.|  
    |<xref:System.ServiceProcess.ServiceBase.CanHandlePowerEvent%2A>|`True` hizmetin bilgisayarın güç durumu değişiklikleri bildirimini işleyebileceğini belirtmek için; `false` bu değişikliklerin bildirilmesini önlemek için.|  
    |<xref:System.ServiceProcess.ServiceBase.AutoLog%2A>|`True` Hizmetiniz bir eylem gerçekleştirdiğinde uygulama olay günlüğüne bilgilendirici girdiler yazmak için; `false` bu işlevi devre dışı bırakmak için. Daha fazla bilgi için [nasıl yapılır: günlük Information Services'ı hakkında](../../../docs/framework/windows-services/how-to-log-information-about-services.md). **Not:** varsayılan olarak, <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> ayarlanır `true`.|  
  
    > [!NOTE]
    >  Zaman <xref:System.ServiceProcess.ServiceBase.CanStop%2A> veya <xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A> ayarlandığından `false`, **Hizmet Denetimi Yöneticisi** durdurmak, duraklatmak veya hizmete devam ilgili menü seçenekleri devre dışı bırakır.  
  
4.  Kod düzenleyicisine erişip ve için istediğiniz işlemeyi doldurun <xref:System.ServiceProcess.ServiceBase.OnStart%2A> ve <xref:System.ServiceProcess.ServiceBase.OnStop%2A> yordamları.  
  
5.  İşlevselliği tanımlamak istediğiniz diğer yöntemleri geçersiz kılın.  
  
6.  Hizmet uygulamanız için gerekli yükleyicileri ekleyin. Daha fazla bilgi için [nasıl yapılır: Hizmet uygulamanız için yükleyicileri ekleyin](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).  
  
7.  Projenizi seçerek **Çözümü Derle** gelen **derleme** menüsü.  
  
    > [!NOTE]
    >  Projenizi çalıştırmak için F5 tuşuna basmayın-bu şekilde bir hizmet projesi çalıştıramazsınız.  
  
8.  Hizmetini yükleyin. Daha fazla bilgi için [nasıl yapılır: yükleme ve kaldırma Hizmetleri](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Hizmeti Uygulamalarına Giriş](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [Nasıl Yapılır: Hizmetleri Programlamayla Yazma](../../../docs/framework/windows-services/how-to-write-services-programmatically.md)  
 [Nasıl Yapılır: Hizmet Uygulamasına Yükleyiciler Ekleme](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)  
 [Nasıl Yapılır: Hizmet Bilgilerini Günlüğe Kaydetme](../../../docs/framework/windows-services/how-to-log-information-about-services.md)  
 [Nasıl Yapılır: Hizmetleri Başlatma](../../../docs/framework/windows-services/how-to-start-services.md)  
 [Nasıl Yapılır: Hizmetler için Güvenlik İçeriği Belirtme](../../../docs/framework/windows-services/how-to-specify-the-security-context-for-services.md)  
 [Nasıl Yapılır: Hizmetleri Yükleme ve Kaldırma](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)  
 [İzlenecek Yol: Bileşen Tasarımcısında Windows Hizmeti Uygulaması Oluşturma](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)
