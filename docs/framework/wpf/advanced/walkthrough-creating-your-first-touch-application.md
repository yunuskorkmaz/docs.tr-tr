---
title: 'İzlenecek yol: İlk dokunmatik uygulamanızı oluşturma'
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
ms.openlocfilehash: 2ebf22775ab9308bc896829be0b4e8cc147a3b4c
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57374160"
---
# <a name="walkthrough-creating-your-first-touch-application"></a>İzlenecek yol: İlk dokunmatik uygulamanızı oluşturma
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dokunmaya yanıt uygulamaları etkinleştirir. Örneğin, birini kullanarak bir uygulama ile etkileşim kurabilir veya daha fazla parmağınızı bir dokunmaya duyarlı cihazda dokunmatik ekranı sunduğumuz taşımak kullanıcı sağlayan bir uygulama oluşturur. Örneğin, yeniden boyutlandırma veya touch'ı kullanarak tek bir nesne döndürme.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:  
  
-   Visual Studio.  
  
-   Dokunma kabul eden bir cihaz Windows Dokunma destekleyen bir dokunmatik gibi girin.  
  
 Ayrıca, uygulamayı oluşturmak nasıl temel bir anlayışa sahip olmalıdır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], özellikle abone olma ve bir olayı işlemek nasıl. Daha fazla bilgi için [izlenecek yol: İlk WPF Masaüstü Uygulamam](../getting-started/walkthrough-my-first-wpf-desktop-application.md).  
  
## <a name="creating-the-application"></a>Uygulama oluşturma  
  
#### <a name="to-create-the-application"></a>Uygulama oluşturmak için  
  
1.  Visual Basic veya Visual C# adlı yeni bir WPF uygulaması projesi oluşturma `BasicManipulation`. Daha fazla bilgi için [izlenecek yol: İlk WPF Masaüstü Uygulamam](../getting-started/walkthrough-my-first-wpf-desktop-application.md).  
  
