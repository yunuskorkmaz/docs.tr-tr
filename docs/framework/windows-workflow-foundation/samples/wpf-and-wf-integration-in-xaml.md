---
description: "Daha fazla bilgi edinin: XAML 'de WPF ve Windows Workflow Foundation tümleştirme"
title: XAML içinde WPF ve WF tümleştirmesi
ms.date: 03/30/2017
ms.assetid: a4f53b48-fc90-4315-bca0-ba009562f488
ms.openlocfilehash: 3cc2d0336a2507dcf36fea3f3d240b95d22193e6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99798114"
---
# <a name="wpf-and-windows-workflow-foundation-integration-in-xaml"></a>XAML 'de WPF ve Windows Workflow Foundation tümleştirme

Bu örnek, tek bir XAML belgesinde Windows Presentation Foundation (WPF) ve Windows Workflow Foundation (WF) özelliklerini kullanan bir uygulamanın nasıl oluşturulacağını gösterir. Bunu gerçekleştirmek için örnek Windows Workflow Foundation ve XAML genişletilebilirliği kullanır.

## <a name="sample-details"></a>Örnek Ayrıntılar

 ShowWindow. xaml dosyası, <xref:System.Activities.Statements.Sequence> sıranın etkinlikleri tarafından yönetilen iki dize değişkeni ile bir etkinliğin serisini kaldırır: `ShowWindow` ve `WriteLine` . <xref:System.Activities.Statements.WriteLine>Etkinlik, konsol penceresine, özelliğe atadığı ifadeyi verir <xref:System.Activities.Statements.WriteLine.Text%2A> . `ShowWindow`Etkinlik, yürütme mantığının bir parçası olarak BIR WPF penceresi görüntüler. <xref:System.Activities.ActivityContext.DataContext%2A>Pencerenin, dizide belirtilen değişkenleri içerir. Etkinlikte belirtilen pencerenin denetimleri, `ShowWindow` Bu değişkenleri işlemek için veri bağlamayı kullanır. Son olarak, pencere bir düğme denetimi içerir. `Click`Düğme olayı, etkinlik içeren bir adlandırılmış tarafından işlenir <xref:System.Activities.ActivityDelegate> `MarkupExtension` `CloseWindow` . `MarkUpExtension` bağlam, tarafından tanımlanan tüm nesneler ve `x:Name` kapsayan pencerenin yanı sıra içerilen etkinlikleri çağırır <xref:System.Activities.ActivityContext.DataContext%2A> . Bu nedenle, `CloseWindow.InArgument<Window>` pencere adına başvuran bir ifade kullanılarak bağlanabilir.

 `ShowWindow`Etkinlik, <xref:System.Activities.AsyncCodeActivity%601> bir WPF penceresini göstermek ve pencere kapatıldığında tamamlanması için sınıfından türetilir. `Window`Özelliği, `Func<Window>` etkinliğin her yürütmesi için isteğe bağlı olarak pencerenin oluşturulmasına izin veren türdür. `Window`Özelliği, <xref:System.Xaml.XamlDeferringLoader> Bu ertelenmiş değerlendirme modelini etkinleştirmek için bir kullanır. , `FuncFactoryDeferringLoader` `XamlReader` Seri hale getirme sırasında yakalanmasına izin verir ve sonra Etkinlik yürütme sırasında okumaya devam edin.

 İyi yazılmış bir etkinlik zamanlayıcı iş parçacığını hiçbir şekilde engelmez. Ancak, `ShowWindow` görüntülenen pencere kapanana kadar etkinlik tamamlanamaz. `ShowWindow`Etkinlik, öğesinden türeterek, yöntemi yöntemi <xref:System.Activities.AsyncCodeActivity> <xref:System.Activities.WorkflowInvoker.BeginInvoke%2A> içinde çağırarak ve pencere yönetimini genel olarak göstererek bu davranışa erişir <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> . Temsilci WPF aracılığıyla çağrılır <xref:System.ServiceModel.InstanceContext.SynchronizationContext%2A> . `ShowWindow`Etkinlik, <xref:System.Activities.ActivityContext.DataContext%2A> `Window.DataContext` tüm veri bağlantılı denetimleri kapsam içi değişkenlere erişimi sağlamak için özelliği özelliğine atar.

 Bu örnekteki son ilgilendiğiniz noktaya bir <xref:System.Workflow.ComponentModel.Serialization.MarkupExtension> çağırılır `DelegateActivityExtension` . `ProvideValue`Bu biçimlendirme uzantısının yöntemi, katıştırılmış etkinlik çağıran bir temsilci döndürür. Bu etkinlik, WPF veri bağlamını ve kapsamdaki tüm değerleri içeren bir ortamda çalışır `x:Name` . `GenericInvoke`Yönteminde, bu ortam bir uzantı aracılığıyla etkinliğe sağlanır <xref:System.Activities.Hosting.SymbolResolver> . Bu uzantı, <xref:System.Activities.WorkflowInvoker> biçimlendirme uzantısının temsilcisi çağrıldığında gömülü etkinliği çağırmak için kullanılan bir öğesine eklenir.

> [!NOTE]
> Varsayılan Tasarımcı ShowWindow etkinliğini desteklemez; Bu nedenle, ShowWindow. xaml dosyası tasarımcıda doğru şekilde görüntülenmez.

## <a name="run-the-sample"></a>Örneği çalıştırma

1. Visual Studio 'yu kullanarak, Wpfwfintefin. sln çözüm dosyasını açın.

2. Çözümü derlemek için **CTRL** + **SHIFT** + **B** tuşlarına basın.

3. Çözümü çalıştırmak için **F5**'e basın.

4. İletişim kutusuna adınızı ve soyadınızı yazın.

5. İletişim kutusunu kapatın ve konsol adınızı yankılar.

> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\WPFWFIntegration`
