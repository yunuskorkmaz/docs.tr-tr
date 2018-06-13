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
ms.openlocfilehash: 71c9b08407c6e570b42c4fbb7dc264829b5dc17c
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/23/2018
ms.locfileid: "34457599"
---
# <a name="datagrid-styles-and-templates"></a>DataGrid Stilleri ve Şablonları
Stilleri ve şablonları için bu konuda açıklanmaktadır <xref:System.Windows.Controls.DataGrid> denetim. Varsayılan değiştirebileceğiniz <xref:System.Windows.Controls.ControlTemplate> denetimi benzersiz bir görünüm vermek için. Daha fazla bilgi için bkz: [ControlTemplate oluşturarak varolan denetiminin görünümünü özelleştirme](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).  
  
## <a name="datagrid-parts"></a>DataGrid bölümleri  
 Adlandırılmış bölümleri için aşağıdaki tabloda listelenmektedir <xref:System.Windows.Controls.DataGrid> denetim.  
  
|Bölümü|Tür|Açıklama|  
|-|-|-|  
|PART_ColumnHeadersPresenter|<xref:System.Windows.Controls.Primitives.DataGridColumnHeadersPresenter>|Sütun üstbilgileri içeren satırı.|  
  
 Oluştururken bir <xref:System.Windows.Controls.ControlTemplate> için bir <xref:System.Windows.Controls.DataGrid>, şablonunuzu içerebilir bir <xref:System.Windows.Controls.ItemsPresenter> içinde bir <xref:System.Windows.Controls.ScrollViewer>. ( <xref:System.Windows.Controls.ItemsPresenter> Her öğe görüntüler <xref:System.Windows.Controls.DataGrid>; <xref:System.Windows.Controls.ScrollViewer> içinde denetimin kaydırma sağlar).  Varsa <xref:System.Windows.Controls.ItemsPresenter> doğrudan alt öğesi değil <xref:System.Windows.Controls.ScrollViewer>, vermeniz gerekir <xref:System.Windows.Controls.ItemsPresenter> adı `ItemsPresenter`.  
  
 İçin varsayılan şablon <xref:System.Windows.Controls.DataGrid> içeren bir <xref:System.Windows.Controls.ScrollViewer> denetim. Tarafından tanımlanan bölümleri hakkında daha fazla bilgi için <xref:System.Windows.Controls.ScrollViewer>, bkz: [ScrollViewer stilleri ve şablonları](../../../../docs/framework/wpf/controls/scrollviewer-styles-and-templates.md).  
  
## <a name="datagrid-states"></a>DataGrid durumları  
 Aşağıdaki tablo için görsel durumlarını listeler <xref:System.Windows.Controls.DataGrid> denetim.  
  
|VisualState adı|VisualStateGroup adı|Açıklama|  
|-|-|-|  
|Normal|CommonStates|Varsayılan durumu.|  
|Devre dışı|CommonStates|Denetim devre dışı bırakıldı.|  
|InvalidFocused|ValidationStates|Denetim geçerli değil ve odağa sahip.|  
|InvalidUnfocused|ValidationStates|Denetim geçerli değil ve odağa sahip değil.|  
|Geçerli|ValidationStates|Denetim geçerli değil.|  
  
## <a name="datagridcell-parts"></a>DataGridCell bölümleri  
 <xref:System.Windows.Controls.DataGridCell> Öğesi adlandırılmış tüm bölümler sahip değil.  
  
## <a name="datagridcell-states"></a>DataGridCell durumları  
 Aşağıdaki tablo için görsel durumlarını listeler <xref:System.Windows.Controls.DataGridCell> öğesi.  
  
|VisualState adı|VisualStateGroup adı|Açıklama|  
|-|-|-|  
|Normal|CommonStates|Varsayılan durumu.|  
|Fare üzerinde|CommonStates|Fare işaretçisini hücrenin üzerine yerleştirilir.|  
|Odaklanmış|FocusStates|Hücre odağa sahip.|  
|Odaksız|FocusStates|Hücre odak yok|  
|Geçerli|CurrentStates|Hücre geçerli hücreyi ' dir.|  
|Normal|CurrentStates|Hücre geçerli hücreyi değil.|  
|Ekran|InteractionStates|Hücre görüntü modunda değil.|  
|Düzenleme|InteractionStates|Hücre düzenleme modunda değil.|  
|Seçili|SelectionStates|Hücre seçilir.|  
|Seçilmemiş|SelectionStates|Hücre seçilmedi.|  
|InvalidFocused|ValidationStates|Hücre geçerli değil ve odağa sahip.|  
|InvalidUnfocused|ValidationStates|Hücre geçerli değil ve odağa sahip değil.|  
|Geçerli|ValidationStates|Hücre geçerli değil.|  
  
