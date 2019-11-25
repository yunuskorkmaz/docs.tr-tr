---
title: PasswordBox Stilleri ve Şablonları
ms.date: 03/30/2017
helpviewer_keywords:
- styles [WPF], PasswordBox
- templates [WPF], PasswordBox
- ControlTemplate [WPF], PasswordBox
- states [WPF], PasswordBox
- PasswordBox [WPF], styles and templates
- parts [WPF], PasswordBox
ms.assetid: deb52107-959f-4a60-b303-d21a0a933060
ms.openlocfilehash: 4ba90182468466773644c7375059f0cc01675b33
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283459"
---
# <a name="passwordbox-styles-and-templates"></a>PasswordBox Stilleri ve Şablonları

Bu konuda <xref:System.Windows.Controls.PasswordBox> denetimine yönelik stiller ve şablonlar açıklanmaktadır. Denetime benzersiz bir görünüm sağlamak için varsayılan <xref:System.Windows.Controls.ControlTemplate> değiştirebilirsiniz. Daha fazla bilgi için bkz. [Denetim için şablon oluşturma](../../../desktop-wpf/themes/how-to-create-apply-template.md).

## <a name="passwordbox-parts"></a>PasswordBox bölümleri

Aşağıdaki tabloda <xref:System.Windows.Controls.PasswordBox> denetimi için adlandırılmış bölümler listelenmektedir.

|Bölümüyle|Type|Açıklama|
|-|-|-|
|PART_ContentHost|<xref:System.Windows.FrameworkElement>|<xref:System.Windows.FrameworkElement>içerebilen görsel öğe. <xref:System.Windows.Controls.PasswordBox> metni bu öğede görüntülenir.|

## <a name="passwordbox-states"></a>PasswordBox durumları

Aşağıdaki tabloda <xref:System.Windows.Controls.PasswordBox> denetimi için görsel durumlar listelenmektedir.

|VisualState adı|VisualStateGroup adı|Açıklama|
|-|-|-|
|Normal|Ortak durumlar|Varsayılan durum.|
|Gelme olayından|Ortak durumlar|Fare işaretçisi denetimin üzerine yerleştirilir.|
|Devre dışı|Ortak durumlar|Denetim devre dışı bırakıldı.|
|Diğinize|Odaklardaki durumlar|Denetim odağa sahiptir.|
|Odaklanmadan gözetle|Odaklardaki durumlar|Denetimin odağı yok.|
|Geçerli|Doğrulama durumları|Denetim, <xref:System.Windows.Controls.Validation> sınıfını ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> iliştirilmiş özelliği `false`kullanır.|
|Invalidodaklanmış|Doğrulama durumları|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği, denetimin odağa sahip `true`.|
|Invalidunodaklanmış|Doğrulama durumları|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği, denetimin odağa sahip `true`.|

## <a name="passwordbox-controltemplate-example"></a>PasswordBox ControlTemplate örneği

Aşağıdaki örnek, <xref:System.Windows.Controls.PasswordBox> denetimi için <xref:System.Windows.Controls.ControlTemplate> tanımlanacağını gösterir.

[!code-xaml[ControlTemplateExamples#PasswordBox](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/textbox.xaml#passwordbox)]

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
