---
title: DataGrid Stilleri ve Şablonları
ms.date: 03/30/2017
helpviewer_keywords:
- states [WPF], DataGrid
- ControlTemplate [WPF], DataGrid
- DataGrid [WPF], styles and templates
- templates [WPF], DataGrid
- styles [WPF], DataGrid
- parts [WPF], DataGrid
ms.assetid: 9cb31d63-f148-4d25-b079-816e73f988c7
ms.openlocfilehash: dacc1222958ab05971c9681d33a0c431b72d0531
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59218465"
---
# <a name="datagrid-styles-and-templates"></a>DataGrid Stilleri ve Şablonları
Bu konu için şablonları ve stilleri açıklar <xref:System.Windows.Controls.DataGrid> denetimi. Varsayılan değiştirebileceğiniz <xref:System.Windows.Controls.ControlTemplate> denetim benzersiz bir görünüm sağlamak için. Daha fazla bilgi için [ControlTemplate oluşturarak varolan denetimin görünümünü özelleştirme](customizing-the-appearance-of-an-existing-control.md).  
  
## <a name="datagrid-parts"></a>DataGrid bölümleri  
 Adlandırılmış bölümleri için aşağıdaki tabloda <xref:System.Windows.Controls.DataGrid> denetimi.  
  
|Bölümü|Tür|Açıklama|  
|-|-|-|  
|PART_ColumnHeadersPresenter|<xref:System.Windows.Controls.Primitives.DataGridColumnHeadersPresenter>|Sütun üst bilgilerini içeren satır.|  
  
 Oluştururken bir <xref:System.Windows.Controls.ControlTemplate> için bir <xref:System.Windows.Controls.DataGrid>, şablonunuzu içerebilir bir <xref:System.Windows.Controls.ItemsPresenter> içinde bir <xref:System.Windows.Controls.ScrollViewer>. ( <xref:System.Windows.Controls.ItemsPresenter> Her öğe görüntüler <xref:System.Windows.Controls.DataGrid>; <xref:System.Windows.Controls.ScrollViewer> denetimi içinde kaydırma sağlar).  Varsa <xref:System.Windows.Controls.ItemsPresenter> doğrudan alt öğesi değil <xref:System.Windows.Controls.ScrollViewer>, size gereken <xref:System.Windows.Controls.ItemsPresenter> adı `ItemsPresenter`.  
  
 İçin varsayılan şablonu <xref:System.Windows.Controls.DataGrid> içeren bir <xref:System.Windows.Controls.ScrollViewer> denetimi. Tarafından tanımlanan bölümleri hakkında daha fazla bilgi için <xref:System.Windows.Controls.ScrollViewer>, bkz: [ScrollViewer stilleri ve şablonları](scrollviewer-styles-and-templates.md).  
  
## <a name="datagrid-states"></a>DataGrid durumları  
 Görsel durumlar için aşağıdaki tabloda <xref:System.Windows.Controls.DataGrid> denetimi.  
  
|VisualState adı|Visualstategroup'u adı|Açıklama|  
|-|-|-|  
|Normal|CommonStates|Varsayılan durumu.|  
|Devre dışı|CommonStates|Denetim devre dışıdır.|  
|InvalidFocused|ValidationStates|Denetim, geçerli değil ve odağa sahip.|  
|InvalidUnfocused|ValidationStates|Denetim, geçerli değil ve odak sahip değil.|  
|Geçerli|ValidationStates|Denetim geçerli değil.|  
  
## <a name="datagridcell-parts"></a>DataGridCell bölümleri  
 <xref:System.Windows.Controls.DataGridCell> Öğesi herhangi bir adlandırılmış bölümü yok.  
  
## <a name="datagridcell-states"></a>DataGridCell durumları  
 Görsel durumlar için aşağıdaki tabloda <xref:System.Windows.Controls.DataGridCell> öğesi.  
  
|VisualState adı|Visualstategroup'u adı|Açıklama|  
|-|-|-|  
|Normal|CommonStates|Varsayılan durumu.|  
|Fareyi üzerine getirme|CommonStates|Fare işaretçisi hücrenin üzerine yerleştirilir.|  
|Odaklanmış|FocusStates|Hücre odağa sahip.|  
|Plana odaklanmadan|FocusStates|Hücre odak yok|  
|Geçerli|CurrentStates|Hücre geçerli hücreyi ' dir.|  
|Normal|CurrentStates|Hücre geçerli hücreyi değil.|  
|Ekran|InteractionStates|Hücre görünen modundadır.|  
|Düzenleme|InteractionStates|Hücre düzenleme modunda olduğu.|  
|Seçildi|SelectionStates|Hücre seçildi.|  
|Seçimi kaldırıldı|SelectionStates|Hücre seçilmedi.|  
|InvalidFocused|ValidationStates|Hücre geçerli değil ve odağa sahip.|  
|InvalidUnfocused|ValidationStates|Hücre geçerli değil ve odak sahip değil.|  
|Geçerli|ValidationStates|Hücre geçerli değil.|  
  
