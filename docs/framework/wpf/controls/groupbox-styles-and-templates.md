---
title: GroupBox Stilleri ve Şablonları
ms.date: 03/30/2017
helpviewer_keywords:
- ControlTemplate [WPF], GroupBox
- parts [WPF], GroupBox
- GroupBox [WPF], styles and templates
- states [WPF], GroupBox
- styles [WPF], GroupBox
- templates [WPF], GroupBox
ms.assetid: 33df7037-0a1b-476f-b9d0-41566a777699
ms.openlocfilehash: 474cda0abc6a18c015836c749c78f4d33aa5abd8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187472"
---
# <a name="groupbox-styles-and-templates"></a>GroupBox Stilleri ve Şablonları
<a name="introduction"></a>Bu <xref:System.Windows.Controls.GroupBox> konu, denetim in stilleri ve şablonlarını açıklar. Denetime benzersiz <xref:System.Windows.Controls.ControlTemplate> bir görünüm kazandırmak için varsayılanı değiştirebilirsiniz. Daha fazla bilgi [için](../../../desktop-wpf/themes/how-to-create-apply-template.md)bkz.  
  
<a name="groupbox_parts"></a>
## <a name="groupbox-parts"></a>GroupBox Parçaları  
 Denetimde <xref:System.Windows.Controls.GroupBox> herhangi bir adlandırılmış parça yok.  
  
<a name="groupbox_states"></a>
## <a name="groupbox-states"></a>GroupBox Durumları  
 Aşağıdaki <xref:System.Windows.Controls.GroupBox> tabloda denetim için görsel durumları listeler.  
  
|VisualState Adı|VisualStateGroup Adı|Açıklama|  
|-|-|-|  
|Geçerli|Doğrulama Durumları|Denetim <xref:System.Windows.Controls.Validation> sınıfı kullanır ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli `false`özellik.|  
|GeçersizOdaklanmış|Doğrulama Durumları|Ekli <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> özellik denetim `true` odak vardır.|  
|Geçersiz Odaklanmış|Doğrulama Durumları|Ekli <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> özellik denetim `true` odak yok olmasıdır.|  
  
<a name="groupbox_controltemplate_example"></a>
## <a name="groupbox-controltemplate-example"></a>GroupBox ControlTemplate Örneği  
 Aşağıdaki örnek, denetim için <xref:System.Windows.Controls.ControlTemplate> a'nın <xref:System.Windows.Controls.GroupBox> nasıl tanımlandığını gösterir.  
  
 [!code-xaml[ControlTemplateExamples#GroupBox](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/groupbox.xaml#groupbox)]  
  
 Aşağıdaki <xref:System.Windows.Controls.ControlTemplate> kaynaklardan birini veya birkaçını kullanır.  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 Tam örnek için [ControlTemplates Örnek ile Şekillendirme'ye](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [Denetim Stilleri ve Şablonları](control-styles-and-templates.md)
- [Denetim Özelleştirme](control-customization.md)
- [Stil ve Şablon Oluşturma](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Denetim için şablon oluşturma](../../../desktop-wpf/themes/how-to-create-apply-template.md)
