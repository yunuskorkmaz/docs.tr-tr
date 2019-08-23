---
title: XAML içinde WPF ve WF tümleştirmesi
ms.date: 03/30/2017
ms.assetid: a4f53b48-fc90-4315-bca0-ba009562f488
ms.openlocfilehash: 8b461ee3185aa60e885d7cc107124c37d9ffacef
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69948958"
---
# <a name="wpf-and-wf-integration-in-xaml"></a>XAML içinde WPF ve WF tümleştirmesi
Bu örnek, tek bir XAML belgesinde Windows Presentation Foundation (WPF) ve Windows Workflow Foundation (WF) özelliklerini kullanan bir uygulamanın nasıl oluşturulacağını gösterir. Bunu gerçekleştirmek için örnek Windows Workflow Foundation (WF) ve XAML genişletilebilirliği kullanır.

## <a name="sample-details"></a>Örnek Ayrıntılar
 ShowWindow. xaml dosyası, sıranın etkinlikleri tarafından yönetilen iki <xref:System.Activities.Statements.Sequence> dize değişkeni ile bir etkinliğin serisini kaldırır: `ShowWindow` ve `WriteLine`. Etkinlik, konsol penceresine, <xref:System.Activities.Statements.WriteLine.Text%2A> özelliğe atadığı ifadeyi verir. <xref:System.Activities.Statements.WriteLine> Etkinlik `ShowWindow` , yürütme mantığının bir parçası olarak bir WPF penceresi görüntüler. Pencerenin <xref:System.Activities.ActivityContext.DataContext%2A> , dizide belirtilen değişkenleri içerir. `ShowWindow` Etkinlikte belirtilen pencerenin denetimleri, bu değişkenleri işlemek için veri bağlamayı kullanır. Son olarak, pencere bir düğme denetimi içerir. Düğme olayı, etkinlik`CloseWindow` içeren bir <xref:System.Activities.ActivityDelegate> adlandırılmış `MarkupExtension` tarafından işlenir. `Click` `MarkUpExtension`bağlam, tarafından `x:Name`tanımlanan tüm nesneler ve kapsayan pencerenin yanı sıra <xref:System.Activities.ActivityContext.DataContext%2A> içerilen etkinlikleri çağırır. `CloseWindow.InArgument<Window>` Bu nedenle, pencere adına başvuran bir ifade kullanılarak bağlanabilir.

 Etkinlik, bir WPF penceresini <xref:System.Activities.AsyncCodeActivity%601> göstermek ve pencere kapatıldığında tamamlanması için sınıfından türetilir. `ShowWindow` Özelliği, etkinliğin her yürütmesi için isteğe bağlı olarak pencerenin oluşturulmasına izin veren türdür `Func<Window>`. `Window` Özelliği `Window` , bu ertelenmiş <xref:System.Xaml.XamlDeferringLoader> değerlendirme modelini etkinleştirmek için bir kullanır. , `FuncFactoryDeferringLoader` Seri hale `XamlReader` getirme sırasında yakalanmasına izin verir ve sonra Etkinlik yürütme sırasında okumaya devam edin.

 İyi yazılmış bir etkinlik zamanlayıcı iş parçacığını hiçbir şekilde engelmez. Ancak, `ShowWindow` görüntülenen pencere kapanana kadar etkinlik tamamlanamaz. Etkinlik, öğesinden <xref:System.Activities.AsyncCodeActivity>türeterek, yöntemi yöntemi içinde <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> çağırarak <xref:System.Activities.WorkflowInvoker.BeginInvoke%2A> ve pencere yönetimini genel olarak göstererek bu davranışa erişir. `ShowWindow` Temsilci WPF <xref:System.ServiceModel.InstanceContext.SynchronizationContext%2A>aracılığıyla çağrılır. Etkinlik, tüm veri <xref:System.Activities.ActivityContext.DataContext%2A> bağlantılı denetimleri kapsam `Window.DataContext` içi değişkenlere erişimi sağlamak için özelliği özelliğine atar. `ShowWindow`

 Bu örnekteki son ilgilendiğiniz noktaya bir <xref:System.Workflow.ComponentModel.Serialization.MarkupExtension> çağırılır. `DelegateActivityExtension` Bu `ProvideValue` biçimlendirme uzantısının yöntemi, katıştırılmış etkinlik çağıran bir temsilci döndürür. Bu etkinlik, WPF veri bağlamını ve kapsamdaki tüm `x:Name` değerleri içeren bir ortamda çalışır. Yönteminde, bu ortam bir <xref:System.Activities.Hosting.SymbolResolver> uzantı aracılığıyla etkinliğe sağlanır. `GenericInvoke` Bu uzantı, biçimlendirme uzantısının temsilcisi <xref:System.Activities.WorkflowInvoker> çağrıldığında gömülü etkinliği çağırmak için kullanılan bir öğesine eklenir.

> [!NOTE]
> Varsayılan Tasarımcı ShowWindow etkinliğini desteklemez; Bu nedenle, ShowWindow. xaml dosyası tasarımcıda doğru şekilde görüntülenmez.

#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için

1. Visual Studio 2010 kullanarak, Wpfwfintefin. sln çözüm dosyasını açın.

2. Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.

3. Çözümü çalıştırmak için F5 'e basın.

4. İletişim kutusuna adınızı ve soyadınızı yazın.

5. İletişim kutusunu kapatın ve konsol adınızı yankılar.

> [!IMPORTANT]
>  Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\WPFWFIntegration`