## <a name="datagridrow-parts"></a>DataGridRow bölümleri  
 <xref:System.Windows.Controls.DataGridRow> Öğesi herhangi bir adlandırılmış bölümü yok.  
  
## <a name="datagridrow-states"></a>DataGridRow durumları  
 Görsel durumlar için aşağıdaki tabloda <xref:System.Windows.Controls.DataGridRow> öğesi.  
  
|VisualState adı|Visualstategroup'u adı|Açıklama|  
|-|-|-|  
|Normal|CommonStates|Varsayılan durumu.|  
|Fareyi üzerine getirme|CommonStates|Fare işaretçisi satırın yerleştirilir.|  
|MouseOver_Editing|CommonStates|Fare işaretçisi satırın yerleştirilir ve düzenleme modunda satırdır.|  
|MouseOver_Selected|CommonStates|Fare işaretçisi satırın yerleştirilir ve satır seçildi.|  
|MouseOver_Unfocused_Editing|CommonStates|Satırın fare işaretçisini konumlandırılmış, satır içinde düzenleme modu ve odak sahip değil.|  
|MouseOver_Unfocused_Selected|CommonStates|Satırın fare işaretçisini konumlandırılmış, satır seçilir ve odak sahip değil.|  
|Normal_AlternatingRow|CommonStates|Satır değişen bir satırdır.|  
|Normal_Editing|CommonStates|Düzenleme modunda satırdır.|  
|Normal_Selected|CommonStates|Satır seçildi.|  
|Unfocused_Editing|CommonStates|Satır düzenleme modundayken ve odak sahip değil.|  
|Unfocused_Selected|CommonStates|Satır seçilir ve odak sahip değil.|  
|InvalidFocused|ValidationStates|Denetim, geçerli değil ve odağa sahip.|  
|InvalidUnfocused|ValidationStates|Denetim, geçerli değil ve odak sahip değil.|  
|Geçerli|ValidationStates|Denetim geçerli değil.|  
  
## <a name="datagridrowheader-parts"></a>DataGridRowHeader bölümleri  
 Adlandırılmış bölümleri için aşağıdaki tabloda <xref:System.Windows.Controls.Primitives.DataGridRowHeader> öğesi.  
  
|Bölümü|Tür|Açıklama|  
|-|-|-|  
|PART_TopHeaderGripper|<xref:System.Windows.Controls.Primitives.Thumb>|Satır üst bilgisi üst yeniden boyutlandırmak için kullanılan öğe.|  
|PART_BottomHeaderGripper|<xref:System.Windows.Controls.Primitives.Thumb>|Satır üst bilgisi aşağıdan yeniden boyutlandırmak için kullanılan öğe.|  
  
## <a name="datagridrowheader-states"></a>DataGridRowHeader durumları  
 Görsel durumlar için aşağıdaki tabloda <xref:System.Windows.Controls.Primitives.DataGridRowHeader> öğesi.  
  
|VisualState adı|Visualstategroup'u adı|Açıklama|  
|-|-|-|  
|Normal|CommonStates|Varsayılan durumu.|  
|Fareyi üzerine getirme|CommonStates|Fare işaretçisi satırın yerleştirilir.|  
|MouseOver_CurrentRow|CommonStates|Fare işaretçisi satırın yerleştirilir ve satır geçerli bir satırdır.|  
|MouseOver_CurrentRow_Selected|CommonStates|Fare işaretçisi satırın yerleştirilir ve satırın geçerli ve seçili.|  
|MouseOver_EditingRow|CommonStates|Fare işaretçisi satırın yerleştirilir ve düzenleme modunda satırdır.|  
|MouseOver_Selected|CommonStates|Fare işaretçisi satırın yerleştirilir ve satır seçildi.|  
|MouseOver_Unfocused_CurrentRow_Selected|CommonStates|Fare işaretçisi yerleştirilmiş satır üzerinde satırın geçerli ve seçili olduğundan ve odak sahip değil.|  
|MouseOver_Unfocused_EditingRow|CommonStates|Satırın fare işaretçisini konumlandırılmış, satır içinde düzenleme modu ve odak sahip değil.|  
|MouseOver_Unfocused_Selected|CommonStates|Satırın fare işaretçisini konumlandırılmış, satır seçilir ve odak sahip değil.|  
|Normal_CurrentRow|CommonStates|Geçerli satırın satırdır.|  
|Normal_CurrentRow_Selected|CommonStates|Satırın geçerli satır ve seçilir.|  
|Normal_EditingRow|CommonStates|Düzenleme modunda satırdır.|  
|Normal_Selected|CommonStates|Satır seçildi.|  
|Unfocused_CurrentRow_Selected|CommonStates|Satırın geçerli satır, seçili olduğundan ve odak sahip değil.|  
|Unfocused_EditingRow|CommonStates|Satır düzenleme modundayken ve odak sahip değil.|  
|Unfocused_Selected|CommonStates|Satır seçilir ve odak sahip değil.|  
|InvalidFocused|ValidationStates|Denetim, geçerli değil ve odağa sahip.|  
|InvalidUnfocused|ValidationStates|Denetim, geçerli değil ve odak sahip değil.|  
|Geçerli|ValidationStates|Denetim geçerli değil.|  
  