## <a name="datagridrow-parts"></a>DataGridRow bölümleri  
 <xref:System.Windows.Controls.DataGridRow> Öğesi adlandırılmış tüm bölümler sahip değil.  
  
## <a name="datagridrow-states"></a>DataGridRow durumları  
 Aşağıdaki tablo için görsel durumlarını listeler <xref:System.Windows.Controls.DataGridRow> öğesi.  
  
|VisualState adı|VisualStateGroup adı|Açıklama|  
|-|-|-|  
|Normal|CommonStates|Varsayılan durumu.|  
|Fare üzerinde|CommonStates|Fare işaretçisini satırın yerleştirilir.|  
|MouseOver_Editing|CommonStates|Fare işaretçisini satırın yerleştirilir ve düzenleme modunda satırıdır.|  
|MouseOver_Selected|CommonStates|Fare işaretçisini satırın yerleştirilir ve satır seçilir.|  
|MouseOver_Unfocused_Editing|CommonStates|Fare işaretçisini satır içinde konumlandırılır, satır içinde düzenleme modu ve odağa sahip değil.|  
|MouseOver_Unfocused_Selected|CommonStates|Fare işaretçisini satır içinde konumlandırılır, satır seçilir ve odağa sahip değil.|  
|Normal_AlternatingRow|CommonStates|Satır değişen bir satırdır.|  
|Normal_Editing|CommonStates|Düzenleme modunda satırıdır.|  
|Normal_Selected|CommonStates|Satır seçilir.|  
|Unfocused_Editing|CommonStates|Satır düzenleme modundayken ve odağa sahip değil.|  
|Unfocused_Selected|CommonStates|Satır seçilir ve odağa sahip değil.|  
|InvalidFocused|ValidationStates|Denetim geçerli değil ve odağa sahip.|  
|InvalidUnfocused|ValidationStates|Denetim geçerli değil ve odağa sahip değil.|  
|Geçerli|ValidationStates|Denetim geçerli değil.|  
  
## <a name="datagridrowheader-parts"></a>DataGridRowHeader bölümleri  
 Adlandırılmış bölümleri için aşağıdaki tabloda listelenmektedir <xref:System.Windows.Controls.Primitives.DataGridRowHeader> öğesi.  
  
|Bölümü|Tür|Açıklama|  
|-|-|-|  
|PART_TopHeaderGripper|<xref:System.Windows.Controls.Primitives.Thumb>|Üst satır başlığından yeniden boyutlandırmak için kullanılan öğe.|  
|PART_BottomHeaderGripper|<xref:System.Windows.Controls.Primitives.Thumb>|Alt satır başlığından yeniden boyutlandırmak için kullanılan öğe.|  
  
## <a name="datagridrowheader-states"></a>DataGridRowHeader durumları  
 Aşağıdaki tablo için görsel durumlarını listeler <xref:System.Windows.Controls.Primitives.DataGridRowHeader> öğesi.  
  
|VisualState adı|VisualStateGroup adı|Açıklama|  
|-|-|-|  
|Normal|CommonStates|Varsayılan durumu.|  
|Fare üzerinde|CommonStates|Fare işaretçisini satırın yerleştirilir.|  
|MouseOver_CurrentRow|CommonStates|Fare işaretçisini satırın yerleştirilir ve geçerli satır satırıdır.|  
|MouseOver_CurrentRow_Selected|CommonStates|Fare işaretçisini satırın yerleştirilir ve geçerli ve seçili satırıdır.|  
|MouseOver_EditingRow|CommonStates|Fare işaretçisini satırın yerleştirilir ve düzenleme modunda satırıdır.|  
|MouseOver_Selected|CommonStates|Fare işaretçisini satırın yerleştirilir ve satır seçilir.|  
|MouseOver_Unfocused_CurrentRow_Selected|CommonStates|Fare işaretçisini konumlandırılmış satır üzerinden satır geçerli ve seçili ve odağa sahip değil.|  
|MouseOver_Unfocused_EditingRow|CommonStates|Fare işaretçisini satır içinde konumlandırılır, satır içinde düzenleme modu ve odağa sahip değil.|  
|MouseOver_Unfocused_Selected|CommonStates|Fare işaretçisini satır içinde konumlandırılır, satır seçilir ve odağa sahip değil.|  
|Normal_CurrentRow|CommonStates|Geçerli satırda satırıdır.|  
|Normal_CurrentRow_Selected|CommonStates|Satır geçerli satır ve seçilir.|  
|Normal_EditingRow|CommonStates|Düzenleme modunda satırıdır.|  
|Normal_Selected|CommonStates|Satır seçilir.|  
|Unfocused_CurrentRow_Selected|CommonStates|Satır geçerli satır, seçilir ve odağa sahip değil.|  
|Unfocused_EditingRow|CommonStates|Satır düzenleme modundayken ve odağa sahip değil.|  
|Unfocused_Selected|CommonStates|Satır seçilir ve odağa sahip değil.|  
|InvalidFocused|ValidationStates|Denetim geçerli değil ve odağa sahip.|  
|InvalidUnfocused|ValidationStates|Denetim geçerli değil ve odağa sahip değil.|  
|Geçerli|ValidationStates|Denetim geçerli değil.|  
  
