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
ms.openlocfilehash: 066e8c9ce1112399be8128d0821498f0d56a3dc3
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283798"
---
# <a name="datagrid-styles-and-templates"></a>DataGrid Stilleri ve Şablonları
Bu konuda <xref:System.Windows.Controls.DataGrid> denetimine yönelik stiller ve şablonlar açıklanmaktadır. Denetime benzersiz bir görünüm sağlamak için varsayılan <xref:System.Windows.Controls.ControlTemplate> değiştirebilirsiniz. Daha fazla bilgi için bkz. [Denetim için şablon oluşturma](../../../desktop-wpf/themes/how-to-create-apply-template.md).  
  
## <a name="datagrid-parts"></a>DataGrid bölümleri  
 Aşağıdaki tabloda <xref:System.Windows.Controls.DataGrid> denetimi için adlandırılmış bölümler listelenmektedir.  
  
|Bölümüyle|Type|Açıklama|  
|-|-|-|  
|PART_ColumnHeadersPresenter|<xref:System.Windows.Controls.Primitives.DataGridColumnHeadersPresenter>|Sütun üst bilgilerini içeren satır.|  
  
 Bir <xref:System.Windows.Controls.DataGrid>için <xref:System.Windows.Controls.ControlTemplate> oluşturduğunuzda, şablonunuz <xref:System.Windows.Controls.ScrollViewer>içinde bir <xref:System.Windows.Controls.ItemsPresenter> içerebilir. (<xref:System.Windows.Controls.ItemsPresenter>, <xref:System.Windows.Controls.DataGrid>her öğeyi görüntüler; <xref:System.Windows.Controls.ScrollViewer> denetimin içinde kaydırmaya izin vermez).  <xref:System.Windows.Controls.ItemsPresenter>, <xref:System.Windows.Controls.ScrollViewer>doğrudan alt öğesi değilse, `ItemsPresenter`adına <xref:System.Windows.Controls.ItemsPresenter> vermelisiniz.  
  
 <xref:System.Windows.Controls.DataGrid> için varsayılan şablon <xref:System.Windows.Controls.ScrollViewer> bir denetim içerir. <xref:System.Windows.Controls.ScrollViewer>tarafından tanımlanan parçalar hakkında daha fazla bilgi için bkz. [ScrollViewer stilleri ve şablonları](scrollviewer-styles-and-templates.md).  
  
## <a name="datagrid-states"></a>DataGrid durumları  
 Aşağıdaki tabloda <xref:System.Windows.Controls.DataGrid> denetimi için görsel durumlar listelenmektedir.  
  
|VisualState adı|VisualStateGroup adı|Açıklama|  
|-|-|-|  
|Normal|Ortak durumlar|Varsayılan durum.|  
|Devre dışı|Ortak durumlar|Denetim devre dışı bırakıldı.|  
|Invalidodaklanmış|Doğrulama durumları|Denetim geçerli değil ve odağa sahip.|  
|Invalidunodaklanmış|Doğrulama durumları|Denetim geçerli değil ve odağa sahip değil.|  
|Geçerli|Doğrulama durumları|Denetim geçerli.|  
  
## <a name="datagridcell-parts"></a>DataGridCell bölümleri  
 <xref:System.Windows.Controls.DataGridCell> öğesinin adlandırılmış bölümü yok.  
  
## <a name="datagridcell-states"></a>DataGridCell durumları  
 Aşağıdaki tabloda <xref:System.Windows.Controls.DataGridCell> öğesi için görsel durumlar listelenmektedir.  
  
|VisualState adı|VisualStateGroup adı|Açıklama|  
|-|-|-|  
|Normal|Ortak durumlar|Varsayılan durum.|  
|Gelme olayından|Ortak durumlar|Fare işaretçisi hücrenin üzerine konumlandırılır.|  
|Diğinize|Odaklardaki durumlar|Hücre odağa sahip.|  
|Odaklanmadan gözetle|Odaklardaki durumlar|Hücrede odak yok|  
|Geçerli|CurrentStates|Hücre geçerli hücredir.|  
|Aralıklarla|CurrentStates|Hücre geçerli hücre değil.|  
|Ekran|Interactionstates|Hücre, görüntüleme modundadır.|  
|Düzenleme|Interactionstates|Hücre düzenleme modunda.|  
|Seçildi|SelectionStates|Hücre seçildi.|  
|Değilken|SelectionStates|Hücre seçilmemiş.|  
|Invalidodaklanmış|Doğrulama durumları|Hücre geçerli değil ve odağa sahip.|  
|Invalidunodaklanmış|Doğrulama durumları|Hücre geçerli değil ve odağı yok.|  
|Geçerli|Doğrulama durumları|Hücre geçerli.|  
  