## <a name="datagridcolumnheaderspresenter-parts"></a>DataGridColumnHeadersPresenter Parts  
 Adlandırılmış bölümleri için aşağıdaki tabloda <xref:System.Windows.Controls.Primitives.DataGridColumnHeadersPresenter> öğesi.  
  
|Bölümü|Tür|Açıklama|  
|-|-|-|  
|PART_FillerColumnHeader|<xref:System.Windows.Controls.Primitives.DataGridColumnHeader>|Sütun başlığı için yer tutucu.|  
  
## <a name="datagridcolumnheaderspresenter-states"></a>DataGridColumnHeadersPresenter States  
 Görsel durumlar için aşağıdaki tabloda <xref:System.Windows.Controls.Primitives.DataGridColumnHeadersPresenter> öğesi.  
  
|VisualState adı|Visualstategroup'u adı|Açıklama|  
|-|-|-|  
|InvalidFocused|ValidationStates|Hücre geçerli değil ve odağa sahip.|  
|InvalidUnfocused|ValidationStates|Hücre geçerli değil ve odak sahip değil.|  
|Geçerli|ValidationStates|Hücre geçerli değil.|  
  
## <a name="datagridcolumnheader-parts"></a>DataGridColumnHeader bölümleri  
 Adlandırılmış bölümleri için aşağıdaki tabloda <xref:System.Windows.Controls.Primitives.DataGridColumnHeader> öğesi.  
  
|Bölümü|Tür|Açıklama|  
|-|-|-|  
|PART_LeftHeaderGripper|<xref:System.Windows.Controls.Primitives.Thumb>|Sol sütun başlığına yeniden boyutlandırmak için kullanılan öğe.|  
|PART_RightHeaderGripper|<xref:System.Windows.Controls.Primitives.Thumb>|Sağ sütun başlığına yeniden boyutlandırmak için kullanılan öğe.|  
  
## <a name="datagridcolumnheader-states"></a>DataGridColumnHeader States  
 Görsel durumlar için aşağıdaki tabloda <xref:System.Windows.Controls.Primitives.DataGridColumnHeader> öğesi.  
  
|VisualState adı|Visualstategroup'u adı|Açıklama|  
|-|-|-|  
|Normal|CommonStates|Varsayılan durumu.|  
|Fareyi üzerine getirme|CommonStates|Fare işaretçisi denetimin üzerine yerleştirilir.|  
|Basılan|CommonStates|Denetime basıldığında.|  
|SortAscending|SortStates|Sütun, artan düzende sıralanır.|  
|SortDescending|SortStates|Sütun, azalan düzende sıralanır.|  
|Sıralanmamış|SortStates|Sütun sıralı değil.|  
|InvalidFocused|ValidationStates|Denetim, geçerli değil ve odağa sahip.|  
|InvalidUnfocused|ValidationStates|Denetim, geçerli değil ve odak sahip değil.|  
|Geçerli|ValidationStates|Denetim geçerli değil.|  
  
## <a name="datagrid-controltemplate-example"></a>DataGrid ControlTemplate Örneği  
 Aşağıdaki örnek nasıl tanımlanacağını gösterir bir <xref:System.Windows.Controls.ControlTemplate> için <xref:System.Windows.Controls.DataGrid> denetimi ve ilişkili türleri.  
  
 [!code-xaml[ControlTemplateExamples#DataGrid](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/datagrid.xaml#datagrid)]  
  
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
