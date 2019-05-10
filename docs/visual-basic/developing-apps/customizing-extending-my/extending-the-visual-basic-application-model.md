---
title: Visual Basic Uygulama Modelini Genişletme
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic Application Model, extending
ms.assetid: e91d3bed-4c27-40e3-871d-2be17467c72c
ms.openlocfilehash: bb87879fdf584a439e09839bf4321b85e7dd6a43
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64602456"
---
# <a name="extending-the-visual-basic-application-model"></a>Visual Basic Uygulama Modelini Genişletme
Uygulama modeli için geçersiz kılarak işlevler ekleyebilirsiniz `Overridable` üyeleri <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> sınıfı. Bu teknik, uygulama modeli davranışını özelleştirip uygulama başlatıldığında ve kapanırken kendi yöntemlere yapılan çağrılar ekleyin sağlar.  
  
## <a name="visual-overview-of-the-application-model"></a>Uygulama modeli görsel genel bakış  
 Bu bölümde, Visual Basic uygulama modeli işlev çağrı görsel olarak sunar. Sonraki bölümde, her işlevin ayrıntılı amacını açıklar.  
  
 Aşağıdaki grafikte, normal bir Visual Basic Windows Forms uygulaması'nda uygulama modeli çağrı dizisini gösterir. Dizisi başlatılır `Sub Main` yordam çağrılarını <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Run%2A> yöntemi.  
  
 ![Uygulama modeli çağrı sırası gösteren diyagram.](./media/extending-the-visual-basic-application-model/application-model-call-sequence.gif)  
  
 Visual Basic uygulama modeli de sağlar <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance> ve <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> olayları. Aşağıdaki grafik, bu olayları oluşturma mekanizması gösterir.  
  
 ![StartupNextInstance olayı OnStartupNextInstance yöntemi gösteren diyagram.](./media/extending-the-visual-basic-application-model/raise-startupnextinstance-event.gif)  
  
 ![OnUnhandledException yöntemin UnhandledException olayı gösteren diyagram.](./media/extending-the-visual-basic-application-model/raise-unhandledexception-event.gif)  
  
## <a name="overriding-the-base-methods"></a>Taban yöntemleri geçersiz  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Run%2A> Yöntemi tanımlar sırası içinde `Application` yöntemleri çalıştırın. Varsayılan olarak, `Sub Main` bir Windows Forms uygulaması için yordam çağrıları <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Run%2A> yöntemi.  
  
 Uygulamanın normal bir uygulama (birden çok örnek uygulaması) veya bir tek örnekli uygulama ilk örneğinin olduğu durumlarda <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Run%2A> yöntemini yürütür `Overridable` aşağıdaki sırayla yöntemleri:  
  
1. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnInitialize%2A>. Varsayılan olarak, bu yöntem görsel stilleri, metin görüntü stilleri ve (uygulama Windows kimlik doğrulaması kullanıyorsa) ana uygulama iş parçacığına, geçerli sorumluyu ayarlar ve çağrıları `ShowSplashScreen` kullanılmazsa `/nosplash` ya da `-nosplash` olarak kullanılan bir komut satırı bağımsız değişkeni.  
  
     Bu işlev döndürürse uygulama başlatma sırası iptal `False`. Bu, uygulama değil çalıştırmalısınız durumlarda yararlı olabilir.  
  
     <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnInitialize%2A> Yöntemini aşağıdaki yöntemleri çağırır:  
  
    1. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.ShowSplashScreen%2A>. Uygulama tanımlı bir giriş ekranı sahip olup olmadığını belirler ve aşması durumunda, ayrı bir iş parçacığında giriş ekranı görüntüler.  
  
         <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.ShowSplashScreen%2A> Yöntemi Karşılama görüntüleyen kodu içeren en az belirtilen milisaniye sayısı için ekran <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MinimumSplashScreenDisplayTime%2A> özelliği. Bu işlevselliği kullanmak için giriş ekranı kullanarak uygulama eklemelisiniz **Proje Tasarımcısı** (hangi kümeleri `My.Application.MinimumSplashScreenDisplayTime` iki saniye özelliğini), veya `My.Application.MinimumSplashScreenDisplayTime` özelliğinde geçersizkılanbiryöntemi<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnInitialize%2A> veya <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateSplashScreen%2A> yöntemi. Daha fazla bilgi için bkz. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MinimumSplashScreenDisplayTime%2A>.  
  
    2. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateSplashScreen%2A>. Giriş ekranı başlatan kodu yaymak bir tasarımcı sağlar.  
  
         Varsayılan olarak, bu yöntemi hiçbir şey yapmaz. Visual Basic'te uygulamanız için giriş ekranı seçerseniz **Proje Tasarımcısı**, Tasarımcı geçersiz kılar <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateSplashScreen%2A> ayarlar yönteminin yöntemiyle <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.SplashScreen%2A> giriş ekranı formun yeni bir örneğini özelliği .  
  
2. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnStartup%2A>. Yükseltme için bir genişletilebilirlik noktası sağlar `Startup` olay. Bu işlev döndürürse, uygulama başlangıç dizisi durdurur `False`.  
  
     Varsayılan olarak, bu yöntem başlatır <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> olay. Olay işleyicisi ayarlarsa <xref:System.ComponentModel.CancelEventArgs.Cancel> olay bağımsız değişkenin özelliği `True`, yöntem döndürür `False` uygulama başlatma iptal etmek için.  
  
3. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnRun%2A>. Ana uygulama başlatma tamamlandıktan sonra çalıştırmaya başlamak hazır olduğunda için başlangıç noktası sağlar.  
  
     Varsayılan olarak, Windows Forms ileti döngüsü girer önce bu yöntemi çağırır `OnCreateMainForm` (uygulamanın ana formu oluşturmak için) ve `HideSplashScreen` (giriş ekranı kapatmak için) yöntemleri:  
  
    1. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A>. Ana formu başlatır kod yaymak bir tasarımcı için bir yol sağlar.  
  
         Varsayılan olarak, bu yöntemi hiçbir şey yapmaz. Ancak, seçtiğinizde, ana formu uygulamanızı Visual Basic için **Proje Tasarımcısı**, Tasarımcı geçersiz kılar <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A> ayarlar yönteminin yöntemiyle <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A> ana formu yeni bir örneğini özelliğini.  
  
    2. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.HideSplashScreen%2A>. Uygulama tanımlı bir giriş ekranı varsa ve açık olduğundan, bu yöntem, giriş ekranı kapatır.  
  
         Varsayılan olarak, bu yöntem, giriş ekranı kapatır.  
  
4. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnStartupNextInstance%2A>. Tek Örnekli uygulama başka bir örneği uygulama başladığında nasıl davranacağını özelleştirmek için bir yol sağlar.  
  
     Varsayılan olarak, bu yöntem başlatır <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance> olay.  
  
5. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnShutdown%2A>. Yükseltme için bir genişletilebilirlik noktası sağlar `Shutdown` olay. Ana uygulama içinde işlenmeyen bir özel durum oluşursa, bu yöntem çalışmaz.  
  
     Varsayılan olarak, bu yöntem başlatır <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown> olay.  
  
6. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnUnhandledException%2A>. Yukarıda listelenen yöntemlerden birini işlenmeyen bir özel durum oluşursa yürütülür.  
  
     Varsayılan olarak, bu yöntem başlatır <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> olay bir hata ayıklayıcısı iliştirilmemiş ve uygulama işleme sürece `UnhandledException` olay.  
  
 Uygulamanın tek örnekli bir uygulamadır ve uygulamanın zaten çalışıyor, uygulamanın sonraki örneği çağrıları <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnStartupNextInstance%2A> yöntemi özgün örneğinde uygulama ve ardından çıkış yapar.  
 
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnStartupNextInstance(Microsoft.VisualBasic.ApplicationServices.StartupNextInstanceEventArgs)> Oluşturucu çağrıları <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UseCompatibleTextRendering%2A> belirlemek için uygulamanın formları kullanmak için hangi metin işleme altyapısı için özellik. Varsayılan olarak, <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UseCompatibleTextRendering%2A> özelliği döndürür `False`, GDI metin işleme altyapısı kullanılması gerektiğini belirten, varsayılan değer olan içinde [!INCLUDE[vbprvblong](~/includes/vbprvblong-md.md)]. Geçersiz kılabilirsiniz <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UseCompatibleTextRendering%2A> dönmesini `True`, GDI +'da metin işleme altyapısı kullanılmasını gösteren Visual Basic .NET 2002 ve Visual Basic .NET 2003'te varsayılan değerdir.  
  
## <a name="configuring-the-application"></a>Uygulamayı yapılandırma  
 Visual Basic uygulama modeli, bir parçası olarak <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UseCompatibleTextRendering> sınıfı uygulamayı yapılandırma korumalı özellikler sağlar. Bu özellikleri uygulayan sınıfın oluşturucusunda ayarlanması gerekir.  
  
 Varsayılan Windows Forms projesinde **Proje Tasarımcısı** Tasarımcı ayarlarla özelliklerini ayarlamak için kod oluşturur. Özellikler, yalnızca uygulama başlatılırken kullanılır; Uygulama başlatıldıktan sonra bunları ayar etkisizdir.  
  
|Özellik|Belirler|Proje Tasarımcısı'nın uygulama bölmesinde ayarlama|  
|---|---|---|  
|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.IsSingleInstance%2A>|Olup uygulama, tekli veya çoklu örnek bir uygulama olarak çalışır.|**Tek Örnekli uygulama** onay kutusu|  
|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.EnableVisualStyles%2A>|Uygulama eşleşen Windows XP görsel stilleri kullanacaksanız.|**XP görsel stilleri etkinleştirme** onay kutusu|  
|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.SaveMySettingsOnExit%2A>|Uygulamadan çıkar zaman uygulama otomatik olarak uygulamanın kullanıcı ayarları değişiklikleri kaydeder|**My.Settings kapanışında Kaydet** onay kutusu|  
|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.ShutdownStyle%2A>|Hangi uygulamanın başlangıç formu kapattığı zaman veya ne zaman son formu kapatır gibi sonlandırılmasına neden olur.|**Kapatma** listesi|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged>
- [Visual Basic Uygulama Modeline Genel Bakış](../../../visual-basic/developing-apps/development-with-my/overview-of-the-visual-basic-application-model.md)
- [Uygulama Sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
