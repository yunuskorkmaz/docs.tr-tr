---
title: Visual Basic Uygulama Modeline Genel Bakış
ms.date: 07/20/2015
helpviewer_keywords:
- My.Application object [Visual Basic], Visual Basic application model
- Visual Basic application model
ms.assetid: 17538984-84fe-43c9-82c8-724c9529fe8b
ms.openlocfilehash: 02cc71dbda47d078284d9a2ec07538dfa063ac75
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58819768"
---
# <a name="overview-of-the-visual-basic-application-model"></a>Visual Basic Uygulama Modeline Genel Bakış
Visual Basic, Windows Forms uygulamalarının davranışını denetlemek için iyi tanımlanmış bir modeli sağlar: Visual Basic uygulama modeli. Bu model, uygulama başlatma ve kapatma yanı çalýþýrçalýþma yakalama işlenmeyen özel durum olaylarını işlemek için olaylarını içerir. Tek örnek uygulamalar geliştirmeye yönelik destek de sağlar. Uygulama modeli Genişletilebilir olduğundan daha fazla denetim gerektiren geliştiriciler kendi geçersiz kılınabilir yöntemleri özelleştirebilirsiniz.  
  
## <a name="uses-for-the-application-model"></a>Uygulama modeli kullanımları  
 Tipik bir uygulaması başlatıldığında ve kapanırken gerçekleştirmeniz gerekir. Örneğin, başlatıldığında, uygulama giriş ekranı görüntülemek, veritabanı bağlantıları oluşturma, kaydedilen bir duruma yük ve benzeri. Uygulama kapatıldığında, veritabanı bağlantıları kapatın, geçerli durumunu kaydetmek ve benzeri. Ayrıca, uygulama kapattığında uygulamanın belirli bir kod yürütebilir beklenmedik şekilde gibi gibi işlenmeyen bir özel durum sırasında aşağı.  
  
 Visual Basic uygulama modeli oluşturmak kolaylaştırır bir *Tek Örnekli* uygulama. Tek Örnekli uygulama uygulamasından bir normal, uygulamanın yalnızca bir örneği aynı anda çalışabilir farklıdır. Tek Örnekli uygulama başka bir örneği başlatma girişimi sonuçları bildirilmesini özgün örneğinde — yoluyla `StartupNextInstance` olay —, başka bir başlatma girişiminde bulunuldu. Bildirim sonraki örneğinin komut satırı bağımsız değişkenleri içerir. Tüm başlatma gerçekleştirilmeden önce uygulamanın sonraki örneğini kapatılır.  
  
 Tek Örnekli uygulama başlar ve ilk örneği veya uygulama bir sonraki örneği olup olmadığını denetler:  
  
-   İlk örnek ise, her zamanki şekilde başlatır.  
  
-   İlk örnek çalışırken, uygulamayı başlatmak için sonraki girişimleri çok farklı davranışa neden olur. Sonraki deneme ilk örnek komut satırı bağımsız değişkenleri bildirir ve hemen çıkar. İlk örnek tutamaçları `StartupNextInstance` ne sonraki örneğinin komut satırı bağımsız değişkenleri olan ve çalışmaya devam eder belirlemek için olay.  
  
     Bir sonraki örneği ilk örneğini nasıl sinyalleri Bu diyagramda gösterilmiştir:  
  
     ![Tek Örnekli uygulama görüntüsü gösteren diyagram.](./media/overview-of-the-visual-basic-application-model/single-instance-application.gif)  
  
 İşleme göre `StartupNextInstance` olayı, tek örnek uygulamanızı nasıl davranacağını denetleyebilirsiniz. Örneğin, Microsoft Outlook, genellikle tek örnekli bir uygulama olarak çalışır; Outlook çalışıyorsa ve Outlook başlatmayı deneyebilirsiniz yeniden özgün örneğe kaydırır ancak başka bir örneği açık değil.  
  
## <a name="events-in-the-application-model"></a>Uygulama modeli olayları  
 Aşağıdaki olaylar uygulama modeli bulundu:  
  
-   **Uygulama başlatma**. Uygulama başlatır <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> başladığında olay. Bu olay işleme tarafından ana formu yüklenmeden önce uygulamayı başlatan bir kodu ekleyebilirsiniz. `Startup` Olay ayrıca sağlayan bu aşamasında bir uygulamanın başlatma işleminin yürütülmesini iptal etmek için isterseniz.  
  
     Uygulama başlangıç koduna çalışırken bir ekranı göstermek için uygulamayı yapılandırabilirsiniz. Varsayılan olarak, uygulama modeli Karşılama bastırır. zaman ekranında da `/nosplash` veya `-nosplash` komut satırı bağımsız değişkeni kullanılmıştır.  
  
-   **Tek örnek uygulamalarına**. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance> Olayı, tek örnekli uygulama bir sonraki örneği başlatıldığında oluşturulur. Olay komut satırı bağımsız değişkenlerini sonraki örneğinin geçirir.  
  
-   **İşlenmeyen özel durumları**. Uygulama işlenmeyen bir özel durumla karşılaşırsa, bilmemektedir <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> olay. Bu olayı işleyicinizi özel durum inceleyebilir ve yürütme devam edilip edilmeyeceğini belirler.  
  
     `UnhandledException` Olayı bazı durumlarda oluşmaz. Daha fazla bilgi için bkz. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>.  
  
-   **Ağ bağlantısı değişiklikleri**. Bilgisayarın ağ kullanılabilirliğini değişirse, uygulamayı başlatır <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged> olay.  
  
     `NetworkAvailabilityChanged` Olayı bazı durumlarda oluşmaz. Daha fazla bilgi için bkz. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged>.  
  
-   **Uygulama kapatma**. Uygulamanın sağladığı <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown> hakkında kapatmak için olduğunda sinyal olay. İlgili olay işleyicisi, işlemleri gerçekleştirmek uygulamanız gereken emin olursunuz; kapatma ve kaydetme, örneğin — tamamlanır. Ana formu kapandığında kapatmak için veya yalnızca tüm forms kapattığınızda kapatmak için yapılandırabilirsiniz.  
  
## <a name="availability"></a>Kullanılabilirlik  
 Varsayılan olarak, Visual Basic uygulama modeli, Windows Forms projeleri için kullanılabilir. Farklı başlangıç nesnesi kullanmak için uygulamayı yapılandırma veya uygulama kodu ile özel bir başlangıç `Sub Main`, nesne veya sınıf bir uygulamasını sağlamak üzere gerekebilir <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> uygulama modelini kullanmak için sınıf. Başlangıç nesnesi değiştirme hakkında daha fazla bilgi için bkz: [uygulama sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>
- [Visual Basic Uygulama Modelini Genişletme](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-visual-basic-application-model.md)
