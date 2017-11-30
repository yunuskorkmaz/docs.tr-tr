---
title: "Visual Basic Uygulama Modeline Genel Bakış"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- My.Application object [Visual Basic], Visual Basic application model
- Visual Basic application model
ms.assetid: 17538984-84fe-43c9-82c8-724c9529fe8b
caps.latest.revision: "30"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 33b0e01317a6dab18ea03047c146def32b5675ad
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="overview-of-the-visual-basic-application-model"></a>Visual Basic Uygulama Modeline Genel Bakış
[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]Windows Forms uygulamaları davranışını denetlemek için iyi tanımlanmış bir modeli sağlar: [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] uygulama modeli. Bu model uygulama başlatma ve kapatma, yanı sıra çalýþýrçalýþma yakalama işlenmeyen özel durum olayları işlemek için olaylarını içerir. Tek örnek uygulamaları geliştirmek için destek de sağlar. Uygulama modeli genişletilebilir, olduğundan daha fazla denetim gerektiren geliştiriciler kendi geçersiz kılınabilir yöntemleri özelleştirebilirsiniz.  
  
## <a name="uses-for-the-application-model"></a>Uygulama modeli kullanımları  
 Tipik bir uygulama başlatıldığında ve kapandıktan görevleri gerçekleştirmek gerekir. Örneğin, başladığında, uygulama bir giriş ekranı, veritabanı bağlantıları oluşturma, kaydedilen bir duruma yük ve benzeri. Uygulama kapatıldığında, veritabanı bağlantıları kapatın, geçerli durumunu kaydetmek ve benzeri. Ayrıca, uygulama kapattığında uygulamanın belirli bir kod yürütebilir beklenmedik şekilde gibi sırasında işlenmeyen bir özel durum olarak gider.  
  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Uygulama modeli oluşturmak kolaylaştırır bir *Tek Örnekli* uygulama. Tek Örnekli uygulama bir uygulamasından normal, uygulamayı yalnızca bir örneği aynı anda çalışabilir farklıdır. Tek Örnekli uygulama başka bir örneği başlatma girişimi sonuçları bildirilmesini özgün örneğinde — yoluyla `StartupNextInstance` olay —, başka bir başlatma girişiminde bulunuldu. Bildirim sonraki örneğinin komut satırı bağımsız değişkenleri içerir. Sıfırlamaları oluşabilmesi için öncelikle uygulamayı sonraki örneği kapatılır.  
  
 Tek Örnekli uygulama başlar ve ilk örneği veya sonraki bir örnek uygulamanın olup olmadığını denetler:  
  
-   İlk örnek ise, her zamanki gibi başlatır.  
  
-   Her sonraki ilk örneği çalışırken, uygulama başlatma girişimi çok farklı davranışa neden olur. Sonraki deneme ilk örnek komut satırı bağımsız değişkenleri hakkında bilgilendirir ve hemen çıkar. İlk örnek tanıtıcıları `StartupNextInstance` ne sonraki örneğinin komut satırı bağımsız değişkenleri olan ve çalışmaya devam eder belirlemek için olay.  
  
     Bu diyagramda, nasıl bir sonraki örneği ilk örneği sinyalleri gösterilmektedir.  
  
     ![Tek örnek uygulama resmi](../../../visual-basic/developing-apps/development-with-my/media/singleinstance.gif "daıtmaktadır")  
  
 İşleme göre `StartupNextInstance` olay, tek örnek uygulamanızı nasıl davranacağını denetleyebilirsiniz. Örneğin, Microsoft Outlook genellikle tek örnekli bir uygulama olarak çalışır; Outlook çalışıyorsa ve Outlook'u girişimi yeniden özgün örneğe odağını kaydırır ancak başka bir örneği açık değil.  
  
## <a name="events-in-the-application-model"></a>Uygulama modeli olayları  
 Aşağıdaki olaylar uygulama modelinde bulunur:  
  
-   **Uygulama başlangıcında**. Uygulama başlatır <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> başladığında olay. Bu olay işleme tarafından ana form yüklenmeden önce uygulamayı başlatır kod ekleyebilirsiniz. `Startup` Olay de sağlar bu aşamasında uygulama başlatma işleminin yürütülmesini iptal etmek için isterseniz.  
  
     Uygulama başlangıç koduna çalışırken giriş ekranı göstermek için uygulamayı yapılandırabilirsiniz. Varsayılan olarak, uygulama modeli giriş bastırır ne zaman ekran ya da `/nosplash` veya `-nosplash` komut satırı bağımsız değişkeni kullanılır.  
  
-   **Tek örnek uygulamaları**. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance> Bir sonraki tek örnekli uygulama örneğini başladığında olay tetiklenir. Olay komut satırı bağımsız değişkenleri sonraki örneğinin geçirir.  
  
-   **İşlenmeyen özel durumlar**. Uygulama işlenmeyen bir özel durum karşılaşırsa başlatır <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> olay. Bu olay için işleyicinizi özel durum inceleyin ve yürütme devam edilip edilmeyeceğini belirler.  
  
     `UnhandledException` Olayı bazı durumlarda oluşmaz. Daha fazla bilgi için bkz. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>.  
  
-   **Ağ bağlantısı değişikliklerini**. Bilgisayarın ağ kullanılabilirliğini değişirse, uygulamayı başlatır <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged> olay.  
  
     `NetworkAvailabilityChanged` Olayı bazı durumlarda oluşmaz. Daha fazla bilgi için bkz. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged>.  
  
-   **Uygulama kapatma**. Uygulamanın sağladığı <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown> olay hakkında kapatmak için olduğunda sinyal. Bu olay işleyicisi, işlemleri gerçekleştirmek uygulamanız gereken emin olabilir — kapatma ve kaydetme, örneğin — tamamlanır. Uygulamanızı ana form kapandığında kapatma ya da yalnızca tüm formları kapattığınızda kapatmak için yapılandırabilirsiniz.  
  
## <a name="availability"></a>Kullanılabilirlik  
 Varsayılan olarak, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] uygulama modeli Windows Forms projeleri için kullanılabilir. Farklı başlangıç nesnesi kullanmak için uygulamayı yapılandırma veya özel bir uygulama kodu Başlat `Sub Main`, bu nesne veya sınıf bir belirtin gerekebilir <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> uygulama modelini kullanmak için sınıf. Başlangıç nesnesi değiştirme hakkında daha fazla bilgi için bkz: [uygulama sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup>  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance>  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown>  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged>  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>  
 [Visual Basic uygulama modelini genişletme](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-visual-basic-application-model.md)
