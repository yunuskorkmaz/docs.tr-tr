---
title: DataGrid Stilleri ve Şablonları
description: Windows Presentation Foundation DataGrid denetimi için stiller ve şablonlar hakkında bilgi edinin. Denetime benzersiz bir görünüm sağlamak için ControlTemplate 'i değiştirin.
ms.date: 03/30/2017
helpviewer_keywords:
- states [WPF], DataGrid
- ControlTemplate [WPF], DataGrid
- DataGrid [WPF], styles and templates
- templates [WPF], DataGrid
- styles [WPF], DataGrid
- parts [WPF], DataGrid
ms.assetid: 9cb31d63-f148-4d25-b079-816e73f988c7
ms.openlocfilehash: dd526ec64d5077dad58f31c004f47e63c57ec9de
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168329"
---
# <a name="datagrid-styles-and-templates"></a>DataGrid Stilleri ve Şablonları
Bu konuda, denetimin stilleri ve şablonları açıklanmaktadır <xref:System.Windows.Controls.DataGrid> . <xref:System.Windows.Controls.ControlTemplate>Denetim için benzersiz bir görünüm sağlamak üzere varsayılan ' i değiştirebilirsiniz. Daha fazla bilgi için bkz. [Denetim için şablon oluşturma](../../../desktop-wpf/themes/how-to-create-apply-template.md).  
  
## <a name="datagrid-parts"></a>DataGrid bölümleri  
 Aşağıdaki tabloda, denetimin adlandırılmış parçaları listelenmektedir <xref:System.Windows.Controls.DataGrid> .  
  
|Bölüm|Tür|Açıklama|  
|-|-|-|  
|PART_ColumnHeadersPresenter|<xref:System.Windows.Controls.Primitives.DataGridColumnHeadersPresenter>|Sütun üst bilgilerini içeren satır.|  
  
 Bir <xref:System.Windows.Controls.ControlTemplate> için oluşturduğunuzda <xref:System.Windows.Controls.DataGrid> , şablonunuz <xref:System.Windows.Controls.ItemsPresenter> bir içinde içerebilir <xref:System.Windows.Controls.ScrollViewer> . (, <xref:System.Windows.Controls.ItemsPresenter> İçindeki her öğeyi görüntüler <xref:System.Windows.Controls.DataGrid> ; <xref:System.Windows.Controls.ScrollViewer> denetim içinde kaydırmayı etkinleştirilir).  <xref:System.Windows.Controls.ItemsPresenter>Öğesinin doğrudan alt öğesi değilse, <xref:System.Windows.Controls.ScrollViewer> <xref:System.Windows.Controls.ItemsPresenter> adını vermelisiniz `ItemsPresenter` .  
  
 İçin varsayılan şablon <xref:System.Windows.Controls.DataGrid> bir <xref:System.Windows.Controls.ScrollViewer> denetim içerir. Tarafından tanımlanan parçalar hakkında daha fazla bilgi için <xref:System.Windows.Controls.ScrollViewer> bkz. [ScrollViewer stilleri ve şablonları](scrollviewer-styles-and-templates.md).  
  
## <a name="datagrid-states"></a>DataGrid durumları  
 Aşağıdaki tabloda denetim için görsel durumlar listelenmektedir <xref:System.Windows.Controls.DataGrid> .  
  
|VisualState adı|VisualStateGroup adı|Açıklama|  
|-|-|-|  
|Normal|Ortak durumlar|Varsayılan durum.|  
|Devre dışı|Ortak durumlar|Denetim devre dışı bırakıldı.|  
|Invalidodaklanmış|Doğrulama durumları|Denetim geçerli değil ve odağa sahip.|  
|Invalidunodaklanmış|Doğrulama durumları|Denetim geçerli değil ve odağa sahip değil.|  
|Geçerli|Doğrulama durumları|Denetim geçerli.|  
  
## <a name="datagridcell-parts"></a>DataGridCell bölümleri  
 <xref:System.Windows.Controls.DataGridCell>Öğede adlandırılmış bölüm yok.  
  
## <a name="datagridcell-states"></a>DataGridCell durumları  
 Aşağıdaki tabloda öğesi için görsel durumlar listelenmektedir <xref:System.Windows.Controls.DataGridCell> .  
  
|VisualState adı|VisualStateGroup adı|Açıklama|  
|-|-|-|  
|Normal|Ortak durumlar|Varsayılan durum.|  
|Gelme olayından|Ortak durumlar|Fare işaretçisi hücrenin üzerine konumlandırılır.|  
|Odaklı|Odaklardaki durumlar|Hücre odağa sahip.|  
|Odaklanmadan gözetle|Odaklardaki durumlar|Hücrede odak yok|  
|Geçerli|CurrentStates|Hücre geçerli hücredir.|  
|Düzenli|CurrentStates|Hücre geçerli hücre değil.|  
|Göster|Interactionstates|Hücre, görüntüleme modundadır.|  
|Düzenleniyor|Interactionstates|Hücre düzenleme modunda.|  
|Seçili|SelectionStates|Hücre seçildi.|  
|Değilken|SelectionStates|Hücre seçilmemiş.|  
|Invalidodaklanmış|Doğrulama durumları|Hücre geçerli değil ve odağa sahip.|  
|Invalidunodaklanmış|Doğrulama durumları|Hücre geçerli değil ve odağı yok.|  
|Geçerli|Doğrulama durumları|Hücre geçerli.|  
  
