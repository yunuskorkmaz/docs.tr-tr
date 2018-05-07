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
ms.openlocfilehash: 47abd36558864116e5f5ed921419c374c064e2cc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-hook-up-a-command-to-a-control-with-command-support"></a>Nasıl yapılır: Komut Destekli Denetime Komut Bağlama
Aşağıdaki örnek e nasıl bağlanacağını gösterir bir <xref:System.Windows.Input.RoutedCommand> için bir <xref:System.Windows.Controls.Control> komutu desteği içinde yerleşik.  Birden çok kaynak komutları tam bir örnek için bkz: [özel bağlayan örneği oluşturma](http://go.microsoft.com/fwlink/?LinkID=159980) örnek.  
  
## <a name="example"></a>Örnek  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Uygulama programcıları düzenli olarak karşılaştığı yaygın komutları kitaplığını sağlar.  Komut kitaplığı oluşturan sınıfları şunlardır: <xref:System.Windows.Input.ApplicationCommands>, <xref:System.Windows.Input.ComponentCommands>, <xref:System.Windows.Input.NavigationCommands>, <xref:System.Windows.Input.MediaCommands>, ve <xref:System.Windows.Documents.EditingCommands>.  
  
 Statik <xref:System.Windows.Input.RoutedCommand> bu sınıfları yapan nesneleri komut mantığı sağlamaz.  Komutu için mantığı komutu ile ilişkilendirilmiş bir <xref:System.Windows.Input.CommandBinding>.  Bazı denetimler CommandBindings bazı komutlar için yerleşik sahiptir.  Bir komut gerçek uygulamayı olsa da aynı kalmasını semantiği değiştirebilirsiniz Bu mekanizma sağlar.  A <xref:System.Windows.Controls.TextBox>, örneğin, işleme <xref:System.Windows.Input.ApplicationCommands.Paste%2A> görüntüleri desteklemek için tasarlanmış bir denetim, ancak bir şeyi yapıştırmanın anlamı temel olarak aynı kalır daha farklı komutu.  Komut mantığı komutu tarafından sağlanan, ancak bunun yerine denetim veya uygulama tarafından sağlanmalıdır.  
  
 Birçok denetimlerinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yerleşik desteğe sahiptir bazı komut kitaplığı komutlar için.  <xref:System.Windows.Controls.TextBox>, örneğin, uygulama Düzenle komutların çoğu gibi destekleyen <xref:System.Windows.Input.ApplicationCommands.Paste%2A>, <xref:System.Windows.Input.ApplicationCommands.Copy%2A>, <xref:System.Windows.Input.ApplicationCommands.Cut%2A>, <xref:System.Windows.Input.ApplicationCommands.Redo%2A>, ve <xref:System.Windows.Input.ApplicationCommands.Undo%2A>.  Uygulama geliştiricisinin bu denetimlerle çalışmak üzere bu komutları almak için özel bir şey yapmanız gerekmez.  Varsa <xref:System.Windows.Controls.TextBox> komut hedefi komutu çalıştırıldığında komutunu kullanarak işleyecek <xref:System.Windows.Input.CommandBinding> denetime oluşturulur.  
  
 Aşağıdaki nasıl kullanılacağını gösterir bir <xref:System.Windows.Controls.MenuItem> komut kaynağı olarak <xref:System.Windows.Input.ApplicationCommands.Paste%2A> komutu, burada bir <xref:System.Windows.Controls.TextBox> komutu hedefidir.  Tanımlayan tüm mantığı nasıl <xref:System.Windows.Controls.TextBox> gerçekleştirir ve yapıştırmayı yerleşik <xref:System.Windows.Controls.TextBox> denetim.  
  
 A <xref:System.Windows.Controls.MenuItem> oluşturulur ve bu <xref:System.Windows.Controls.MenuItem.Command%2A> özelliği ayarlanmış <xref:System.Windows.Input.ApplicationCommands.Paste%2A> komutu.  <xref:System.Windows.Controls.MenuItem.CommandTarget%2A> Açıkça ayarlanmazsa <xref:System.Windows.Controls.TextBox> nesnesi.  Zaman <xref:System.Windows.Controls.MenuItem.CommandTarget%2A> ayarlı değil, hedef komutu klavye odağı olan öğedir.  Klavye odağı olan öğe desteklemiyorsa <xref:System.Windows.Input.ApplicationCommands.Paste%2A> komutunu veya şu anda (Pano boş olduğundan, örneğin) Yapıştır komutu yürütülemiyor sonra <xref:System.Windows.Controls.MenuItem> gri.  
  
 [!code-xaml[MenuItemCommandTask_XAML#MenuItemCommanding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuItemCommandTask_XAML/CS/Window1.xaml#menuitemcommanding)]  
  
 [!code-csharp[MenuItemCommandTask#MenuItemCommandingCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuItemCommandTask/CSharp/Window1.xaml.cs#menuitemcommandingcodebehind)]
 [!code-vb[MenuItemCommandTask#MenuItemCommandingCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MenuItemCommandTask/VisualBasic/Window1.xaml.vb#menuitemcommandingcodebehind)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Komut Vermeye Genel Bakış](../../../../docs/framework/wpf/advanced/commanding-overview.md)  
 [Komut Desteği Olmadan Denetime Komut Bağlama](../../../../docs/framework/wpf/advanced/how-to-hook-up-a-command-to-a-control-with-no-command-support.md)
