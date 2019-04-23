---
title: 'Nasıl yapılır: Komutu Etkinleştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CommandBindings [WPF]
- commanding [WPF]
ms.assetid: d8016266-58d9-48f7-8298-a86b7ed49fbd
ms.openlocfilehash: bf01066a35672e1996f193abc6d76153e5e9dd46
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59181707"
---
# <a name="how-to-enable-a-command"></a>Nasıl yapılır: Komutu Etkinleştirme
Aşağıdaki örnek, komut vermeye genel kullanımı gösterilmiştir [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  Örnek nasıl ilişkilendirildiğini gösterir. bir <xref:System.Windows.Input.RoutedCommand> için bir <xref:System.Windows.Controls.Button>, oluşturun bir <xref:System.Windows.Input.CommandBinding>ve uygulama olay işleyicileri oluşturma <xref:System.Windows.Input.RoutedCommand>.  Komut vermeye genel ile ilgili daha fazla bilgi için bkz: [komut vermeye genel genel bakış](commanding-overview.md).  
  
## <a name="example"></a>Örnek  
 Kodun ilk bölümünü oluşturur [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)], oluşan ve bir <xref:System.Windows.Controls.Button> ve <xref:System.Windows.Controls.StackPanel>, oluşturur bir <xref:System.Windows.Input.CommandBinding> komut işleyicileri ile ilişkilendirir <xref:System.Windows.Input.RoutedCommand>.  
  
 <xref:System.Windows.Input.ICommandSource.Command%2A> Özelliği <xref:System.Windows.Controls.Button> ilişkili olduğu <xref:System.Windows.Input.ApplicationCommands.Close%2A> komutu.  
  
 <xref:System.Windows.Input.CommandBinding> Eklenir <xref:System.Windows.Input.CommandBindingCollection> kök <xref:System.Windows.Window>. <xref:System.Windows.Input.CommandBinding.Executed> Ve <xref:System.Windows.Input.CommandBinding.CanExecute> olay işleyicileri bu bağlama bağlı ve ilişkili <xref:System.Windows.Input.ApplicationCommands.Close%2A> komutu.  
  
 Olmadan <xref:System.Windows.Input.CommandBinding> hiçbir komut mantığı çağırmak için yalnızca bir mekanizma yoktur.  Zaman <xref:System.Windows.Controls.Button> tıklandığında <xref:System.Windows.Input.CommandManager.PreviewExecuted> <xref:System.Windows.RoutedEvent> sonrasında komut hedefi üzerinde yükseltilmiş <xref:System.Windows.Input.CommandManager.Executed> <xref:System.Windows.RoutedEvent>.  Bu olayları aranırken öğesi ağacı gezme bir <xref:System.Windows.Input.CommandBinding> bu komuta için.  Bu, çünkü hatalarının ayıklanabileceğini belirtmekte yarar <xref:System.Windows.RoutedEvent> tüneli ve kabarcık öğe ağacında aracılığıyla, dikkatli olmalıdır alınması nerede <xref:System.Windows.Input.CommandBinding> konur.   Varsa <xref:System.Windows.Input.CommandBinding> komut hedefi üzerinde rotası değil başka bir düğüme veya bir eşdüzey açıktır <xref:System.Windows.RoutedEvent>, <xref:System.Windows.Input.CommandBinding> erişilemeyecektir.  
  
 [!code-xaml[EnableCloseCommand#CloseCommandBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/EnableCloseCommand/CSharp/Window1.xaml#closecommandbinding)]  
  
 [!code-csharp[EnableCloseCommand#CloseCommandBindingCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/EnableCloseCommand/CSharp/Window1.xaml.cs#closecommandbindingcodebehind)]
 [!code-vb[EnableCloseCommand#CloseCommandBindingCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/EnableCloseCommand/VisualBasic/Window1.xaml.vb#closecommandbindingcodebehind)]  
  
 Kod uygular, bir sonraki bölümüne <xref:System.Windows.Input.CommandManager.Executed> ve <xref:System.Windows.Input.CommandBinding.CanExecute> olay işleyicileri.  
  
 <xref:System.Windows.Input.CommandManager.Executed> İşleyici açık dosyayı kapatmak için bir yöntem çağırır.  <xref:System.Windows.Input.CommandBinding.CanExecute> İşleyici, bir dosya açık olup olmadığını belirlemek için bir yöntem çağırır.  Bir dosya açıksa <xref:System.Windows.Input.CanExecuteRoutedEventArgs.CanExecute%2A> ayarlanır `true`; Aksi takdirde ayarlanmış `false`.  
  
 [!code-csharp[EnableCloseCommand#CloseCommandHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/EnableCloseCommand/CSharp/Window1.xaml.cs#closecommandhandler)]
 [!code-vb[EnableCloseCommand#CloseCommandHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/EnableCloseCommand/VisualBasic/Window1.xaml.vb#closecommandhandler)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Komut Vermeye Genel Bakış](commanding-overview.md)
