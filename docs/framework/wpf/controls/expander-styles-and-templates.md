---
title: Genişletici Stilleri ve Şablonları
ms.date: 03/30/2017
helpviewer_keywords:
- styles [WPF], Expander
- ControlTemplate [WPF], Expander
- templates [WPF], Expander
- Expander [WPF], styles and templates
- states [WPF], Expander
- parts [WPF], Expander
ms.assetid: da2e5a1c-5230-4c21-98a5-59c7895facd7
ms.openlocfilehash: ba31543a21b13817bfd7ea5740d15afcae25fdeb
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57366822"
---
# <a name="expander-styles-and-templates"></a>Genişletici Stilleri ve Şablonları
Bu konu için şablonları ve stilleri açıklar <xref:System.Windows.Controls.Expander> denetimi. Varsayılan değiştirebileceğiniz <xref:System.Windows.Controls.ControlTemplate> denetim benzersiz bir görünüm sağlamak için. Daha fazla bilgi için [ControlTemplate oluşturarak varolan denetimin görünümünü özelleştirme](customizing-the-appearance-of-an-existing-control.md).  
  
## <a name="expander-parts"></a>Genişletici bölümleri  
 <xref:System.Windows.Controls.Expander> Denetim herhangi bir adlandırılmış bölümü yok.  
  
## <a name="expander-states"></a>Genişletici durumları  
 Görsel durumlar için aşağıdaki tabloda <xref:System.Windows.Controls.Expander> denetimi.  
  
|VisualState adı|Visualstategroup'u adı|Açıklama|  
|-|-|-|  
|Normal|CommonStates|Varsayılan durumu.|  
|Fareyi üzerine getirme|CommonStates|Fare işaretçisi denetimin üzerine yerleştirilir.|  
|Devre dışı|CommonStates|Denetim devre dışıdır.|  
|Odaklanmış|FocusStates|Denetim odağa sahip.|  
|Plana odaklanmadan|FocusStates|Denetim odağa sahip değil.|  
|Genişletilmiş|ExpansionStates|Denetim genişletilir.|  
|Daraltılmış|ExpansionStates|Denetim genişletilmemiştir.|  
|ExpandDown|ExpandDirectionStates|Aşağı denetimi genişletir.|  
|ExpandUp|ExpandDirectionStates|Denetimi yukarı genişletir.|  
|ExpandLeft|ExpandDirectionStates|Denetimi sol genişletir.|  
|ExpandRight|ExpandDirectionStates|Denetimi sağ genişletir.|  
|Geçerli|ValidationStates|Denetimi kullanan <xref:System.Windows.Controls.Validation> sınıfı ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği `false`.|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özelliği `true` olan denetim odağa sahip.|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özelliği `true` olan denetim odağa sahip değil.|  
  
## <a name="expander-controltemplate-example"></a>Genişletici ControlTemplate Örneği  
 Aşağıdaki örnek nasıl tanımlanacağını gösterir bir <xref:System.Windows.Controls.ControlTemplate> için <xref:System.Windows.Controls.Expander> denetimi.  
  
 [!code-xaml[ControlTemplateExamples#Expander](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/expander.xaml#expander)]  
  
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
