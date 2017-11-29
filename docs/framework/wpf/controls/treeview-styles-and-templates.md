---
title: "TreeView Stilleri ve Şablonları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ControlTemplate [WPF], TreeView
- templates [WPF], TreeView
- parts [WPF], TreeView
- states [WPF], TreeView
- styles [WPF], TreeView
- TreeView [WPF], styles and templates
ms.assetid: a49adb77-0202-4caa-b94a-8bb110d7fa9a
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 78e5faf7aab684f2a8760204079a26a61b9c3fda
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="treeview-styles-and-templates"></a>TreeView Stilleri ve Şablonları
Stilleri ve şablonları için bu konuda açıklanmaktadır <xref:System.Windows.Controls.TreeView> denetim. Varsayılan değiştirebileceğiniz <xref:System.Windows.Controls.ControlTemplate> denetimi benzersiz bir görünüm vermek için. Daha fazla bilgi için bkz: [ControlTemplate oluşturarak varolan denetiminin görünümünü özelleştirme](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).  
  
## <a name="treeview-parts"></a>TreeView bölümleri  
 <xref:System.Windows.Controls.TreeView> Denetim adlandırılmış tüm bölümler sahip değil.  
  
 Oluştururken bir <xref:System.Windows.Controls.ControlTemplate> için bir <xref:System.Windows.Controls.TreeView>, şablonunuzu içerebilir bir <xref:System.Windows.Controls.ItemsPresenter> içinde bir <xref:System.Windows.Controls.ScrollViewer>. ( <xref:System.Windows.Controls.ItemsPresenter> Her öğe görüntüler <xref:System.Windows.Controls.TreeView>; <xref:System.Windows.Controls.ScrollViewer> içinde denetimin kaydırma sağlar).  Varsa <xref:System.Windows.Controls.ItemsPresenter> doğrudan alt öğesi değil <xref:System.Windows.Controls.ScrollViewer>, vermeniz gerekir <xref:System.Windows.Controls.ItemsPresenter> adı `ItemsPresenter`.  
  
## <a name="treeview-states"></a>TreeView durumları  
 Aşağıdaki tablo için görsel durumlarını listeler <xref:System.Windows.Controls.TreeView> denetim.  
  
|VisualState adı|VisualStateGroup adı|Açıklama|  
|-|-|-|  
|Geçerli|ValidationStates|Denetim kullanan <xref:System.Windows.Controls.Validation> sınıfı ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> iliştirilmiş özelliği `false`.|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özellik `true` sahip denetimi odağa sahip.|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özellik `true` sahip denetimi odağa sahip değil.|  
  
## <a name="treeviewitem-parts"></a>TreeViewItem bölümleri  
 Adlandırılmış bölümleri için aşağıdaki tabloda listelenmektedir <xref:System.Windows.Controls.TreeViewItem> denetim.  
  
|Bölümü|Tür|Açıklama|  
|----------|----------|-----------------|  
|PART_Header|<xref:System.Windows.FrameworkElement>|İçeriği bu üst bilgiyi içeren bir görsel öğe <xref:System.Windows.Controls.TreeView> denetim.|  
  
## <a name="treeviewitem-states"></a>TreeViewItem durumları  
 Aşağıdaki tablo için görsel durumlarını listeler <xref:System.Windows.Controls.TreeViewItem> denetim.  
  
|VisualState adı|VisualStateGroup adı|Açıklama|  
|----------------------|---------------------------|-----------------|  
|Normal|CommonStates|Varsayılan durumu.|  
|Fare üzerinde|CommonStates|Fare işaretçisini üzerine getirildiği <xref:System.Windows.Controls.TreeViewItem>.|  
|Devre dışı|CommonStates|<xref:System.Windows.Controls.TreeViewItem> Devre dışı bırakılır.|  
|Odaklanmış|FocusStates|<xref:System.Windows.Controls.TreeViewItem> Odağa sahip.|  
|Odaksız|FocusStates|<xref:System.Windows.Controls.TreeViewItem> Odağa sahip değil.|  
|Genişletilmiş|ExpansionStates|<xref:System.Windows.Controls.TreeViewItem> Denetim genişletilir.|  
|Daraltılmış|ExpansionStates|<xref:System.Windows.Controls.TreeViewItem> Denetimi daraltıldığında.|  
|Hasıtems|HasItemsStates|<xref:System.Windows.Controls.TreeViewItem> Öğelerine sahip.|  
|NoItems|HasItemsStates|<xref:System.Windows.Controls.TreeViewItem> Öğe yok.|  
|Seçili|SelectionStates|<xref:System.Windows.Controls.TreeViewItem> Seçilir.|  
|SelectedInactive|SelectionStates|<xref:System.Windows.Controls.TreeViewItem> Seçili ancak etkin değil.|  
|Seçilmemiş|SelectionStates|<xref:System.Windows.Controls.TreeViewItem> Seçilmemiş.|  
|Geçerli|ValidationStates|Denetim kullanan <xref:System.Windows.Controls.Validation> sınıfı ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> iliştirilmiş özelliği `false`.|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özellik `true` sahip denetimi odağa sahip.|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özellik `true` sahip denetimi odağa sahip değil.|  
  
## <a name="treeview-controltemplate-example"></a>TreeView ControlTemplate Örneği  
 Aşağıdaki örnekte nasıl tanımlanacağı gösterilmektedir bir <xref:System.Windows.Controls.ControlTemplate> için <xref:System.Windows.Controls.TreeView> denetimi ve onun ilişkili türler.  
  
 [!code-xaml[ControlTemplateExamples#TreeView](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/treeview.xaml#treeview)]  
  
 Önceki örnekte, bir veya daha fazla aşağıdaki kaynakları kullanır.  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 Tam bir örnek için bkz: [ControlTemplates örneği ile stil oluşturma](http://go.microsoft.com/fwlink/?LinkID=160041).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [Denetim stilleri ve şablonları](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [Denetim özelleştirme](../../../../docs/framework/wpf/controls/control-customization.md)  
 [Stil ve şablon oluşturma](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [ControlTemplate oluşturarak varolan denetiminin görünümünü özelleştirme](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