## <a name="datagridrow-parts"></a>DataGridRow parçaları  
 <xref:System.Windows.Controls.DataGridRow> öğesinin adlandırılmış bölümü yok.  
  
## <a name="datagridrow-states"></a>DataGridRow durumları  
 Aşağıdaki tabloda <xref:System.Windows.Controls.DataGridRow> öğesi için görsel durumlar listelenmektedir.  
  
|VisualState adı|VisualStateGroup adı|Açıklama|  
|-|-|-|  
|Normal|Ortak durumlar|Varsayılan durum.|  
|Gelme olayından|Ortak durumlar|Fare işaretçisi, satırın üzerine yerleştirilir.|  
|MouseOver_Editing|Ortak durumlar|Fare işaretçisi, satırın üzerine konumlandırılır ve satır düzenleme modundadır.|  
|MouseOver_Selected|Ortak durumlar|Fare işaretçisi, satırın üzerine konumlandırılır ve satır seçilir.|  
|MouseOver_Unfocused_Editing|Ortak durumlar|Fare işaretçisi, satırın üzerine konumlandırılır, satır düzenleme modundadır ve odağa sahip değildir.|  
|MouseOver_Unfocused_Selected|Ortak durumlar|Fare işaretçisi, satırın üzerine konumlandırılır, satır seçilir ve odağa sahip değildir.|  
|Normal_AlternatingRow|Ortak durumlar|Satır, alternatif bir satırdır.|  
|Normal_Editing|Ortak durumlar|Satır düzenleme modundadır.|  
|Normal_Selected|Ortak durumlar|Satır seçilir.|  
|Unfocused_Editing|Ortak durumlar|Satır düzenleme modundadır ve odağa sahip değildir.|  
|Unfocused_Selected|Ortak durumlar|Satır seçilir ve odağa sahip değildir.|  
|Invalidodaklanmış|Doğrulama durumları|Denetim geçerli değil ve odağa sahip.|  
|Invalidunodaklanmış|Doğrulama durumları|Denetim geçerli değil ve odağa sahip değil.|  
|Geçerli|Doğrulama durumları|Denetim geçerli.|  
  
## <a name="datagridrowheader-parts"></a>DataGridRowHeader parçaları  
 Aşağıdaki tabloda <xref:System.Windows.Controls.Primitives.DataGridRowHeader> öğesi için adlandırılmış bölümler listelenmektedir.  
  
|Bölümüyle|Type|Açıklama|  
|-|-|-|  
|PART_TopHeaderGripper|<xref:System.Windows.Controls.Primitives.Thumb>|Üstteki satır üstbilgisini yeniden boyutlandırmak için kullanılan öğe.|  
|PART_BottomHeaderGripper|<xref:System.Windows.Controls.Primitives.Thumb>|Satır üstbilgisini alttan yeniden boyutlandırmak için kullanılan öğe.|  
  
## <a name="datagridrowheader-states"></a>DataGridRowHeader durumları  
 Aşağıdaki tabloda <xref:System.Windows.Controls.Primitives.DataGridRowHeader> öğesi için görsel durumlar listelenmektedir.  
  
|VisualState adı|VisualStateGroup adı|Açıklama|  
|-|-|-|  
|Normal|Ortak durumlar|Varsayılan durum.|  
|Gelme olayından|Ortak durumlar|Fare işaretçisi, satırın üzerine yerleştirilir.|  
|MouseOver_CurrentRow|Ortak durumlar|Fare işaretçisi, satırın üzerine konumlandırılır ve satır geçerli satırdır.|  
|MouseOver_CurrentRow_Selected|Ortak durumlar|Fare işaretçisi, satırın üzerine konumlandırılır ve satır geçerli ve seçilir.|  
|MouseOver_EditingRow|Ortak durumlar|Fare işaretçisi, satırın üzerine konumlandırılır ve satır düzenleme modundadır.|  
|MouseOver_Selected|Ortak durumlar|Fare işaretçisi, satırın üzerine konumlandırılır ve satır seçilir.|  
|MouseOver_Unfocused_CurrentRow_Selected|Ortak durumlar|Fare işaretçisi, satırın üzerine konumlandırılır, satır geçerli ve seçilir ve odağa sahip değildir.|  
|MouseOver_Unfocused_EditingRow|Ortak durumlar|Fare işaretçisi, satırın üzerine konumlandırılır, satır düzenleme modundadır ve odağa sahip değildir.|  
|MouseOver_Unfocused_Selected|Ortak durumlar|Fare işaretçisi, satırın üzerine konumlandırılır, satır seçilir ve odağa sahip değildir.|  
|Normal_CurrentRow|Ortak durumlar|Satır geçerli satırdır.|  
|Normal_CurrentRow_Selected|Ortak durumlar|Satır geçerli satırdır ve seçilir.|  
|Normal_EditingRow|Ortak durumlar|Satır düzenleme modundadır.|  
|Normal_Selected|Ortak durumlar|Satır seçilir.|  
|Unfocused_CurrentRow_Selected|Ortak durumlar|Satır geçerli satırdır, seçilir ve odağa sahip değildir.|  
|Unfocused_EditingRow|Ortak durumlar|Satır düzenleme modundadır ve odağa sahip değildir.|  
|Unfocused_Selected|Ortak durumlar|Satır seçilir ve odağa sahip değildir.|  
|Invalidodaklanmış|Doğrulama durumları|Denetim geçerli değil ve odağa sahip.|  
|Invalidunodaklanmış|Doğrulama durumları|Denetim geçerli değil ve odağa sahip değil.|  
|Geçerli|Doğrulama durumları|Denetim geçerli.|  
  