## <a name="datagridcolumnheaderspresenter-parts"></a>DataGridColumnHeadersPresenter bölümleri  
 Adlandırılmış bölümleri için aşağıdaki tabloda listelenmektedir <xref:System.Windows.Controls.Primitives.DataGridColumnHeadersPresenter> öğesi.  
  
|Bölümü|Tür|Açıklama|  
|-|-|-|  
|PART_FillerColumnHeader|<xref:System.Windows.Controls.Primitives.DataGridColumnHeader>|Sütun başlığı için yer tutucu.|  
  
## <a name="datagridcolumnheaderspresenter-states"></a>DataGridColumnHeadersPresenter durumları  
 Aşağıdaki tablo için görsel durumlarını listeler <xref:System.Windows.Controls.Primitives.DataGridColumnHeadersPresenter> öğesi.  
  
|VisualState adı|VisualStateGroup adı|Açıklama|  
|-|-|-|  
|InvalidFocused|ValidationStates|Hücre geçerli değil ve odağa sahip.|  
|InvalidUnfocused|ValidationStates|Hücre geçerli değil ve odağa sahip değil.|  
|Geçerli|ValidationStates|Hücre geçerli değil.|  
  
## <a name="datagridcolumnheader-parts"></a>DataGridColumnHeader bölümleri  
 Adlandırılmış bölümleri için aşağıdaki tabloda listelenmektedir <xref:System.Windows.Controls.Primitives.DataGridColumnHeader> öğesi.  
  
|Bölümü|Tür|Açıklama|  
|-|-|-|  
|PART_LeftHeaderGripper|<xref:System.Windows.Controls.Primitives.Thumb>|Soluna sütun başlığına yeniden boyutlandırmak için kullanılan öğe.|  
|PART_RightHeaderGripper|<xref:System.Windows.Controls.Primitives.Thumb>|Sağ sütun başlığına yeniden boyutlandırmak için kullanılan öğe.|  
  
## <a name="datagridcolumnheader-states"></a>DataGridColumnHeader durumları  
 Aşağıdaki tablo için görsel durumlarını listeler <xref:System.Windows.Controls.Primitives.DataGridColumnHeader> öğesi.  
  
|VisualState adı|VisualStateGroup adı|Açıklama|  
|-|-|-|  
|Normal|CommonStates|Varsayılan durumu.|  
|Fare üzerinde|CommonStates|Fare işaretçisini üzerinde denetim konumlandırıldı.|  
|Basılı|CommonStates|Denetim basıldığında.|  
|SortAscending|SortStates|Sütun artan düzende sıralanır.|  
|SortDescending|SortStates|Sütun, azalan sırada sıralanır.|  
|Sıralanmamış|SortStates|Sütun sıralı değil.|  
|InvalidFocused|ValidationStates|Denetim geçerli değil ve odağa sahip.|  
|InvalidUnfocused|ValidationStates|Denetim geçerli değil ve odağa sahip değil.|  
|Geçerli|ValidationStates|Denetim geçerli değil.|  
  
## <a name="datagrid-controltemplate-example"></a>DataGrid ControlTemplate Örneği  
 Aşağıdaki örnekte nasıl tanımlanacağı gösterilmektedir bir <xref:System.Windows.Controls.ControlTemplate> için <xref:System.Windows.Controls.DataGrid> denetimi ve onun ilişkili türler.  
  
 [!code-xaml[ControlTemplateExamples#DataGrid](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/datagrid.xaml#datagrid)]  
  
 Önceki örnekte, bir veya daha fazla aşağıdaki kaynakları kullanır.  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 Tam bir örnek için bkz: [ControlTemplates örneği ile stil oluşturma](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [Denetim Stilleri ve Şablonları](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [Denetim Özelleştirme](../../../../docs/framework/wpf/controls/control-customization.md)  
 [Stil ve Şablon Oluşturma](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [ControlTemplate Oluşturarak Varolan Denetimin Görünümünü Özelleştirme](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
