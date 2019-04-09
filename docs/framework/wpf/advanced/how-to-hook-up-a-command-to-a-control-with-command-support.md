---
title: 'Nasıl yapılır: Komut Destekli Denetime Komut Bağlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Control class [WPF], attaching a RoutedCommand
- classes [WPF], Control [WPF], attaching a RoutedCommand
- RoutedCommand class [WPF], attaching to a Control
- classes [WPF], RoutedCommand [WPF], attaching to a Control
ms.assetid: 8d8592ae-0c91-469e-a1cd-d179c4544548
ms.openlocfilehash: 981fecf33b60c76ecab760185db7dab4bbb254d7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59165212"
---
# <a name="how-to-hook-up-a-command-to-a-control-with-command-support"></a>Nasıl yapılır: Komut Destekli Denetime Komut Bağlama
Aşağıdaki örnek e nasıl bağlanacağını gösterir. bir <xref:System.Windows.Input.RoutedCommand> için bir <xref:System.Windows.Controls.Control> komutu desteği de yerleşik.  Komutları için birden çok kaynaktan eksiksiz bir örnek için bkz. [örnek bir özel RoutedCommand oluşturma](https://github.com/Microsoft/WPF-Samples/tree/master/Input%20and%20Commands/CustomRoutedCommand) örnek.  
  
## <a name="example"></a>Örnek  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] düzenli olarak uygulama programcıların karşılaştığı yaygın komutları içeren bir kitaplık sağlar.  Komut kitaplığı oluşturan sınıfları: <xref:System.Windows.Input.ApplicationCommands>, <xref:System.Windows.Input.ComponentCommands>, <xref:System.Windows.Input.NavigationCommands>, <xref:System.Windows.Input.MediaCommands>, ve <xref:System.Windows.Documents.EditingCommands>.  
  
 Statik <xref:System.Windows.Input.RoutedCommand> bu sınıfları oluşturan nesneleri komut mantıksal sağlamaz.  Mantıksal komutu için komut ile ilişkili bir <xref:System.Windows.Input.CommandBinding>.  Bazı denetimler CommandBindings bazı komutlar için oluşturdunuz.  Bu mekanizma, bir komut gerçek uygulama olsa da aynı kalmasını semantiği değiştirebilirsiniz sağlar.  A <xref:System.Windows.Controls.TextBox>, örneğin, işleme <xref:System.Windows.Input.ApplicationCommands.Paste%2A> görüntüleri desteklemek için tasarlanmış bir denetimi, ancak yapıştırmanın ne demek, temel olarak aynı kalır daha farklı komutu.  Komut mantığını komutu tarafından sağlanan, ancak bunun yerine bir denetim veya uygulama tarafından sağlanmalıdır.  
  
 Birçok denetimlerinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sahip yerleşik bazı komut kitaplığındaki komutları için destek.  <xref:System.Windows.Controls.TextBox>, örneğin, birçok uygulama Düzenle komutu gibi destekleyen <xref:System.Windows.Input.ApplicationCommands.Paste%2A>, <xref:System.Windows.Input.ApplicationCommands.Copy%2A>, <xref:System.Windows.Input.ApplicationCommands.Cut%2A>, <xref:System.Windows.Input.ApplicationCommands.Redo%2A>, ve <xref:System.Windows.Input.ApplicationCommands.Undo%2A>.  Uygulama geliştiricisinin bu denetimleri ile çalışmak için bu komutları almak için özel bir şey yapmanız gerekmez.  Varsa <xref:System.Windows.Controls.TextBox> komut hedefi komut yürütüldüğünde, komutunu kullanarak işleyecek <xref:System.Windows.Input.CommandBinding> denetime oluşturulur.  
  
 Aşağıdakileri nasıl kullanılacağını gösterir. bir <xref:System.Windows.Controls.MenuItem> komut kaynağı olarak <xref:System.Windows.Input.ApplicationCommands.Paste%2A> komutu, burada bir <xref:System.Windows.Controls.TextBox> komut hedefi.  Tanımlayan tüm mantığı nasıl <xref:System.Windows.Controls.TextBox> gerçekleştirir ve yapıştırmayı yerleşiktir <xref:System.Windows.Controls.TextBox> denetimi.  
  
 A <xref:System.Windows.Controls.MenuItem> oluşturulur ve <xref:System.Windows.Controls.MenuItem.Command%2A> özelliği <xref:System.Windows.Input.ApplicationCommands.Paste%2A> komutu.  <xref:System.Windows.Controls.MenuItem.CommandTarget%2A> Açıkça ayarlanmazsa <xref:System.Windows.Controls.TextBox> nesne.  Zaman <xref:System.Windows.Controls.MenuItem.CommandTarget%2A> ayarlı değil, hedef komut için klavye girintisine sahip olan öğe.  Klavye girintisine sahip olan öğe desteklemiyorsa <xref:System.Windows.Input.ApplicationCommands.Paste%2A> komutunu ya da şu anda (Pano boş olduğundan, örneğin) Yapıştır komut yürütülemiyor sonra <xref:System.Windows.Controls.MenuItem> gri.  
  
 [!code-xaml[MenuItemCommandTask_XAML#MenuItemCommanding](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuItemCommandTask_XAML/CS/Window1.xaml#menuitemcommanding)]  
  
 [!code-csharp[MenuItemCommandTask#MenuItemCommandingCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuItemCommandTask/CSharp/Window1.xaml.cs#menuitemcommandingcodebehind)]
 [!code-vb[MenuItemCommandTask#MenuItemCommandingCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MenuItemCommandTask/VisualBasic/Window1.xaml.vb#menuitemcommandingcodebehind)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Komut Vermeye Genel Bakış](commanding-overview.md)
- [Komut Desteği Olmadan Denetime Komut Bağlama](how-to-hook-up-a-command-to-a-control-with-no-command-support.md)