## <a name="datagridcolumnheaderspresenter-parts"></a>DataGridColumnHeadersPresenter bölümleri  
 Aşağıdaki tabloda <xref:System.Windows.Controls.Primitives.DataGridColumnHeadersPresenter> öğesi için adlandırılmış bölümler listelenmektedir.  
  
|Bölümüyle|Type|Açıklama|  
|-|-|-|  
|PART_FillerColumnHeader|<xref:System.Windows.Controls.Primitives.DataGridColumnHeader>|Sütun üst bilgileri için yer tutucu.|  
  
## <a name="datagridcolumnheaderspresenter-states"></a>DataGridColumnHeadersPresenter durumları  
 Aşağıdaki tabloda <xref:System.Windows.Controls.Primitives.DataGridColumnHeadersPresenter> öğesi için görsel durumlar listelenmektedir.  
  
|VisualState adı|VisualStateGroup adı|Açıklama|  
|-|-|-|  
|Invalidodaklanmış|Doğrulama durumları|Hücre geçerli değil ve odağa sahip.|  
|Invalidunodaklanmış|Doğrulama durumları|Hücre geçerli değil ve odağı yok.|  
|Geçerli|Doğrulama durumları|Hücre geçerli.|  
  
## <a name="datagridcolumnheader-parts"></a>DataGridColumnHeader parçaları  
 Aşağıdaki tabloda <xref:System.Windows.Controls.Primitives.DataGridColumnHeader> öğesi için adlandırılmış bölümler listelenmektedir.  
  
|Bölümüyle|Type|Açıklama|  
|-|-|-|  
|PART_LeftHeaderGripper|<xref:System.Windows.Controls.Primitives.Thumb>|Sol taraftaki sütun üst bilgisini yeniden boyutlandırmak için kullanılan öğe.|  
|PART_RightHeaderGripper|<xref:System.Windows.Controls.Primitives.Thumb>|Sağdaki sütun üst bilgisini yeniden boyutlandırmak için kullanılan öğesi.|  
  
## <a name="datagridcolumnheader-states"></a>DataGridColumnHeader durumları  
 Aşağıdaki tabloda <xref:System.Windows.Controls.Primitives.DataGridColumnHeader> öğesi için görsel durumlar listelenmektedir.  
  
|VisualState adı|VisualStateGroup adı|Açıklama|  
|-|-|-|  
|Normal|Ortak durumlar|Varsayılan durum.|  
|Gelme olayından|Ortak durumlar|Fare işaretçisi denetimin üzerine yerleştirilir.|  
|Basılan|Ortak durumlar|Denetime basıldığında.|  
|Sortascbitiriliyor|SortStates|Sütun artan düzende sıralanır.|  
|Sortazalan|SortStates|Sütun, azalan düzende sıralanır.|  
|Olmayan|SortStates|Sütun sıralanmaz.|  
|Invalidodaklanmış|Doğrulama durumları|Denetim geçerli değil ve odağa sahip.|  
|Invalidunodaklanmış|Doğrulama durumları|Denetim geçerli değil ve odağa sahip değil.|  
|Geçerli|Doğrulama durumları|Denetim geçerli.|  
  
## <a name="datagrid-controltemplate-example"></a>DataGrid ControlTemplate örneği  
 Aşağıdaki örnek, <xref:System.Windows.Controls.DataGrid> denetimi ve ilişkili türleri için <xref:System.Windows.Controls.ControlTemplate> nasıl tanımlanacağını gösterir.  
  
 [!code-xaml[ControlTemplateExamples#DataGrid](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/datagrid.xaml#datagrid)]  
  
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
