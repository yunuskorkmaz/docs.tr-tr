---
title: "Menüye Genel Bakış"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Menu control [WPF]
- controls [WPF], Menu
ms.assetid: 67df6de5-db96-4c71-b752-af90729a6537
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8ab5092b1bc9db22390a18b2c1cb1ad5725a2037
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="menu-overview"></a>Menüye Genel Bakış
<xref:System.Windows.Controls.Menu> Sınıfı komutlar ve hiyerarşik sırada olay işleyicileri ile ilişkili öğeleri düzenlemenizi sağlar. Her <xref:System.Windows.Controls.Menu> öğesi içeren bir koleksiyonu <xref:System.Windows.Controls.MenuItem> öğeleri.  
  
  
<a name="menu_control"></a>   
## <a name="menu-control"></a>Menü denetimi  
 <xref:System.Windows.Controls.Menu> Denetimi komutları veya bir uygulama için seçenekler belirtin öğelerin listesini gösterir. Genellikle, tıklatarak bir <xref:System.Windows.Controls.MenuItem> bir alt açar veya bir komutu gerçekleştirmek bir uygulamanın neden olur.  
  
<a name="creating_menus"></a>   
## <a name="creating-menus"></a>Menüleri oluşturma  
 Aşağıdaki örnekte bir <xref:System.Windows.Controls.Menu> içindeki metni düzenlemek için bir <xref:System.Windows.Controls.TextBox>. <xref:System.Windows.Controls.Menu> İçeren <xref:System.Windows.Controls.MenuItem> nesneleri kullanan <xref:System.Windows.Controls.MenuItem.Command%2A>, <xref:System.Windows.Controls.MenuItem.IsCheckable%2A>, ve <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> özellikleri ve <xref:System.Windows.Controls.MenuItem.Checked>, <xref:System.Windows.Controls.MenuItem.Unchecked>, ve <xref:System.Windows.Controls.MenuItem.Click> olaylar.  
  
 [!code-xaml[MenuItemCommandsAndEvents#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuItemCommandsAndEvents/CSharp/Window1.xaml#1)]  
  
 [!code-csharp[MenuItemCommandsAndEvents#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuItemCommandsAndEvents/CSharp/Window1.xaml.cs#2)]
 [!code-vb[MenuItemCommandsAndEvents#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MenuItemCommandsAndEvents/VisualBasic/Window1.xaml.vb#2)]  
  
<a name="menus_with_shortcutkeys"></a>   
## <a name="menuitems-with-keyboard-shortcuts"></a>Klavye kısayolu olan MenuItems  
 Klavye kısayolları olan çağrılacak klavyeyle girilebilir karakter birleşimleri <xref:System.Windows.Controls.Menu> komutları. Örneğin, için kısayol **kopyalama** CTRL + C'dir. Klavye kısayolları ve menü öğeleri ile kullanmak için iki özellik —<xref:System.Windows.Controls.MenuItem.InputGestureText%2A> veya <xref:System.Windows.Controls.MenuItem.Command%2A>.  
  
<a name="menus_inputgesturetext"></a>   
### <a name="inputgesturetext"></a>InputGestureText  
 Aşağıdaki örnekte nasıl kullanılacağını gösterir <xref:System.Windows.Controls.MenuItem.InputGestureText%2A> klavye kısayol metni atamak için özellik <xref:System.Windows.Controls.MenuItem> kontrol eder. Bu, yalnızca klavye kısayol menü öğesi yerleştirir.  Komutuyla ilişkilendirmez <xref:System.Windows.Controls.MenuItem>. Uygulama eylemi gerçekleştirmek için kullanıcının giriş işlemelidir.  
  
 [!code-xaml[MenuEvent#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuEvent/CSharp/Pane1.xaml#6)]  
  
<a name="menus_commands"></a>   
### <a name="command"></a>Komut  
 Aşağıdaki örnekte nasıl kullanılacağını gösterir <xref:System.Windows.Controls.MenuItem.Command%2A> ilişkilendirilecek özellik **açık** ve **kaydetmek** ile komutları <xref:System.Windows.Controls.MenuItem> kontrol eder. Komut özelliği yalnızca bir komutla ilişkilendirmek bir <xref:System.Windows.Controls.MenuItem>, ancak bir kısayol olarak kullanılacak giriş hareketi metin de sağlar.  
  
 [!code-xaml[MenuEvent#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuEvent/CSharp/Pane1.xaml#8)]  
  
 <xref:System.Windows.Controls.MenuItem> Sınıfı ayrıca sahip bir <xref:System.Windows.Controls.MenuItem.CommandTarget%2A> komutu oluştuğu öğesi belirttiğinden özelliği. Varsa <xref:System.Windows.Controls.MenuItem.CommandTarget%2A> ayarlanmazsa klavye odağı olan öğe komutu alır. Komutlar hakkında daha fazla bilgi için bkz: [kumanda genel bakış](../../../../docs/framework/wpf/advanced/commanding-overview.md).  
  
<a name="menu_styling"></a>   
## <a name="menu-styling"></a>Menü stil  
 Denetim stil ile önemli ölçüde görünümünü ve davranışını değiştirebilirsiniz <xref:System.Windows.Controls.Menu> özel denetim yazmak zorunda kalmadan kontrol eder. Görsel özellikler ayarlamaya ek olarak, aynı zamanda uygulayabilirsiniz bir <xref:System.Windows.Style> tek tek parçaları bir denetimin denetimi özellikleri, aracılığıyla bölümlerini davranışını değiştirmek veya ek bölümleri eklemek veya bir denetimi düzenini değiştirme. Aşağıdaki örnekler eklemek için çeşitli yollar gösterir bir <xref:System.Windows.Style> için bir <xref:System.Windows.Controls.Menu> denetim.  
  
 İlk örnek kod tanımlayan bir <xref:System.Windows.Style> adlı `Simple` geçerli sistem ayarları stil kodunuzu nasıl kullanılacağı gösterilmektedir. Rengi kodunu atar `MenuHighlightBrush` menünün arka plan rengi olarak ve `MenuTextBrush` menünün ön plan rengini olarak. Fırçalar atamak için kaynak anahtarları kullandığına dikkat edin.  
  
 [!code-xaml[MenuStylesSnippet#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuStylesSnippet/CS/app.xaml#1)]  
  
 Aşağıdaki örnek kullanır <xref:System.Windows.Trigger> görünümünü değiştirmenizi etkinleştiren öğelerini bir <xref:System.Windows.Controls.MenuItem> üzerinde gerçekleşen olaylara yanıt olarak <xref:System.Windows.Controls.Menu>. Fare taşıdığınızda <xref:System.Windows.Controls.Menu>, ön plan rengini ve menü öğelerinin yazı tipi özelliklerini değiştirin.  
  
 [!code-xaml[MenuStylesSnippet#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuStylesSnippet/CS/app.xaml#2)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WPF denetimleri galeri örneği](http://go.microsoft.com/fwlink/?LinkID=160053)
