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
ms.openlocfilehash: e055dcbd557f9b90eb2fe99ad15a05b6f229fd28
ms.sourcegitcommit: f87ad41b8e62622da126aa928f7640108c4eff98
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/07/2020
ms.locfileid: "80805917"
---
# <a name="togglebutton-styles-and-templates"></a>ToggleButton Stilleri ve Şablonları

Bu <xref:System.Windows.Controls.Primitives.ToggleButton> konu, denetim in stilleri ve şablonlarını açıklar. Denetime benzersiz <xref:System.Windows.Controls.ControlTemplate> bir görünüm kazandırmak için varsayılanı değiştirebilirsiniz. Daha fazla bilgi [için](../../../desktop-wpf/themes/how-to-create-apply-template.md)bkz.

## <a name="togglebutton-parts"></a>Düğme Parçaları

Denetimde <xref:System.Windows.Controls.Primitives.ToggleButton> herhangi bir adlandırılmış parça yok.

## <a name="togglebutton-states"></a>ToggleButton Durumları

Aşağıdaki <xref:System.Windows.Controls.Primitives.ToggleButton> tabloda denetim için görsel durumları listeler.

|VisualState Adı|VisualStateGroup Adı|Açıklama|
|-|-|-|
|Normal|Commonstates|Varsayılan durum.|
|Mouseover|Commonstates|Fare işaretçisi denetimin üzerine konumlandırılır.|
|Pressed|Commonstates|Kontrol basılı.|
|Devre dışı|Commonstates|Denetim devre dışı.|
|Odaklı|Odak Devletler|Kontrol odak noktası.|
|Odaklanmamış|Odak Devletler|Denetimin odak noktası yok.|
|İşaretli|Çek Durumları|<xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A>`true`.|
|Denetlenme -yen|Çek Durumları|<xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A>`false`.|
|Belirsiz|Çek Durumları|<xref:System.Windows.Controls.Primitives.ToggleButton.IsThreeState%2A>' `true`dir <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> `null`ve .|
|Geçerli|Doğrulama Durumları|Denetim <xref:System.Windows.Controls.Validation> sınıfı kullanır ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli `false`özellik.|
|GeçersizOdaklanmış|Doğrulama Durumları|Ekli <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> özellik ve `true` denetim odak vardır.|
|Geçersiz Odaklanmış|Doğrulama Durumları|Ekli <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> özellik ve `true` denetim odak yok.|

> [!NOTE]
> Denetim şablonunuzda Belirsiz görsel durum yoksa, denetlenmemiş görsel durum varsayılan görsel durum olarak kullanılır.

## <a name="togglebutton-controltemplate-example"></a>Düğme DenetimiŞablon Örneği

Aşağıdaki örnek, denetim için <xref:System.Windows.Controls.ControlTemplate> a'nın <xref:System.Windows.Controls.Primitives.ToggleButton> nasıl tanımlandığını gösterir.

[!code-xaml[ControlTemplateExamples#ToggleButton](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/combobox.xaml#togglebutton)]

Önceki örnekte aşağıdaki kaynaklardan biri veya birkaçı kullanır.

[!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]

Tam örnek için [ControlTemplates Örnek ile Şekillendirme'ye](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)bakın.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [Denetim Stilleri ve Şablonları](control-styles-and-templates.md)
- [Denetim Özelleştirme](control-customization.md)
- [Stil ve Şablon Oluşturma](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Denetim için şablon oluşturma](../../../desktop-wpf/themes/how-to-create-apply-template.md)
