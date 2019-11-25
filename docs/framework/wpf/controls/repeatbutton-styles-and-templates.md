---
title: RepeatButton Stilleri ve Şablonları
ms.date: 03/30/2017
helpviewer_keywords:
- RepeatButton [WPF], styles and templates
- styles [WPF], RepeatButton
- templates [WPF], RepeatButton
- parts [WPF], RepeatButton
- ControlTemplate [WPF], RepeatButton
- states [WPF], RepeatButton
ms.assetid: fd340743-f44f-4990-9077-085301469670
ms.openlocfilehash: 8585e98536fd908daa11f21da395cab44924d612
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283422"
---
# <a name="repeatbutton-styles-and-templates"></a>RepeatButton Stilleri ve Şablonları

Bu konuda <xref:System.Windows.Controls.Primitives.RepeatButton> denetimine yönelik stiller ve şablonlar açıklanmaktadır. Denetime benzersiz bir görünüm sağlamak için varsayılan <xref:System.Windows.Controls.ControlTemplate> değiştirebilirsiniz. Daha fazla bilgi için bkz. [Denetim için şablon oluşturma](../../../desktop-wpf/themes/how-to-create-apply-template.md).

## <a name="repeatbutton-parts"></a>RepeatButton bölümleri

<xref:System.Windows.Controls.Primitives.RepeatButton> denetiminde hiç adlandırılmış bölüm yok.

## <a name="repeatbutton-states"></a>RepeatButton durumları

Aşağıdaki tabloda <xref:System.Windows.Controls.Primitives.RepeatButton> denetimi için görsel durumlar listelenmektedir.

|VisualState adı|VisualStateGroup adı|Açıklama|
|-|-|-|
|Normal|Ortak durumlar|Varsayılan durum.|
|Gelme olayından|Ortak durumlar|Fare işaretçisi denetimin üzerine yerleştirilir.|
|Basılan|Ortak durumlar|Denetime basıldığında.|
|Devre dışı|Ortak durumlar|Denetim devre dışı bırakıldı.|
|Diğinize|Odaklardaki durumlar|Denetim odağa sahiptir.|
|Odaklanmadan gözetle|Odaklardaki durumlar|Denetimin odağı yok.|
|Geçerli|Doğrulama durumları|Denetim, <xref:System.Windows.Controls.Validation> sınıfını ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> iliştirilmiş özelliği `false`kullanır.|
|Invalidodaklanmış|Doğrulama durumları|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği, denetimin odağa sahip `true`.|
|Invalidunodaklanmış|Doğrulama durumları|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği, denetimin odağa sahip `true`.|

## <a name="repeatbutton-controltemplate-example"></a>RepeatButton ControlTemplate örneği

Aşağıdaki örnek, <xref:System.Windows.Controls.Primitives.RepeatButton> denetimi için <xref:System.Windows.Controls.ControlTemplate> tanımlanacağını gösterir.

[!code-xaml[ControlTemplateExamples#RepeatButton](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/scrollbar.xaml#repeatbutton)]

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
