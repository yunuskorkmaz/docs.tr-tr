---
title: Menüye Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- Menu control [WPF]
- controls [WPF], Menu
ms.assetid: 67df6de5-db96-4c71-b752-af90729a6537
ms.openlocfilehash: 3d5cfba0734e684349f7d73b7242f4b69089b94d
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124656"
---
# <a name="menu-overview"></a>Menüye Genel Bakış
<xref:System.Windows.Controls.Menu> sınıfı, komutlarla ve olay işleyicileriyle ilişkili öğeleri hiyerarşik bir düzende düzenlemenizi sağlar. Her <xref:System.Windows.Controls.Menu> öğesi bir <xref:System.Windows.Controls.MenuItem> öğeleri koleksiyonu içerir.  

<a name="menu_control"></a>   
## <a name="menu-control"></a>Menü denetimi  
 <xref:System.Windows.Controls.Menu> denetim, bir uygulama için komutları veya seçenekleri belirten öğelerin bir listesini sunar. Genellikle, bir <xref:System.Windows.Controls.MenuItem> tıklamak bir alt menü açar veya bir uygulamanın bir komutu gerçekleştirmesini sağlar.  
  
<a name="creating_menus"></a>   
## <a name="creating-menus"></a>Menüler oluşturma  
 Aşağıdaki örnek, bir <xref:System.Windows.Controls.TextBox>metni işlemek için bir <xref:System.Windows.Controls.Menu> oluşturur. <xref:System.Windows.Controls.Menu>, <xref:System.Windows.Controls.MenuItem.Command%2A>, <xref:System.Windows.Controls.MenuItem.IsCheckable%2A>ve <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> özelliklerini ve <xref:System.Windows.Controls.MenuItem.Checked>, <xref:System.Windows.Controls.MenuItem.Unchecked>ve <xref:System.Windows.Controls.MenuItem.Click> olaylarını kullanan <xref:System.Windows.Controls.MenuItem> nesneleri içerir.  
  
 [!code-xaml[MenuItemCommandsAndEvents#1](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuItemCommandsAndEvents/CSharp/Window1.xaml#1)]  
  
 [!code-csharp[MenuItemCommandsAndEvents#2](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuItemCommandsAndEvents/CSharp/Window1.xaml.cs#2)]
 [!code-vb[MenuItemCommandsAndEvents#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MenuItemCommandsAndEvents/VisualBasic/Window1.xaml.vb#2)]  
  
<a name="menus_with_shortcutkeys"></a>   
## <a name="menuitems-with-keyboard-shortcuts"></a>Klavye kısayollarıyla MenuItems  
 Klavye kısayolları, <xref:System.Windows.Controls.Menu> komutları çağırmak için klavyeyle girilebilecek karakter birleşimleridir. Örneğin, **Kopyala** kısayolu Ctrl + C ' dir. Klavye kısayolları ve menü öğeleri (<xref:System.Windows.Controls.MenuItem.InputGestureText%2A> veya <xref:System.Windows.Controls.MenuItem.Command%2A>ile birlikte kullanabileceğiniz iki özellik vardır.  
  
<a name="menus_inputgesturetext"></a>   
### <a name="inputgesturetext"></a>InputGestureText  
 Aşağıdaki örnek, <xref:System.Windows.Controls.MenuItem> denetimlerine klavye kısayol metni atamak için <xref:System.Windows.Controls.MenuItem.InputGestureText%2A> özelliğinin nasıl kullanılacağını gösterir. Bu yalnızca klavye kısayolunu menü öğesine koyar.  Komutu <xref:System.Windows.Controls.MenuItem>ile ilişkilendirmez. Uygulamanın, eylemi gerçekleştirmek için kullanıcının girişini işlemesi gerekir.  
  
 [!code-xaml[MenuEvent#6](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuEvent/CSharp/Pane1.xaml#6)]  
  
<a name="menus_commands"></a>   
### <a name="command"></a>Komut  
 Aşağıdaki örnek, **Aç** ve **Kaydet** komutlarını <xref:System.Windows.Controls.MenuItem> denetimleriyle ilişkilendirmek için <xref:System.Windows.Controls.MenuItem.Command%2A> özelliğinin nasıl kullanılacağını gösterir. Komut özelliği yalnızca bir komutu <xref:System.Windows.Controls.MenuItem>ile ilişkilendirmez, ancak kısayol olarak kullanılacak giriş hareketi metnini de sağlar.  
  
 [!code-xaml[MenuEvent#8](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuEvent/CSharp/Pane1.xaml#8)]  
  
 <xref:System.Windows.Controls.MenuItem> sınıfı ayrıca komutun gerçekleştiği öğeyi belirten bir <xref:System.Windows.Controls.MenuItem.CommandTarget%2A> özelliğine sahiptir. <xref:System.Windows.Controls.MenuItem.CommandTarget%2A> ayarlanmamışsa, klavye odağı olan öğe komutu alır. Komutlar hakkında daha fazla bilgi için bkz. [komut verme genel bakış](../advanced/commanding-overview.md).  
  
<a name="menu_styling"></a>   
## <a name="menu-styling"></a>Menü stili oluşturma  
 Denetim stillendirmesiyle, <xref:System.Windows.Controls.Menu> denetimlerinin görünümünü ve davranışını özel bir denetim yazmak zorunda kalmadan önemli ölçüde değiştirebilirsiniz. Görsel özellikleri ayarlamaya ek olarak, bir denetimin tek tek bölümlerine bir <xref:System.Windows.Style> uygulayabilir, denetimin bölümlerinin davranışını özellikler aracılığıyla değiştirebilir veya bir denetimin yerleşimini değiştirebilirsiniz. Aşağıdaki örneklerde, bir <xref:System.Windows.Controls.Menu> denetimine <xref:System.Windows.Style> eklemenin birkaç yolu gösterilmektedir.  
  
 İlk kod örneği, stilinize geçerli sistem ayarlarının nasıl kullanılacağını gösteren `Simple` adlı bir <xref:System.Windows.Style> tanımlar. Kod, `MenuHighlightBrush` rengini menünün arka plan rengi ve `MenuTextBrush` menünün ön plan rengi olarak atar. Fırçaları atamak için kaynak anahtarlarını kullanacağınızı unutmayın.  
  
 [!code-xaml[MenuStylesSnippet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuStylesSnippet/CS/app.xaml#1)]  
  
 Aşağıdaki örnek, <xref:System.Windows.Controls.Menu>oluşan olaylara yanıt olarak bir <xref:System.Windows.Controls.MenuItem> görünümünü değiştirmenize olanak tanıyan <xref:System.Windows.Trigger> öğelerini kullanır. Fareyi <xref:System.Windows.Controls.Menu>üzerine getirdiğinizde, ön plan rengi ve menü öğelerinin yazı tipi özellikleri değişir.  
  
 [!code-xaml[MenuStylesSnippet#2](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuStylesSnippet/CS/app.xaml#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WPF denetimleri Galeri örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/ControlsAndLayout)
