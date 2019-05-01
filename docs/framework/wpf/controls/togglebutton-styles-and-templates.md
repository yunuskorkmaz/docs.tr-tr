---
title: ToggleButton Stilleri ve Şablonları
ms.date: 03/30/2017
helpviewer_keywords:
- states [WPF], ToggleButton
- ToggleButton [WPF], styles and templates
- ControlTemplate [WPF], ToggleButton
- styles [WPF], ToggleButton
- templates [WPF], ToggleButton
- parts [WPF], ToggleButton
ms.assetid: 54f23f30-4bcb-4f09-8ce4-376a13a255a1
ms.openlocfilehash: 46fd7d07c3904ee752ae3f467f65af4b0c031c84
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61790760"
---
# <a name="togglebutton-styles-and-templates"></a>ToggleButton Stilleri ve Şablonları

Bu konu için şablonları ve stilleri açıklar <xref:System.Windows.Controls.Primitives.ToggleButton> denetimi. Varsayılan değiştirebileceğiniz <xref:System.Windows.Controls.ControlTemplate> denetim benzersiz bir görünüm sağlamak için. Daha fazla bilgi için [ControlTemplate oluşturarak varolan denetimin görünümünü özelleştirme](customizing-the-appearance-of-an-existing-control.md).

## <a name="togglebutton-parts"></a>ToggleButton bölümleri

<xref:System.Windows.Controls.Primitives.ToggleButton> Denetim herhangi bir adlandırılmış bölümü yok.

## <a name="togglebutton-states"></a>ToggleButton durumları

Görsel durumlar için aşağıdaki tabloda <xref:System.Windows.Controls.Primitives.ToggleButton> denetimi.

|VisualState adı|Visualstategroup'u adı|Açıklama|
|-|-|-|
|Normal|CommonStates|Varsayılan durumu.|
|Fareyi üzerine getirme|CommonStates|Fare işaretçisi denetimin üzerine yerleştirilir.|
|Basılan|CommonStates|Denetime basıldığında.|
|Devre dışı|CommonStates|Denetim devre dışıdır.|
|Odaklanmış|FocusStates|Denetim odağa sahip.|
|Plana odaklanmadan|FocusStates|Denetim odağa sahip değil.|
|İşaretli|CheckStates|<xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> olan `true`.|
|Denetlenmeyen|CheckStates|<xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> olan `false`.|
|Belirsiz|CheckStates|<xref:System.Windows.Controls.Primitives.ToggleButton.IsThreeState%2A> olan `true`, ve <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> olduğu `null`.|
|Geçerli|ValidationStates|Denetimi kullanan <xref:System.Windows.Controls.Validation> sınıfı ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği `false`.|
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özelliği `true` olan denetim odağa sahip.|
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özelliği `true` olan denetim odağa sahip değil.|

> [!NOTE]
> Belirsiz görsel durum denetimi şablonunuzda yoksa denetlenmeyen görsel durum varsayılan görsel durum kullanılır.

## <a name="togglebutton-controltemplate-example"></a>ToggleButton ControlTemplate Örneği

Aşağıdaki örnek nasıl tanımlanacağını gösterir bir <xref:System.Windows.Controls.ControlTemplate> için <xref:System.Windows.Controls.Primitives.ToggleButton> denetimi.

[!code-xaml[ControlTemplateExamples#ToggleButton](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/combobox.xaml#togglebutton)]

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
