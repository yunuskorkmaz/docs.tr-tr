---
title: TreeView Stilleri ve Şablonları
ms.date: 03/30/2017
helpviewer_keywords:
- ControlTemplate [WPF], TreeView
- templates [WPF], TreeView
- parts [WPF], TreeView
- states [WPF], TreeView
- styles [WPF], TreeView
- TreeView [WPF], styles and templates
ms.assetid: a49adb77-0202-4caa-b94a-8bb110d7fa9a
ms.openlocfilehash: 01841bb828594dd4cac0c179d70495fe392c8de5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59142714"
---
# <a name="treeview-styles-and-templates"></a>TreeView Stilleri ve Şablonları
Bu konu için şablonları ve stilleri açıklar <xref:System.Windows.Controls.TreeView> denetimi. Varsayılan değiştirebileceğiniz <xref:System.Windows.Controls.ControlTemplate> denetim benzersiz bir görünüm sağlamak için. Daha fazla bilgi için [ControlTemplate oluşturarak varolan denetimin görünümünü özelleştirme](customizing-the-appearance-of-an-existing-control.md).  
  
## <a name="treeview-parts"></a>TreeView bölümleri  
 <xref:System.Windows.Controls.TreeView> Denetim herhangi bir adlandırılmış bölümü yok.  
  
 Oluştururken bir <xref:System.Windows.Controls.ControlTemplate> için bir <xref:System.Windows.Controls.TreeView>, şablonunuzu içerebilir bir <xref:System.Windows.Controls.ItemsPresenter> içinde bir <xref:System.Windows.Controls.ScrollViewer>. ( <xref:System.Windows.Controls.ItemsPresenter> Her öğe görüntüler <xref:System.Windows.Controls.TreeView>; <xref:System.Windows.Controls.ScrollViewer> denetimi içinde kaydırma sağlar).  Varsa <xref:System.Windows.Controls.ItemsPresenter> doğrudan alt öğesi değil <xref:System.Windows.Controls.ScrollViewer>, size gereken <xref:System.Windows.Controls.ItemsPresenter> adı `ItemsPresenter`.  
  
## <a name="treeview-states"></a>TreeView durumları  
 Görsel durumlar için aşağıdaki tabloda <xref:System.Windows.Controls.TreeView> denetimi.  
  
|VisualState adı|Visualstategroup'u adı|Açıklama|  
|-|-|-|  
|Geçerli|ValidationStates|Denetimi kullanan <xref:System.Windows.Controls.Validation> sınıfı ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği `false`.|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özelliği `true` olan denetim odağa sahip.|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özelliği `true` olan denetim odağa sahip değil.|  
  
## <a name="treeviewitem-parts"></a>TreeViewItem bölümleri  
 Adlandırılmış bölümleri için aşağıdaki tabloda <xref:System.Windows.Controls.TreeViewItem> denetimi.  
  
|Bölümü|Tür|Açıklama|  
|----------|----------|-----------------|  
|PART_Header|<xref:System.Windows.FrameworkElement>|Bu üst bilgi içeriği içeren bir görsel öğe <xref:System.Windows.Controls.TreeView> denetimi.|  
  
## <a name="treeviewitem-states"></a>TreeViewItem durumları  
 Görsel durumlar için aşağıdaki tabloda <xref:System.Windows.Controls.TreeViewItem> denetimi.  
  
|VisualState adı|Visualstategroup'u adı|Açıklama|  
|----------------------|---------------------------|-----------------|  
|Normal|CommonStates|Varsayılan durumu.|  
|Fareyi üzerine getirme|CommonStates|Fareyi üzerine getirildiği <xref:System.Windows.Controls.TreeViewItem>.|  
|Devre dışı|CommonStates|<xref:System.Windows.Controls.TreeViewItem> Devre dışı bırakıldı.|  
|Odaklanmış|FocusStates|<xref:System.Windows.Controls.TreeViewItem> Odağa sahip.|  
|Plana odaklanmadan|FocusStates|<xref:System.Windows.Controls.TreeViewItem> Odağa sahip değil.|  
|Genişletilmiş|ExpansionStates|<xref:System.Windows.Controls.TreeViewItem> Denetim genişletilir.|  
|Daraltılmış|ExpansionStates|<xref:System.Windows.Controls.TreeViewItem> Denetimini daralttı.|  
|Hasıtems|HasItemsStates|<xref:System.Windows.Controls.TreeViewItem> Öğeler içeriyor.|  
|NoItems|HasItemsStates|<xref:System.Windows.Controls.TreeViewItem> Öğe yok.|  
|Seçildi|SelectionStates|<xref:System.Windows.Controls.TreeViewItem> Seçilir.|  
|SelectedInactive|SelectionStates|<xref:System.Windows.Controls.TreeViewItem> Seçili ancak etkin değil.|  
|Seçimi kaldırıldı|SelectionStates|<xref:System.Windows.Controls.TreeViewItem> Seçilmez.|  
|Geçerli|ValidationStates|Denetimi kullanan <xref:System.Windows.Controls.Validation> sınıfı ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği `false`.|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özelliği `true` olan denetim odağa sahip.|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özelliği `true` olan denetim odağa sahip değil.|  
  
## <a name="treeview-controltemplate-example"></a>TreeView ControlTemplate Örneği  
 Aşağıdaki örnek nasıl tanımlanacağını gösterir bir <xref:System.Windows.Controls.ControlTemplate> için <xref:System.Windows.Controls.TreeView> denetimi ve ilişkili türleri.  
  
 [!code-xaml[ControlTemplateExamples#TreeView](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/treeview.xaml#treeview)]  
  
 Yukarıdaki örnekte, bir veya daha fazla aşağıdaki kaynakları kullanır.  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 Tam bir örnek için bkz. [ControlTemplates örneği ile stillendirme](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [Denetim Stilleri ve Şablonları](control-styles-and-templates.md)
- [Denetim Özelleştirme](control-customization.md)
- [Stil ve Şablon Oluşturma](styling-and-templating.md)
- [ControlTemplate Oluşturarak Varolan Denetimin Görünümünü Özelleştirme](customizing-the-appearance-of-an-existing-control.md)
