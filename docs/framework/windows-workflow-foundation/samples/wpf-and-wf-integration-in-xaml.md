---
title: WPF ve WF tümleştirmesi XAML
ms.date: 03/30/2017
ms.assetid: a4f53b48-fc90-4315-bca0-ba009562f488
ms.openlocfilehash: ce6fc259b4e8743abd71e979825545183eef136a
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48777860"
---
# <a name="wpf-and-wf-integration-in-xaml"></a>WPF ve WF tümleştirmesi XAML
Bu örnek, tek bir XAML belgesi içinde Windows Presentation Foundation (WPF) ve Windows Workflow Foundation (WF) özelliklerini kullanan bir uygulamanın nasıl oluşturulacağını gösterir. Bunu yapmak için Windows Workflow Foundation (WF) ve XAML genişletilebilirlik örnek kullanır.

## <a name="sample-details"></a>Örnek Ayrıntıları
 İçine ShowWindow.xaml dosyası seri durumdan çıkarır bir <xref:System.Activities.Statements.Sequence> sırasının etkinlikleri tarafından yönetilen iki dize değişkeni etkinlikli: `ShowWindow` ve `WriteLine`. <xref:System.Activities.Statements.WriteLine> Etkinlik atar ifadesi konsol penceresine çıkarır <xref:System.Activities.Statements.WriteLine.Text%2A> özelliği. `ShowWindow` Etkinlik görüntüler bir [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] penceresi, yürütme mantığının parçası olarak. <xref:System.Activities.ActivityContext.DataContext%2A> Pencerenin sırada bildirilen değişkenler içerir. Pencerenin denetimleri bildirilen `ShowWindow` etkinliği değişkenlere işlemek için veri bağlama kullanın. Son olarak, bir düğme denetimi penceresi içerir. `Click` Düğme olayı tarafından işlenir bir <xref:System.Activities.ActivityDelegate> adlı `MarkupExtension` içeren bir `CloseWindow` etkinlik. `MarkUpExtension` çağıran tarafından tanımlanan herhangi bir nesne bağlamı olarak sağlayan içerilen bir etkinliği bir `x:Name`, hem de <xref:System.Activities.ActivityContext.DataContext%2A> içeren penceresinin. Bu nedenle, `CloseWindow.InArgument<Window>` pencerenin adına başvuran bir ifade kullanarak bağlanabilir.

 `ShowWindow` Etkinlik türetilir <xref:System.Activities.AsyncCodeActivity%601> görüntülenecek sınıf bir [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] penceresi ve penceresi kapatıldığında tamamlar. `Window` Özelliği türüdür `Func<Window>` her etkinliği yürütülmesi için isteğe bağlı olarak oluşturulacak penceresi sağlar. `Window` Özelliği kullanan bir <xref:System.Xaml.XamlDeferringLoader> bu ertelenmiş Değerlendirme modelini etkinleştirecek şekilde. `FuncFactoryDeferringLoader` Sağlayan bir `XamlReader` serileştirme sırasında yakalanan ve sonra da etkinlik yürütme sırasında okuyun.

 İyi yazılmış bir etkinlik, hiçbir zaman Zamanlayıcı iş parçacığını engeller. Ancak, `ShowWindow` etkinliği görüntüleme penceresi kapatılana kadar tamamlayamıyor. `ShowWindow` Etkinlik türeterek bu davranışı elde <xref:System.Activities.AsyncCodeActivity>çağırarak <xref:System.Activities.WorkflowInvoker.BeginInvoke%2A> yönteminde <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> yöntemi ve pencerenin kalıcı olarak gösteriliyor. Temsilci WPF çağrılan <xref:System.ServiceModel.InstanceContext.SynchronizationContext%2A>. `ShowWindow` Etkinlik atar <xref:System.Activities.ActivityContext.DataContext%2A> özelliğini `Window.DataContext` kapsamındaki değişkenlere herhangi bir veri sağlamak için özellik bağlı erişimi denetler.

 Bu örnekte ilgi son nokta bir <xref:System.Workflow.ComponentModel.Serialization.MarkupExtension> adlı `DelegateActivityExtension`. `ProvideValue` Yöntemi bu işaretleme uzantısı, katıştırılmış bir etkinlik çağıran bir temsilci döndürür. Bu etkinlik içeren bir ortamda çalışıyorsa [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] veri bağlamını ve `x:Name` kapsam değerleri. İçinde `GenericInvoke` yöntemi, bu ortama etkinliğine sağlanır bir <xref:System.Activities.Hosting.SymbolResolver> uzantısı. Bu uzantı eklenir bir <xref:System.Activities.WorkflowInvoker> sonra biçimlendirme uzantının temsilci çağrılır her katıştırılmış etkinlik çağırmak için kullanılır.

> [!NOTE]
>  Varsayılan Tasarımcı ShowWindow etkinlik desteklemiyor; Bu nedenle, ShowWindow.Xaml dosya Tasarımcısı'nda düzgün görüntülenmiyor.

#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için

1.  Visual Studio 2010 kullanarak WPFWFIntegration.sln çözüm dosyasını açın.

2.  Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.

3.  Çözümü çalıştırmak için F5 tuşuna basın.

4.  İlk ve son adınızı iletişim kutusuna yazın.

5.  İletişim kutusunu kapatın ve konsol adınızı görüntülemektedir.

> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\WPFWFIntegration`