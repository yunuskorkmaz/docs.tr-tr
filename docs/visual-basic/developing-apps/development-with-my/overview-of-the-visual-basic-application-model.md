---
title: Visual Basic Uygulama Modeline Genel Bakış
ms.date: 07/20/2015
helpviewer_keywords:
- My.Application object [Visual Basic], Visual Basic application model
- Visual Basic application model
ms.assetid: 17538984-84fe-43c9-82c8-724c9529fe8b
ms.openlocfilehash: 46177d0af7e5df767eb8421caf424880baac615e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411733"
---
# <a name="overview-of-the-visual-basic-application-model"></a>Visual Basic Uygulama Modeline Genel Bakış

Visual Basic, Windows Forms uygulamaların davranışını denetlemek için iyi tanımlanmış bir model sağlar: Visual Basic uygulama modeli. Bu model, uygulamanın başlangıcını ve kapatılmasını işlemeye yönelik olayları, ayrıca işlenmemiş özel durumları yakalama olaylarını içerir. Ayrıca, tek örnekli uygulamalar geliştirmeye yönelik destek sağlar. Uygulama modeli Genişletilebilir, bu nedenle daha fazla denetim gerektiren geliştiriciler geçersiz kılınabilir yöntemleri özelleştirebilir.  
  
## <a name="uses-for-the-application-model"></a>Uygulama modeli için kullanımlar  

 Tipik bir uygulamanın, başlatıldığında ve kapandığında görevler gerçekleştirmesi gerekir. Örneğin, başlatıldığında uygulama bir giriş ekranı görüntüleyebilir, veritabanı bağlantıları yapabilir, kaydedilmiş bir durum yükleyebilir ve bu şekilde devam edebilir. Uygulama kapandığında, veritabanı bağlantılarını kapatabilir, geçerli durumu kaydedebilir ve bu şekilde devam edebilir. Ayrıca uygulama, işlenmeyen bir özel durum gibi beklenmedik şekilde kapandığında, uygulama belirli kodu yürütebilir.  
  
 Visual Basic uygulama modeli, *tek örnekli* bir uygulama oluşturmayı kolaylaştırır. Tek örnekli bir uygulama, aynı anda yalnızca bir uygulamanın bir örneğinin çalıştırılmasına yönelik olan normal uygulamalardan farklıdır. Tek örnekli bir uygulamanın başka bir örneğini başlatma denemesi, `StartupNextInstance` başka bir başlatma denemesinin yapıldığı, olay (Event) tarafından bildirilmekte olan özgün örneğe neden olur. Bildirim, sonraki örneğin komut satırı bağımsız değişkenlerini içerir. Uygulamanın sonraki örneği, herhangi bir başlatma gerçekleşebilmesi için daha sonra kapatılır.  
  
 Tek örnekli bir uygulama başlar ve uygulamanın ilk örnek mi yoksa sonraki bir örneği mi olduğunu denetler:  
  
- İlk örnek ise her zamanki gibi başlatılır.  
  
- İlk örnek çalışırken uygulamayı başlatmak için sonraki her girişim, çok farklı davranışa neden olur. Sonraki girişim, ilk örneğe komut satırı bağımsız değişkenleriyle bildirir ve ardından hemen çıkar. İlk örnek, `StartupNextInstance` sonraki örneğin komut satırı bağımsız değişkenlerinin ne olduğunu belirlemek için olayını işler ve çalışmaya devam eder.  
  
     Bu diyagram, sonraki bir örneğin ilk örneği nasıl sinyalinin olduğunu gösterir:  
  
     ![Tek örnekli bir uygulama görüntüsünü gösteren diyagram.](./media/overview-of-the-visual-basic-application-model/single-instance-application.gif)  
  
 `StartupNextInstance`Olayı işleyerek, tek örnekli uygulamanızın nasıl davranacağını kontrol edebilirsiniz. Örneğin, Microsoft Outlook genellikle tek örnekli bir uygulama olarak çalışır; Outlook çalışırken ve Outlook 'U yeniden başlatmaya çalıştığınızda, odak orijinal örneğe kayar, ancak başka bir örnek açılmaz.  
  
## <a name="events-in-the-application-model"></a>Uygulama modelindeki olaylar  

 Aşağıdaki olaylar uygulama modelinde bulunur:  
  
- **Uygulama başlatma**. Uygulama <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> başlatıldığında olayı başlatır. Bu olayı işleyerek, ana form yüklenmeden önce uygulamayı başlatan kodu ekleyebilirsiniz. `Startup`Bu olay, istenirse, başlangıç sürecinin bu aşaması sırasında uygulamanın yürütülmesini iptal etmeyi de sağlar.  
  
     Uygulama başlangıç kodu çalışırken uygulamayı bir giriş ekranı gösterecek şekilde yapılandırabilirsiniz. Varsayılan olarak, uygulama modeli `/nosplash` veya `-nosplash` komut satırı bağımsız değişkeni kullanıldığında giriş ekranını bastırır.  
  
- **Tek örnekli uygulamalar**. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance>Tek örnekli bir uygulamanın sonraki bir örneği başlatıldığında olay tetiklenir. Olay, sonraki örneğin komut satırı bağımsız değişkenlerini geçirir.  
  
- **İşlenmemiş özel durumlar**. Uygulama işlenmeyen bir özel durumla karşılaşırsa <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> olayı başlatır. Bu olaya yönelik işleyiciniz özel durumu inceleyebilir ve yürütmeye devam edilip edilmeyeceğini tespit edebilir.  
  
     `UnhandledException`Olay bazı koşullarda oluşturulmaz. Daha fazla bilgi için bkz. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>.  
  
- **Ağ bağlantısı değişiklikleri**. Bilgisayarın ağ kullanılabilirliği değişirse uygulama <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged> olayı başlatır.  
  
     `NetworkAvailabilityChanged`Olay bazı koşullarda oluşturulmaz. Daha fazla bilgi için bkz. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged>.  
  
- **Uygulama kapatıldı**. Uygulama, <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown> kapanmak üzere olduğunda, olayı işaret etmek üzere sağlar. Bu olay işleyicisinde, uygulamanızın gerçekleştirmesi gereken işlemlerin (örneğin, kapatma ve kaydetme) tamamlanmasını sağlayabilirsiniz. Uygulamanızı ana form kapandığında kapatılacak şekilde veya yalnızca tüm formlar kapandığında kapatmak için yapılandırabilirsiniz.  
  
## <a name="availability"></a>Kullanılabilirlik  

 Varsayılan olarak Visual Basic uygulama modeli Windows Forms projeleri için kullanılabilir. Uygulamayı farklı bir başlangıç nesnesini kullanacak şekilde yapılandırırsanız veya uygulama kodunu özel bir ile başlatırsanız `Sub Main` , bu nesnenin veya sınıfın <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> uygulama modelini kullanmak için sınıfın bir uygulamasını sağlaması gerekebilir. Başlangıç nesnesini değiştirme hakkında daha fazla bilgi için bkz. [uygulama sayfası, proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>
- [Visual Basic Uygulama Modelini Genişletme](../customizing-extending-my/extending-the-visual-basic-application-model.md)
