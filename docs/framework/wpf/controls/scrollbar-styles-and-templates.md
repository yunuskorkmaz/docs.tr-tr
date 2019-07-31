---
title: ScrollBar Stilleri ve Şablonları
ms.date: 03/30/2017
helpviewer_keywords:
- styles [WPF], ScrollBar
- ControlTemplate [WPF], ScrollBar
- states [WPF], ScrollBar
- ScrollBar [WPF], styles and templates
- templates [WPF], ScrollBar
- parts [WPF], ScrollBar
ms.assetid: 066ea45a-e27d-43b0-adfe-cce6934c22f5
ms.openlocfilehash: 016556fb825ddf60af7dc572d6fda7323b9bb09d
ms.sourcegitcommit: 3eeea78f52ca771087a6736c23f74600cc662658
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/31/2019
ms.locfileid: "68671977"
---
# <a name="scrollbar-styles-and-templates"></a>ScrollBar Stilleri ve Şablonları
Bu konuda, <xref:System.Windows.Controls.Primitives.ScrollBar> denetimin stilleri ve şablonları açıklanmaktadır. Denetim için benzersiz bir görünüm <xref:System.Windows.Controls.ControlTemplate> sağlamak üzere varsayılan ' i değiştirebilirsiniz. Daha fazla bilgi için, bkz. [bir ControlTemplate oluşturarak varolan denetimin görünümünü özelleştirme](customizing-the-appearance-of-an-existing-control.md).  
  
## <a name="scrollbar-parts"></a>Kaydırma çubuğu bölümleri  
 Aşağıdaki tabloda, <xref:System.Windows.Controls.Primitives.ScrollBar> denetimin adlandırılmış parçaları listelenmektedir.  
  
|Bölümüyle|Tür|Açıklama|  
|-|-|-|  
|PART_Track|<xref:System.Windows.Controls.Primitives.Track>|Öğesinin konumunu <xref:System.Windows.Controls.Primitives.ScrollBar>gösteren öğesi için kapsayıcı.|  
  
## <a name="scrollbar-states"></a>Kaydırma çubuğu durumları  
 Aşağıdaki tabloda <xref:System.Windows.Controls.Primitives.ScrollBar> denetim için görsel durumlar listelenmektedir.  
  
|VisualState adı|VisualStateGroup adı|Açıklama|  
|----------------------|---------------------------|-----------------|  
|Normal|Ortak durumlar|Varsayılan durum.|  
|Gelme olayından|Ortak durumlar|Fare işaretçisi denetimin üzerine yerleştirilir.|  
|Devre dışı|Ortak durumlar|Denetim devre dışı bırakıldı.|  
|Geçerli|Doğrulama durumları|Denetim, <xref:System.Windows.Controls.Validation> sınıfını <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ve ekli özelliği `false`kullanır.|  
|Invalidodaklanmış|Doğrulama durumları|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> İliştirilmiş`true` özelliği ve denetim odağa sahiptir.|  
|Invalidunodaklanmış|Doğrulama durumları|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> İliştirilmiş`true` özelliği ve denetim odağa sahip değildir.|  
  
## <a name="scrollbar-controltemplate-example"></a>ScrollBar ControlTemplate örneği  
 Aşağıdaki örnek, <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.Primitives.ScrollBar> denetimi için nasıl tanımlanacağını gösterir.  
  
 [!code-xaml[ControlTemplateExamples#ScrollBar](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/scrollbar.xaml#scrollbar)]  
  
 Yukarıdaki örnekte aşağıdaki kaynaklardan biri veya daha fazlası kullanılmaktadır.  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 Tüm örnek için bkz. [ControlTemplates Ile stillendirme örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [Denetim Stilleri ve Şablonları](control-styles-and-templates.md)
- [Denetim Özelleştirme](control-customization.md)
- [Stil ve Şablon Oluşturma](styling-and-templating.md)
- [ControlTemplate Oluşturarak Varolan Denetimin Görünümünü Özelleştirme](customizing-the-appearance-of-an-existing-control.md)
