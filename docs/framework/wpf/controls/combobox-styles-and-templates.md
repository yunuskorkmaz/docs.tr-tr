---
title: ComboBox Stilleri ve Şablonları
description: Windows Presentation Foundation ComboBox denetimi için stiller ve şablonlar hakkında bilgi edinin. Denetime benzersiz bir görünüm sağlamak için ControlTemplate 'i değiştirin.
ms.date: 03/30/2017
helpviewer_keywords:
- ComboBox [WPF], styles and templates
- states [WPF], ComboBox
- ControlTemplate [WPF], ComboBox
- styles [WPF], ComboBox
- templates [WPF], ComboBox
- parts [WPF], ComboBox
ms.assetid: b0662fa1-16d7-4320-b26b-c1804e565a44
ms.openlocfilehash: 5e929bafeaf849b4b5682a17ca51cb0aab963613
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165918"
---
# <a name="combobox-styles-and-templates"></a>ComboBox Stilleri ve Şablonları
Bu konuda, denetimin stilleri ve şablonları açıklanmaktadır <xref:System.Windows.Controls.ComboBox> . <xref:System.Windows.Controls.ControlTemplate>Denetim için benzersiz bir görünüm sağlamak üzere varsayılan ' i değiştirebilirsiniz. Daha fazla bilgi için bkz. [Denetim için şablon oluşturma](../../../desktop-wpf/themes/how-to-create-apply-template.md).  
  
## <a name="combobox-parts"></a>ComboBox bölümleri  
 Aşağıdaki tabloda, denetimin adlandırılmış parçaları listelenmektedir <xref:System.Windows.Controls.ComboBox> .  
  
|Bölüm|Tür|Açıklama|  
|-|-|-|  
|PART_EditableTextBox|<xref:System.Windows.Controls.TextBox>|Metnini içerir <xref:System.Windows.Controls.ComboBox> .|  
|PART_Popup|<xref:System.Windows.Controls.Primitives.Popup>|Birleşik giriş kutusundaki öğeleri içeren açılır liste.|  
  
 Bir <xref:System.Windows.Controls.ControlTemplate> için oluşturduğunuzda <xref:System.Windows.Controls.ComboBox> , şablonunuz <xref:System.Windows.Controls.ItemsPresenter> bir içinde içerebilir <xref:System.Windows.Controls.ScrollViewer> . (, <xref:System.Windows.Controls.ItemsPresenter> İçindeki her öğeyi görüntüler <xref:System.Windows.Controls.ComboBox> ; <xref:System.Windows.Controls.ScrollViewer> denetim içinde kaydırmayı etkinleştirilir).  <xref:System.Windows.Controls.ItemsPresenter>Öğesinin doğrudan alt öğesi değilse, <xref:System.Windows.Controls.ScrollViewer> <xref:System.Windows.Controls.ItemsPresenter> adını vermelisiniz `ItemsPresenter` .  
  
## <a name="combobox-states"></a>ComboBox durumları  
 Aşağıdaki tabloda, denetimin durumları listelenmektedir <xref:System.Windows.Controls.ComboBox> .  
  
|VisualState adı|VisualStateGroup adı|Açıklama|  
|-|-|-|  
|Normal|Ortak durumlar|Varsayılan durum.|  
|Devre dışı|Ortak durumlar|Denetim devre dışı bırakıldı.|  
|Gelme olayından|Ortak durumlar|Fare işaretçisi <xref:System.Windows.Controls.ComboBox> denetimin üzerinde.|  
|Odaklı|Odaklardaki durumlar|Denetim odağa sahiptir.|  
|Odaklanmadan gözetle|Odaklardaki durumlar|Denetimin odağı yok.|  
|FocusedDropDown|Odaklardaki durumlar|İçin açılan liste <xref:System.Windows.Controls.ComboBox> odağa sahiptir.|  
|Geçerli|Doğrulama durumları|Denetim, <xref:System.Windows.Controls.Validation> sınıfını ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği kullanır `false` .|  
|Invalidodaklanmış|Doğrulama durumları|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>İliştirilmiş özelliği `true` ve denetim odağa sahiptir.|  
|Invalidunodaklanmış|Doğrulama durumları|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>İliştirilmiş özelliği `true` ve denetim odağa sahip değildir.|  
|Yapılamaz|EditStates|<xref:System.Windows.Controls.ComboBox.IsEditable%2A>Özelliği `true` .|  
|Düzenlenemez|EditStates|<xref:System.Windows.Controls.ComboBox.IsEditable%2A>Özelliği `false` .|  
  
## <a name="comboboxitem-parts"></a>ComboBoxItem parçaları  
 <xref:System.Windows.Controls.ComboBoxItem>Denetimde hiçbir adlandırılmış bölüm yok.  
  
## <a name="comboboxitem-states"></a>ComboBoxItem durumları  
 Aşağıdaki tabloda, denetimin durumları listelenmektedir <xref:System.Windows.Controls.ComboBoxItem> .  
  
|VisualState adı|VisualStateGroup adı|Açıklama|  
|-|-|-|  
|Normal|Ortak durumlar|Varsayılan durum.|  
|Devre dışı|Ortak durumlar|Denetim devre dışı bırakıldı.|  
|Gelme olayından|Ortak durumlar|Fare işaretçisi <xref:System.Windows.Controls.ComboBoxItem> denetimin üzerinde.|  
|Odaklı|Odaklardaki durumlar|Denetim odağa sahiptir.|  
|Odaklanmadan gözetle|Odaklardaki durumlar|Denetimin odağı yok.|  
|Seçili|SelectionStates|Öğe şu anda seçili durumda.|  
|Değilken|SelectionStates|Öğe seçilmemiş.|  
|Selectedunodaklanmış|SelectionStates|Öğe seçilir, ancak odağa sahip değildir.|  
|Geçerli|Doğrulama durumları|Denetim, <xref:System.Windows.Controls.Validation> sınıfını ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği kullanır `false` .|  
|Invalidodaklanmış|Doğrulama durumları|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>İliştirilmiş özelliği `true` ve denetim odağa sahiptir.|  
|Invalidunodaklanmış|Doğrulama durumları|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>İliştirilmiş özelliği `true` ve denetim odağa sahip değildir.|  
  
## <a name="combobox-controltemplate-example"></a>ComboBox ControlTemplate örneği  
 Aşağıdaki örnek, <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.ComboBox> denetimin ve ilişkili türlerin nasıl tanımlanacağını gösterir.  
  
 [!code-xaml[ControlTemplateExamples#ComboBox](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/combobox.xaml#combobox)]  
  
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
