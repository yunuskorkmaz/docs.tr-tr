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
ms.openlocfilehash: 54fd823594fba4500f35ed1d69720a3309e54a36
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44130532"
---
# <a name="contextmenu-overview"></a>ContextMenu Genel Bakışı
<xref:System.Windows.Controls.ContextMenu> Sınıfı temsil eder, bağlam özgü kullanarak işlevselliği ortaya koyan öğe <xref:System.Windows.Controls.Menu>. Genellikle, bir kullanıcı sunan <xref:System.Windows.Controls.ContextMenu> içinde [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] fare düğmesine tıklanarak. Bu konu tanıtır <xref:System.Windows.Controls.ContextMenu> öğe ve içindeki kullanma örnekleri sağlar [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] ve kod.  
  
  
  
<a name="contextmenu_control"></a>   
## <a name="contextmenu-control"></a>ContextMenu denetimi  
 A <xref:System.Windows.Controls.ContextMenu> belirli bir denetime bağlı. <xref:System.Windows.Controls.ContextMenu> Öğesi, kullanıcıların mevcut komutları veya örneğin, belirli bir denetimle ilişkilendirilen seçenekleri belirten öğeleri listesini olanak tanır bir <xref:System.Windows.Controls.Button>. Kullanıcı denetim menüsünün görünür hale getirmek için sağ tıklayın. Genellikle, tıklayarak bir <xref:System.Windows.Controls.MenuItem> bir alt açar veya bir uygulamanın bir komutu yürütür.  
  
<a name="creating_contextmenus"></a>   
## <a name="creating-contextmenus"></a>ContextMenus oluşturma  
 Aşağıdaki örnekler nasıl oluşturulacağını gösterir. bir <xref:System.Windows.Controls.ContextMenu> menülerinde ile. <xref:System.Windows.Controls.ContextMenu> Denetimleri için düğme denetimleri eklenir.  
  
 [!code-xaml[ContextMenu#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ContextMenu/CSharp/Pane1.xaml#1)]  
  
 [!code-csharp[ContextMenu#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ContextMenu/CSharp/Pane1.xaml.cs#2)]
 [!code-vb[ContextMenu#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ContextMenu/VisualBasic/Pane1.xaml.vb#2)]  
  
<a name="applying_styles_to_contextmenu"></a>   
## <a name="applying-styles-to-a-contextmenu"></a>Uygulama bir ContextMenu stilleri  
 Bir denetimi kullanarak <xref:System.Windows.Style>, önemli ölçüde görünümünü ve davranışını değiştirebilirsiniz bir <xref:System.Windows.Controls.ContextMenu> özel denetim yazmadan. Görsel özelliklerini ayarlamaktan ek olarak, stilleri bir denetimin bölümleri de uygulayabilirsiniz. Örneğin, özelliklerini kullanarak denetim bölümlerini davranışını değiştirebilirsiniz veya bölümleri ekleyin veya düzenini değiştirebilirsiniz bir <xref:System.Windows.Controls.ContextMenu>. Aşağıdaki örnekler stil eklemek için çeşitli yollar <xref:System.Windows.Controls.ContextMenu> kontrol eder.  
  
 İlk örnek adlı bir stil tanımlar `SimpleSysResources`, geçerli sistem ayarlarını, stili kullanmayı gösterir. Örnek atar <xref:System.Windows.SystemColors.MenuHighlightBrushKey%2A> olarak <xref:System.Windows.Controls.Control.Background%2A> renk ve <xref:System.Windows.SystemColors.MenuTextBrushKey%2A> olarak <xref:System.Windows.Controls.Control.Foreground%2A> rengini <xref:System.Windows.Controls.ContextMenu>.  
  
```xaml  
<Style x:Key="SimpleSysResources" TargetType="{x:Type MenuItem}">  
  <Setter Property = "Background" Value=   
    "{DynamicResource {x:Static SystemColors.MenuHighlightBrushKey}}"/>  
  <Setter Property = "Foreground" Value=   
    "{DynamicResource {x:Static SystemColors.MenuTextBrushKey}}"/>  
</Style>  
```  
  
 Aşağıdaki örnekte <xref:System.Windows.Trigger> görünümünü değiştirmek için öğenin bir <xref:System.Windows.Controls.Menu> üzerinde gerçekleşen olaylara yanıt olarak <xref:System.Windows.Controls.ContextMenu>. Ne zaman bir kullanıcı hareket fare görünümünü menüye <xref:System.Windows.Controls.ContextMenu> öğelerini değişiklikler.  
  
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
 [WPF denetimleri Galerisi örneği](https://go.microsoft.com/fwlink/?LinkID=160053)
