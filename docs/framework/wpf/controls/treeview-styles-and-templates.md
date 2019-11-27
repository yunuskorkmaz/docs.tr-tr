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
ms.openlocfilehash: 45276d23380fe956fc3d59b90d5baae23ee8a7e2
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283630"
---
# <a name="treeview-styles-and-templates"></a>TreeView Stilleri ve Şablonları
Bu konuda <xref:System.Windows.Controls.TreeView> denetimine yönelik stiller ve şablonlar açıklanmaktadır. Denetime benzersiz bir görünüm sağlamak için varsayılan <xref:System.Windows.Controls.ControlTemplate> değiştirebilirsiniz. Daha fazla bilgi için bkz. [Denetim için şablon oluşturma](../../../desktop-wpf/themes/how-to-create-apply-template.md).  
  
## <a name="treeview-parts"></a>TreeView parçaları  
 <xref:System.Windows.Controls.TreeView> denetiminde hiç adlandırılmış bölüm yok.  
  
 Bir <xref:System.Windows.Controls.TreeView>için <xref:System.Windows.Controls.ControlTemplate> oluşturduğunuzda, şablonunuz <xref:System.Windows.Controls.ScrollViewer>içinde bir <xref:System.Windows.Controls.ItemsPresenter> içerebilir. (<xref:System.Windows.Controls.ItemsPresenter>, <xref:System.Windows.Controls.TreeView>her öğeyi görüntüler; <xref:System.Windows.Controls.ScrollViewer> denetimin içinde kaydırmaya izin vermez).  <xref:System.Windows.Controls.ItemsPresenter>, <xref:System.Windows.Controls.ScrollViewer>doğrudan alt öğesi değilse, `ItemsPresenter`adına <xref:System.Windows.Controls.ItemsPresenter> vermelisiniz.  
  
## <a name="treeview-states"></a>TreeView durumları  
 Aşağıdaki tabloda <xref:System.Windows.Controls.TreeView> denetimi için görsel durumlar listelenmektedir.  
  
|VisualState adı|VisualStateGroup adı|Açıklama|  
|-|-|-|  
|Geçerli|Doğrulama durumları|Denetim, <xref:System.Windows.Controls.Validation> sınıfını ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> iliştirilmiş özelliği `false`kullanır.|  
|Invalidodaklanmış|Doğrulama durumları|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği, denetimin odağa sahip `true`.|  
|Invalidunodaklanmış|Doğrulama durumları|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği, denetimin odağa sahip `true`.|  
  
## <a name="treeviewitem-parts"></a>TreeViewItem parçalar  
 Aşağıdaki tabloda <xref:System.Windows.Controls.TreeViewItem> denetimi için adlandırılmış bölümler listelenmektedir.  
  
|Bölümüyle|Type|Açıklama|  
|----------|----------|-----------------|  
|PART_Header|<xref:System.Windows.FrameworkElement>|<xref:System.Windows.Controls.TreeView> denetiminin üst bilgi içeriğini içeren bir görsel öğe.|  
  
## <a name="treeviewitem-states"></a>TreeViewItem durumlar  
 Aşağıdaki tabloda <xref:System.Windows.Controls.TreeViewItem> denetimi için görsel durumlar listelenmektedir.  
  
|VisualState adı|VisualStateGroup adı|Açıklama|  
|----------------------|---------------------------|-----------------|  
|Normal|Ortak durumlar|Varsayılan durum.|  
|Gelme olayından|Ortak durumlar|Fare işaretçisi <xref:System.Windows.Controls.TreeViewItem>yerleştirilir.|  
|Devre dışı|Ortak durumlar|<xref:System.Windows.Controls.TreeViewItem> devre dışı bırakıldı.|  
|Diğinize|Odaklardaki durumlar|<xref:System.Windows.Controls.TreeViewItem> odağa sahip.|  
|Odaklanmadan gözetle|Odaklardaki durumlar|<xref:System.Windows.Controls.TreeViewItem> odağı yok.|  
|Genişletilmiş|ExpansionStates|<xref:System.Windows.Controls.TreeViewItem> denetimi genişletilir.|  
|Daraltılmış|ExpansionStates|<xref:System.Windows.Controls.TreeViewItem> denetimi daraltılır.|  
|HasItems|HasItemsStates|<xref:System.Windows.Controls.TreeViewItem> öğeler vardır.|  
|Noıtems|HasItemsStates|<xref:System.Windows.Controls.TreeViewItem> öğe yok.|  
|Seçildi|SelectionStates|<xref:System.Windows.Controls.TreeViewItem> seçilidir.|  
|SelectedInactive|SelectionStates|<xref:System.Windows.Controls.TreeViewItem> seçili ancak etkin değil.|  
|Değilken|SelectionStates|<xref:System.Windows.Controls.TreeViewItem> seçilmemiş.|  
|Geçerli|Doğrulama durumları|Denetim, <xref:System.Windows.Controls.Validation> sınıfını ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> iliştirilmiş özelliği `false`kullanır.|  
|Invalidodaklanmış|Doğrulama durumları|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği, denetimin odağa sahip `true`.|  
|Invalidunodaklanmış|Doğrulama durumları|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği, denetimin odağa sahip `true`.|  
  
## <a name="treeview-controltemplate-example"></a>TreeView ControlTemplate örneği  
 Aşağıdaki örnek, <xref:System.Windows.Controls.TreeView> denetimi ve ilişkili türleri için <xref:System.Windows.Controls.ControlTemplate> nasıl tanımlanacağını gösterir.  
  
 [!code-xaml[ControlTemplateExamples#TreeView](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/treeview.xaml#treeview)]  
  
 Yukarıdaki örnekte aşağıdaki kaynaklardan biri veya daha fazlası kullanılmaktadır.  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 Tüm örnek için bkz. [ControlTemplates Ile stillendirme örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [Denetim Stilleri ve Şablonları](control-styles-and-templates.md)
- [Denetim Özelleştirme](control-customization.md)
- [Stil ve Şablon Oluşturma](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Denetim için şablon oluşturma](../../../desktop-wpf/themes/how-to-create-apply-template.md)
