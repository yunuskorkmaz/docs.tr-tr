---
title: ContextMenu Genel Bakışı
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], ContextMenu
- ContextMenu controls [WPF], about ContextMenu controls
ms.assetid: 16909c42-799a-4561-91e0-7d69dcfeea91
ms.openlocfilehash: e862f02e736cb8507dde5036700d751f8af0a226
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="contextmenu-overview"></a>ContextMenu Genel Bakışı
<xref:System.Windows.Controls.ContextMenu> Sınıf bağlamı özgü kullanarak işlevselliği kullanıma sunan bir öğeyi temsil eder <xref:System.Windows.Controls.Menu>. Genellikle, bir kullanıcı sunan <xref:System.Windows.Controls.ContextMenu> içinde [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] fare düğmesini sağ tıklanarak. Bu konu tanıtır <xref:System.Windows.Controls.ContextMenu> öğesi ve içinde kullanma örnekleri sağlar [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] ve kod.  
  
  
  
<a name="contextmenu_control"></a>   
## <a name="contextmenu-control"></a>ContextMenu denetimi  
 A <xref:System.Windows.Controls.ContextMenu> belirli bir denetime bağlı. <xref:System.Windows.Controls.ContextMenu> Öğeleri sağlar, kullanıcılar, komutları veya örneğin, belirli bir denetim ile ilişkili olan seçenekleri belirtin öğelerin bir listesi sunmak bir <xref:System.Windows.Controls.Button>. Kullanıcılar menüyü görünür yapmak için denetimi sağ tıklatın. Genellikle, tıklatarak bir <xref:System.Windows.Controls.MenuItem> bir alt açar veya bir komutu gerçekleştirmek bir uygulamanın neden olur.  
  
<a name="creating_contextmenus"></a>   
## <a name="creating-contextmenus"></a>ContextMenus oluşturma  
 Aşağıdaki örnekler nasıl oluşturulacağı bir <xref:System.Windows.Controls.ContextMenu> alt menüler ile. <xref:System.Windows.Controls.ContextMenu> Denetimleri düğme denetimlerine iliştirilir.  
  
 [!code-xaml[ContextMenu#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ContextMenu/CSharp/Pane1.xaml#1)]  
  
 [!code-csharp[ContextMenu#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ContextMenu/CSharp/Pane1.xaml.cs#2)]
 [!code-vb[ContextMenu#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ContextMenu/VisualBasic/Pane1.xaml.vb#2)]  
  
<a name="applying_styles_to_contextmenu"></a>   
## <a name="applying-styles-to-a-contextmenu"></a>Bir ContextMenu uygulanan stilleri  
 Bir denetimi kullanarak <xref:System.Windows.Style>, önemli ölçüde görünümünü ve davranışını değiştirebilirsiniz bir <xref:System.Windows.Controls.ContextMenu> özel bir denetim yazma olmadan. Görsel özellikler ayarlamaya ek olarak, bir denetim bölümlerine stilleri de uygulayabilirsiniz. Örneğin, özelliklerini kullanarak denetim bölümlerini davranışını değiştirebilir veya bölümlerine ekleme veya düzenini değiştirme bir <xref:System.Windows.Controls.ContextMenu>. Aşağıdaki örnekler stil eklemek için çeşitli yollar <xref:System.Windows.Controls.ContextMenu> kontrol eder.  
  
 İlk örnek adlı bir stil tanımlar `SimpleSysResources`, geçerli sistem ayarları stil kodunuzu nasıl kullanılacağı gösterilmektedir. Örnek atar <xref:System.Windows.SystemColors.MenuHighlightBrushKey%2A> olarak <xref:System.Windows.Controls.Control.Background%2A> renk ve <xref:System.Windows.SystemColors.MenuTextBrushKey%2A> olarak <xref:System.Windows.Controls.Control.Foreground%2A> rengini <xref:System.Windows.Controls.ContextMenu>.  
  
```xaml  
<Style x:Key="SimpleSysResources" TargetType="{x:Type MenuItem}">  
  <Setter Property = "Background" Value=   
    "{DynamicResource {x:Static SystemColors.MenuHighlightBrushKey}}"/>  
  <Setter Property = "Foreground" Value=   
    "{DynamicResource {x:Static SystemColors.MenuTextBrushKey}}"/>  
</Style>  
```  
  
 Aşağıdaki örnek kullanır <xref:System.Windows.Trigger> öğesinin görünümünü değiştirmek için bir <xref:System.Windows.Controls.Menu> üzerinde ortaya olaylarına yanıt olarak <xref:System.Windows.Controls.ContextMenu>. Ne zaman bir kullanıcı hareket fare görünümünü menüye <xref:System.Windows.Controls.ContextMenu> öğelerini değişiklikleri.  
  
```xaml  
<Style x:Key="Triggers" TargetType="{x:Type MenuItem}">  
  <Style.Triggers>  
    <Trigger Property="MenuItem.IsMouseOver" Value="true">  
      <Setter Property = "FontSize" Value="16"/>  
      <Setter Property = "FontStyle" Value="Italic"/>  
      <Setter Property = "Foreground" Value="Red"/>  
    </Trigger>  
  </Style.Triggers>  
</Style>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Controls.ContextMenu>  
 <xref:System.Windows.Style>  
 <xref:System.Windows.Controls.Menu>  
 <xref:System.Windows.Controls.MenuItem>  
 [ContextMenu](../../../../docs/framework/wpf/controls/contextmenu.md)  
 [ContextMenu Stilleri ve Şablonları](../../../../docs/framework/wpf/controls/contextmenu-styles-and-templates.md)  
 [WPF denetimleri galeri örneği](http://go.microsoft.com/fwlink/?LinkID=160053)
