---
title: Visual Basic Uygulama Modelini Genişletme
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic Application Model, extending
ms.assetid: e91d3bed-4c27-40e3-871d-2be17467c72c
ms.openlocfilehash: 02a964506d976cb10f3f28f83f0655fecc447e59
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582759"
---
# <a name="extending-the-visual-basic-application-model"></a>Visual Basic Uygulama Modelini Genişletme

@No__t_1 sınıfının `Overridable` üyelerini geçersiz kılarak uygulama modeline işlevler ekleyebilirsiniz. Bu teknik, uygulama modelinin davranışını özelleştirmenize ve uygulama Başlarken ve kapandığında kendi yöntemlerinize çağrılar eklemenize olanak tanır.

## <a name="visual-overview-of-the-application-model"></a>Uygulama modeline görsel genel bakış

Bu bölüm, Visual Basic uygulama modelindeki işlev çağrılarının dizisini görsel olarak gösterir. Sonraki bölümde her bir işlevin amacı ayrıntılı olarak açıklanmaktadır.

Aşağıdaki grafikte, bir normal Visual Basic Windows Forms uygulamasındaki uygulama modeli çağrı sırası gösterilmektedir. Sıra, `Sub Main` yordam <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Run%2A> yöntemini çağırdığında başlar.

![Uygulama modeli çağrı sırasını gösteren diyagram.](./media/extending-the-visual-basic-application-model/application-model-call-sequence.gif)

Visual Basic uygulama modeli <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance> ve <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> olaylarını da sağlar. Aşağıdaki grafiklerde bu olayları oluşturma mekanizması gösterilmektedir.

![StartupNextInstance olayını harekete yükselterek OnStartupNextInstance metodunu gösteren diyagram.](./media/extending-the-visual-basic-application-model/raise-startupnextinstance-event.gif)

![UnhandledException olayını harekete yükselterek OnUnhandledException metodunu gösteren diyagram.](./media/extending-the-visual-basic-application-model/raise-unhandledexception-event.gif)

## <a name="overriding-the-base-methods"></a>Temel yöntemleri geçersiz kılma

@No__t_0 yöntemi, `Application` yöntemlerinin çalıştığı sırayı tanımlar. Varsayılan olarak, bir Windows Forms uygulaması için `Sub Main` yordamı <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Run%2A> yöntemini çağırır.

Uygulama normal bir uygulama (birden çok örnekli uygulama) veya tek örnekli bir uygulamanın ilk örneği ise <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Run%2A> yöntemi `Overridable` yöntemlerini aşağıdaki sırayla yürütür:

1. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnInitialize%2A>. Varsayılan olarak, bu yöntem, ana uygulama iş parçacığı için görsel stilleri, metin görüntüleme stillerini ve geçerli sorumluyu (uygulama Windows kimlik doğrulaması kullanıyorsa) ve bir komut satırı bağımsız değişkeni olarak ne `/nosplash` ne de `-nosplash` kullanılmazsa `ShowSplashScreen` çağırır.

     Bu işlev `False` döndürürse uygulama başlatma sırası iptal edilir. Bu, uygulamanın çalıştırılmamalıdır durumlar olduğunda yararlı olabilir.

     @No__t_0 yöntemi aşağıdaki yöntemleri çağırır:

    1. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.ShowSplashScreen%2A>. Uygulamanın tanımlanmış bir giriş ekranı olup olmadığını belirler ve varsa, giriş ekranını ayrı bir iş parçacığında görüntüler.

         @No__t_0 yöntemi, en az <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MinimumSplashScreenDisplayTime%2A> özelliği tarafından belirtilen milisaniye sayısı için giriş ekranını görüntüleyen kodu içerir. Bu işlevi kullanmak için, **Proje tasarımcısını** kullanarak (`My.Application.MinimumSplashScreenDisplayTime` özelliğini iki saniye olarak ayarlayan) Giriş ekranını uygulamanıza eklemeniz veya <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnInitialize%2A> ya da <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateSplashScreen%2A> yöntemini geçersiz kılan bir yöntemde `My.Application.MinimumSplashScreenDisplayTime` özelliğini ayarlamanız gerekir. Daha fazla bilgi için bkz. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MinimumSplashScreenDisplayTime%2A>.

    2. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateSplashScreen%2A>. Tasarımcı 'nın giriş ekranını başlatan kodu yaymanızı sağlar.

         Varsayılan olarak, bu yöntem hiçbir şey yapmaz. Visual Basic **Proje tasarımcısında**uygulamanız için bir giriş ekranı seçerseniz, tasarımcı, <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateSplashScreen%2A> yöntemini <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.SplashScreen%2A> özelliğini giriş ekranı formunun yeni bir örneğine ayarlayan bir yöntemle geçersiz kılar.

2. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnStartup%2A>. @No__t_0 olayını yükseltmek için bir genişletilebilirlik noktası sağlar. Bu işlev `False` döndürürse uygulama başlatma sırası duraklar.

     Varsayılan olarak, bu yöntem <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> olayını başlatır. Olay işleyicisi, olay bağımsız değişkeninin <xref:System.ComponentModel.CancelEventArgs.Cancel> özelliğini `True` olarak ayarlarsa, yöntem uygulama başlangıcını iptal etmek için `False` döndürür.

3. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnRun%2A>. Başlatma yapıldıktan sonra, ana uygulamanın çalışmaya başlamaya hazırlandığı zaman için başlangıç noktası sağlar.

     Varsayılan olarak, Windows Forms ileti döngüsüne girmeden önce, bu yöntem `OnCreateMainForm` (uygulamanın ana formunu oluşturmak için) ve `HideSplashScreen` (Giriş ekranını kapatmak için) yöntemleri çağırır:

    1. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A>. Tasarımcı 'nın ana formu başlatan kodu yayma yolunu sağlar.

         Varsayılan olarak, bu yöntem hiçbir şey yapmaz. Ancak, Visual Basic **projesi tasarımcısında**uygulamanız için bir ana form seçtiğinizde, tasarımcı, <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A> yöntemini <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A> özelliğini bir ana formun yeni bir örneğine ayarlayan bir yöntemle geçersiz kılar.

    2. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.HideSplashScreen%2A>. Uygulamanın tanımlanmış bir giriş ekranı varsa ve açık ise, bu yöntem giriş ekranını kapatır.

         Varsayılan olarak, bu yöntem giriş ekranını kapatır.

4. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnStartupNextInstance%2A>. Uygulamanın başka bir örneği başlatıldığında tek örnekli bir uygulamanın nasıl davrandığını özelleştirmek için bir yol sağlar.

     Varsayılan olarak, bu yöntem <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance> olayını başlatır.

5. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnShutdown%2A>. @No__t_0 olayını yükseltmek için bir genişletilebilirlik noktası sağlar. Bu yöntem, ana uygulamada işlenmeyen bir özel durum oluşursa çalışmaz.

     Varsayılan olarak, bu yöntem <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown> olayını başlatır.

6. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnUnhandledException%2A>. Yukarıda listelenen yöntemlerin herhangi birinde işlenmeyen bir özel durum oluşursa yürütülür.

     Varsayılan olarak, bu yöntem bir hata ayıklayıcı bağlı olmadığı ve uygulamanın `UnhandledException` olayını işlediği sürece <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> olayını oluşturur.

 Uygulama tek örnekli bir uygulama ise ve uygulama zaten çalışıyorsa, uygulamanın sonraki örneği uygulamanın özgün örneğinde <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnStartupNextInstance%2A> yöntemini çağırır ve sonra çıkar.

 @No__t_0 Oluşturucusu, uygulamanın formları için hangi metin işleme altyapısının kullanılacağını belirleyen <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UseCompatibleTextRendering%2A> özelliğini çağırır. Varsayılan olarak, <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UseCompatibleTextRendering%2A> özelliği `False` döndürür ve bu, Visual Basic 2005 ve sonraki sürümlerde varsayılan değer olan GDI metin işleme altyapısının kullanıldığını gösterir. @No__t_1 döndürmek için <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UseCompatibleTextRendering%2A> özelliğini geçersiz kılabilirsiniz. Bu, Visual Basic .NET 2002 ve Visual Basic .NET 2003 ' de varsayılan değer olan GDI+ metin işleme altyapısının kullanıldığını gösterir.

## <a name="configuring-the-application"></a>Uygulamayı yapılandırma
 Visual Basic uygulama modelinin bir parçası olarak, <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> sınıfı, uygulamayı yapılandıran korumalı özellikler sağlar. Bu özellikler, uygulama sınıfının oluşturucusunda ayarlanmalıdır.

 Varsayılan Windows Forms projesinde **Proje Tasarımcısı** , özellikleri tasarımcı ayarlarıyla ayarlamak için kod oluşturur. Özellikler yalnızca uygulama başlatıldığında kullanılır; uygulamanın başladıktan sonra ayarların ayarlanması etkisizdir.

|Özellik|Saptayan|Proje Tasarımcısı 'nın uygulama bölmesinde ayarı|
|---|---|---|
|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.IsSingleInstance%2A>|Uygulamanın tek örnekli veya birden çok örnekli bir uygulama olarak çalıştırılıp çalıştırılmayacağı.|**Tek örnekli uygulama oluştur** onay kutusu|
|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.EnableVisualStyles%2A>|Uygulama, Windows XP ile eşleşen görsel stilleri kullanacaksanız.|**XP görsel stillerini etkinleştir** onay kutusu|
|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.SaveMySettingsOnExit%2A>|Uygulama, uygulamanın çıkış sırasında otomatik olarak uygulamanın kullanıcı ayarları değişikliklerini kaydederse.|**My. Settings 'ı kapatmadan kaydet** onay kutusu|
|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.ShutdownStyle%2A>|Başlangıç formu kapandığında veya son form kapandığında, uygulamanın sonlanmasına neden olur.|**Kapalı mod** listesi|

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged>
- [Visual Basic Uygulama Modeline Genel Bakış](../../../visual-basic/developing-apps/development-with-my/overview-of-the-visual-basic-application-model.md)
- [Uygulama Sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
