---
title: PasswordBox stilleri ve şablonları
ms.date: 03/30/2017
helpviewer_keywords:
- styles [WPF], PasswordBox
- templates [WPF], PasswordBox
- ControlTemplate [WPF], PasswordBox
- states [WPF], PasswordBox
- PasswordBox [WPF], styles and templates
- parts [WPF], PasswordBox
ms.assetid: deb52107-959f-4a60-b303-d21a0a933060
ms.openlocfilehash: 7783330dd56ec5b2759e783a6935761eb3587978
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57507300"
---
# <a name="passwordbox-styles-and-templates"></a>PasswordBox stilleri ve şablonları

Bu konu için şablonları ve stilleri açıklar <xref:System.Windows.Controls.PasswordBox> denetimi. Varsayılan değiştirebileceğiniz <xref:System.Windows.Controls.ControlTemplate> denetim benzersiz bir görünüm sağlamak için. Daha fazla bilgi için [ControlTemplate oluşturarak varolan denetimin görünümünü özelleştirme](customizing-the-appearance-of-an-existing-control.md).

## <a name="passwordbox-parts"></a>PasswordBox bölümleri

Adlandırılmış bölümleri için aşağıdaki tabloda <xref:System.Windows.Controls.PasswordBox> denetimi.

|Bölümü|Tür|Açıklama|
|-|-|-|
|PART_ContentHost|<xref:System.Windows.FrameworkElement>|İçeren bir görsel öğe bir <xref:System.Windows.FrameworkElement>. Metnin <xref:System.Windows.Controls.PasswordBox> bu öğe görüntülenir.|

## <a name="passwordbox-states"></a>PasswordBox durumları

Görsel durumlar için aşağıdaki tabloda <xref:System.Windows.Controls.PasswordBox> denetimi.

|VisualState adı|Visualstategroup'u adı|Açıklama|
|-|-|-|
|Normal|CommonStates|Varsayılan durumu.|
|Fareyi üzerine getirme|CommonStates|Fare işaretçisi denetimin üzerine yerleştirilir.|
|Devre dışı|CommonStates|Denetim devre dışıdır.|
|Odaklanmış|FocusStates|Denetim odağa sahip.|
|Plana odaklanmadan|FocusStates|Denetim odağa sahip değil.|
|Geçerli|ValidationStates|Denetimi kullanan <xref:System.Windows.Controls.Validation> sınıfı ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği `false`.|
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özelliği `true` olan denetim odağa sahip.|
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özelliği `true` olan denetim odağa sahip değil.|

## <a name="passwordbox-controltemplate-example"></a>PasswordBox ControlTemplate Örneği

Aşağıdaki örnek nasıl tanımlanacağını gösterir bir <xref:System.Windows.Controls.ControlTemplate> için <xref:System.Windows.Controls.PasswordBox> denetimi.

[!code-xaml[ControlTemplateExamples#PasswordBox](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/textbox.xaml#passwordbox)]

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
