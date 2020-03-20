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
ms.openlocfilehash: 4d2d8db0f614b5240705146dbe91432b96b46dd6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185912"
---
# <a name="contextmenu-overview"></a>ContextMenu Genel Bakışı
Sınıf, <xref:System.Windows.Controls.ContextMenu> içeriğe özgü <xref:System.Windows.Controls.Menu>bir öğe kullanarak işlevselliği ortaya çıkaran öğeyi temsil eder. Genellikle, bir kullanıcı fare <xref:System.Windows.Controls.ContextMenu> düğmesini [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] sağ tıklayarak içinde ortaya çıkarır. Bu konu öğeyi <xref:System.Windows.Controls.ContextMenu> tanır ve nasıl kullanılacağı [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] ve kod örnekler sağlar.  

<a name="contextmenu_control"></a>
## <a name="contextmenu-control"></a>ContextMenu Denetimi  
 A <xref:System.Windows.Controls.ContextMenu> belirli bir denetime eklenir. Öğe, <xref:System.Windows.Controls.ContextMenu> kullanıcılara belirli bir denetimle ilişkili komutları veya seçenekleri belirten öğelerin bir listesini <xref:System.Windows.Controls.Button>sunmanızı sağlar, örneğin, bir . Kullanıcılar, menüyü görüntülemek için denetimi sağ tıklatın. Genellikle, bir <xref:System.Windows.Controls.MenuItem> alt menüyü tıklatmak bir alt menüyü açar veya bir uygulamanın bir komut u gerçekleştirmesine neden olur.  
  
<a name="creating_contextmenus"></a>
## <a name="creating-contextmenus"></a>ContextMenüoluşturma  
 Aşağıdaki örnekler, alt <xref:System.Windows.Controls.ContextMenu> menülerle nasıl oluşturulacak larını gösterir. Denetimler <xref:System.Windows.Controls.ContextMenu> düğme denetimlerine eklenir.  
  
 [!code-xaml[ContextMenu#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ContextMenu/CSharp/Pane1.xaml#1)]  
  
 [!code-csharp[ContextMenu#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ContextMenu/CSharp/Pane1.xaml.cs#2)]
 [!code-vb[ContextMenu#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ContextMenu/VisualBasic/Pane1.xaml.vb#2)]  
  
<a name="applying_styles_to_contextmenu"></a>
## <a name="applying-styles-to-a-contextmenu"></a>Bağlam Menüsüne Stilleri Uygulama  
 Bir denetim <xref:System.Windows.Style>kullanarak, özel bir denetim yazmadan <xref:System.Windows.Controls.ContextMenu> bir görünümünü ve davranışını önemli ölçüde değiştirebilirsiniz. Görsel özellikler ayarlamaya ek olarak, stilleri denetimin bölümlerine de uygulayabilirsiniz. Örneğin, özellikleri kullanarak denetim bölümlerinin davranışını değiştirebilir veya bir <xref:System.Windows.Controls.ContextMenu>. Aşağıdaki örnekler, denetimlere stil <xref:System.Windows.Controls.ContextMenu> eklemenin çeşitli yollarını gösterir.  
  
 İlk örnek, stilinizde `SimpleSysResources`geçerli sistem ayarlarının nasıl kullanılacağını gösteren , adlı bir stil tanımlar. Örnek, <xref:System.Windows.SystemColors.MenuHighlightBrushKey%2A> <xref:System.Windows.Controls.Control.Background%2A> renk ve <xref:System.Windows.SystemColors.MenuTextBrushKey%2A> <xref:System.Windows.Controls.Control.Foreground%2A> renk olarak <xref:System.Windows.Controls.ContextMenu>atar.  
  
```xaml  
<Style x:Key="SimpleSysResources" TargetType="{x:Type MenuItem}">  
  <Setter Property = "Background" Value=
    "{DynamicResource {x:Static SystemColors.MenuHighlightBrushKey}}"/>  
  <Setter Property = "Foreground" Value=
    "{DynamicResource {x:Static SystemColors.MenuTextBrushKey}}"/>  
</Style>  
```  
  
 Aşağıdaki örnekte, <xref:System.Windows.Trigger> <xref:System.Windows.Controls.ContextMenu>'de yükseltilen <xref:System.Windows.Controls.Menu> olaylara yanıt olarak bir görünümü değiştirmek için öğe yi kullanır. Bir kullanıcı fareyi menünün üzerinde hareket <xref:System.Windows.Controls.ContextMenu> ettirdiğinde, öğelerin görünümü değişir.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Controls.ContextMenu>
- <xref:System.Windows.Style>
- <xref:System.Windows.Controls.Menu>
- <xref:System.Windows.Controls.MenuItem>
- [ContextMenu](contextmenu.md)
- [ContextMenu Stilleri ve Şablonları](contextmenu-styles-and-templates.md)
- [WPF Denetimleri Galeri Örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/ControlsAndLayout)
