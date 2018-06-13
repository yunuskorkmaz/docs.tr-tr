---
title: 'İzlenecek yol: İlk Dokunmatik Uygulamanızı Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- creating a touch-sensitive application [WPF]
- touchscreen applications [WPF], creating
- touch-sensitive applications [WPF], creating
- creating a touchscreen application [WPF]
ms.assetid: d69e602e-9a25-4e24-950b-e89eaa2a906b
ms.openlocfilehash: 94a97c30179f7a8231426e31b8cacc364629ffc3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33548357"
---
# <a name="walkthrough-creating-your-first-touch-application"></a>İzlenecek yol: İlk Dokunmatik Uygulamanızı Oluşturma
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamaları dokunma yanıtlamak için etkinleştirir. Örneğin, birini kullanarak bir uygulama ile etkileşim kurabilir veya dokunmatik aygıtta, bu kılavuzda taşımak kullanıcı sağlayan bir uygulama oluşturur dokunmatik gibi daha fazla parmakları yeniden boyutlandırın veya touch kullanarak tek bir nesneyi döndürme.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:  
  
-   [!INCLUDE[vs_dev10_ext](../../../../includes/vs-dev10-ext-md.md)].  
  
-   Windows 7.  
  
-   Dokunma kabul eden bir aygıtı Windows Touch destekleyen bir dokunmatik gibi girin.  
  
 Ayrıca, bir uygulama oluşturmak nasıl temel bir anlayış olmalıdır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], abone ve bir olay işlemek özellikle nasıl. Daha fazla bilgi için bkz: [gözden geçirme: ilk WPF Masaüstü Uygulamam](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md).  
  
## <a name="creating-the-application"></a>Uygulama oluşturma  
  
#### <a name="to-create-the-application"></a>Uygulama oluşturmak için  
  
1.  Visual Basic veya Visual C# adlı yeni bir WPF uygulaması projesi oluşturduğunuzda `BasicManipulation`. Daha fazla bilgi için bkz: [nasıl yapılır: yeni bir WPF uygulaması projesi oluşturduğunuzda](http://msdn.microsoft.com/library/1f6aea7a-33e1-4d3f-8555-1daa42e95d82).  
  
