---
title: ProgressBar Stilleri ve Şablonları
ms.date: 03/30/2017
helpviewer_keywords:
- parts [WPF], ProgressBar
- ProgressBar [WPF], styles and templates
- styles [WPF], ProgressBar
- ControlTemplate [WPF], ProgressBar
- templates [WPF], ProgressBar
- states [WPF], ProgressBar
ms.assetid: 935aa600-16e6-4947-a905-37a189a583dd
ms.openlocfilehash: 7e410642e6153ed8064b2ddfb38fddd9cce6f4de
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54525386"
---
# <a name="progressbar-styles-and-templates"></a>ProgressBar Stilleri ve Şablonları
Bu konu için şablonları ve stilleri açıklar <xref:System.Windows.Controls.ProgressBar> denetimi. Varsayılan değiştirebileceğiniz <xref:System.Windows.Controls.ControlTemplate> denetim benzersiz bir görünüm sağlamak için. Daha fazla bilgi için [ControlTemplate oluşturarak varolan denetimin görünümünü özelleştirme](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).  
  
## <a name="progressbar-parts"></a>ProgressBar bölümleri  
 Adlandırılmış bölümleri için aşağıdaki tabloda <xref:System.Windows.Controls.ProgressBar> denetimi.  
  
|Bölümü|Tür|Açıklama|  
|-|-|-|  
|PART_Indicator|<xref:System.Windows.FrameworkElement>|İlerleme durumunu gösteren nesne.|  
|PART_Track|<xref:System.Windows.FrameworkElement>|İlerleme göstergesi yolunu tanımlayan nesne.|  
|PART_GlowRect|<xref:System.Windows.FrameworkElement>|İlerleme çubuğu embellishes bir nesne.|  
  
## <a name="progressbar-states"></a>ProgressBar durumları  
 Görsel durumlar için aşağıdaki tabloda <xref:System.Windows.Controls.ProgressBar> denetimi.  
  
|VisualState adı|Visualstategroup'u adı|Açıklama|  
|----------------------|---------------------------|-----------------|  
|Kararlı|CommonStates|<xref:System.Windows.Controls.ProgressBar> göre ilerleme raporlarınızı <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> özelliği.|  
|Belirsiz|CommonStates|<xref:System.Windows.Controls.ProgressBar> Yinelenen bir desen ile genel ilerlemeyi raporlar.|  
|Geçerli|ValidationStates|Denetimi kullanan <xref:System.Windows.Controls.Validation> sınıfı ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği `false`.|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özelliği `true` olan denetim odağa sahip.|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özelliği `true` olan denetim odağa sahip değil.|  
  
## <a name="progressbar-controltemplate-example"></a>ProgressBar ControlTemplate Örneği  
 Aşağıdaki örnek nasıl tanımlanacağını gösterir bir <xref:System.Windows.Controls.ControlTemplate> için <xref:System.Windows.Controls.ProgressBar> denetimi.  
  
 [!code-xaml[ControlTemplateExamples#ProgressBar](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/progressbar.xaml#progressbar)]  
  
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
