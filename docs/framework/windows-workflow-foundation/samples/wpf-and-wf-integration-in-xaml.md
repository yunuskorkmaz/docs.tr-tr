---
title: XAML içinde WPF ve WF tümleştirmesi
ms.date: 03/30/2017
ms.assetid: a4f53b48-fc90-4315-bca0-ba009562f488
ms.openlocfilehash: b8015e5c526f58875beb58ab48a21c050bdc8a06
ms.sourcegitcommit: 42ed59871db1f29a32b3d8e7abeb20e6eceeda7c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74960094"
---
# <a name="wpf-and-windows-workflow-foundation-integration-in-xaml"></a>XAML 'de WPF ve Windows Workflow Foundation tümleştirme

Bu örnek, tek bir XAML belgesinde Windows Presentation Foundation (WPF) ve Windows Workflow Foundation (WF) özelliklerini kullanan bir uygulamanın nasıl oluşturulacağını gösterir. Bunu gerçekleştirmek için örnek Windows Workflow Foundation ve XAML genişletilebilirliği kullanır.

## <a name="sample-details"></a>Örnek Ayrıntılar

 ShowWindow. xaml dosyası, sıranın etkinlikleri tarafından yönetilen iki dize değişkeni ile <xref:System.Activities.Statements.Sequence> bir etkinlikte serileştirilenleri gösterir: `ShowWindow` ve `WriteLine`. <xref:System.Activities.Statements.WriteLine> etkinliği konsol penceresine çıktı ve bu, <xref:System.Activities.Statements.WriteLine.Text%2A> özelliğine atadığı ifadedir. `ShowWindow` etkinliği, kendi yürütme mantığının bir parçası olarak bir WPF penceresi görüntüler. Pencerenin <xref:System.Activities.ActivityContext.DataContext%2A>, dizide belirtilen değişkenleri içerir. `ShowWindow` etkinliğinde belirtilen pencerenin denetimleri, bu değişkenleri işlemek için veri bağlamayı kullanır. Son olarak, pencere bir düğme denetimi içerir. Düğme için `Click` olayı, `CloseWindow` etkinliği içeren `MarkupExtension` adlı bir <xref:System.Activities.ActivityDelegate> tarafından işlenir. `MarkUpExtension`, bağlam, `x:Name`tarafından tanımlanan tüm nesneler ve kapsayan pencerenin <xref:System.Activities.ActivityContext.DataContext%2A> sağlayan içerilen etkinliği çağırır. Bu nedenle, `CloseWindow.InArgument<Window>` pencerenin adına başvuran bir ifade kullanılarak bağlanabilir.

 `ShowWindow` etkinliği, bir WPF penceresini göstermek ve pencere kapatıldığında tamamlanması için <xref:System.Activities.AsyncCodeActivity%601> sınıfından türetilir. `Window` özelliği, etkinliğin her yürütmesi için isteğe bağlı olarak pencerenin oluşturulmasına izin veren `Func<Window>` türüdür. `Window` özelliği, bu ertelenmiş değerlendirme modelini etkinleştirmek için bir <xref:System.Xaml.XamlDeferringLoader> kullanır. `FuncFactoryDeferringLoader`, serileştirme sırasında bir `XamlReader` yakalanmasına ve sonra Etkinlik yürütme sırasında okumaya olanak tanır.

 İyi yazılmış bir etkinlik zamanlayıcı iş parçacığını hiçbir şekilde engelmez. Ancak, `ShowWindow` etkinlik, görüntülenen pencere kapatılıncaya kadar tamamlanamaz. `ShowWindow` etkinliği, <xref:System.Activities.AsyncCodeActivity>türeterek, <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> yönteminde <xref:System.Activities.WorkflowInvoker.BeginInvoke%2A> yöntemini çağırarak ve pencere yönetimini bir şekilde göstererek bu davranışa erişir. Temsilci WPF <xref:System.ServiceModel.InstanceContext.SynchronizationContext%2A>çağrılır. `ShowWindow` etkinliği, tüm veri bağlantılı denetimleri kapsam içi değişkenlere erişimi sağlamak için `Window.DataContext` özelliğine <xref:System.Activities.ActivityContext.DataContext%2A> özelliğini atar.

 Bu örnekteki son ilgilendiğiniz nokta, `DelegateActivityExtension`adlı bir <xref:System.Workflow.ComponentModel.Serialization.MarkupExtension>. Bu biçimlendirme uzantısının `ProvideValue` yöntemi, katıştırılmış etkinlik çağıran bir temsilci döndürür. Bu etkinlik, WPF veri bağlamını ve kapsamdaki `x:Name` değerlerini içeren bir ortamda çalışır. `GenericInvoke` yönteminde, bu ortam etkinliğe bir <xref:System.Activities.Hosting.SymbolResolver> uzantısı aracılığıyla sağlanır. Bu uzantı, biçimlendirme uzantısının temsilcisi her çağrıldığında ekli etkinliği çağırmak için kullanılan bir <xref:System.Activities.WorkflowInvoker> eklenir.

> [!NOTE]
> Varsayılan Tasarımcı ShowWindow etkinliğini desteklemez; Bu nedenle, ShowWindow. xaml dosyası tasarımcıda doğru şekilde görüntülenmez.

## <a name="run-the-sample"></a>Örneği çalıştırma

1. Visual Studio 'yu kullanarak, Wpfwfintefin. sln çözüm dosyasını açın.

2. Çözümü derlemek için **Ctrl**+**SHIFT**+**B**' ye basın.

3. Çözümü çalıştırmak için **F5**'e basın.

4. İletişim kutusuna adınızı ve soyadınızı yazın.

5. İletişim kutusunu kapatın ve konsol adınızı yankılar.

> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek, aşağıdaki dizinde bulunur.
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\WPFWFIntegration`
