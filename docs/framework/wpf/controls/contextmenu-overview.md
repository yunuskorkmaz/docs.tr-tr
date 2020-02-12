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
ms.openlocfilehash: b973d47711632f4c0fe56f042545598272c79d2d
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124370"
---
# <a name="contextmenu-overview"></a>ContextMenu Genel Bakışı
<xref:System.Windows.Controls.ContextMenu> sınıfı, içeriğe özgü bir <xref:System.Windows.Controls.Menu>kullanarak işlevselliği kullanıma sunan öğeyi temsil eder. Genellikle, bir Kullanıcı fare düğmesine sağ tıklayarak [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] <xref:System.Windows.Controls.ContextMenu> kullanıma sunar. Bu konu, <xref:System.Windows.Controls.ContextMenu> öğesini tanıtır ve [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] ve kodda nasıl kullanılacağına ilişkin örnekler sağlar.  

<a name="contextmenu_control"></a>   
## <a name="contextmenu-control"></a>ContextMenu denetimi  
 <xref:System.Windows.Controls.ContextMenu> belirli bir denetime iliştirilir. <xref:System.Windows.Controls.ContextMenu> öğesi, kullanıcılara belirli bir denetimle ilişkili komutları veya seçenekleri belirten bir öğe listesi (örneğin, bir <xref:System.Windows.Controls.Button>) sunmanızı sağlar. Kullanıcılar, menünün görünmesini sağlamak için denetime sağ tıklayın. Genellikle, bir <xref:System.Windows.Controls.MenuItem> tıklamak bir alt menü açar veya bir uygulamanın bir komutu gerçekleştirmesini sağlar.  
  
<a name="creating_contextmenus"></a>   
## <a name="creating-contextmenus"></a>ContextMenus oluşturma  
 Aşağıdaki örneklerde, alt menülerde <xref:System.Windows.Controls.ContextMenu> oluşturma gösterilmektedir. <xref:System.Windows.Controls.ContextMenu> denetimleri düğme denetimlerine iliştirilir.  
  
 [!code-xaml[ContextMenu#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ContextMenu/CSharp/Pane1.xaml#1)]  
  
 [!code-csharp[ContextMenu#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ContextMenu/CSharp/Pane1.xaml.cs#2)]
 [!code-vb[ContextMenu#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ContextMenu/VisualBasic/Pane1.xaml.vb#2)]  
  
<a name="applying_styles_to_contextmenu"></a>   
## <a name="applying-styles-to-a-contextmenu"></a>ContextMenu 'ye stil uygulama  
 Bir denetim <xref:System.Windows.Style>kullanarak, bir <xref:System.Windows.Controls.ContextMenu> görünümünü ve davranışını özel bir denetim yazmadan önemli ölçüde değiştirebilirsiniz. Görsel özellikleri ayarlamaya ek olarak, bir denetimin bölümlerine da stil uygulayabilirsiniz. Örneğin, özellikleri kullanarak denetimin bölümlerinin davranışını değiştirebilir veya bir <xref:System.Windows.Controls.ContextMenu>için parçalar ekleyebilir veya yerleşimini değiştirebilirsiniz. Aşağıdaki örneklerde <xref:System.Windows.Controls.ContextMenu> denetimlerine stil eklemenin birkaç yolu gösterilmektedir.  
  
 İlk örnek, `SimpleSysResources`adlı bir stil tanımlar, bu, stilinize geçerli sistem ayarlarının nasıl kullanılacağını gösterir. Örnek, <xref:System.Windows.SystemColors.MenuHighlightBrushKey%2A> <xref:System.Windows.Controls.Control.Background%2A> rengi olarak atar ve <xref:System.Windows.Controls.ContextMenu><xref:System.Windows.Controls.Control.Foreground%2A> rengi olarak <xref:System.Windows.SystemColors.MenuTextBrushKey%2A>.  
  
```xaml  
<Style x:Key="SimpleSysResources" TargetType="{x:Type MenuItem}">  
  <Setter Property = "Background" Value=   
    "{DynamicResource {x:Static SystemColors.MenuHighlightBrushKey}}"/>  
  <Setter Property = "Foreground" Value=   
    "{DynamicResource {x:Static SystemColors.MenuTextBrushKey}}"/>  
</Style>  
```  
  
 Aşağıdaki örnek, <xref:System.Windows.Controls.ContextMenu>oluşturulan olaylara yanıt olarak bir <xref:System.Windows.Controls.Menu> görünümünü değiştirmek için <xref:System.Windows.Trigger> öğesini kullanır. Kullanıcı fareyi menünün üzerine taşıdıkça <xref:System.Windows.Controls.ContextMenu> öğelerinin görünümü değişir.  
  
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
- [WPF denetimleri Galeri örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/ControlsAndLayout)