2.  MainWindow.xaml içeriğini aşağıdaki XAML ile değiştirin.  
  
     Bu işaretleme kırmızı içeren basit bir uygulama oluşturur <xref:System.Windows.Shapes.Rectangle> üzerinde bir <xref:System.Windows.Controls.Canvas>. <xref:System.Windows.UIElement.IsManipulationEnabled%2A> Özelliği <xref:System.Windows.Shapes.Rectangle> olayları düzenleme alabileceklerdir true olarak ayarlanır. Uygulama abone <xref:System.Windows.UIElement.ManipulationStarting>, <xref:System.Windows.UIElement.ManipulationDelta>, ve <xref:System.Windows.UIElement.ManipulationInertiaStarting> olayları. Bu olaylar taşımak için mantığı içeren <xref:System.Windows.Shapes.Rectangle> zaman kullanıcı yönetir.  
  
     [!code-xaml[BasicManipulation#UI](~/samples/snippets/csharp/VS_Snippets_Wpf/basicmanipulation/csharp/mainwindow.xaml#ui)]  
  
3.  Visual Basic kullanıyorsanız MainWindow.xaml öğesinin ilk satırı değiştirin `x:Class="BasicManipulation.MainWindow"` ile `x:Class="MainWindow"`.  
  
4.  İçinde `MainWindow` sınıfında, aşağıdaki <xref:System.Windows.UIElement.ManipulationStarting> olay işleyicisi.  
  
     <xref:System.Windows.UIElement.ManipulationStarting> Olaylarının zaman [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dokunma algılar nesneyi işlemek için giriş başlar. Kod düzenleme konumu göreli olması gerektiğini belirtir. <xref:System.Windows.Window> ayarlayarak <xref:System.Windows.Input.ManipulationStartingEventArgs.ManipulationContainer%2A> özelliği.  
  
     [!code-csharp[BasicManipulation#ManipulationStarting](~/samples/snippets/csharp/VS_Snippets_Wpf/basicmanipulation/csharp/mainwindow.xaml.cs#manipulationstarting)]
     [!code-vb[BasicManipulation#ManipulationStarting](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicmanipulation/visualbasic/mainwindow.xaml.vb#manipulationstarting)]

5.  İçinde `MainWindow` sınıfında, aşağıdaki <xref:System.Windows.Input.ManipulationDelta> olay işleyicisi.

     <xref:System.Windows.Input.ManipulationDelta> Olaylarının dokunma girişi değişiklikleri konumu ve düzenleme sırasında birden çok kez gerçekleşebilir. Olay, bir parmak kaldırıldıktan sonra da meydana gelebilir. Örneğin, kullanıcı bir ekranda bir parmak sürüklediğinde <xref:System.Windows.Input.ManipulationDelta> olay parmağınızı hareket ettikçe birden çok kez gerçekleşir. Kullanıcı bir parmak ekranından çektiğinde <xref:System.Windows.Input.ManipulationDelta> tutan bir olayın gerçekleşmesi Eylemsizliği benzetimini yapmak için.

     Kod geçerli <xref:System.Windows.Input.ManipulationDeltaEventArgs.DeltaManipulation%2A> için <xref:System.Windows.UIElement.RenderTransform%2A> , <xref:System.Windows.Shapes.Rectangle> taşımak için kullanıcı touch taşınırken giriş. Ayrıca denetler olmadığını <xref:System.Windows.Shapes.Rectangle> sınırları dışında <xref:System.Windows.Window> sırasında Eylemsizliği oluştuğunda olay. Bu nedenle, uygulama çağırırsa <xref:System.Windows.Input.ManipulationDeltaEventArgs.Complete%2A?displayProperty=nameWithType> düzenlemeyi sonlandırmak için yöntemi.

     [!code-csharp[BasicManipulation#ManipulationDelta](~/samples/snippets/csharp/VS_Snippets_Wpf/basicmanipulation/csharp/mainwindow.xaml.cs#manipulationdelta)]
     [!code-vb[BasicManipulation#ManipulationDelta](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicmanipulation/visualbasic/mainwindow.xaml.vb#manipulationdelta)]

6.  İçinde `MainWindow` sınıfında, aşağıdaki <xref:System.Windows.UIElement.ManipulationInertiaStarting> olay işleyicisi.

     <xref:System.Windows.UIElement.ManipulationInertiaStarting> Olay kullanıcı ekrandan tüm parmağınızı çektiğinde gerçekleşir. Bu kod, taşıma, genişletmeyi ve döndürme için yavaşlama ve başlangıç hızı ayarlar.

     [!code-csharp[BasicManipulation#ManipulationInertiaStarting](~/samples/snippets/csharp/VS_Snippets_Wpf/basicmanipulation/csharp/mainwindow.xaml.cs#manipulationinertiastarting)]
     [!code-vb[BasicManipulation#ManipulationInertiaStarting](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicmanipulation/visualbasic/mainwindow.xaml.vb#manipulationinertiastarting)]

7.  Derleme ve projeyi çalıştırın.

     Penceresinde görünen bir kırmızı kare görmeniz gerekir.

## <a name="testing-the-application"></a>Uygulamayı Test Etme
 Uygulamayı test etmek için aşağıdaki düzenlemeleri deneyin. Aşağıdaki aynı anda birden çok işlemi gerçekleştirebileceğinizi unutmayın.

-   Taşımak <xref:System.Windows.Shapes.Rectangle>, böylece parmağınızı yerleştirip <xref:System.Windows.Shapes.Rectangle> ve ekranda parmağınızı hareket ettirin.

-   Yeniden boyutlandırmak için <xref:System.Windows.Shapes.Rectangle>, iki parmağınızı yerleştirip <xref:System.Windows.Shapes.Rectangle> parmağınızı yaklaşacak şekilde veya birbirlerinden küçüldükleri taşıyın.

-   Döndürülecek <xref:System.Windows.Shapes.Rectangle>, iki parmağınızı yerleştirip <xref:System.Windows.Shapes.Rectangle> ve parmağınızı birbirine etrafında döndürün.

 Eylemsizlik neden olmak için önceki işlemeleri gerçekleştirme gibi parmaklarınızın ekranından hızlı bir şekilde yükseltin. <xref:System.Windows.Shapes.Rectangle> Taşıma, yeniden boyutlandırmak veya durdurulmadan önce birkaç saniye boyunca devam eder.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.UIElement.ManipulationStarting?displayProperty=nameWithType>
- <xref:System.Windows.UIElement.ManipulationDelta?displayProperty=nameWithType>
- <xref:System.Windows.UIElement.ManipulationInertiaStarting?displayProperty=nameWithType>