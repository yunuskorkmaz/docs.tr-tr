---
title: Visual Basic Uygulama Modelini Genişletme
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic Application Model, extending
ms.assetid: e91d3bed-4c27-40e3-871d-2be17467c72c
ms.openlocfilehash: 64c175216cf21b7947462cf79e4b88ab6fcd6d86
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="extending-the-visual-basic-application-model"></a>Visual Basic Uygulama Modelini Genişletme
Geçersiz kılarak uygulama modeli işlevselliği ekleyebilirsiniz `Overridable` üyeleri <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> sınıfı. Bu teknik uygulama modeli davranışını özelleştirmek ve uygulama başlatıldığı ve kapandıktan gibi kendi yöntem çağrıları eklemenize izin verir.  
  
## <a name="visual-overview-of-the-application-model"></a>Uygulama modeli Visual genel bakış  
 Bu bölümde, Visual Basic uygulama modeli görsel olarak işlev çağrıları dizisini gösterir. Sonraki bölümde ayrıntılı her işlevin amacı açıklar.  
  
 Aşağıdaki grafikte normal bir Visual Basic Windows Forms uygulaması'nda uygulama modeli çağrı sırası gösterir. Ne zaman dizisini başlatır `Sub Main` yordam çağrıları <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Run%2A> yöntemi.  
  
 ![Visual Basic uygulama modeli &#45; &#45; çalıştırmak](../../../visual-basic/developing-apps/customizing-extending-my/media/vb_modelrun.gif "VB_ModelRun")  
  
 Visual Basic uygulama modeli de sağlar <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance> ve <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> olaylar. Bu olaylar oluşturma için mekanizma aşağıdaki grafik gösterir.  
  
 ![Visual Basic uygulama modeli &#45; &#45; sonraki örnek](../../../visual-basic/developing-apps/customizing-extending-my/media/vb_modelnext.gif "VB_ModelNext")  
  
 ![Visual Basic uygulama modeli işlenmemiş özel durum](../../../visual-basic/developing-apps/customizing-extending-my/media/vb_unhandex.gif "VB_UnhandEx")  
  
## <a name="overriding-the-base-methods"></a>Taban yöntemleri geçersiz kılma  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Run%2A> Yöntemi tanımlar sırası içinde `Application` yöntemleri çalıştırın. Varsayılan olarak, `Sub Main` bir Windows Forms uygulaması için yordam çağrıları <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Run%2A> yöntemi.  
  
 Uygulamanın normal uygulama (birden çok örnekli uygulama) ya da tek örnekli uygulama ilk örneğini ise <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Run%2A> yöntemini yürütür `Overridable` aşağıdaki sırayla yöntemleri:  
  
1.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnInitialize%2A>. Varsayılan olarak, bu yöntem görsel stiller, metin görüntü stilleri ve (uygulamayı Windows kimlik doğrulaması kullanıyorsa) ana uygulama iş parçacığı için geçerli sorumluyu ayarlar ve çağrıları `ShowSplashScreen` ne `/nosplash` ya da `-nosplash` olarak kullanılan bir komut satırı bağımsız değişkeni.  
  
     Bu işlev döndürürse, uygulama başlatma sırası iptal `False`. Bu uygulama değil çalıştırmalısınız durumlarda yararlı olabilir.  
  
     <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnInitialize%2A> Yöntemini aşağıdaki yöntemleri çağırır:  
  
    1.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.ShowSplashScreen%2A>. Uygulama tanımlı bir giriş ekranı olup olmadığını belirler ve bulursa, ayrı bir iş parçacığı üzerinde giriş ekranı görüntüler.  
  
         <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.ShowSplashScreen%2A> Yöntem giriş görüntüler kod içeriyor için en az tarafından belirtilen milisaniye sayısını ekran <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MinimumSplashScreenDisplayTime%2A> özelliği. Bu işlevselliği kullanmak için giriş ekranı kullanarak uygulamanızı eklemelisiniz **Proje Tasarımcısı** (hangi kümeleri `My.Application.MinimumSplashScreenDisplayTime` iki saniye özelliğine), veya `My.Application.MinimumSplashScreenDisplayTime` geçersizkılanbiryöntemözelliği<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnInitialize%2A> veya <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateSplashScreen%2A> yöntemi. Daha fazla bilgi için bkz. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MinimumSplashScreenDisplayTime%2A>.  
  
    2.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateSplashScreen%2A>. Giriş ekranı başlatır kod yaymak üzere bir tasarımcı sağlar.  
  
         Varsayılan olarak, bu yöntem hiçbir şey yapmaz. Visual Basic'te, uygulamanız için bir giriş ekranı seçerseniz **Proje Tasarımcısı**, Tasarımcı geçersiz kılmaları <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateSplashScreen%2A> ayarlar yöntemiyle yöntemini <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.SplashScreen%2A> giriş ekranı formun yeni bir örneğini özelliğine .  
  
2.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnStartup%2A>. Yükseltme için bir genişletilebilirlik noktasıdır `Startup` olay. Bu işlev döndürürse, uygulama başlatma sırası durdurur `False`.  
  
     Varsayılan olarak, bu yöntem başlatır <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> olay. Olay işleyicisi ayarlarsa <xref:System.ComponentModel.CancelEventArgs.Cancel> olay bağımsız değişkeninin özelliğine `True`, yöntem döndürür `False` uygulama başlangıç iptal etmek için.  
  
3.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnRun%2A>. Ana uygulama başlatma tamamlandıktan sonra çalışan başlatmaya hazır olduğunda için başlangıç noktası sağlar.  
  
     Varsayılan olarak, bir Windows Forms ileti döngüye girer önce bu yöntemi çağırır `OnCreateMainForm` (uygulamanın ana form oluşturmak için) ve `HideSplashScreen` (giriş ekranı kapatmak için) yöntemleri:  
  
    1.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A>. Ana form başlatır kod yaymak üzere designer için bir yol sağlar.  
  
         Varsayılan olarak, bu yöntem hiçbir şey yapmaz. Ancak, seçtiğinizde, ana form Visual Basic'te, uygulamanız için **Proje Tasarımcısı**, Tasarımcı geçersiz kılmaları <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A> ayarlar yöntemiyle yöntemini <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A> ana formun yeni bir örneğini özelliğine.  
  
    2.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.HideSplashScreen%2A>. Uygulama tanımlı bir giriş ekranı sahiptir ve açık ise, bu yöntem giriş ekranı kapatır.  
  
         Varsayılan olarak, bu yöntem giriş ekranı kapatır.  
  
4.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnStartupNextInstance%2A>. Uygulama başka bir örneği başladığında Tek Örnekli uygulama nasıl davranacağını özelleştirmek için bir yol sağlar.  
  
     Varsayılan olarak, bu yöntem başlatır <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance> olay.  
  
5.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnShutdown%2A>. Yükseltme için bir genişletilebilirlik noktasıdır `Shutdown` olay. Ana uygulamada işlenmeyen bir özel durum oluşursa, bu yöntem çalışmaz.  
  
     Varsayılan olarak, bu yöntem başlatır <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown> olay.  
  
6.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnUnhandledException%2A>. Yukarıda listelenen yöntemlerden birini işlenmeyen bir özel durum oluşursa yürütüldü.  
  
     Varsayılan olarak, bu yöntem başlatır <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> olay bir hata ayıklayıcısı iliştirilmemiş ve uygulama işleme sürece `UnhandledException` olay.  
  
 Uygulama tek örnekli uygulama ve uygulamanın zaten çalıştığından, uygulamanın sonraki örneği çağırır <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnStartupNextInstance%2A> uygulama ve ardından çıkar özgün örneğinde yöntemi.  
 
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnStartupNextInstance(Microsoft.VisualBasic.ApplicationServices.StartupNextInstanceEventArgs)> Oluşturucu çağrıları <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UseCompatibleTextRendering%2A> belirlemek için uygulamanın formları kullanmak için hangi metin işleme altyapısı için özellik. Varsayılan olarak, <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UseCompatibleTextRendering%2A> özelliği döndürür `False`, GDI metin işleme altyapısı kullanılması gerektiğini belirten, olduğu varsayılan olarak [!INCLUDE[vbprvblong](~/includes/vbprvblong-md.md)]. Geçersiz kılabilirsiniz <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UseCompatibleTextRendering%2A> dönmek için özellik `True`, belirten GDI + metin işleme altyapısı kullanılmasını Visual Basic .NET 2002 ve Visual Basic .NET 2003'te varsayılan değerdir.  
  
## <a name="configuring-the-application"></a>Uygulamayı yapılandırma  
 Visual Basic uygulama modeli bir parçası olarak <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UseCompatibleTextRendering> sınıfı, uygulamayı yapılandırma korumalı özellikleri sağlar. Bu özellikleri uygulayan sınıfa oluşturucuda ayarlamanız gerekir.  
  
 Bir varsayılan Windows Forms projesinde **Proje Tasarımcısı** Tasarımcı ayarlarla özelliklerini ayarlamak için kod oluşturur. Yalnızca uygulama başlatılırken özellikleri kullanılır; Uygulama başlatıldıktan sonra bunları ayar etkisizdir.  
  
|Özellik|Belirler|Proje Tasarımcısı'nın uygulama bölmesinde ayarlama|  
|---|---|---|  
|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.IsSingleInstance%2A>|Olup uygulama Tek Örnekli veya birden çok örnek bir uygulama olarak çalışır.|**Tek örnek uygulamayı** onay kutusu|  
|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.EnableVisualStyles%2A>|Uygulamayı Windows XP eşleşen görsel stiller kullanıyorsa.|**XP görsel stilleri etkinleştir** onay kutusu|  
|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.SaveMySettingsOnExit%2A>|Uygulama çıktığında uygulama otomatik olarak uygulamanın kullanıcı ayarları değişikliklerini kaydederse.|**My.Settings kapanışında Kaydet** onay kutusu|  
|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.ShutdownStyle%2A>|Ne zaman başlangıç formu kapatır veya son form kapattığı zaman gibi sonlandırmak uygulamanın neden olur.|**Kapatma modu** listesi|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup>  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance>  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown>  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged>  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged>  
 [Visual Basic Uygulama Modeline Genel Bakış](../../../visual-basic/developing-apps/development-with-my/overview-of-the-visual-basic-application-model.md)  
 [Uygulama Sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
