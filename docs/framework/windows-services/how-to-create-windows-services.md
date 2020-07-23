---
title: 'Nasıl yapılır: Windows Hizmetleri Oluşturma'
description: Bir hizmet oluşturmak için Windows hizmeti proje şablonunu kullanın. ServiceName özelliğini ayarlayın, yükleyiciler oluşturun ve OnStart ve OnStop yöntemlerini geçersiz kılın.
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Service applications, creating
- templates, Windows Service
ms.assetid: 0f5e2cbb-d95d-477c-b2b5-4b990e6b86ff
author: ghogen
ms.openlocfilehash: 6918225e39c15a52710fd0d56342aae869b42325
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925780"
---
# <a name="how-to-create-windows-services"></a>Nasıl yapılır: Windows Hizmetleri Oluşturma
Bir hizmet oluşturduğunuzda, **Windows hizmeti**adlı bir Visual Studio proje şablonu kullanabilirsiniz. Bu şablon uygun sınıflara ve ad alanlarına başvurarak, hizmetler için temel sınıftan devralmayı ayarlayarak ve büyük olasılıkla geçersiz kılmak istediğiniz yöntemlerin birkaçını geçersiz kılarak sizin için işin çoğunu otomatik olarak yapar.  
  
> [!WARNING]
> Windows Hizmetleri proje şablonu, Visual Studio 'nun Express sürümünde kullanılamaz.  
  
 Bir işlevsel hizmet oluşturmak için en azından şunları yapmanız gerekir:  
  
- Özelliği ayarlayın <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> .  
  
- Hizmet uygulamanız için gerekli yükleyicileri oluşturun.  
  
- <xref:System.ServiceProcess.ServiceBase.OnStart%2A>Hizmetinizin davranışını özelleştirmek için ve yöntemlerinin kodunu geçersiz kılın ve belirtin <xref:System.ServiceProcess.ServiceBase.OnStop%2A> .  
  
### <a name="to-create-a-windows-service-application"></a>Bir Windows hizmet uygulaması oluşturmak için  
  
1. Bir **Windows hizmeti** projesi oluşturun.  
  
    > [!NOTE]
    > Şablon kullanmadan bir hizmet yazma yönergeleri için bkz. [nasıl yapılır: Hizmetleri program aracılığıyla yazma](how-to-write-services-programmatically.md).  
  
2. **Özellikler** penceresinde <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> hizmetinizin özelliğini ayarlayın.  
  
     ![ServiceName özelliğini ayarlayın.](./media/windowsservice-servicename.PNG "WindowsService_ServiceName")  
  
    > [!NOTE]
    > <xref:System.ServiceProcess.ServiceBase.ServiceName%2A>Özelliğin değeri her zaman yükleyici sınıflarında kaydedilen adla eşleşmelidir. Bu özelliği değiştirirseniz, <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> yükleyici sınıflarının özelliğini de güncelleştirmeniz gerekir.  
  
3. Hizmetinizin nasıl çalışacağını öğrenmek için aşağıdaki özelliklerden herhangi birini ayarlayın.  
  
    |Özellik|Ayar|  
    |--------------|-------------|  
    |<xref:System.ServiceProcess.ServiceBase.CanStop%2A>|`True`hizmetin çalışmayı durdurmak için istekleri kabul edeceğini belirtmek için; `false`hizmetin durdurulmasını engellemek için.|  
    |<xref:System.ServiceProcess.ServiceBase.CanShutdown%2A>|`True`hizmetin, yaşadığı bilgisayar kapandığında bildirim almak istediğini göstermek için, yordamı çağırabileceği şekilde etkinleştirir <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> .|  
    |<xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A>|`True`hizmetin çalışmayı duraklatmak veya çalışmaya devam etmek için istekleri kabul edeceğini belirtmek için; `false`hizmetin duraklatılmasını ve devam ettirmasını engellemek için.|  
    |<xref:System.ServiceProcess.ServiceBase.CanHandlePowerEvent%2A>|`True`hizmetin bilgisayarın güç durumundaki değişikliklerin bildirimini işleyebileceğini belirtmek için; `false`hizmetin bu değişiklikler hakkında bildirilmesini engellemek için.|  
    |<xref:System.ServiceProcess.ServiceBase.AutoLog%2A>|`True`Hizmetiniz bir eylem gerçekleştirdiğinde Uygulama olay günlüğü 'ne bilgilendirici girişler yazmak için; `false`Bu işlevi devre dışı bırakmak için. Daha fazla bilgi için bkz. [nasıl yapılır: hizmetlerle Ilgili bilgileri günlüğe kaydetme](how-to-log-information-about-services.md). **Note:**  Varsayılan olarak, <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> olarak ayarlanır `true` .|  
  
    > [!NOTE]
    > <xref:System.ServiceProcess.ServiceBase.CanStop%2A>Veya <xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A> olarak ayarlandığında `false` , **hizmet denetimi Yöneticisi** hizmeti durdurmak, duraklatmak veya devam ettirmek için ilgili menü seçeneklerini devre dışı bırakır.  
  
4. Kod düzenleyicisine erişin ve yordamları için istediğiniz işlemeyi girin <xref:System.ServiceProcess.ServiceBase.OnStart%2A> <xref:System.ServiceProcess.ServiceBase.OnStop%2A> .  
  
5. İşlevselliği tanımlamak istediğiniz diğer yöntemleri geçersiz kılın.  
  
6. Hizmet uygulamanız için gerekli yükleyicileri ekleyin. Daha fazla bilgi için bkz. [nasıl yapılır: hizmet uygulamanıza yükleyiciler ekleme](how-to-add-installers-to-your-service-application.md).  
  
7. **Build** menüsünden **Build Solution** ' i seçerek projenizi oluşturun.  
  
    > [!NOTE]
    > Projenizi çalıştırmak için F5 tuşuna basmayın; bir hizmet projesini bu şekilde çalıştıramazsınız.  
  
8. Hizmeti yükler. Daha fazla bilgi için bkz. [nasıl yapılır: Hizmetleri yükleme ve kaldırma](how-to-install-and-uninstall-services.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Hizmet Uygulamalarına Giriş](introduction-to-windows-service-applications.md)
- [Nasıl yapılır: Hizmetleri Program Aracılığıyla Yazma](how-to-write-services-programmatically.md)
- [Nasıl yapılır: Hizmet Uygulamasına Yükleyiciler Ekleme](how-to-add-installers-to-your-service-application.md)
- [Nasıl yapılır: Hizmet Bilgilerini Günlüğe Kaydetme](how-to-log-information-about-services.md)
- [Nasıl yapılır: Hizmetleri Başlatma](how-to-start-services.md)
- [Nasıl yapılır: Hizmetler için Güvenlik İçeriği Belirtme](how-to-specify-the-security-context-for-services.md)
- [Nasıl yapılır: Hizmetleri Yükleme ve Kaldırma](how-to-install-and-uninstall-services.md)
- [İzlenecek Yol: Bileşen Tasarımcısında Windows Hizmeti Uygulaması Oluşturma](walkthrough-creating-a-windows-service-application-in-the-component-designer.md)
