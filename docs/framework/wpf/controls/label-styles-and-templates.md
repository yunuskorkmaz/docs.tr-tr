---
title: Etiket Stilleri ve Şablonları
ms.date: 03/30/2017
helpviewer_keywords:
- templates [WPF], Label
- parts [WPF], Label
- ControlTemplate [WPF], Label
- styles [WPF], Label
- Label [WPF], styles and templates
- states [WPF], Label
ms.assetid: c1d5359a-8e4a-4925-ab3e-e92bf6694859
ms.openlocfilehash: c3bf4dc629bbb3e4ea21862c6893b001749f4649
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459393"
---
# <a name="label-styles-and-templates"></a>Etiket Stilleri ve Şablonları
Bu konuda <xref:System.Windows.Controls.Label> denetimine yönelik stiller ve şablonlar açıklanmaktadır. Denetime benzersiz bir görünüm sağlamak için, varsayılan <xref:System.Windows.Controls.ControlTemplate> ' i değiştirebilirsiniz. Daha fazla bilgi için, bkz. [bir ControlTemplate oluşturarak varolan denetimin görünümünü özelleştirme](customizing-the-appearance-of-an-existing-control.md).  
  
## <a name="label-parts"></a>Etiket bölümleri  
 <xref:System.Windows.Controls.Label> denetiminde hiç adlandırılmış bölüm yok.  
  
## <a name="label-states"></a>Etiket durumları  
 Aşağıdaki tabloda <xref:System.Windows.Controls.Label> denetimi için görsel durumlar listelenmektedir.  
  
|VisualState adı|VisualStateGroup adı|Açıklama|  
|-|-|-|  
|Geçerli|Doğrulama durumları|Denetim, <xref:System.Windows.Controls.Validation> sınıfını ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> iliştirilmiş özelliği `false`kullanır.|  
|Invalidodaklanmış|Doğrulama durumları|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği, denetimin odağa sahip `true`.|  
|Invalidunodaklanmış|Doğrulama durumları|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği, denetimin odağa sahip `true`.|  
  
## <a name="label-controltemplate-example"></a>Label ControlTemplate örneği  
 Aşağıdaki örnek, <xref:System.Windows.Controls.Label> denetimi için <xref:System.Windows.Controls.ControlTemplate> tanımlanacağını gösterir.  
  
 [!code-xaml[ControlTemplateExamples#Label](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/label.xaml#label)]  
  
 <xref:System.Windows.Controls.ControlTemplate> aşağıdaki kaynaklardan bir veya daha fazlasını kullanır.  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 Tüm örnek için bkz. [ControlTemplates Ile stillendirme örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [Denetim Stilleri ve Şablonları](control-styles-and-templates.md)
- [Denetim Özelleştirme](control-customization.md)
- [Stil ve Şablon Oluşturma](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [ControlTemplate Oluşturarak Varolan Denetimin Görünümünü Özelleştirme](customizing-the-appearance-of-an-existing-control.md)
