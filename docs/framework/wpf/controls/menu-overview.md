---
title: Menüye Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- Menu control [WPF]
- controls [WPF], Menu
ms.assetid: 67df6de5-db96-4c71-b752-af90729a6537
ms.openlocfilehash: a3250cfd3fd651cb4ed3c4fd6975f5b5c89195f9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59166380"
---
# <a name="menu-overview"></a>Menüye Genel Bakış
<xref:System.Windows.Controls.Menu> Sınıfı komutlara ve olay işleyicilerine hiyerarşik sırayla ilişkili öğeleri düzenlemenize olanak sağlar. Her <xref:System.Windows.Controls.Menu> öğesi içeren bir koleksiyon, <xref:System.Windows.Controls.MenuItem> öğeleri.  

<a name="menu_control"></a>   
## <a name="menu-control"></a>Menü denetimi  
 <xref:System.Windows.Controls.Menu> Denetimi komutları veya bir uygulama için seçenekler belirtin öğelerinin bir listesini sunar. Genellikle, tıklayarak bir <xref:System.Windows.Controls.MenuItem> bir alt açar veya bir uygulamanın bir komutu yürütür.  
  
<a name="creating_menus"></a>   
## <a name="creating-menus"></a>Menüler oluşturma  
 Aşağıdaki örnek, oluşturur bir <xref:System.Windows.Controls.Menu> içindeki metni düzenlemek için bir <xref:System.Windows.Controls.TextBox>. <xref:System.Windows.Controls.Menu> İçeren <xref:System.Windows.Controls.MenuItem> nesneleri kullanan <xref:System.Windows.Controls.MenuItem.Command%2A>, <xref:System.Windows.Controls.MenuItem.IsCheckable%2A>, ve <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> özellikleri ve <xref:System.Windows.Controls.MenuItem.Checked>, <xref:System.Windows.Controls.MenuItem.Unchecked>, ve <xref:System.Windows.Controls.MenuItem.Click> olayları.  
  
 [!code-xaml[MenuItemCommandsAndEvents#1](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuItemCommandsAndEvents/CSharp/Window1.xaml#1)]  
  
 [!code-csharp[MenuItemCommandsAndEvents#2](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuItemCommandsAndEvents/CSharp/Window1.xaml.cs#2)]
 [!code-vb[MenuItemCommandsAndEvents#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MenuItemCommandsAndEvents/VisualBasic/Window1.xaml.vb#2)]  
  
<a name="menus_with_shortcutkeys"></a>   
## <a name="menuitems-with-keyboard-shortcuts"></a>Klavye kısayolları ile MenuItems  
 Klavye kısayolları olan çağırmak için klavye ile girilebilecek bileşimler <xref:System.Windows.Controls.Menu> komutları. Örneğin, kısayolunu **kopyalama** CTRL + C'dir. Klavye kısayolları ve menü öğeleri ile kullanmak için iki özellik vardır —<xref:System.Windows.Controls.MenuItem.InputGestureText%2A> veya <xref:System.Windows.Controls.MenuItem.Command%2A>.  
  
<a name="menus_inputgesturetext"></a>   
### <a name="inputgesturetext"></a>InputGestureText  
 Aşağıdaki örnek nasıl kullanılacağını gösterir <xref:System.Windows.Controls.MenuItem.InputGestureText%2A> klavye kısayolu metni atamak için özellik <xref:System.Windows.Controls.MenuItem> kontrol eder. Bu, yalnızca klavye kısayol menü öğesi yerleştirir.  Komutu ile ilişkilendirmez <xref:System.Windows.Controls.MenuItem>. Uygulamanın eylemi gerçekleştirmek için kullanıcının girişi işlemesi gerekir.  
  
 [!code-xaml[MenuEvent#6](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuEvent/CSharp/Pane1.xaml#6)]  
  
<a name="menus_commands"></a>   
### <a name="command"></a>Komut  
 Aşağıdaki örnek nasıl kullanılacağını gösterir <xref:System.Windows.Controls.MenuItem.Command%2A> ilişkilendirilecek özellik **açık** ve **Kaydet** ile komutları <xref:System.Windows.Controls.MenuItem> kontrol eder. Komut özelliği yalnızca bir komutla ilişkilendirmek bir <xref:System.Windows.Controls.MenuItem>, ancak aynı zamanda bir kısayol olarak kullanmak için giriş ilişkilendirmekle sağlar.  
  
 [!code-xaml[MenuEvent#8](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuEvent/CSharp/Pane1.xaml#8)]  
  
 <xref:System.Windows.Controls.MenuItem> Sınıfı de sahip bir <xref:System.Windows.Controls.MenuItem.CommandTarget%2A> komutu oluştuğu olan öğeyi belirten özelliği. Varsa <xref:System.Windows.Controls.MenuItem.CommandTarget%2A> ayarlanmazsa komutu klavye girintisine sahip öğeyi alır. Komutlar hakkında daha fazla bilgi için bkz. [komut vermeye genel genel bakış](../advanced/commanding-overview.md).  
  
<a name="menu_styling"></a>   
## <a name="menu-styling"></a>Menü stil  
 Denetim stili ile önemli ölçüde görünümünü ve davranışını değiştirebilirsiniz <xref:System.Windows.Controls.Menu> özel bir denetim yazmak zorunda kalmadan denetimleri. Görsel özelliklerini ayarlamanın yanı sıra, ayrıca uygulayabileceğiniz bir <xref:System.Windows.Style> tek tek parçaları bir denetimin özellikleri aracılığıyla denetim bölümlerini davranışını değiştirmek veya ek bölümleri ekleme ya da bir denetimi düzenini değiştirme. Aşağıdaki örnekler eklemek için çeşitli yollar gösterir bir <xref:System.Windows.Style> için bir <xref:System.Windows.Controls.Menu> denetimi.  
  
 İlk örnek kod tanımlayan bir <xref:System.Windows.Style> adlı `Simple` , geçerli sistem ayarlarını, stili kullanma işlemini gösterir. Kod rengini atar `MenuHighlightBrush` menünün arka plan rengi olarak ve `MenuTextBrush` menünün ön plan rengi. Fırçalar atamak için kaynak anahtarlarını kullandığına dikkat edin.  
  
 [!code-xaml[MenuStylesSnippet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuStylesSnippet/CS/app.xaml#1)]  
  
 Aşağıdaki örnek kullanımları <xref:System.Windows.Trigger> görünümünü değiştirebilmek için öğeleri bir <xref:System.Windows.Controls.MenuItem> gerçekleşen olaylara yanıt olarak <xref:System.Windows.Controls.Menu>. Fareyi taşıdığınızda <xref:System.Windows.Controls.Menu>, ön plan rengini ve menü öğeleri yazı tipi özelliklerini değiştirin.  
  
 [!code-xaml[MenuStylesSnippet#2](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuStylesSnippet/CS/app.xaml#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WPF denetimleri Galerisi örneği](https://go.microsoft.com/fwlink/?LinkID=160053)
