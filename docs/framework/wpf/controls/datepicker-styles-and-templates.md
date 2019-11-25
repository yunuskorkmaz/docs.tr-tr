---
title: DatePicker Stilleri ve Şablonları
ms.date: 03/30/2017
helpviewer_keywords:
- ControlTemplate [WPF], DatePicker
- DatePicker [WPF], styles and templates
- templates [WPF], DatePicker
- parts [WPF], DatePicker
- styles [WPF], DatePicker
- states [WPF], DatePicker
ms.assetid: c430a657-692f-44bd-a549-2341f92d6115
ms.openlocfilehash: 002d1c3271827239dcd3a319621f66fb5bc68d4e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283780"
---
# <a name="datepicker-styles-and-templates"></a>DatePicker Stilleri ve Şablonları
Bu konuda <xref:System.Windows.Controls.DatePicker> denetimine yönelik stiller ve şablonlar açıklanmaktadır. Denetime benzersiz bir görünüm sağlamak için varsayılan <xref:System.Windows.Controls.ControlTemplate> değiştirebilirsiniz. Daha fazla bilgi için bkz. [Denetim için şablon oluşturma](../../../desktop-wpf/themes/how-to-create-apply-template.md).  
  
## <a name="datepicker-parts"></a>DatePicker bölümleri  
 Aşağıdaki tabloda <xref:System.Windows.Controls.DatePicker> denetimi için adlandırılmış bölümler listelenmektedir.  
  
|Bölümüyle|Type|Açıklama|  
|-|-|-|  
|PART_Root|<xref:System.Windows.Controls.Grid>|Denetimin kökü.|  
|PART_Button|<xref:System.Windows.Controls.Button>|<xref:System.Windows.Controls.Calendar>açan ve kapatan düğme.|  
|PART_TextBox|<xref:System.Windows.Controls.Primitives.DatePickerTextBox>|Bir tarih girmenize izin veren metin kutusu.|  
|PART_Popup|<xref:System.Windows.Controls.Primitives.Popup>|<xref:System.Windows.Controls.DatePicker> denetimi için açılan pencere.|  
  
## <a name="datepicker-states"></a>DatePicker durumları  
 Aşağıdaki tabloda <xref:System.Windows.Controls.DatePicker> denetimi için görsel durumlar listelenmektedir.  
  
|VisualState adı|VisualStateGroup adı|Açıklama|  
|-|-|-|  
|Normal|Ortak durumlar|Varsayılan durum.|  
|Devre dışı|Ortak durumlar|<xref:System.Windows.Controls.DatePicker> devre dışı bırakıldı.|  
|Geçerli|Doğrulama durumları|Denetim, <xref:System.Windows.Controls.Validation> sınıfını ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> iliştirilmiş özelliği `false`kullanır.|  
|Invalidodaklanmış|Doğrulama durumları|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği, denetimin odağa sahip `true`.|  
|Invalidunodaklanmış|Doğrulama durumları|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği, denetimin odağa sahip `true`.|  
  
## <a name="datepickertextbox-parts"></a>DatePickerTextBox parçaları  
 Aşağıdaki tabloda <xref:System.Windows.Controls.Primitives.DatePickerTextBox> denetimi için adlandırılmış bölümler listelenmektedir.  
  
|Bölümüyle|Type|Açıklama|  
|-|-|-|  
|PART_Watermark|<xref:System.Windows.Controls.ContentControl>|<xref:System.Windows.Controls.DatePicker>ilk metni içeren öğe.|  
|PART_ContentElement|<xref:System.Windows.FrameworkElement>|<xref:System.Windows.FrameworkElement>içerebilen görsel öğe. <xref:System.Windows.Controls.TextBox> metni bu öğede görüntülenir.|  
  
## <a name="datepickertextbox-states"></a>DatePickerTextBox durumları  
 Aşağıdaki tabloda <xref:System.Windows.Controls.Primitives.DatePickerTextBox> denetimi için görsel durumlar listelenmektedir.  
  
|VisualState adı|VisualStateGroup adı|Açıklama|  
|-|-|-|  
|Normal|Ortak durumlar|Varsayılan durum.|  
|Devre dışı|Ortak durumlar|<xref:System.Windows.Controls.Primitives.DatePickerTextBox> devre dışı bırakıldı.|  
|Gelme olayından|Ortak durumlar|Fare işaretçisi <xref:System.Windows.Controls.Primitives.DatePickerTextBox>yerleştirilir.|  
|ReadOnly|Ortak durumlar|Kullanıcı <xref:System.Windows.Controls.Primitives.DatePickerTextBox>metni değiştiremiyor.|  
|Diğinize|Odaklardaki durumlar|Denetim odağa sahiptir.|  
|Odaklanmadan gözetle|Odaklardaki durumlar|Denetimin odağı yok.|  
|Değerlendirebilmek|Su Markstates|Denetim, ilk metnini görüntüler.  <xref:System.Windows.Controls.Primitives.DatePickerTextBox>, Kullanıcı metin girmemiş veya bir tarih seçtiği zaman durumundadır.|  
|Unsu işaretlendi|Su Markstates|Kullanıcı <xref:System.Windows.Controls.Primitives.DatePickerTextBox> metin girmiştir veya <xref:System.Windows.Controls.DatePicker>bir tarih seçti.|  
|Geçerli|Doğrulama durumları|Denetim, <xref:System.Windows.Controls.Validation> sınıfını ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> iliştirilmiş özelliği `false`kullanır.|  
|Invalidodaklanmış|Doğrulama durumları|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği `true` ve denetim odağa sahiptir.|  
|Invalidunodaklanmış|Doğrulama durumları|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği `true` ve denetim odağa sahip değil.|  
  
## <a name="datepicker-controltemplate-example"></a>DatePicker ControlTemplate örneği  
 Aşağıdaki örnek, <xref:System.Windows.Controls.DatePicker> denetimi için <xref:System.Windows.Controls.ControlTemplate> tanımlanacağını gösterir.  
  
 [!code-xaml[ControlTemplateExamples#DatePicker](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/datepicker.xaml#datepicker)]  
  
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
