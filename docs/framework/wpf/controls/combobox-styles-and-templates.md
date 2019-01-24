---
title: ComboBox Stilleri ve Şablonları
ms.date: 03/30/2017
helpviewer_keywords:
- ComboBox [WPF], styles and templates
- states [WPF], ComboBox
- ControlTemplate [WPF], ComboBox
- styles [WPF], ComboBox
- templates [WPF], ComboBox
- parts [WPF], ComboBox
ms.assetid: b0662fa1-16d7-4320-b26b-c1804e565a44
ms.openlocfilehash: 5cca162137b603f36dffb044d5954c3947964cf9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54712856"
---
# <a name="combobox-styles-and-templates"></a>ComboBox Stilleri ve Şablonları
Bu konu için şablonları ve stilleri açıklar <xref:System.Windows.Controls.ComboBox> denetimi. Varsayılan değiştirebileceğiniz <xref:System.Windows.Controls.ControlTemplate> denetim benzersiz bir görünüm sağlamak için. Daha fazla bilgi için [ControlTemplate oluşturarak varolan denetimin görünümünü özelleştirme](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).  
  
## <a name="combobox-parts"></a>ComboBox bölümleri  
 Adlandırılmış bölümleri için aşağıdaki tabloda <xref:System.Windows.Controls.ComboBox> denetimi.  
  
|Bölümü|Tür|Açıklama|  
|-|-|-|  
|PART_EditableTextBox|<xref:System.Windows.Controls.TextBox>|Metni içeren <xref:System.Windows.Controls.ComboBox>.|  
|PART_Popup|<xref:System.Windows.Controls.Primitives.Popup>|Birleşik giriş kutusu öğeleri içeren açılır.|  
  
 Oluştururken bir <xref:System.Windows.Controls.ControlTemplate> için bir <xref:System.Windows.Controls.ComboBox>, şablonunuzu içerebilir bir <xref:System.Windows.Controls.ItemsPresenter> içinde bir <xref:System.Windows.Controls.ScrollViewer>. ( <xref:System.Windows.Controls.ItemsPresenter> Her öğe görüntüler <xref:System.Windows.Controls.ComboBox>; <xref:System.Windows.Controls.ScrollViewer> denetimi içinde kaydırma sağlar).  Varsa <xref:System.Windows.Controls.ItemsPresenter> doğrudan alt öğesi değil <xref:System.Windows.Controls.ScrollViewer>, size gereken <xref:System.Windows.Controls.ItemsPresenter> adı `ItemsPresenter`.  
  
## <a name="combobox-states"></a>ComboBox durumları  
 Aşağıdaki tabloda durumları <xref:System.Windows.Controls.ComboBox> denetimi.  
  
|VisualState adı|Visualstategroup'u adı|Açıklama|  
|-|-|-|  
|Normal|CommonStates|Varsayılan durumu.|  
|Devre dışı|CommonStates|Denetim devre dışıdır.|  
|Fareyi üzerine getirme|CommonStates|Fare işaretçisi bittikten <xref:System.Windows.Controls.ComboBox> denetimi.|  
|Odaklanmış|FocusStates|Denetim odağa sahip.|  
|Plana odaklanmadan|FocusStates|Denetim odağa sahip değil.|  
|FocusedDropDown|FocusStates|Açılan listesine <xref:System.Windows.Controls.ComboBox> odağa sahip.|  
|Geçerli|ValidationStates|Denetimi kullanan <xref:System.Windows.Controls.Validation> sınıfı ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği `false`.|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özelliği `true` olan denetim odağa sahip.|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özelliği `true` olan denetim odağa sahip değil.|  
|Düzenlenebilir|EditStates|<xref:System.Windows.Controls.ComboBox.IsEditable%2A> Özelliği `true`.|  
|Düzenlenemez|EditStates|<xref:System.Windows.Controls.ComboBox.IsEditable%2A> Özelliği `false`.|  
  
## <a name="comboboxitem-parts"></a>ComboBoxItem bölümleri  
 <xref:System.Windows.Controls.ComboBoxItem> Denetim herhangi bir adlandırılmış bölümü yok.  
  
## <a name="comboboxitem-states"></a>ComboBoxItem durumları  
 Aşağıdaki tabloda durumları <xref:System.Windows.Controls.ComboBoxItem> denetimi.  
  
|VisualState adı|Visualstategroup'u adı|Açıklama|  
|-|-|-|  
|Normal|CommonStates|Varsayılan durumu.|  
|Devre dışı|CommonStates|Denetim devre dışıdır.|  
|Fareyi üzerine getirme|CommonStates|Fare işaretçisi bittikten <xref:System.Windows.Controls.ComboBox> denetimi.|  
|Odaklanmış|FocusStates|Denetim odağa sahip.|  
|Plana odaklanmadan|FocusStates|Denetim odağa sahip değil.|  
|Seçildi|SelectionStates|Öğe şu anda seçilir.|  
|Seçimi kaldırıldı|SelectionStates|Öğe seçilmedi.|  
|SelectedUnfocused|SelectionStates|Öğe seçilir, ancak odağa sahip değil.|  
|Geçerli|ValidationStates|Denetimi kullanan <xref:System.Windows.Controls.Validation> sınıfı ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği `false`.|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özelliği `true` olan denetim odağa sahip.|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özelliği `true` olan denetim odağa sahip değil.|  
  
## <a name="combobox-controltemplate-example"></a>ComboBox ControlTemplate Örneği  
 Aşağıdaki örnek nasıl tanımlanacağını gösterir bir <xref:System.Windows.Controls.ControlTemplate> için <xref:System.Windows.Controls.ComboBox> denetimi ve ilişkili tür.  
  
 [!code-xaml[ControlTemplateExamples#ComboBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/combobox.xaml#combobox)]  
  
 Yukarıdaki örnekte, bir veya daha fazla aşağıdaki kaynakları kullanır.  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 Tam bir örnek için bkz. [ControlTemplates örneği ile stillendirme](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [Denetim Stilleri ve Şablonları](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)
- [Denetim Özelleştirme](../../../../docs/framework/wpf/controls/control-customization.md)
- [Stil ve Şablon Oluşturma](../../../../docs/framework/wpf/controls/styling-and-templating.md)
- [ControlTemplate Oluşturarak Varolan Denetimin Görünümünü Özelleştirme](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
