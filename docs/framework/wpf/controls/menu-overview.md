---
title: Menüye Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- Menu control [WPF]
- controls [WPF], Menu
ms.assetid: 67df6de5-db96-4c71-b752-af90729a6537
ms.openlocfilehash: 53bc8f10e61b6e4e9e1f3b9a484340d9e2ec2a85
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186968"
---
# <a name="menu-overview"></a>Menüye Genel Bakış
Sınıf, <xref:System.Windows.Controls.Menu> komutlar ve olay işleyicileri ile ilişkili öğeleri hiyerarşik bir sırada düzenlemenize olanak tanır. Her <xref:System.Windows.Controls.Menu> öğe bir <xref:System.Windows.Controls.MenuItem> öğe koleksiyonu içerir.  

<a name="menu_control"></a>
## <a name="menu-control"></a>Menü Kontrolü  
 Denetim, <xref:System.Windows.Controls.Menu> bir uygulama için komutları veya seçenekleri belirten öğelerin listesini sunar. Genellikle, bir <xref:System.Windows.Controls.MenuItem> alt menüyü tıklatmak bir alt menüyü açar veya bir uygulamanın bir komut u gerçekleştirmesine neden olur.  
  
<a name="creating_menus"></a>
## <a name="creating-menus"></a>Menü Oluşturma  
 Aşağıdaki örnekte bir <xref:System.Windows.Controls.Menu> 'deki metni <xref:System.Windows.Controls.TextBox>işlemek için bir . <xref:System.Windows.Controls.Menu> ", <xref:System.Windows.Controls.MenuItem> <xref:System.Windows.Controls.MenuItem.Command%2A>, , <xref:System.Windows.Controls.MenuItem.IsCheckable%2A>ve özellikleri <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> ve <xref:System.Windows.Controls.MenuItem.Checked>, <xref:System.Windows.Controls.MenuItem.Unchecked>, <xref:System.Windows.Controls.MenuItem.Click> ve olayları kullanan nesneleri içerir.  
  
 [!code-xaml[MenuItemCommandsAndEvents#1](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuItemCommandsAndEvents/CSharp/Window1.xaml#1)]  
  
 [!code-csharp[MenuItemCommandsAndEvents#2](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuItemCommandsAndEvents/CSharp/Window1.xaml.cs#2)]
 [!code-vb[MenuItemCommandsAndEvents#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MenuItemCommandsAndEvents/VisualBasic/Window1.xaml.vb#2)]  
  
<a name="menus_with_shortcutkeys"></a>
## <a name="menuitems-with-keyboard-shortcuts"></a>Klavye Kısayollarından MenüÖğeler  
 Klavye kısayolları, komutları çağırmak <xref:System.Windows.Controls.Menu> için klavyeyle girilebilen karakter birleşimleridir. Örneğin, **Kopyalama** için kısayol CTRL+C'dir. Klavye kısayolları ve menü öğeleriyle birlikte<xref:System.Windows.Controls.MenuItem.InputGestureText%2A> kullanılacak <xref:System.Windows.Controls.MenuItem.Command%2A>iki özellik vardır — veya .  
  
<a name="menus_inputgesturetext"></a>
### <a name="inputgesturetext"></a>GirişJestMetni  
 Aşağıdaki örnekte, <xref:System.Windows.Controls.MenuItem.InputGestureText%2A> <xref:System.Windows.Controls.MenuItem> denetimlere klavye kısayol metni atamak için özelliğin nasıl kullanılacağı gösterilmektedir. Bu yalnızca klavye kısayolu menü öğesine yerleştirir.  Komutu <xref:System.Windows.Controls.MenuItem>. Uygulama, eylemi gerçekleştirmek için kullanıcının girdisini işlemelidir.  
  
 [!code-xaml[MenuEvent#6](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuEvent/CSharp/Pane1.xaml#6)]  
  
<a name="menus_commands"></a>
### <a name="command"></a>Komut  
 Aşağıdaki örnek, **Aç** ve <xref:System.Windows.Controls.MenuItem.Command%2A> **Kaydet** komutlarını denetimlerle <xref:System.Windows.Controls.MenuItem> ilişkilendirmek için özelliğin nasıl kullanılacağını gösterir. Komut özelliği yalnızca bir komutu <xref:System.Windows.Controls.MenuItem>bir , aynı zamanda kısayol olarak kullanmak üzere giriş hareketi metnini de sağlar.  
  
 [!code-xaml[MenuEvent#8](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuEvent/CSharp/Pane1.xaml#8)]  
  
 Sınıfın, <xref:System.Windows.Controls.MenuItem> komutun <xref:System.Windows.Controls.MenuItem.CommandTarget%2A> oluştuğu öğeyi belirten bir özelliği de vardır. Ayarlı <xref:System.Windows.Controls.MenuItem.CommandTarget%2A> değilse, klavye odağı olan öğe komutu alır. Komutlar hakkında daha fazla bilgi için komuta [genel bakışı'na](../advanced/commanding-overview.md)bakın.  
  
<a name="menu_styling"></a>
## <a name="menu-styling"></a>Menü Şekillendirme  
 Denetim stili ile, özel bir denetim yazmak <xref:System.Windows.Controls.Menu> zorunda kalmadan denetimlerin görünümünü ve davranışını önemli ölçüde değiştirebilirsiniz. Görsel özellikler ayarlamaya ek olarak, <xref:System.Windows.Style> denetimin tek tek bölümlerine de uygulayabilir, özellikler aracılığıyla denetimin bölümlerinin davranışını değiştirebilir veya ek parçalar ekleyebilir veya denetimin düzenini değiştirebilirsiniz. Aşağıdaki örnekler, denetime <xref:System.Windows.Style> <xref:System.Windows.Controls.Menu> a eklemenin çeşitli yollarını gösterir.  
  
 İlk kod örneği, <xref:System.Windows.Style> stilinizdeki geçerli sistem ayarlarını nasıl kullanacağınızı gösteren bir çağrı `Simple` tanımlar. Kod, menünün arka `MenuHighlightBrush` plan rengi olarak rengi ve `MenuTextBrush` menünün ön plan rengi olarak atar. Fırçaları atamak için kaynak anahtarlarını kullandığınıza dikkat edin.  
  
 [!code-xaml[MenuStylesSnippet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuStylesSnippet/CS/app.xaml#1)]  
  
 Aşağıdaki örnekte, <xref:System.Windows.Trigger> <xref:System.Windows.Controls.MenuItem> <xref:System.Windows.Controls.Menu>'de meydana gelen olaylara yanıt olarak bir görünümü değiştirmenizi sağlayan öğeler kullanılır. Fareyi , ön <xref:System.Windows.Controls.Menu>plan rengi ve menü öğelerinin yazı tipi özellikleri üzerinde hareket ettirdiğinizde değişir.  
  
 [!code-xaml[MenuStylesSnippet#2](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuStylesSnippet/CS/app.xaml#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WPF Denetimleri Galeri Örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/ControlsAndLayout)
