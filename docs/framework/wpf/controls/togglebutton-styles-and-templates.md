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
ms.openlocfilehash: 981a487b9935a86595a9caca03b4371326924642
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458227"
---
# <a name="togglebutton-styles-and-templates"></a>ToggleButton Stilleri ve Şablonları

Bu konuda <xref:System.Windows.Controls.Primitives.ToggleButton> denetimine yönelik stiller ve şablonlar açıklanmaktadır. Denetime benzersiz bir görünüm sağlamak için, varsayılan <xref:System.Windows.Controls.ControlTemplate> ' i değiştirebilirsiniz. Daha fazla bilgi için, bkz. [bir ControlTemplate oluşturarak varolan denetimin görünümünü özelleştirme](customizing-the-appearance-of-an-existing-control.md).

## <a name="togglebutton-parts"></a>ToggleButton bölüm

<xref:System.Windows.Controls.Primitives.ToggleButton> denetiminde hiç adlandırılmış bölüm yok.

## <a name="togglebutton-states"></a>ToggleButton durumları

Aşağıdaki tabloda <xref:System.Windows.Controls.Primitives.ToggleButton> denetimi için görsel durumlar listelenmektedir.

|VisualState adı|VisualStateGroup adı|Açıklama|
|-|-|-|
|Olağan|Ortak durumlar|Varsayılan durum.|
|Gelme olayından|Ortak durumlar|Fare işaretçisi denetimin üzerine yerleştirilir.|
|Basılması|Ortak durumlar|Denetime basıldığında.|
|Devre dışı|Ortak durumlar|Denetim devre dışı bırakıldı.|
|Diğinize|Odaklardaki durumlar|Denetim odağa sahiptir.|
|Odaklanmadan gözetle|Odaklardaki durumlar|Denetimin odağı yok.|
|Edildikten|CheckStates|<xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> `true`.|
|Olmayan|CheckStates|<xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> `false`.|
|'Dır|CheckStates|<xref:System.Windows.Controls.Primitives.ToggleButton.IsThreeState%2A> `true`ve <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> `null`.|
|Geçerli|Doğrulama durumları|Denetim, <xref:System.Windows.Controls.Validation> sınıfını ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> iliştirilmiş özelliği `false`kullanır.|
|Invalidodaklanmış|Doğrulama durumları|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği, denetimin odağa sahip `true`.|
|Invalidunodaklanmış|Doğrulama durumları|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği, denetimin odağa sahip `true`.|

> [!NOTE]
> Denetim şablonunuzda belirsiz görsel durumu yoksa, denetlenmeyen görsel durum varsayılan görsel durum olarak kullanılır.

## <a name="togglebutton-controltemplate-example"></a>ToggleButton ControlTemplate örneği

Aşağıdaki örnek, <xref:System.Windows.Controls.Primitives.ToggleButton> denetimi için <xref:System.Windows.Controls.ControlTemplate> tanımlanacağını gösterir.

[!code-xaml[ControlTemplateExamples#ToggleButton](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/combobox.xaml#togglebutton)]

Yukarıdaki örnekte aşağıdaki kaynaklardan biri veya daha fazlası kullanılmaktadır.

[!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]

Tüm örnek için bkz. [ControlTemplates Ile stillendirme örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [Denetim Stilleri ve Şablonları](control-styles-and-templates.md)
- [Denetim Özelleştirme](control-customization.md)
- [Stil ve Şablon Oluşturma](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [ControlTemplate Oluşturarak Varolan Denetimin Görünümünü Özelleştirme](customizing-the-appearance-of-an-existing-control.md)