2.  MainWindow.xaml içeriğini aşağıdaki XAML ile değiştirin.  
  
     Kırmızı içeren basit bir uygulama bu biçimlendirme oluşturur <xref:System.Windows.Shapes.Rectangle> üzerinde bir <xref:System.Windows.Controls.Canvas>. <xref:System.Windows.UIElement.IsManipulationEnabled%2A> Özelliği <xref:System.Windows.Shapes.Rectangle> işleme olayları alacak böylece true olarak ayarlanır. Uygulama abone <xref:System.Windows.UIElement.ManipulationStarting>, <xref:System.Windows.UIElement.ManipulationDelta>, ve <xref:System.Windows.UIElement.ManipulationInertiaStarting> olaylar. Bu olaylar taşımak için mantığı içeren <xref:System.Windows.Shapes.Rectangle> zaman kullanıcı yönetir.  
  
     [!code-xaml[BasicManipulation#UI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicmanipulation/csharp/mainwindow.xaml#ui)]  
  
3.  Visual Basic, ilk satırındaki kullanıyorsanız yerine `x:Class="BasicManipulation.MainWindow"` ile `x:Class="MainWindow"`.  
  
4.  İçinde `MainWindow` sınıfında, aşağıdaki ekleyin <xref:System.Windows.UIElement.ManipulationStarting> olay işleyicisi.  
  
     <xref:System.Windows.UIElement.ManipulationStarting> Olaylarının zaman [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dokunma algılar bir nesneyi düzenlemek için giriş başlar. Kod düzenleme konumunu göreli olması gerektiğini belirtir <xref:System.Windows.Window> ayarlayarak <xref:System.Windows.Input.ManipulationStartingEventArgs.ManipulationContainer%2A> özelliği.  
  
     [!code-csharp[BasicManipulation#ManipulationStarting](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicmanipulation/csharp/mainwindow.xaml.cs#manipulationstarting)]
     [!code-vb[BasicManipulation#ManipulationStarting](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/basicmanipulation/visualbasic/mainwindow.xaml.vb#manipulationstarting)]  
  
5.  İçinde `MainWindow` sınıfında, aşağıdaki ekleyin <xref:System.Windows.Input.ManipulationDelta> olay işleyicisi.  
  
     <xref:System.Windows.Input.ManipulationDelta> Olay oluşur dokunma girişi konumu değiştirdiğinde ve birden çok kez yaptığı değişiklik sırasında ortaya çıkabilir. Olay, bir parmak kaldırıldıktan sonra da oluşabilir. Örneğin, kullanıcının bir parmak ekran boyunca sürüklediği <xref:System.Windows.Input.ManipulationDelta> olayı parmak hareket ettikçe birden çok kez oluşur. Kullanıcı bir parmak ekranından başlatır, <xref:System.Windows.Input.ManipulationDelta> olay eylemsizlik benzetimini yapmak için gerçekleşen tutar.  
  
     Kod uygular <xref:System.Windows.Input.ManipulationDeltaEventArgs.DeltaManipulation%2A> için <xref:System.Windows.UIElement.RenderTransform%2A> , <xref:System.Windows.Shapes.Rectangle> taşımak için kullanıcı dokunma taşınırken giriş. Ayrıca denetler olup olmadığını <xref:System.Windows.Shapes.Rectangle> sınırları dışında <xref:System.Windows.Window> olayı sırasında eylemsizlik oluştuğunda. Bu nedenle, uygulama çağırırsa <xref:System.Windows.Input.ManipulationDeltaEventArgs.Complete%2A?displayProperty=nameWithType> düzenlemeyi sonlandırmak için yöntem.  
  
     [!code-csharp[BasicManipulation#ManipulationDelta](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicmanipulation/csharp/mainwindow.xaml.cs#manipulationdelta)]
     [!code-vb[BasicManipulation#ManipulationDelta](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/basicmanipulation/visualbasic/mainwindow.xaml.vb#manipulationdelta)]  
  
6.  İçinde `MainWindow` sınıfında, aşağıdaki ekleyin <xref:System.Windows.UIElement.ManipulationInertiaStarting> olay işleyicisi.  
  
     <xref:System.Windows.UIElement.ManipulationInertiaStarting> Kullanıcı ekranından tüm parmakları başlatır olay oluşur. Kod ilk hız ve taşıma, genişletme ve dikdörtgen dönüşünü yavaşlama ayarlar.  
  
     [!code-csharp[BasicManipulation#ManipulationInertiaStarting](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicmanipulation/csharp/mainwindow.xaml.cs#manipulationinertiastarting)]
     [!code-vb[BasicManipulation#ManipulationInertiaStarting](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/basicmanipulation/visualbasic/mainwindow.xaml.vb#manipulationinertiastarting)]  
  
7.  Oluşturun ve projeyi çalıştırın.  
  
     Penceresinde görünür bir kırmızı kare görmeniz gerekir.  
  
## <a name="testing-the-application"></a>Uygulamayı Test Etme  
 Uygulamayı test etmek için aşağıdaki düzenlemeleri deneyin. Aşağıdaki aynı anda birden çok işlemi gerçekleştirebileceğinizi unutmayın.  
  
-   Taşımak için <xref:System.Windows.Shapes.Rectangle>, bir parmak yerleştirin <xref:System.Windows.Shapes.Rectangle> ve parmak ekranda hareket ettirin.  
  
-   Yeniden boyutlandırmak için <xref:System.Windows.Shapes.Rectangle>, iki parmakları yerleştirin <xref:System.Windows.Shapes.Rectangle> ve parmakları yakın birlikte veya birbirlerinden uzağına taşıyın.  
  
-   Döndürmek için <xref:System.Windows.Shapes.Rectangle>, iki parmakları yerleştirin <xref:System.Windows.Shapes.Rectangle> ve parmakları birbiri etrafında döndürün.  
  
 Eylemsizlik neden olmak için önceki işlemeleri gerçekleştirme gibi parmakları ekranından hızlı bir şekilde yükseltin. <xref:System.Windows.Shapes.Rectangle> Taşımak, yeniden boyutlandırmak veya durdurulmadan önce birkaç saniye boyunca devam eder.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.UIElement.ManipulationStarting?displayProperty=nameWithType>  
 <xref:System.Windows.UIElement.ManipulationDelta?displayProperty=nameWithType>  
 <xref:System.Windows.UIElement.ManipulationInertiaStarting?displayProperty=nameWithType>