## <a name="datagridrow-parts"></a>DataGridRow parçaları  
 <xref:System.Windows.Controls.DataGridRow>Öğede adlandırılmış bölüm yok.  
  
## <a name="datagridrow-states"></a>DataGridRow durumları  
 Aşağıdaki tabloda öğesi için görsel durumlar listelenmektedir <xref:System.Windows.Controls.DataGridRow> .  
  
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
 Aşağıdaki tabloda öğesi için adlandırılmış bölümler listelenmektedir <xref:System.Windows.Controls.Primitives.DataGridRowHeader> .  
  
|Bölüm|Tür|Açıklama|  
|-|-|-|  
|PART_TopHeaderGripper|<xref:System.Windows.Controls.Primitives.Thumb>|Üstteki satır üstbilgisini yeniden boyutlandırmak için kullanılan öğe.|  
|PART_BottomHeaderGripper|<xref:System.Windows.Controls.Primitives.Thumb>|Satır üstbilgisini alttan yeniden boyutlandırmak için kullanılan öğe.|  
  
## <a name="datagridrowheader-states"></a>DataGridRowHeader durumları  
 Aşağıdaki tabloda öğesi için görsel durumlar listelenmektedir <xref:System.Windows.Controls.Primitives.DataGridRowHeader> .  
  
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
 Aşağıdaki tabloda öğesi için adlandırılmış bölümler listelenmektedir <xref:System.Windows.Controls.Primitives.DataGridColumnHeadersPresenter> .  
  
|Bölüm|Tür|Açıklama|  
|-|-|-|  
|PART_FillerColumnHeader|<xref:System.Windows.Controls.Primitives.DataGridColumnHeader>|Sütun üst bilgileri için yer tutucu.|  
  
## <a name="datagridcolumnheaderspresenter-states"></a>DataGridColumnHeadersPresenter durumları  
 Aşağıdaki tabloda öğesi için görsel durumlar listelenmektedir <xref:System.Windows.Controls.Primitives.DataGridColumnHeadersPresenter> .  
  
|VisualState adı|VisualStateGroup adı|Açıklama|  
|-|-|-|  
|Invalidodaklanmış|Doğrulama durumları|Hücre geçerli değil ve odağa sahip.|  
|Invalidunodaklanmış|Doğrulama durumları|Hücre geçerli değil ve odağı yok.|  
|Geçerli|Doğrulama durumları|Hücre geçerli.|  
  
## <a name="datagridcolumnheader-parts"></a>DataGridColumnHeader parçaları  
 Aşağıdaki tabloda öğesi için adlandırılmış bölümler listelenmektedir <xref:System.Windows.Controls.Primitives.DataGridColumnHeader> .  
  
|Bölüm|Tür|Açıklama|  
|-|-|-|  
|PART_LeftHeaderGripper|<xref:System.Windows.Controls.Primitives.Thumb>|Sol taraftaki sütun üst bilgisini yeniden boyutlandırmak için kullanılan öğe.|  
|PART_RightHeaderGripper|<xref:System.Windows.Controls.Primitives.Thumb>|Sağdaki sütun üst bilgisini yeniden boyutlandırmak için kullanılan öğesi.|  
  
## <a name="datagridcolumnheader-states"></a>DataGridColumnHeader durumları  
 Aşağıdaki tabloda öğesi için görsel durumlar listelenmektedir <xref:System.Windows.Controls.Primitives.DataGridColumnHeader> .  
  
|VisualState adı|VisualStateGroup adı|Açıklama|  
|-|-|-|  
|Normal|Ortak durumlar|Varsayılan durum.|  
|Gelme olayından|Ortak durumlar|Fare işaretçisi denetimin üzerine yerleştirilir.|  
|Pressed|Ortak durumlar|Denetime basıldığında.|  
|Sortascbitiriliyor|SortStates|Sütun artan düzende sıralanır.|  
|Sortazalan|SortStates|Sütun, azalan düzende sıralanır.|  
|Olmayan|SortStates|Sütun sıralanmaz.|  
|Invalidodaklanmış|Doğrulama durumları|Denetim geçerli değil ve odağa sahip.|  
|Invalidunodaklanmış|Doğrulama durumları|Denetim geçerli değil ve odağa sahip değil.|  
|Geçerli|Doğrulama durumları|Denetim geçerli.|  
  
## <a name="datagrid-controltemplate-example"></a>DataGrid ControlTemplate örneği  
 Aşağıdaki örnek, <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.DataGrid> denetimin ve ilişkili türlerinin nasıl tanımlanacağını gösterir.  
  
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
