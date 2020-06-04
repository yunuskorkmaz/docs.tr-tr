---
title: Visual Basic Uygulama Modelini Genişletme
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic Application Model, extending
ms.assetid: e91d3bed-4c27-40e3-871d-2be17467c72c
ms.openlocfilehash: e707f034f05aababdc70d5d6e1f9e1da0ed558bc
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410237"
---
# <a name="extending-the-visual-basic-application-model"></a>Visual Basic Uygulama Modelini Genişletme

Sınıfının üyelerini geçersiz kılarak uygulama modeline işlevler ekleyebilirsiniz `Overridable` <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> . Bu teknik, uygulama modelinin davranışını özelleştirmenize ve uygulama Başlarken ve kapandığında kendi yöntemlerinize çağrılar eklemenize olanak tanır.

## <a name="visual-overview-of-the-application-model"></a>Uygulama modeline görsel genel bakış

Bu bölüm, Visual Basic uygulama modelindeki işlev çağrılarının dizisini görsel olarak gösterir. Sonraki bölümde her bir işlevin amacı ayrıntılı olarak açıklanmaktadır.

Aşağıdaki grafikte, bir normal Visual Basic Windows Forms uygulamasındaki uygulama modeli çağrı sırası gösterilmektedir. Dizi, `Sub Main` yordam yöntemini çağırdığında başlar <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Run%2A> .

![Uygulama modeli çağrı sırasını gösteren diyagram.](./media/extending-the-visual-basic-application-model/application-model-call-sequence.gif)

Visual Basic uygulama modeli ve olaylarını da sağlar <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance> <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> . Aşağıdaki grafiklerde bu olayları oluşturma mekanizması gösterilmektedir.

![StartupNextInstance olayını harekete yükselterek OnStartupNextInstance metodunu gösteren diyagram.](./media/extending-the-visual-basic-application-model/raise-startupnextinstance-event.gif)

![UnhandledException olayını harekete yükselterek OnUnhandledException metodunu gösteren diyagram.](./media/extending-the-visual-basic-application-model/raise-unhandledexception-event.gif)

## <a name="overriding-the-base-methods"></a>Temel yöntemleri geçersiz kılma

<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Run%2A>Yöntemi, `Application` yöntemlerinin çalıştırılacağı sırayı tanımlar. Varsayılan olarak, `Sub Main` bir Windows Forms uygulama yordamı <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Run%2A> yöntemini çağırır.

Uygulama normal bir uygulama (birden çok örnekli uygulama) veya tek örnekli bir uygulamanın ilk örneği ise, <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Run%2A> yöntemi `Overridable` aşağıdaki sırayla yöntemleri yürütür:

1. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnInitialize%2A>. Bu yöntem, varsayılan olarak, görsel stilleri, metin görüntüleme stillerini ve ana uygulama iş parçacığı (uygulama Windows kimlik doğrulaması kullanıyorsa) için geçerli sorumluyu ve `ShowSplashScreen` `/nosplash` `-nosplash` bir komut satırı bağımsız değişkeni olarak ne yoksa veya kullanılmıyorsa çağrıları ayarlar.

     Bu işlev döndürürse uygulama başlatma sırası iptal edilir `False` . Bu, uygulamanın çalıştırılmamalıdır durumlar olduğunda yararlı olabilir.

     <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnInitialize%2A>Yöntemi aşağıdaki yöntemleri çağırır:

    1. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.ShowSplashScreen%2A>. Uygulamanın tanımlanmış bir giriş ekranı olup olmadığını belirler ve varsa, giriş ekranını ayrı bir iş parçacığında görüntüler.

         <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.ShowSplashScreen%2A>Yöntemi, en az özelliği tarafından belirtilen milisaniye sayısı için giriş ekranını görüntüleyen kodu içerir <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MinimumSplashScreenDisplayTime%2A> . Bu işlevi kullanmak için, **Proje tasarımcısını** kullanarak (özelliği iki saniyeye ayarlayan) Giriş ekranını uygulamanıza eklemeniz `My.Application.MinimumSplashScreenDisplayTime` veya `My.Application.MinimumSplashScreenDisplayTime` özelliğini veya yöntemini geçersiz kılan bir yöntemde ayarlamanız gerekir <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnInitialize%2A> <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateSplashScreen%2A> . Daha fazla bilgi için bkz. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MinimumSplashScreenDisplayTime%2A>.

    2. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateSplashScreen%2A>. Tasarımcı 'nın giriş ekranını başlatan kodu yaymanızı sağlar.

         Varsayılan olarak, bu yöntem hiçbir şey yapmaz. Visual Basic **Proje tasarımcısında**uygulamanız için bir giriş ekranı seçerseniz, tasarımcı <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateSplashScreen%2A> yöntemi, <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.SplashScreen%2A> özelliği giriş ekranı formunun yeni bir örneğine ayarlayan bir yöntemle geçersiz kılar.

2. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnStartup%2A>. Olayı yükseltmek için bir genişletilebilirlik noktası sağlar `Startup` . Bu işlev döndürürse uygulama başlatma sırası duraklar `False` .

     Bu yöntem, varsayılan olarak olayını oluşturur <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> . Olay işleyicisi, <xref:System.ComponentModel.CancelEventArgs.Cancel> olay bağımsız değişkeninin özelliğini olarak ayarlarsa `True` , yöntemi `False` uygulama başlangıcını iptal etmek için döndürür.

3. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnRun%2A>. Başlatma yapıldıktan sonra, ana uygulamanın çalışmaya başlamaya hazırlandığı zaman için başlangıç noktası sağlar.

     Varsayılan olarak, Windows Forms ileti döngüsüne girmeden önce, bu yöntem `OnCreateMainForm` (uygulamanın ana formunu oluşturmak için) ve `HideSplashScreen` (Giriş ekranını kapatmak için) yöntemlerini çağırır:

    1. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A>. Tasarımcı 'nın ana formu başlatan kodu yayma yolunu sağlar.

         Varsayılan olarak, bu yöntem hiçbir şey yapmaz. Ancak, Visual Basic **projesi tasarımcısında**uygulamanız için bir ana form seçtiğinizde, tasarımcı <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A> yöntemi <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A> özelliği, ana formun yeni bir örneğine ayarlayan bir yöntemle geçersiz kılar.

    2. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.HideSplashScreen%2A>. Uygulamanın tanımlanmış bir giriş ekranı varsa ve açık ise, bu yöntem giriş ekranını kapatır.

         Varsayılan olarak, bu yöntem giriş ekranını kapatır.

4. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnStartupNextInstance%2A>. Uygulamanın başka bir örneği başlatıldığında tek örnekli bir uygulamanın nasıl davrandığını özelleştirmek için bir yol sağlar.

     Bu yöntem, varsayılan olarak olayını oluşturur <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance> .

5. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnShutdown%2A>. Olayı yükseltmek için bir genişletilebilirlik noktası sağlar `Shutdown` . Bu yöntem, ana uygulamada işlenmeyen bir özel durum oluşursa çalışmaz.

     Bu yöntem, varsayılan olarak olayını oluşturur <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown> .

6. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnUnhandledException%2A>. Yukarıda listelenen yöntemlerin herhangi birinde işlenmeyen bir özel durum oluşursa yürütülür.

     Varsayılan olarak, bu yöntem <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> bir hata ayıklayıcı bağlı olmadığı ve uygulamanın olayı işlediği sürece olayı başlatır `UnhandledException` .

 Uygulama tek örnekli bir uygulama ise ve uygulama zaten çalışıyorsa, uygulamanın sonraki örneği uygulamanın <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnStartupNextInstance%2A> özgün örneğindeki yöntemi çağırır ve sonra çıkar.

 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnStartupNextInstance(Microsoft.VisualBasic.ApplicationServices.StartupNextInstanceEventArgs)>Oluşturucu, <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UseCompatibleTextRendering%2A> uygulamanın formları için hangi metin işleme altyapısının kullanılacağını belirleyen özelliği çağırır. Varsayılan olarak, <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UseCompatibleTextRendering%2A> özelliği, `False` GDI metin işleme altyapısının kullanıldığını (Visual Basic 2005 ve sonraki sürümlerde varsayılan değer) gösterir. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UseCompatibleTextRendering%2A> `True` Visual Basic .NET 2002 ve Visual Basic .NET 2003 ' de varsayılan değer olan GDI+ metin işleme altyapısının kullanıldığını gösteren döndürecek özelliği geçersiz kılabilirsiniz.

## <a name="configuring-the-application"></a>Uygulamayı yapılandırma

 Visual Basic uygulama modelinin bir parçası olarak <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> sınıfı, uygulamayı yapılandıran korumalı özellikler sağlar. Bu özellikler, uygulama sınıfının oluşturucusunda ayarlanmalıdır.

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
- [Visual Basic Uygulama Modeline Genel Bakış](../development-with-my/overview-of-the-visual-basic-application-model.md)
- [Uygulama Sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
