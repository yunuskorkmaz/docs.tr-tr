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
ms.openlocfilehash: 5c8e199dd7123e1490c8a836a62ffea158797eb8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59206141"
---
# <a name="datepicker-styles-and-templates"></a>DatePicker Stilleri ve Şablonları
Bu konu için şablonları ve stilleri açıklar <xref:System.Windows.Controls.DatePicker> denetimi. Varsayılan değiştirebileceğiniz <xref:System.Windows.Controls.ControlTemplate> denetim benzersiz bir görünüm sağlamak için. Daha fazla bilgi için [ControlTemplate oluşturarak varolan denetimin görünümünü özelleştirme](customizing-the-appearance-of-an-existing-control.md).  
  
## <a name="datepicker-parts"></a>DatePicker bölümleri  
 Adlandırılmış bölümleri için aşağıdaki tabloda <xref:System.Windows.Controls.DatePicker> denetimi.  
  
|Bölümü|Tür|Açıklama|  
|-|-|-|  
|PART_Root|<xref:System.Windows.Controls.Grid>|Denetim kökü.|  
|PART_Button|<xref:System.Windows.Controls.Button>|Açılır ve kapatır düğme <xref:System.Windows.Controls.Calendar>.|  
|PART_TextBox|<xref:System.Windows.Controls.Primitives.DatePickerTextBox>|Bir tarih girmenizi sağlayan metin kutusu.|  
|PART_Popup|<xref:System.Windows.Controls.Primitives.Popup>|Popup için <xref:System.Windows.Controls.DatePicker> denetimi.|  
  
## <a name="datepicker-states"></a>DatePicker durumları  
 Görsel durumlar için aşağıdaki tabloda <xref:System.Windows.Controls.DatePicker> denetimi.  
  
|VisualState adı|Visualstategroup'u adı|Açıklama|  
|-|-|-|  
|Normal|CommonStates|Varsayılan durumu.|  
|Devre dışı|CommonStates|<xref:System.Windows.Controls.DatePicker> Devre dışı bırakıldı.|  
|Geçerli|ValidationStates|Denetimi kullanan <xref:System.Windows.Controls.Validation> sınıfı ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği `false`.|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özelliği `true` olan denetim odağa sahip.|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özelliği `true` olan denetim odağa sahip değil.|  
  
## <a name="datepickertextbox-parts"></a>DatePickerTextBox bölümleri  
 Adlandırılmış bölümleri için aşağıdaki tabloda <xref:System.Windows.Controls.Primitives.DatePickerTextBox> denetimi.  
  
|Bölümü|Tür|Açıklama|  
|-|-|-|  
|PART_Watermark|<xref:System.Windows.Controls.ContentControl>|İlk metin içeren öğe <xref:System.Windows.Controls.DatePicker>.|  
|PART_ContentElement|<xref:System.Windows.FrameworkElement>|İçeren bir görsel öğe bir <xref:System.Windows.FrameworkElement>. Metnin <xref:System.Windows.Controls.TextBox> bu öğe görüntülenir.|  
  
## <a name="datepickertextbox-states"></a>DatePickerTextBox durumları  
 Görsel durumlar için aşağıdaki tabloda <xref:System.Windows.Controls.Primitives.DatePickerTextBox> denetimi.  
  
|VisualState adı|Visualstategroup'u adı|Açıklama|  
|-|-|-|  
|Normal|CommonStates|Varsayılan durumu.|  
|Devre dışı|CommonStates|<xref:System.Windows.Controls.Primitives.DatePickerTextBox> Devre dışı bırakıldı.|  
|Fareyi üzerine getirme|CommonStates|Fareyi üzerine getirildiği <xref:System.Windows.Controls.Primitives.DatePickerTextBox>.|  
|ReadOnly|CommonStates|Kullanıcının metni değiştiremezsiniz <xref:System.Windows.Controls.Primitives.DatePickerTextBox>.|  
|Odaklanmış|FocusStates|Denetim odağa sahip.|  
|Plana odaklanmadan|FocusStates|Denetim odağa sahip değil.|  
|Filigran|WatermarkStates|Denetimin ilk metnini görüntüler.  <xref:System.Windows.Controls.Primitives.DatePickerTextBox> Kullanıcıya olmayan metin girildiğinde veya bir tarih seçtiğini durumdadır.|  
|Unwatermarked|WatermarkStates|Metne kullanıcının girdiği <xref:System.Windows.Controls.Primitives.DatePickerTextBox> veya içinde bir tarih seçtiğini <xref:System.Windows.Controls.DatePicker>.|  
|Geçerli|ValidationStates|Denetimi kullanan <xref:System.Windows.Controls.Validation> sınıfı ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği `false`.|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özelliği `true` olan denetim odağa sahip.|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özelliği `true` olan denetim odağa sahip değil.|  
  
## <a name="datepicker-controltemplate-example"></a>DatePicker ControlTemplate Örneği  
 Aşağıdaki örnek nasıl tanımlanacağını gösterir bir <xref:System.Windows.Controls.ControlTemplate> için <xref:System.Windows.Controls.DatePicker> denetimi.  
  
 [!code-xaml[ControlTemplateExamples#DatePicker](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/datepicker.xaml#datepicker)]  
  
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
