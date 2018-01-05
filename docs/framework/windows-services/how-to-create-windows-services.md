---
title: "Nasıl Yapılır: Windows Hizmetleri Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Service applications, creating
- templates, Windows Service
ms.assetid: 0f5e2cbb-d95d-477c-b2b5-4b990e6b86ff
caps.latest.revision: "18"
author: ghogen
ms.author: ghogen
manager: douge
ms.workload: dotnet
ms.openlocfilehash: 7d93f8543b9e6e370827f5a666315d562e28ee76
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-windows-services"></a>Nasıl Yapılır: Windows Hizmetleri Oluşturma
Bir hizmet oluşturduğunuzda adlı bir Visual Studio Proje şablonu kullanabilirsiniz **Windows hizmeti**. Bu şablon otomatik olarak işin çoğunu sizin için uygun sınıfları ve ad alanları, hizmetleri, temel sınıfından devralma ayarlama başvurarak yapar ve birkaç yöntemleri geçersiz kılma, büyük bir olasılıkla geçersiz kılmak istiyor.  
  
> [!WARNING]
>  Windows Hizmetleri Proje şablonu Visual Studio Express Edition'da kullanılabilir değil.  
  
 En azından, işlevsel bir hizmet oluşturmak için yapmanız gerekir:  
  
-   Ayarlama <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> özelliği.  
  
-   Hizmet uygulamanız için gerekli yükleyicileri oluşturun.  
  
-   Geçersiz kılmak ve kodunu belirtmek <xref:System.ServiceProcess.ServiceBase.OnStart%2A> ve <xref:System.ServiceProcess.ServiceBase.OnStop%2A> , hizmetinizin davranış yöntemlerini özelleştirmek için yöntem.  
  
### <a name="to-create-a-windows-service-application"></a>Windows hizmet uygulaması oluşturmak için  
  
1.  Oluşturma bir **Windows hizmeti** projesi.  
  
    > [!NOTE]
    >  Bir hizmet şablonunu kullanmadan yazma ile ilgili yönergeler için bkz: [nasıl yapılır: Hizmetleri programlamayla yazma](../../../docs/framework/windows-services/how-to-write-services-programmatically.md).  
  
2.  İçinde **özellikleri** penceresindeki ayarlayın <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> hizmetiniz için özellik.  
  
     ![ServiceName özelliğini ayarlayın. ] (../../../docs/framework/windows-services/media/windowsservice-servicename.PNG "WindowsService_ServiceName")  
  
    > [!NOTE]
    >  Değeri <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> özelliği her zaman yükleyici sınıflarda kayıtlı adı eşleşmelidir. Bu özelliği değiştirirseniz, güncelleştirmelisiniz <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> yükleyici sınıfları özelliği.  
  
3.  Hizmetinizin nasıl işlev gösterdiğini belirlemek için aşağıdaki özelliklerden herhangi birini ayarlayın.  
  
    |Özellik|Ayar|  
    |--------------|-------------|  
    |<xref:System.ServiceProcess.ServiceBase.CanStop%2A>|`True`hizmeti çalışmayı durdurmak için istekleri kabul ettiğinizi belirtmek için; `false` hizmetin durdurulmasını önlemek için.|  
    |<xref:System.ServiceProcess.ServiceBase.CanShutdown%2A>|`True`hizmet üzerinde bulunduğu bilgisayar aşağı çağırmak etkinleştirmeden kapattığında bildirim almak istediği belirtmek için <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> yordamı.|  
    |<xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A>|`True`Hizmeti duraklatmak veya sürdürmek için istekleri kabul ettiğinizi belirtmek için çalışan; `false` hizmetinin duraklatılmasını ve önlemek için.|  
    |<xref:System.ServiceProcess.ServiceBase.CanHandlePowerEvent%2A>|`True`Hizmet bildirim bilgisayarın güç durumu değişiklikleri işleyebileceğini belirtmek için; `false` bu değişikliklerden haberdar hizmetin önlemek için.|  
    |<xref:System.ServiceProcess.ServiceBase.AutoLog%2A>|`True`Hizmetiniz bir eylem gerçekleştirdiğinde bilgilendirici girdiler için uygulama olay günlüğüne yazmak için; `false` bu işlev devre dışı bırakmak için. Daha fazla bilgi için bkz: [nasıl yapılır: günlük Information Services'ı hakkında](../../../docs/framework/windows-services/how-to-log-information-about-services.md). **Not:** varsayılan olarak, <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> ayarlanır `true`.|  
  
    > [!NOTE]
    >  Zaman <xref:System.ServiceProcess.ServiceBase.CanStop%2A> veya <xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A> ayarlanır `false`, **Hizmet Denetim Yöneticisi** durdurmak, duraklatmak veya hizmet devam etmek için ilgili menü seçenekleri devre dışı bırakır.  
  
4.  Kod Düzenleyicisi'ne erişmek ve için istediğiniz işleme doldurun <xref:System.ServiceProcess.ServiceBase.OnStart%2A> ve <xref:System.ServiceProcess.ServiceBase.OnStop%2A> yordamları.  
  
5.  İşlevselliği tanımlamak istediğiniz diğer yöntemleri geçersiz kılın.  
  
6.  Hizmet uygulamanız için gerekli yükleyicileri ekleyin. Daha fazla bilgi için bkz: [nasıl yapılır: Hizmet uygulamanız için yükleyiciler ekleme](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).  
  
7.  Seçerek projenizi derleme **yapı çözümü** gelen **yapı** menüsü.  
  
    > [!NOTE]
    >  Projenizi çalıştırmak için F5 tuşuna basmayın — bir hizmet projesi bu şekilde çalıştıramazsınız.  
  
8.  Hizmetini yükleyin. Daha fazla bilgi için bkz: [nasıl yapılır: yükleme ve kaldırma Hizmetleri](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Hizmeti Uygulamalarına Giriş](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [Nasıl Yapılır: Hizmetleri Programlamayla Yazma](../../../docs/framework/windows-services/how-to-write-services-programmatically.md)  
 [Nasıl Yapılır: Hizmet Uygulamasına Yükleyiciler Ekleme](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)  
 [Nasıl Yapılır: Hizmet Bilgilerini Günlüğe Kaydetme](../../../docs/framework/windows-services/how-to-log-information-about-services.md)  
 [Nasıl Yapılır: Hizmetleri Başlatma](../../../docs/framework/windows-services/how-to-start-services.md)  
 [Nasıl Yapılır: Hizmetler için Güvenlik İçeriği Belirtme](../../../docs/framework/windows-services/how-to-specify-the-security-context-for-services.md)  
 [Nasıl Yapılır: Hizmetleri Yükleme ve Kaldırma](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)  
 [İzlenecek Yol: Bileşen Tasarımcısında Windows Hizmeti Uygulaması Oluşturma](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)
